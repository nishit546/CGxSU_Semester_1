# File Upload with Multer

**Topic:** Uploading files and images with `multer` | **Database:** MongoDB + Mongoose

---

## What Is File Upload?

By default, Express can only handle **JSON data** (`application/json`). When a user sends a file — like a profile photo, a resume, or a document — it arrives in a completely different format called `multipart/form-data`.

Express cannot read this format on its own. That is where **Multer** comes in.

> **Multer** is a middleware that reads `multipart/form-data` requests, processes the file, saves it to your disk, and puts the file information on `req.file` so your controller can use it.

### Why can't we just use `express.json()` for files?

```
JSON body      →  express.json()  →  req.body  
Form data      →  express.json()  →  req.body  (undefined)
File upload    →  express.json()  →  req.file  (undefined)
File upload    →  multer          →  req.file  
```

---

## Folder Structure

```
file-upload-app/
│
├── src/
│   ├── config/
│   │   └── db.js                  ← MongoDB connection
│   │
│   ├── models/
│   │   └── user.model.js          ← User schema with avatar field
│   │
│   ├── controllers/
│   │   └── user.controller.js     ← All upload logic
│   │
│   ├── routes/
│   │   └── user.routes.js         ← Route definitions
│   │
│   ├── middlewares/
│   │   └── upload.js              ← All multer configuration lives here
│   │
│   ├── app.js                     ← Express setup
│   └── index.js                   ← Server start
│
├── uploads/                       ← Uploaded files saved here (create manually)
├── .env
├── .env.example
└── package.json
```

> **Important:** The `uploads/` folder sits at the root of the project — not inside `src/`. Create it manually before running the server:
> ```bash
> mkdir uploads
> ```

---

## Installation

```bash
npm install express mongoose multer dotenv
npm install --save-dev nodemon
```

Add scripts to `package.json`:

```json
"scripts": {
  "start": "node src/index.js",
  "dev":   "nodemon src/index.js"
}
```

---

## Step-by-Step Implementation

---

### Step 1 — `src/config/db.js`

```js
const mongoose = require("mongoose");

const connectDB = async () => {
  try {
    await mongoose.connect(process.env.MONGO_URI);
    console.log("MongoDB connected");
  } catch (error) {
    console.error("MongoDB connection failed:", error.message);
    process.exit(1);
  }
};

module.exports = connectDB;
```

---

### Step 2 — `src/models/user.model.js`

We store only the **filename** in the database — not the file itself. The actual file lives on disk inside the `uploads/` folder.

```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema(
  {
    name:   { type: String, required: [true, "Name is required"] },
    email:  { type: String, required: [true, "Email is required"], unique: true },
    avatar: { type: String, default: null },   // stores filename e.g. "1700000000000.jpg"
  },
  { timestamps: true }
);

module.exports = mongoose.model("User", userSchema);
```

**Why store only the filename?**

| What you store in DB | What you store on disk |
|----------------------|------------------------|
| `"1700000000000.jpg"` | The actual image file |

When you need to display the image, you combine the base URL + filename:
```
http://localhost:5000/uploads/1700000000000.jpg
```

---

### Step 3 — `src/middlewares/upload.js`

This is the most important file in this topic. All Multer configuration lives here.

