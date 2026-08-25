# Project Setup & Structure — Assignments

## Assignment 1 — App Router Project Structure

**Title:** Create and Organize a Next.js App Router Project

**Implementation:**

- Create a new Next.js project with TypeScript, ESLint, App Router, import alias, and `src/` directory enabled
- Inside `src/`, create three folders: `components/`, `lib/`, and `hooks/`
- In `components/`, create a `Navbar` component with three text items: Home, About, and Contact
- In `components/`, create a `Footer` component with a copyright line
- In `lib/`, create a `utils.ts` file and export a `formatDate` function that takes a `Date` and returns it in `DD/MM/YYYY` format
- In `hooks/`, create a `useWindowWidth.ts` file and export a custom hook that returns the current window width
- Import `Navbar` and `Footer` into the root layout so they appear on every page
- Inside `src/app/`, create three routes: `about/`, `services/`, and `contact/` — each returning a heading with that page's name
- Create a `dashboard/` route with its own layout containing a sidebar with the text "Menu", and a page with a "Dashboard" heading
- Show a loading message on the `services/` route while it loads
- Show an error message with a button that retries the render when the `services/` route throws an error
- Show a custom 404 message for URLs that do not exist — navigate to a non-existent URL and confirm it appears
- Add any image renamed to `logo.png` inside `public/` and confirm it is accessible from the browser
- Create a `.env` file with one server-only variable and one browser-exposed variable, then create a `.env.example` with the same keys but empty values
- Start the development server and verify every route works correctly in the browser

---

## Assignment 2 — Pages Router Project Structure

**Title:** Create and Explore a Next.js Pages Router Project

**Implementation:**

- Create a new Next.js project with TypeScript, ESLint, Pages Router, and import alias enabled — without the `src/` directory
- Inside `pages/`, create three route files: `about.tsx`, `services.tsx`, and `contact.tsx` — each returning a heading with that page's name
- Inside `pages/`, create a `products/` folder containing `index.tsx` and `[id].tsx` — each returning a heading with that page's name
- Create a `_app.tsx` file that imports `globals.css` and wraps the application component
- Create a `_document.tsx` file with a basic custom document structure
- Create a `404.tsx` file with a custom not-found message — navigate to a non-existent URL and confirm it appears
- Add any image renamed to `banner.jpg` inside `public/images/` and confirm it is accessible directly by its path in the URL
- Create a `.env` file with one server-only variable and one `NEXT_PUBLIC_` variable, then create a `.env.example` with the same keys but empty values
- Start the development server and verify every route works correctly in the browser