```js
const multer = require("multer");
const path   = require("path");
const fs     = require("fs");

// ─────────────────────────────────────────────
// 1. ENSURE UPLOADS FOLDER EXISTS
// ─────────────────────────────────────────────
// If the uploads folder doesn't exist, create it automatically
const uploadDir = "uploads/";
if (!fs.existsSync(uploadDir)) {
  fs.mkdirSync(uploadDir, { recursive: true });
}

// ─────────────────────────────────────────────
// 2. DISK STORAGE CONFIGURATION
// ─────────────────────────────────────────────
const storage = multer.diskStorage({

  // destination — which folder to save the file in
  destination: (req, file, cb) => {
    cb(null, "uploads/");
  },

  // filename — what to name the saved file
  // We use timestamp + original extension to make every filename unique
  // e.g. original: "photo.jpg"  →  saved as: "1700000000000.jpg"
  filename: (req, file, cb) => {
    const uniqueName = Date.now() + path.extname(file.originalname);
    cb(null, uniqueName);
  },

});

// ─────────────────────────────────────────────
// 3. FILE FILTER — only accept certain types
// ─────────────────────────────────────────────
const imageFilter = (req, file, cb) => {
  const allowedTypes = ["image/jpeg", "image/jpg", "image/png", "image/gif", "image/webp"];

  if (allowedTypes.includes(file.mimetype)) {
    cb(null, true);    // accept the file
  } else {
    cb(new Error("Only image files are allowed: jpeg, jpg, png, gif, webp"), false); // reject
  }
};

const documentFilter = (req, file, cb) => {
  const allowedTypes = ["application/pdf", "application/msword",
    "application/vnd.openxmlformats-officedocument.wordprocessingml.document"];

  if (allowedTypes.includes(file.mimetype)) {
    cb(null, true);
  } else {
    cb(new Error("Only PDF and Word documents are allowed"), false);
  }
};

// ─────────────────────────────────────────────
// 4. MULTER INSTANCES
// ─────────────────────────────────────────────

// For single image upload (profile avatar, post image etc.)
const uploadImage = multer({
  storage,
  fileFilter: imageFilter,
  limits: {
    fileSize: 2 * 1024 * 1024,   // 2MB max
  },
});

// For single document upload (resume, PDF etc.)
const uploadDocument = multer({
  storage,
  fileFilter: documentFilter,
  limits: {
    fileSize: 5 * 1024 * 1024,   // 5MB max
  },
});

// For multiple image uploads (gallery, product images etc.)
const uploadMultiple = multer({
  storage,
  fileFilter: imageFilter,
  limits: {
    fileSize:  2 * 1024 * 1024,  // 2MB per file
    files:     5,                 // max 5 files at once
  },
});

module.exports = { uploadImage, uploadDocument, uploadMultiple };
```

---

### Step 4 — `src/controllers/user.controller.js`

```js
const User = require("../models/user.model");
const fs   = require("fs");
const path = require("path");

// ─────────────────────────────────────────────
// CREATE USER (no file)
// ─────────────────────────────────────────────
const createUser = async (req, res) => {
  try {
    const { name, email } = req.body;

    if (!name || !email) {
      return res.status(400).json({
        success: false,
        message: "Name and email are required",
        data: null,
      });
    }

    const user = await User.create({ name, email });

    res.status(201).json({
      success: true,
      message: "User created successfully",
      data: user,
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

// ─────────────────────────────────────────────
// GET ALL USERS
// ─────────────────────────────────────────────
const getAllUsers = async (req, res) => {
  try {
    const users = await User.find();

    // Build full avatar URL for each user
    const usersWithUrl = users.map((user) => ({
      _id:       user._id,
      name:      user.name,
      email:     user.email,
      avatarUrl: user.avatar
        ? `${req.protocol}://${req.get("host")}/uploads/${user.avatar}`
        : null,
      createdAt: user.createdAt,
    }));

    res.status(200).json({
      success: true,
      message: "Users fetched successfully",
      count:   users.length,
      data:    usersWithUrl,
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

// ─────────────────────────────────────────────
// GET SINGLE USER
// ─────────────────────────────────────────────
const getUserById = async (req, res) => {
  try {
    const user = await User.findById(req.params.id);

    if (!user) {
      return res.status(404).json({ success: false, message: "User not found", data: null });
    }

    res.status(200).json({
      success: true,
      message: "User fetched successfully",
      data: {
        _id:       user._id,
        name:      user.name,
        email:     user.email,
        avatarUrl: user.avatar
          ? `${req.protocol}://${req.get("host")}/uploads/${user.avatar}`
          : null,
        createdAt: user.createdAt,
      },
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

// ─────────────────────────────────────────────
// UPLOAD AVATAR — single image for a user
// ─────────────────────────────────────────────
const uploadAvatar = async (req, res) => {
  try {
    // req.file is set by multer middleware before this runs
    if (!req.file) {
      return res.status(400).json({
        success: false,
        message: "No file uploaded",
        data: null,
      });
    }

    const user = await User.findById(req.params.id);

    if (!user) {
      // File was saved to disk but user doesn't exist
      // Delete the orphaned file
      fs.unlinkSync(req.file.path);
      return res.status(404).json({ success: false, message: "User not found", data: null });
    }

    // If user already has an avatar, delete the old file from disk
    if (user.avatar) {
      const oldFilePath = path.join("uploads", user.avatar);
      if (fs.existsSync(oldFilePath)) {
        fs.unlinkSync(oldFilePath);
      }
    }

    // Save the new filename to DB
    user.avatar = req.file.filename;
    await user.save();

    res.status(200).json({
      success: true,
      message: "Avatar uploaded successfully",
      data: {
        _id:       user._id,
        name:      user.name,
        email:     user.email,
        avatarUrl: `${req.protocol}://${req.get("host")}/uploads/${user.avatar}`,
      },
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

// ─────────────────────────────────────────────
// DELETE AVATAR — remove from disk + clear DB field
// ─────────────────────────────────────────────
const deleteAvatar = async (req, res) => {
  try {
    const user = await User.findById(req.params.id);

    if (!user) {
      return res.status(404).json({ success: false, message: "User not found", data: null });
    }

    if (!user.avatar) {
      return res.status(400).json({
        success: false,
        message: "This user has no avatar to delete",
        data: null,
      });
    }

    // Delete file from disk
    const filePath = path.join("uploads", user.avatar);
    if (fs.existsSync(filePath)) {
      fs.unlinkSync(filePath);
    }

    // Clear the field in DB
    user.avatar = null;
    await user.save();

    res.status(200).json({
      success: true,
      message: "Avatar deleted successfully",
      data: null,
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

// ─────────────────────────────────────────────
// UPLOAD MULTIPLE IMAGES
// ─────────────────────────────────────────────
const uploadMultipleImages = async (req, res) => {
  try {
    if (!req.files || req.files.length === 0) {
      return res.status(400).json({
        success: false,
        message: "No files uploaded",
        data: null,
      });
    }

    const fileDetails = req.files.map((file) => ({
      originalName: file.originalname,
      savedAs:      file.filename,
      size:         `${(file.size / 1024).toFixed(2)} KB`,
      url:          `${req.protocol}://${req.get("host")}/uploads/${file.filename}`,
    }));

    res.status(200).json({
      success: true,
      message: `${req.files.length} files uploaded successfully`,
      count:   req.files.length,
      data:    fileDetails,
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

// ─────────────────────────────────────────────
// SEED — create test users
// ─────────────────────────────────────────────
const seedUsers = async (req, res) => {
  try {
    await User.deleteMany({});
    const users = await User.insertMany([
      { name: "Rahul Sharma",  email: "rahul@example.com"  },
      { name: "Ayesha Khan",   email: "ayesha@example.com" },
      { name: "Priya Patel",   email: "priya@example.com"  },
    ]);
    res.status(201).json({
      success: true,
      message: "3 test users created",
      data: users,
    });
  } catch (error) {
    res.status(500).json({ success: false, message: error.message, data: null });
  }
};

module.exports = {
  createUser,
  getAllUsers,
  getUserById,
  uploadAvatar,
  deleteAvatar,
  uploadMultipleImages,
  seedUsers,
};
```

---

### Step 5 — `src/routes/user.routes.js`

```js
const express  = require("express");
const router   = express.Router();
const { uploadImage, uploadMultiple } = require("../middlewares/upload");
const {
  createUser,
  getAllUsers,
  getUserById,
  uploadAvatar,
  deleteAvatar,
  uploadMultipleImages,
  seedUsers,
} = require("../controllers/user.controller");

// ── Seed
router.get("/seed", seedUsers);

// ── Basic CRUD
router.post(  "/",    createUser);
router.get(   "/",    getAllUsers);
router.get(   "/:id", getUserById);

// ── File upload routes
// uploadImage.single("avatar") runs BEFORE uploadAvatar controller
router.post(  "/:id/avatar", uploadImage.single("avatar"),      uploadAvatar);
router.delete("/:id/avatar",                                    deleteAvatar);

// Multiple files — field name "images", max 5
router.post("/upload/multiple", uploadMultiple.array("images", 5), uploadMultipleImages);

module.exports = router;
```

---

### Step 6 — `src/app.js`

```js
const express = require("express");
const path    = require("path");

const userRoutes = require("./routes/user.routes");

const app = express();

// Body parsing
app.use(express.json());

// Serve the uploads folder as static files
// Files at uploads/photo.jpg are accessible at /uploads/photo.jpg
app.use("/uploads", express.static(path.join(__dirname, "..", "uploads")));

// Routes
app.use("/api/users", userRoutes);

// 404 handler
app.use((req, res) => {
  res.status(404).json({ success: false, message: "Route not found", data: null });
});

// Multer error handler + global error handler
app.use((err, req, res, next) => {
  const multer = require("multer");

  if (err instanceof multer.MulterError) {
    // Multer-specific errors
    if (err.code === "LIMIT_FILE_SIZE") {
      return res.status(400).json({
        success: false,
        message: "File too large. Check the size limit for this upload.",
        data: null,
      });
    }
    if (err.code === "LIMIT_FILE_COUNT") {
      return res.status(400).json({
        success: false,
        message: "Too many files. Maximum allowed is 5.",
        data: null,
      });
    }
    if (err.code === "LIMIT_UNEXPECTED_FILE") {
      return res.status(400).json({
        success: false,
        message: `Unexpected field name. Use the correct field name in your form.`,
        data: null,
      });
    }
  }

  // General errors (including fileFilter rejections)
  res.status(err.status || 500).json({
    success: false,
    message: err.message || "Internal Server Error",
    data: null,
  });
});

module.exports = app;
```

---

### Step 7 — `src/index.js`

```js
require("dotenv").config();
const app       = require("./app");
const connectDB = require("./config/db");

const PORT = process.env.PORT || 5000;

connectDB().then(() => {
  app.listen(PORT, () => {
    console.log(`Server running at http://localhost:${PORT}`);
  });
});
```

---

### Step 8 — `.env`

```
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/file-upload-db
PORT=5000
```

---

## All API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/users/seed` | Create 3 test users |
| `POST` | `/api/users` | Create a user (JSON body) |
| `GET` | `/api/users` | Get all users with avatar URLs |
| `GET` | `/api/users/:id` | Get a single user |
| `POST` | `/api/users/:id/avatar` | Upload/replace avatar image |
| `DELETE` | `/api/users/:id/avatar` | Remove avatar from disk + DB |
| `POST` | `/api/users/upload/multiple` | Upload up to 5 images at once |

---

## Deep Dive — Multer Configuration

### `multer.diskStorage()` — how it works

```js
const storage = multer.diskStorage({

  destination: (req, file, cb) => {
    // req  → the Express request object
    // file → info about the incoming file (name, type, size)
    // cb   → callback — call it with (error, folderPath)
    cb(null, "uploads/");
  },

  filename: (req, file, cb) => {
    // file.originalname → "my photo.jpg"
    // path.extname()    → ".jpg"
    // Date.now()        → 1700000000000  (milliseconds since 1970)
    const uniqueName = Date.now() + path.extname(file.originalname);
    // Result: "1700000000000.jpg"
    cb(null, uniqueName);
  },

});
```

**Why use `Date.now()` for the filename?**

If two users both upload `photo.jpg`, without renaming, the second file would overwrite the first. `Date.now()` guarantees every filename is unique.

---

### The `file` Object Inside Multer Callbacks

When multer processes a file, it creates a `file` object with these properties:

| Property | Example Value | Description |
|----------|---------------|-------------|
| `file.fieldname` | `"avatar"` | The form field name used in the request |
| `file.originalname` | `"profile.jpg"` | Original filename from the user's device |
| `file.mimetype` | `"image/jpeg"` | MIME type of the file |
| `file.size` | `204800` | File size in bytes |
| `file.filename` | `"1700000000000.jpg"` | Saved filename (set in `filename` config) |
| `file.path` | `"uploads/1700000000000.jpg"` | Full path where file was saved |

---

### `req.file` vs `req.files`

| Method | When to use | Populated on |
|--------|-------------|-------------|
| `upload.single("fieldname")` | One file | `req.file` |
| `upload.array("fieldname", max)` | Multiple files, same field | `req.files` (array) |
| `upload.fields([...])` | Multiple files, different fields | `req.files` (object) |

```js
// single — one file
router.post("/avatar", upload.single("avatar"), (req, res) => {
  console.log(req.file);   // object
});

// array — multiple files from same field
router.post("/gallery", upload.array("images", 5), (req, res) => {
  console.log(req.files);  // array of file objects
});

// fields — files from different fields in the same form
router.post("/profile", upload.fields([
  { name: "avatar",   maxCount: 1 },
  { name: "document", maxCount: 1 },
]), (req, res) => {
  console.log(req.files.avatar[0]);    // first avatar file
  console.log(req.files.document[0]); // first document file
});
```

---

### fileFilter — Accept or Reject Files

```js
const fileFilter = (req, file, cb) => {
  // cb(null, true)               → accept the file
  // cb(null, false)              → silently reject, no error
  // cb(new Error("reason"), false) → reject with error message

  const allowedTypes = ["image/jpeg", "image/png", "image/webp"];

  if (allowedTypes.includes(file.mimetype)) {
    cb(null, true);
  } else {
    cb(new Error("Only JPEG, PNG and WebP images are allowed"), false);
  }
};
```

---

### Multer Error Codes

When multer rejects a file, it throws a `MulterError` with a `code` property:

| Code | What happened |
|------|---------------|
| `LIMIT_FILE_SIZE` | File exceeds `limits.fileSize` |
| `LIMIT_FILE_COUNT` | More files sent than `limits.files` allows |
| `LIMIT_FIELD_KEY` | Field name too long |
| `LIMIT_UNEXPECTED_FILE` | Field name does not match what `upload.single()` or `upload.array()` expects |

Catch these in the error handler in `app.js`:

```js
app.use((err, req, res, next) => {
  if (err instanceof multer.MulterError) {
    if (err.code === "LIMIT_FILE_SIZE") { ... }
    if (err.code === "LIMIT_FILE_COUNT") { ... }
    if (err.code === "LIMIT_UNEXPECTED_FILE") { ... }
  }
});
```

---

### memoryStorage vs diskStorage

| | `diskStorage` | `memoryStorage` |
|-|---------------|-----------------|
| **Saves to** | Disk (`uploads/` folder) | RAM (memory buffer) |
| **Access via** | `req.file.path` | `req.file.buffer` |
| **Use when** | Saving files locally | Uploading to cloud (S3, Cloudinary) |
| **Risk** | Disk space | Memory overflow on large files |

```js
// memoryStorage — file is in RAM as a Buffer, not saved to disk
const storage = multer.memoryStorage();

const upload = multer({ storage });

router.post("/upload", upload.single("image"), (req, res) => {
  console.log(req.file.buffer); // raw file bytes — useful for cloud upload
});
```

---

## How to Test in Postman

File uploads **cannot** be tested with a JSON body. You must use **form-data**.

### Test 1 — Create a test user first
```
GET http://localhost:5000/api/users/seed
```
Copy one of the `_id` values from the response.

---

### Test 2 — Upload an avatar
```
POST http://localhost:5000/api/users/PASTE_ID_HERE/avatar
```
In Postman:
- Go to **Body** tab
- Select **form-data**
- Add a row: Key = `avatar`, change type dropdown from **Text** to **File**
- Click **Select Files** and pick an image from your computer
- Send

---

### Test 3 — Upload multiple images
```
POST http://localhost:5000/api/users/upload/multiple
```
In Postman:
- Body → form-data
- Add multiple rows — all with Key = `images`, type = **File**
- Select a different image for each row
- Send

---

### Test 4 — View uploaded image in browser
```
GET http://localhost:5000/uploads/PASTE_FILENAME_HERE.jpg
```

---

### Test 5 — Delete avatar
```
DELETE http://localhost:5000/api/users/PASTE_ID_HERE/avatar
```

---

## What `req.file` Contains After Upload

```js
{
  fieldname:    "avatar",
  originalname: "profile.jpg",
  encoding:     "7bit",
  mimetype:     "image/jpeg",
  destination:  "uploads/",
  filename:     "1700000000000.jpg",
  path:         "uploads/1700000000000.jpg",
  size:         204800                        // bytes
}
```

---

## Common Mistakes

| Mistake | What happens | Fix |
|---------|-------------|-----|
| Forgetting `upload.single()` on the route | `req.file` is `undefined` | Always add multer middleware before the controller |
| Using JSON body in Postman | `req.file` is `undefined` | Switch to `form-data` in Postman |
| Not checking `req.file` before using it | `Cannot read properties of undefined` | Always check `if (!req.file)` first |
| Not deleting old file when replacing avatar | Orphaned files pile up on disk | Use `fs.unlinkSync()` to delete the old file first |
| Not handling `MulterError` separately | Generic 500 error instead of clear message | Add `if (err instanceof multer.MulterError)` in error handler |
| Hardcoding `http://localhost:3000` in URLs | URL breaks in production | Use `req.protocol + "://" + req.get("host")` |

---

## Status Codes Reference

| Code | When |
|------|------|
| `200` | File uploaded / deleted successfully |
| `201` | User created |
| `400` | No file sent / wrong file type / file too large / wrong field name |
| `404` | User not found |
| `500` | Server or database error |

---

## What You Learned

- Why `multipart/form-data` is needed for file uploads and why JSON cannot handle it
- How `multer.diskStorage()` configures destination and filename
- What properties the `file` object has inside multer callbacks
- How `fileFilter` accepts or rejects files by MIME type
- The difference between `upload.single()`, `upload.array()`, and `upload.fields()`
- What `req.file` and `req.files` contain after a successful upload
- How to serve uploaded files as static assets using `express.static()`
- How to delete old files from disk when replacing an avatar
- How to catch and handle `MulterError` codes cleanly
- The difference between `diskStorage` and `memoryStorage`
