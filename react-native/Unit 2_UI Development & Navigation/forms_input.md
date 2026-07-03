
# React Native – Forms & User Input

Forms are one of the most important parts of any mobile application. This module teaches you how to collect, validate, and handle user input professionally.

---

## What are Forms in React Native?

Forms allow users to interact with your app by entering data — such as logging in, signing up, searching, submitting feedback, or making payments.

In React Native, forms are built using components like `TextInput`, `Switch`, `Picker`, and others, combined with state management and validation logic.

Good form design leads to:
- Better user experience
- Higher conversion rates
- Fewer errors
- Professional app feel

---


### Key Components 

| Component         | Purpose |
|-------------------|--------|
| `TextInput`       | Main input field for text, email, password, number |
| `KeyboardAvoidingView` | Prevent keyboard from covering inputs |
| `TouchableOpacity` / `Pressable` | Submit buttons |
| `ActivityIndicator` | Show loading during form submission |

---

### Basic Form Structure (Preview)

```jsx
import React, { useState } from 'react';
import { View, TextInput, TouchableOpacity, Text, StyleSheet } from 'react-native';

const LoginScreen = () => {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  const handleLogin = () => {
    // Handle form submission
    console.log('Email:', email, 'Password:', password);
  };

  return (
    <View style={styles.container}>
      <TextInput
        style={styles.input}
        placeholder="Email"
        value={email}
        onChangeText={setEmail}
        keyboardType="email-address"
      />
      <TextInput
        style={styles.input}
        placeholder="Password"
        value={password}
        onChangeText={setPassword}
        secureTextEntry
      />
      <TouchableOpacity style={styles.button} onPress={handleLogin}>
        <Text style={styles.buttonText}>Login</Text>
      </TouchableOpacity>
    </View>
  );
};

export default LoginScreen;
```

---

## 1. User Input

**Description**: `TextInput` is the primary component for collecting text input from users in React Native. It is similar to the `<input>` element in web development and is used for forms, search bars, login screens, etc.

### **What is User Input?**
`TextInput` allows users to enter and edit text. It supports various input types such as plain text, email, password, numbers, and more. You can control its behavior with props like `keyboardType`, `secureTextEntry`, `placeholder`, `value`, and `onChangeText`.

It is the main component for handling:
- Name, Email, Password
- Phone number
- Search queries
- OTP codes
- Comments / Feedback

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import { View, TextInput, Text, StyleSheet, Button } from 'react-native';

const App = () => {
  const [text, setText] = useState('');

  return (
    <View style={styles.container}>
      <Text style={styles.label}>Enter your name:</Text>
      <TextInput
        style={styles.input}
        placeholder="Type here..."
        value={text}
        onChangeText={setText}
      />
      <Text style={styles.output}>You typed: {text}</Text>
      <Button title="Submit" onPress={() => alert(`Submitted: ${text}`)} />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    justifyContent: 'center',
  },
  label: {
    fontSize: 16,
    marginBottom: 8,
  },
  input: {
    height: 50,
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 8,
    paddingHorizontal: 12,
    fontSize: 16,
    marginBottom: 12,
  },
  output: {
    marginTop: 10,
    fontSize: 16,
    color: '#333',
  },
});

export default App;
```

---

### **Important Props**
| Prop                  | What it does                                      | Common Values                          |
|-----------------------|---------------------------------------------------|----------------------------------------|
| `value`               | Controlled input value                            | `string`                               |
| `onChangeText`        | Callback when text changes                        | `(text) => {}`                         |
| `placeholder`         | Hint text when input is empty                     | `string`                               |
| `keyboardType`        | Type of keyboard to show                          | `'default'`, `'email-address'`, `'numeric'`, `'phone-pad'` |
| `secureTextEntry`     | Hides input (for passwords)                       | `true` / `false`                       |
| `autoCapitalize`      | Capitalization behavior                           | `'none'`, `'sentences'`, `'words'`     |
| `maxLength`           | Maximum characters allowed                        | `number`                               |
| `editable`            | Whether user can edit the input                   | `true` / `false`                       |
| `multiline`           | Allows multiple lines                             | `true` / `false`                       |

---

### **More Examples**

#### **1. Basic TextInput**
```jsx
<TextInput
  style={styles.input}
  placeholder="Enter text here"
/>
```

#### **2. Password Input**
```jsx
<TextInput
  style={styles.input}
  placeholder="Password"
  secureTextEntry={true}
/>
```

#### **3. Email Input with Custom Keyboard**
```jsx
<TextInput
  style={styles.input}
  placeholder="your@email.com"
  keyboardType="email-address"
  autoCapitalize="none"
/>
```

#### **4. Multiline TextInput (Comments)**
```jsx
<TextInput
  style={[styles.input, { height: 100 }]}
  placeholder="Write your feedback..."
  multiline={true}
  numberOfLines={4}
/>
```

#### **5. Controlled Input with State**
```jsx
const [email, setEmail] = useState('');

<TextInput
  value={email}
  onChangeText={setEmail}
  keyboardType="email-address"
/>
```

**Style for Input (Common Pattern):**
```jsx
input: {
  height: 50,
  borderWidth: 1,
  borderColor: '#ddd',
  borderRadius: 8,
  paddingHorizontal: 15,
  fontSize: 16,
  backgroundColor: '#fff',
},
```

## 2. TextInput Component

**Description**: The `TextInput` component is used to take input from the user via the keyboard. It is the primary way to collect text data such as names, emails, passwords, search queries, and more in React Native.

### **What is TextInput?**
`TextInput` is React Native’s core component for user text input. It supports single-line and multi-line inputs, different keyboard types, password masking, placeholders, and controlled/uncontrolled usage.

It is essential for building forms, login screens, search bars, OTP verification, and comment sections.

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import { View, TextInput, Text, StyleSheet } from 'react-native';

const App = () => {
  const [name, setName] = useState('');

  return (
    <View style={styles.container}>
      <Text style={styles.label}>Enter your name:</Text>
      <TextInput
        style={styles.input}
        placeholder="Enter your name"
        value={name}
        onChangeText={setName}
      />
      <Text style={styles.output}>Hello, {name || 'there'}!</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    justifyContent: 'center',
  },
  label: {
    fontSize: 16,
    marginBottom: 8,
  },
  input: {
    height: 50,
    borderWidth: 1,
    borderColor: '#ccc',
    borderRadius: 8,
    paddingHorizontal: 12,
    fontSize: 16,
    backgroundColor: '#fff',
  },
  output: {
    marginTop: 12,
    fontSize: 16,
    color: '#333',
  },
});

export default App;
```

---

### **Important Props**
| Prop                | Description                                      | Common Values                          |
|---------------------|--------------------------------------------------|----------------------------------------|
| `placeholder`       | Hint text when input is empty                    | `"Enter email"`                        |
| `value`             | Current value (Controlled Input)                 | `email` (string)                       |
| `onChangeText`      | Called when text changes                         | `setEmail`                             |
| `keyboardType`      | Type of keyboard to show                         | `"email-address"`, `"numeric"`, `"phone-pad"` |
| `secureTextEntry`   | Hides characters (for password)                  | `true` / `false`                       |
| `maxLength`         | Maximum characters allowed                       | `6` (for OTP)                          |
| `multiline`         | Allows multiple lines                            | `true` / `false`                       |
| `autoFocus`         | Focus automatically when screen loads            | `true` / `false`                       |
| `editable`          | Disable input                                    | `true` / `false`                       |
| `autoCapitalize`    | Controls capitalization                         | `"none"`, `"sentences"`, `"words"`     |

---

### **More Examples**

#### **1. Basic TextInput**
```jsx
<TextInput
  placeholder="Enter your name"
  style={styles.input}
/>
```

#### **2. Password Input**
```jsx
<TextInput
  placeholder="Password"
  secureTextEntry={true}
  style={styles.input}
/>
```

#### **3. Email Input**
```jsx
<TextInput
  placeholder="your@email.com"
  keyboardType="email-address"
  autoCapitalize="none"
  style={styles.input}
/>
```

#### **4. Multiline Input (Feedback)**
```jsx
<TextInput
  style={[styles.input, { height: 100 }]}
  placeholder="Write your feedback here..."
  multiline={true}
  numberOfLines={4}
/>
```

#### **5. Controlled Input (Recommended)**
```jsx
const [name, setName] = useState('');

<TextInput
  value={name}
  onChangeText={setName}
  placeholder="Your full name"
  style={styles.input}
/>
```

**Common Input Style:**
```jsx
input: {
  height: 50,
  borderWidth: 1,
  borderColor: '#ccc',
  borderRadius: 8,
  paddingHorizontal: 12,
  fontSize: 16,
},
```

---

## 3. Keyboard Handling

**Description**: Keyboard handling is essential in React Native when building forms. When the keyboard appears, it can cover input fields, making it difficult for users to see what they are typing. Proper keyboard handling improves UX significantly.

### **What is Keyboard Handling?**
React Native provides built-in tools to manage the keyboard:

- **`KeyboardAvoidingView`** – Automatically adjusts the screen when the keyboard opens.
- **`Keyboard.dismiss()`** – Hides the keyboard when tapping outside inputs.
- **`TouchableWithoutFeedback`** – Wraps content to detect taps outside fields.

These tools are commonly used together in login, signup, and form screens.

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  KeyboardAvoidingView,
  TouchableWithoutFeedback,
  Keyboard,
  Platform,
  Button,
} from 'react-native';

const App = () => {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');

  return (
    <TouchableWithoutFeedback onPress={Keyboard.dismiss}>
      <KeyboardAvoidingView
        behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
        style={styles.container}
      >
        <View style={styles.form}>
          <Text style={styles.title}>Login</Text>

          <Text style={styles.label}>Email</Text>
          <TextInput
            style={styles.input}
            placeholder="Enter your email"
            keyboardType="email-address"
            value={email}
            onChangeText={setEmail}
            autoCapitalize="none"
          />

          <Text style={styles.label}>Password</Text>
          <TextInput
            style={styles.input}
            placeholder="Enter your password"
            secureTextEntry
            value={password}
            onChangeText={setPassword}
          />

          <Button title="Login" onPress={() => alert('Login Pressed')} />
        </View>
      </KeyboardAvoidingView>
    </TouchableWithoutFeedback>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
  },
  form: {
    flex: 1,
    justifyContent: 'center',
    paddingHorizontal: 20,
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 40,
  },
  label: {
    fontSize: 16,
    marginBottom: 8,
    fontWeight: '500',
  },
  input: {
    height: 50,
    borderWidth: 1,
    borderColor: '#ddd',
    borderRadius: 8,
    paddingHorizontal: 12,
    fontSize: 16,
    marginBottom: 20,
    backgroundColor: '#fff',
  },
});

export default App;
```

---

### **Important Components & Props**

| Component / Prop              | What it does                                      | Common Values                          |
|-------------------------------|---------------------------------------------------|----------------------------------------|
| `KeyboardAvoidingView`        | Adjusts layout when keyboard appears              | `behavior`, `style`                    |
| `behavior`                    | Platform-specific behavior                        | `'padding'`, `'height'`, `'position'`  |
| `TouchableWithoutFeedback`    | Dismisses keyboard on tap outside                 | `onPress={Keyboard.dismiss}`          |
| `Keyboard.dismiss()`          | Programmatically hide keyboard                    | Function call                          |
| `enabled`                     | Enable/disable KeyboardAvoidingView               | `true` / `false`                       |
| `keyboardVerticalOffset`      | Extra offset for iOS (status bar, header, etc.)   | `number` (e.g. 0, 20, 100)             |

---

### **More Examples**

#### **1. KeyboardAvoidingView (Basic)**
```jsx
<KeyboardAvoidingView
  behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
  style={{ flex: 1 }}
>
  {/* Form Content */}
</KeyboardAvoidingView>
```

#### **2. Dismiss Keyboard on Outside Tap**
```jsx
<TouchableWithoutFeedback onPress={Keyboard.dismiss}>
  <View style={{ flex: 1 }}>
    {/* All form fields */}
  </View>
</TouchableWithoutFeedback>
```

#### **3. With ScrollView (Recommended for long forms)**
```jsx
<KeyboardAvoidingView behavior="padding" style={{ flex: 1 }}>
  <ScrollView>
    {/* Multiple TextInputs */}
  </ScrollView>
</KeyboardAvoidingView>
```

#### **4. Custom Offset for iOS**
```jsx
<KeyboardAvoidingView
  behavior="padding"
  keyboardVerticalOffset={Platform.OS === 'ios' ? 64 : 0}
  style={{ flex: 1 }}
>
```

#### **5. Programmatic Dismiss**
```jsx
const dismissKeyboard = () => Keyboard.dismiss();

// Use in onSubmit or button press
<Button title="Submit" onPress={dismissKeyboard} />
```

**Common Pattern (Recommended Wrapper):**
```jsx
<TouchableWithoutFeedback onPress={Keyboard.dismiss}>
  <KeyboardAvoidingView
    behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
    style={{ flex: 1 }}
  >
    {/* Content */}
  </KeyboardAvoidingView>
</TouchableWithoutFeedback>
```

---

## 4. Search Bar

**Description**: A Search Bar is one of the most common UI elements in mobile apps. It allows users to search through lists, products, users, or content. In React Native, it is typically built using `TextInput` with additional features like clear button, debounce, and loading state.

### **What is a Search Bar?**
A well-designed search bar provides instant feedback, filters data in real-time, and improves user experience. It usually includes:
- Placeholder text
- Controlled input
- Clear button (`X`)
- Search icon
- Debounced search (to reduce API calls)

It is commonly used with `FlatList`, `SectionList`, or API-driven results.

---

### **Basic Complete Example**
```jsx
import React, { useState, useEffect } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  FlatList,
  TouchableOpacity,
  ActivityIndicator,
} from 'react-native';
import { Ionicons } from '@expo/vector-icons'; // or react-native-vector-icons

const App = () => {
  const [searchQuery, setSearchQuery] = useState('');
  const [filteredData, setFilteredData] = useState([]);
  const [loading, setLoading] = useState(false);

  const data = [
    'Apple', 'Banana', 'Cherry', 'Date', 'Elderberry',
    'Fig', 'Grape', 'Honeydew', 'Kiwi', 'Lemon'
  ];

  // Debounced Search
  useEffect(() => {
    if (searchQuery.trim() === '') {
      setFilteredData(data);
      return;
    }

    setLoading(true);
    const timeoutId = setTimeout(() => {
      const results = data.filter(item =>
        item.toLowerCase().includes(searchQuery.toLowerCase())
      );
      setFilteredData(results);
      setLoading(false);
    }, 300);

    return () => clearTimeout(timeoutId);
  }, [searchQuery]);

  const clearSearch = () => {
    setSearchQuery('');
  };

  return (
    <View style={styles.container}>
      <View style={styles.searchContainer}>
        <Ionicons name="search" size={20} color="#888" style={styles.searchIcon} />
        
        <TextInput
          style={styles.searchBar}
          placeholder="Search fruits..."
          value={searchQuery}
          onChangeText={setSearchQuery}
          autoCapitalize="none"
          clearButtonMode="while-editing" // iOS only
        />

        {searchQuery.length > 0 && (
          <TouchableOpacity onPress={clearSearch} style={styles.clearButton}>
            <Ionicons name="close-circle" size={20} color="#888" />
          </TouchableOpacity>
        )}
      </View>

      {loading ? (
        <ActivityIndicator size="large" color="#007AFF" style={styles.loader} />
      ) : (
        <FlatList
          data={filteredData}
          keyExtractor={(item, index) => index.toString()}
          renderItem={({ item }) => (
            <View style={styles.item}>
              <Text style={styles.itemText}>{item}</Text>
            </View>
          )}
        />
      )}
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
    paddingTop: 50,
  },
  searchContainer: {
    flexDirection: 'row',
    alignItems: 'center',
    backgroundColor: '#fff',
    borderRadius: 12,
    marginHorizontal: 16,
    marginBottom: 16,
    paddingHorizontal: 12,
    borderWidth: 1,
    borderColor: '#ddd',
  },
  searchIcon: {
    marginRight: 8,
  },
  searchBar: {
    flex: 1,
    height: 50,
    fontSize: 16,
  },
  clearButton: {
    padding: 8,
  },
  item: {
    padding: 16,
    borderBottomWidth: 1,
    borderBottomColor: '#eee',
    backgroundColor: '#fff',
  },
  itemText: {
    fontSize: 16,
  },
  loader: {
    marginTop: 50,
  },
});

export default App;
```

---

### **Important Props & Techniques**

| Feature                    | What it does                              | Common Values / Usage                  |
|---------------------------|-------------------------------------------|----------------------------------------|
| `value`                   | Controlled search text                    | `searchQuery`                          |
| `onChangeText`            | Update search state                       | `setSearchQuery`                       |
| `placeholder`             | Hint text                                 | `"Search products..."`                 |
| `clearButtonMode`         | iOS native clear button                   | `"while-editing"`, `"always"`          |
| `debounce`                | Delay search to reduce API calls          | `useEffect` + `setTimeout` (300ms)     |
| `autoCapitalize`          | Disable auto-capitalization               | `"none"`                               |
| `returnKeyType`           | Keyboard "Search" button                  | `"search"`                             |

---

### **More Examples**

#### **1. Simple Search Bar**
```jsx
<TextInput
  style={styles.searchBar}
  placeholder="Search..."
  value={searchQuery}
  onChangeText={setSearchQuery}
/>
```

#### **2. Search with Icon**
```jsx
<View style={styles.searchContainer}>
  <Ionicons name="search" size={20} color="#888" />
  <TextInput style={styles.searchInput} placeholder="Search" />
</View>
```

#### **3. With Clear Button**
```jsx
{searchQuery.length > 0 && (
  <TouchableOpacity onPress={() => setSearchQuery('')}>
    <Ionicons name="close-circle" size={22} color="#999" />
  </TouchableOpacity>
)}
```

#### **4. Search in Header (Common Pattern)**
```jsx
<View style={styles.header}>
  <TextInput
    style={styles.headerSearch}
    placeholder="Search"
    value={searchQuery}
    onChangeText={setSearchQuery}
  />
</View>
```

#### **5. Debounced Search Function**
```jsx
const debouncedSearch = useCallback(
  debounce((query) => {
    // API call here
  }, 400),
  []
);
```

**Common Search Bar Style:**
```jsx
searchContainer: {
  flexDirection: 'row',
  alignItems: 'center',
  backgroundColor: '#f1f1f1',
  borderRadius: 12,
  margin: 16,
  paddingHorizontal: 12,
},
searchBar: {
  flex: 1,
  height: 48,
  fontSize: 16,
  paddingVertical: 8,
},
```

---

## 5. Login Form Example

**Description**: The Login Form is one of the most common screens in mobile applications. It typically includes email/username, password fields, a login button, loading state, and basic validation.

### **What is a Login Form?**
A well-built login screen provides a smooth user experience with proper keyboard handling, input validation, loading indicators, and error feedback. It usually combines `TextInput`, `Pressable`/`TouchableOpacity`, `KeyboardAvoidingView`, and state management.

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  Pressable,
  Alert,
  KeyboardAvoidingView,
  TouchableWithoutFeedback,
  Keyboard,
  Platform,
  ActivityIndicator,
} from 'react-native';

const LoginScreen = () => {
  const [email, setEmail] = useState('');
  const [password, setPassword] = useState('');
  const [loading, setLoading] = useState(false);

  const handleLogin = () => {
    if (!email || !password) {
      Alert.alert('Error', 'Please fill in all fields');
      return;
    }

    if (!email.includes('@')) {
      Alert.alert('Error', 'Please enter a valid email');
      return;
    }

    setLoading(true);

    // Simulate API call
    setTimeout(() => {
      setLoading(false);
      Alert.alert('Success', 'Logged in successfully! ');
      // Usually navigate to Home screen here
    }, 1500);
  };

  return (
    <TouchableWithoutFeedback onPress={Keyboard.dismiss}>
      <KeyboardAvoidingView
        behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
        style={styles.container}
      >
        <View style={styles.formContainer}>
          <Text style={styles.title}>Welcome Back</Text>
          <Text style={styles.subtitle}>Sign in to continue</Text>

          <TextInput
            style={styles.input}
            placeholder="Email Address"
            value={email}
            onChangeText={setEmail}
            keyboardType="email-address"
            autoCapitalize="none"
            autoCorrect={false}
          />

          <TextInput
            style={styles.input}
            placeholder="Password"
            value={password}
            onChangeText={setPassword}
            secureTextEntry
          />

          <Pressable
            style={[styles.button, loading && styles.buttonDisabled]}
            onPress={handleLogin}
            disabled={loading}
          >
            {loading ? (
              <ActivityIndicator color="#fff" />
            ) : (
              <Text style={styles.buttonText}>Login</Text>
            )}
          </Pressable>

          <Text style={styles.forgotPassword}>Forgot Password?</Text>
        </View>
      </KeyboardAvoidingView>
    </TouchableWithoutFeedback>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
  },
  formContainer: {
    flex: 1,
    justifyContent: 'center',
    paddingHorizontal: 24,
  },
  title: {
    fontSize: 32,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 8,
  },
  subtitle: {
    fontSize: 16,
    color: '#666',
    textAlign: 'center',
    marginBottom: 40,
  },
  input: {
    height: 52,
    backgroundColor: '#fff',
    borderRadius: 12,
    paddingHorizontal: 16,
    fontSize: 16,
    marginBottom: 16,
    borderWidth: 1,
    borderColor: '#e0e0e0',
  },
  button: {
    backgroundColor: '#007AFF',
    height: 52,
    borderRadius: 12,
    justifyContent: 'center',
    alignItems: 'center',
    marginTop: 16,
  },
  buttonDisabled: {
    backgroundColor: '#80bfff',
  },
  buttonText: {
    color: '#fff',
    fontSize: 17,
    fontWeight: '600',
  },
  forgotPassword: {
    textAlign: 'center',
    marginTop: 24,
    color: '#007AFF',
    fontSize: 15,
  },
});

export default LoginScreen;
```

---

### **Important Techniques & Props**

| Feature                    | What it does                                   | Common Usage                          |
|---------------------------|------------------------------------------------|---------------------------------------|
| `KeyboardAvoidingView`    | Prevents keyboard from covering inputs         | Wrap the form                         |
| `TouchableWithoutFeedback`| Dismiss keyboard on outside tap                | Wrap whole screen                     |
| `secureTextEntry`         | Hide password characters                       | Password field                        |
| `loading` state           | Show loading indicator on button               | Disable button during API call        |
| `validation`              | Check input before API call                    | Email format, required fields         |
| `Pressable`               | Modern button with press feedback              | Preferred over `Button`               |

---

### **More Examples**

#### **1. Basic Email + Password Fields**
```jsx
<TextInput
  style={styles.input}
  placeholder="Email"
  keyboardType="email-address"
  autoCapitalize="none"
/>
```

#### **2. Loading Button with ActivityIndicator**
```jsx
<Pressable style={styles.button} disabled={loading}>
  {loading ? <ActivityIndicator color="#fff" /> : <Text>Login</Text>}
</Pressable>
```

#### **3. Input Validation**
```jsx
if (!email.includes('@')) {
  Alert.alert('Invalid Email');
  return;
}
```

#### **4. Remember Me Toggle**
```jsx
<Switch value={rememberMe} onValueChange={setRememberMe} />
```

#### **5. Social Login Buttons**
```jsx
<Pressable style={styles.googleButton}>
  <Text>Continue with Google</Text>
</Pressable>
```

**Common Login Form Style Pattern:**
```jsx
input: {
  height: 52,
  backgroundColor: '#fff',
  borderRadius: 12,
  paddingHorizontal: 16,
  fontSize: 16,
  borderWidth: 1,
  borderColor: '#ddd',
},
button: {
  backgroundColor: '#007AFF',
  height: 52,
  borderRadius: 12,
  justifyContent: 'center',
  alignItems: 'center',
},
```

---

## 6. OTP Input Screen

**Description**: OTP (One-Time Password) Input Screen is commonly used for phone/email verification. It usually consists of multiple single-digit input boxes that automatically focus the next field when a digit is entered.

### **What is OTP Input?**
An OTP screen provides a smooth and secure way to enter verification codes. Key features include:
- Individual boxes for each digit
- Auto-focus to next input
- Auto-submit when complete
- Number-only keyboard
- Resend OTP option
- Timer countdown

---

### **Basic Complete Example**
```jsx
import React, { useState, useRef, useEffect } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  Pressable,
  KeyboardAvoidingView,
  TouchableWithoutFeedback,
  Keyboard,
  Platform,
  Alert,
} from 'react-native';

const OTPScreen = () => {
  const [otp, setOtp] = useState(['', '', '', '', '', '']);
  const [loading, setLoading] = useState(false);
  const [timer, setTimer] = useState(60);

  const inputRefs = useRef([]);

  // Timer Countdown
  useEffect(() => {
    if (timer > 0) {
      const interval = setInterval(() => setTimer((prev) => prev - 1), 1000);
      return () => clearInterval(interval);
    }
  }, [timer]);

  const handleOtpChange = (text, index) => {
    const newOtp = [...otp];
    newOtp[index] = text;
    setOtp(newOtp);

    // Auto focus next input
    if (text && index < 5) {
      inputRefs.current[index + 1]?.focus();
    }

    // Auto submit when all fields are filled
    if (index === 5 && text) {
      const otpCode = newOtp.join('');
      if (otpCode.length === 6) {
        handleVerify(otpCode);
      }
    }
  };

  const handleVerify = (otpCode) => {
    setLoading(true);
    setTimeout(() => {
      setLoading(false);
      Alert.alert('Success', `OTP Verified: ${otpCode}`);
      // Navigate to next screen
    }, 1200);
  };

  const handleKeyPress = (e, index) => {
    if (e.nativeEvent.key === 'Backspace' && otp[index] === '' && index > 0) {
      inputRefs.current[index - 1]?.focus();
    }
  };

  const resendOTP = () => {
    setTimer(60);
    Alert.alert('Resent', 'New OTP has been sent');
    // Call your resend API here
  };

  return (
    <TouchableWithoutFeedback onPress={Keyboard.dismiss}>
      <KeyboardAvoidingView
        behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
        style={styles.container}
      >
        <View style={styles.content}>
          <Text style={styles.title}>Enter Verification Code</Text>
          <Text style={styles.subtitle}>
            We have sent a 6-digit code to your mobile number
          </Text>

          <View style={styles.otpContainer}>
            {otp.map((digit, index) => (
              <TextInput
                key={index}
                ref={(ref) => (inputRefs.current[index] = ref)}
                style={styles.otpInput}
                keyboardType="number-pad"
                maxLength={1}
                value={digit}
                onChangeText={(text) => handleOtpChange(text, index)}
                onKeyPress={(e) => handleKeyPress(e, index)}
                autoFocus={index === 0}
              />
            ))}
          </View>

          <Pressable
            style={[styles.verifyButton, loading && styles.buttonDisabled]}
            onPress={() => handleVerify(otp.join(''))}
            disabled={loading || otp.join('').length !== 6}
          >
            <Text style={styles.verifyButtonText}>
              {loading ? 'Verifying...' : 'Verify OTP'}
            </Text>
          </Pressable>

          <View style={styles.resendContainer}>
            {timer > 0 ? (
              <Text style={styles.timer}>Resend code in {timer}s</Text>
            ) : (
              <Pressable onPress={resendOTP}>
                <Text style={styles.resendText}>Resend OTP</Text>
              </Pressable>
            )}
          </View>
        </View>
      </KeyboardAvoidingView>
    </TouchableWithoutFeedback>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
  },
  content: {
    flex: 1,
    justifyContent: 'center',
    paddingHorizontal: 24,
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 8,
  },
  subtitle: {
    fontSize: 16,
    color: '#666',
    textAlign: 'center',
    marginBottom: 40,
  },
  otpContainer: {
    flexDirection: 'row',
    justifyContent: 'space-between',
    marginBottom: 40,
  },
  otpInput: {
    width: 48,
    height: 58,
    borderWidth: 1.5,
    borderColor: '#ddd',
    borderRadius: 12,
    textAlign: 'center',
    fontSize: 24,
    fontWeight: '600',
    backgroundColor: '#fff',
  },
  verifyButton: {
    backgroundColor: '#007AFF',
    height: 54,
    borderRadius: 12,
    justifyContent: 'center',
    alignItems: 'center',
  },
  buttonDisabled: {
    backgroundColor: '#80bfff',
  },
  verifyButtonText: {
    color: '#fff',
    fontSize: 17,
    fontWeight: '600',
  },
  resendContainer: {
    marginTop: 24,
    alignItems: 'center',
  },
  timer: {
    color: '#888',
    fontSize: 15,
  },
  resendText: {
    color: '#007AFF',
    fontSize: 16,
    fontWeight: '500',
  },
});

export default OTPScreen;
```

---

### **Important Techniques**

| Technique                    | Purpose                                      | Implementation                     |
|-----------------------------|----------------------------------------------|------------------------------------|
| `useRef` for inputs         | Auto-focus management                        | `inputRefs.current[index]`         |
| `maxLength={1}`             | Single digit per box                         | Required for OTP                   |
| `keyboardType="number-pad"` | Numeric keyboard                             | Best for OTP                       |
| `onKeyPress`                | Handle backspace between fields              | Move focus to previous box         |
| Timer + Resend              | Prevent spam                                 | Countdown logic                    |

---

### **More Examples**

#### **1. Basic 4-Digit OTP**
```jsx
{Array(4).fill('').map((_, index) => (
  <TextInput
    key={index}
    style={styles.otpInput}
    maxLength={1}
    keyboardType="number-pad"
  />
))}
```

#### **2. Auto-focus Next Field**
```jsx
onChangeText={(text) => {
  handleChange(text, index);
  if (text) inputRefs.current[index + 1]?.focus();
}}
```

#### **3. Paste Support**
```jsx
onChangeText={(text) => {
  if (text.length > 1) {
    // Handle paste full OTP
  }
}}
```

#### **4. Highlight Focused Box**
```jsx
style={[styles.otpInput, focusedIndex === index && styles.focusedInput]}
```

#### **5. Error State**
```jsx
borderColor: error ? 'red' : '#ddd'
```

**Common OTP Input Style:**
```jsx
otpInput: {
  width: 48,
  height: 58,
  borderWidth: 1.5,
  borderRadius: 12,
  textAlign: 'center',
  fontSize: 24,
  fontWeight: '600',
},
```

---

## 7. Form Validation

**Description**: Form Validation is crucial for ensuring users enter correct and complete data before submission. Proper validation improves data quality, user experience, and security.

### **What is Form Validation?**
In React Native, form validation can be done using:
- Simple JavaScript checks (for small forms)
- Regular expressions (Regex)
- Real-time validation (as user types)
- Third-party libraries (like `formik` + `yup` for complex forms)

Common validations include required fields, email format, password strength, phone number, etc.

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  Pressable,
  Alert,
  KeyboardAvoidingView,
  TouchableWithoutFeedback,
  Keyboard,
  Platform,
} from 'react-native';

const SignupScreen = () => {
  const [formData, setFormData] = useState({
    name: '',
    email: '',
    password: '',
    confirmPassword: '',
  });

  const [errors, setErrors] = useState({});

  const validateForm = () => {
    let newErrors = {};

    // Name validation
    if (!formData.name.trim()) {
      newErrors.name = 'Name is required';
    } else if (formData.name.trim().length < 3) {
      newErrors.name = 'Name must be at least 3 characters';
    }

    // Email validation
    const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    if (!formData.email) {
      newErrors.email = 'Email is required';
    } else if (!emailRegex.test(formData.email)) {
      newErrors.email = 'Please enter a valid email';
    }

    // Password validation
    const passwordRegex = /^(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/;
    if (!formData.password) {
      newErrors.password = 'Password is required';
    } else if (!passwordRegex.test(formData.password)) {
      newErrors.password = 'Password must be 8+ chars with uppercase, number & special char';
    }

    // Confirm Password
    if (formData.password !== formData.confirmPassword) {
      newErrors.confirmPassword = 'Passwords do not match';
    }

    setErrors(newErrors);
    return Object.keys(newErrors).length === 0;
  };

  const handleSubmit = () => {
    if (validateForm()) {
      Alert.alert('Success', 'Form submitted successfully!');
      // Proceed with API call
    }
  };

  const updateField = (field, value) => {
    setFormData(prev => ({ ...prev, [field]: value }));
    // Clear error when user starts typing
    if (errors[field]) {
      setErrors(prev => ({ ...prev, [field]: '' }));
    }
  };

  return (
    <TouchableWithoutFeedback onPress={Keyboard.dismiss}>
      <KeyboardAvoidingView
        behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
        style={styles.container}
      >
        <View style={styles.form}>
          <Text style={styles.title}>Create Account</Text>

          <TextInput
            style={[styles.input, errors.name && styles.inputError]}
            placeholder="Full Name"
            value={formData.name}
            onChangeText={(text) => updateField('name', text)}
          />
          {errors.name && <Text style={styles.errorText}>{errors.name}</Text>}

          <TextInput
            style={[styles.input, errors.email && styles.inputError]}
            placeholder="Email Address"
            keyboardType="email-address"
            autoCapitalize="none"
            value={formData.email}
            onChangeText={(text) => updateField('email', text)}
          />
          {errors.email && <Text style={styles.errorText}>{errors.email}</Text>}

          <TextInput
            style={[styles.input, errors.password && styles.inputError]}
            placeholder="Password"
            secureTextEntry
            value={formData.password}
            onChangeText={(text) => updateField('password', text)}
          />
          {errors.password && <Text style={styles.errorText}>{errors.password}</Text>}

          <TextInput
            style={[styles.input, errors.confirmPassword && styles.inputError]}
            placeholder="Confirm Password"
            secureTextEntry
            value={formData.confirmPassword}
            onChangeText={(text) => updateField('confirmPassword', text)}
          />
          {errors.confirmPassword && <Text style={styles.errorText}>{errors.confirmPassword}</Text>}

          <Pressable style={styles.button} onPress={handleSubmit}>
            <Text style={styles.buttonText}>Sign Up</Text>
          </Pressable>
        </View>
      </KeyboardAvoidingView>
    </TouchableWithoutFeedback>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
  },
  form: {
    flex: 1,
    justifyContent: 'center',
    paddingHorizontal: 24,
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 30,
  },
  input: {
    height: 52,
    backgroundColor: '#fff',
    borderRadius: 12,
    paddingHorizontal: 16,
    fontSize: 16,
    marginBottom: 8,
    borderWidth: 1,
    borderColor: '#ddd',
  },
  inputError: {
    borderColor: '#ff3b30',
  },
  errorText: {
    color: '#ff3b30',
    fontSize: 13,
    marginBottom: 12,
    marginLeft: 4,
  },
  button: {
    backgroundColor: '#007AFF',
    height: 54,
    borderRadius: 12,
    justifyContent: 'center',
    alignItems: 'center',
    marginTop: 20,
  },
  buttonText: {
    color: '#fff',
    fontSize: 17,
    fontWeight: '600',
  },
});

export default SignupScreen;
```

---

### **Important Validation Rules**

| Field              | Validation Rules                                      | Regex / Logic |
|--------------------|-------------------------------------------------------|-------------|
| **Email**          | Required + Valid format                               | `/^[^\s@]+@[^\s@]+\.[^\s@]+$/` |
| **Password**       | Min 8 chars, 1 Upper, 1 Number, 1 Special            | Complex regex (shown above) |
| **Name**           | Required, Min length                                  | `length >= 3` |
| **Phone**          | Valid phone format                                    | Country-specific regex |
| **Confirm Password** | Must match password                                 | Direct comparison |

---

### **More Examples**

#### **1. Basic Required Field Check**
```jsx
if (!email.trim()) {
  Alert.alert('Error', 'Email is required');
}
```

#### **2. Password Strength Regex**
```jsx
const strongPassword = /^(?=.*[A-Z])(?=.*\d)(?=.*[@$!%*?&])[A-Za-z\d@$!%*?&]{8,}$/;
```

#### **3. Real-time Validation**
```jsx
onChangeText={(text) => {
  updateField('email', text);
  if (errors.email) clearError('email');
}}
```

#### **4. Show/Hide Password**
```jsx
const [showPassword, setShowPassword] = useState(false);
< TextInput secureTextEntry={!showPassword} />
```

#### **5. Multiple Field Validation**
```jsx
const isValid = Object.values(errors).every(err => !err);
```

**Common Error Style:**
```jsx
errorText: {
  color: '#ff3b30',
  fontSize: 13,
  marginLeft: 8,
  marginBottom: 12,
},
inputError: {
  borderColor: '#ff3b30',
  borderWidth: 1.5,
},
```

---

## 8. Common Keyboard Types

**Description**: `keyboardType` is a prop of `TextInput` that determines which keyboard layout appears when the user focuses on the input field. Choosing the right keyboard type improves user experience and reduces input errors.

### **What are Keyboard Types?**
React Native provides several built-in keyboard types optimized for different kinds of input. Using the correct `keyboardType` helps users enter data faster and more accurately.

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  ScrollView,
  Platform,
} from 'react-native';

const KeyboardTypesScreen = () => {
  const [form, setForm] = useState({
    name: '',
    email: '',
    phone: '',
    pin: '',
    amount: '',
    url: '',
  });

  const updateForm = (key, value) => {
    setForm(prev => ({ ...prev, [key]: value }));
  };

  return (
    <ScrollView style={styles.container}>
      <View style={styles.content}>
        <Text style={styles.title}>Keyboard Types Demo</Text>

        {/* Default */}
        <Text style={styles.label}>Name (default)</Text>
        <TextInput
          style={styles.input}
          placeholder="Enter your name"
          value={form.name}
          onChangeText={(text) => updateForm('name', text)}
          keyboardType="default"
          autoCapitalize="words"
        />

        {/* Email */}
        <Text style={styles.label}>Email Address</Text>
        <TextInput
          style={styles.input}
          placeholder="your@email.com"
          value={form.email}
          onChangeText={(text) => updateForm('email', text)}
          keyboardType="email-address"
          autoCapitalize="none"
          autoCorrect={false}
        />

        {/* Phone */}
        <Text style={styles.label}>Phone Number</Text>
        <TextInput
          style={styles.input}
          placeholder="+91 98765 43210"
          value={form.phone}
          onChangeText={(text) => updateForm('phone', text)}
          keyboardType="phone-pad"
        />

        {/* Number Pad (OTP/PIN) */}
        <Text style={styles.label}>PIN / OTP</Text>
        <TextInput
          style={styles.input}
          placeholder="123456"
          value={form.pin}
          onChangeText={(text) => updateForm('pin', text)}
          keyboardType="number-pad"
          maxLength={6}
        />

        {/* Decimal */}
        <Text style={styles.label}>Amount (Decimal)</Text>
        <TextInput
          style={styles.input}
          placeholder="99.99"
          value={form.amount}
          onChangeText={(text) => updateForm('amount', text)}
          keyboardType="decimal-pad"
        />

        <Text style={styles.note}>
          Note: Behavior may vary slightly between iOS and Android
        </Text>
      </View>
    </ScrollView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
  },
  content: {
    padding: 20,
  },
  title: {
    fontSize: 26,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 30,
  },
  label: {
    fontSize: 16,
    fontWeight: '500',
    marginTop: 16,
    marginBottom: 6,
  },
  input: {
    height: 52,
    backgroundColor: '#fff',
    borderRadius: 12,
    paddingHorizontal: 16,
    fontSize: 16,
    borderWidth: 1,
    borderColor: '#ddd',
  },
  note: {
    marginTop: 30,
    fontSize: 14,
    color: '#666',
    textAlign: 'center',
    fontStyle: 'italic',
  },
});

export default KeyboardTypesScreen;
```

---

### **Important Keyboard Types**

| `keyboardType`         | Best Use Case                     | Features                              |
|------------------------|-----------------------------------|---------------------------------------|
| `default`              | General text input                | Full QWERTY keyboard                  |
| `email-address`        | Email fields                      | Includes `@` and `.`                  |
| `numeric`              | Numbers with symbols              | Numbers + basic operators             |
| `number-pad`           | OTP, PIN, Codes                   | Only numbers (no symbols)             |
| `phone-pad`            | Phone numbers                     | Numbers + `+` * #                     |
| `decimal-pad`          | Prices, Amounts                   | Numbers + decimal point               |
| `url`                  | Website URLs                      | Includes `/` `.` `:`                  |
| `visible-password`     | Password with visible chars       | Shows characters clearly              |
| `ascii-capable`        | Custom text                       | ASCII characters only                 |

---

### **More Examples**

#### **1. Email Keyboard**
```jsx
<TextInput
  keyboardType="email-address"
  autoCapitalize="none"
  autoCorrect={false}
/>
```

#### **2. OTP / PIN Input**
```jsx
<TextInput
  keyboardType="number-pad"
  maxLength={6}
  textAlign="center"
/>
```

#### **3. Phone Number**
```jsx
<TextInput
  keyboardType="phone-pad"
  placeholder="+91 9876543210"
/>
```

#### **4. Decimal Input (Price)**
```jsx
<TextInput
  keyboardType="decimal-pad"
  placeholder="1299.99"
/>
```

#### **5. URL Input**
```jsx
<TextInput
  keyboardType="url"
  placeholder="https://example.com"
/>
```

**Pro Tip**: Combine with other props:
```jsx
autoCapitalize="none"
autoCorrect={false}
returnKeyType="done"
```

---

## 9. Best Practices for Forms

**Description**: Following best practices while building forms in React Native ensures better user experience, fewer bugs, improved performance, and higher security.

### **What are Form Best Practices?**
Good form design goes beyond just UI. It includes proper state management, validation, accessibility, keyboard handling, loading states, and cross-platform consistency.

---

### **Basic Complete Example**
```jsx
import React, { useState } from 'react';
import {
  View,
  TextInput,
  Text,
  StyleSheet,
  Pressable,
  Alert,
  KeyboardAvoidingView,
  TouchableWithoutFeedback,
  Keyboard,
  Platform,
  ActivityIndicator,
} from 'react-native';

const BestPracticesForm = () => {
  const [formData, setFormData] = useState({
    email: '',
    password: '',
  });

  const [errors, setErrors] = useState({});
  const [loading, setLoading] = useState(false);

  const updateField = (field, value) => {
    setFormData(prev => ({ ...prev, [field]: value }));
    
    // Clear error when user starts typing
    if (errors[field]) {
      setErrors(prev => ({ ...prev, [field]: '' }));
    }
  };

  const validateAndSubmit = async () => {
    let newErrors = {};

    // Trim and validate
    const email = formData.email.trim();
    const password = formData.password.trim();

    if (!email) newErrors.email = 'Email is required';
    else if (!email.includes('@')) newErrors.email = 'Invalid email format';

    if (!password) newErrors.password = 'Password is required';
    else if (password.length < 6) newErrors.password = 'Password must be at least 6 characters';

    setErrors(newErrors);

    if (Object.keys(newErrors).length > 0) return;

    setLoading(true);

    try {
      // Simulate API call
      await new Promise(resolve => setTimeout(resolve, 1500));
      Alert.alert('Success', 'Form submitted successfully!');
      
      // Reset form after success
      setFormData({ email: '', password: '' });
    } catch (error) {
      Alert.alert('Error', 'Something went wrong. Please try again.');
    } finally {
      setLoading(false);
    }
  };

  return (
    <TouchableWithoutFeedback onPress={Keyboard.dismiss}>
      <KeyboardAvoidingView
        behavior={Platform.OS === 'ios' ? 'padding' : 'height'}
        style={styles.container}
      >
        <View style={styles.form}>
          <Text style={styles.title}>Best Practices Form</Text>

          <Text style={styles.label}>Email Address</Text>
          <TextInput
            style={[styles.input, errors.email && styles.inputError]}
            placeholder="Enter your email"
            value={formData.email}
            onChangeText={(text) => updateField('email', text)}
            keyboardType="email-address"
            autoCapitalize="none"
            autoCorrect={false}
          />
          {errors.email && <Text style={styles.errorText}>{errors.email}</Text>}

          <Text style={styles.label}>Password</Text>
          <TextInput
            style={[styles.input, errors.password && styles.inputError]}
            placeholder="Enter your password"
            value={formData.password}
            onChangeText={(text) => updateField('password', text)}
            secureTextEntry
          />
          {errors.password && <Text style={styles.errorText}>{errors.password}</Text>}

          <Pressable
            style={[styles.button, loading && styles.buttonDisabled]}
            onPress={validateAndSubmit}
            disabled={loading}
          >
            {loading ? (
              <ActivityIndicator color="#fff" />
            ) : (
              <Text style={styles.buttonText}>Submit</Text>
            )}
          </Pressable>
        </View>
      </KeyboardAvoidingView>
    </TouchableWithoutFeedback>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f8f9fa',
  },
  form: {
    flex: 1,
    justifyContent: 'center',
    paddingHorizontal: 24,
  },
  title: {
    fontSize: 28,
    fontWeight: 'bold',
    textAlign: 'center',
    marginBottom: 40,
  },
  label: {
    fontSize: 16,
    fontWeight: '500',
    marginBottom: 6,
    marginTop: 12,
  },
  input: {
    height: 52,
    backgroundColor: '#fff',
    borderRadius: 12,
    paddingHorizontal: 16,
    fontSize: 16,
    borderWidth: 1,
    borderColor: '#ddd',
  },
  inputError: {
    borderColor: '#ff3b30',
  },
  errorText: {
    color: '#ff3b30',
    fontSize: 13,
    marginLeft: 4,
    marginTop: 4,
  },
  button: {
    backgroundColor: '#007AFF',
    height: 54,
    borderRadius: 12,
    justifyContent: 'center',
    alignItems: 'center',
    marginTop: 30,
  },
  buttonDisabled: {
    backgroundColor: '#80bfff',
  },
  buttonText: {
    color: '#fff',
    fontSize: 17,
    fontWeight: '600',
  },
});

export default BestPracticesForm;
```

---

### **Important Best Practices**

| Best Practice                        | Why It Matters                              | How to Implement |
|-------------------------------------|---------------------------------------------|------------------|
| Use **Controlled Inputs**           | Predictable behavior                        | `value` + `onChangeText` |
| **Validate before submit**          | Prevent bad data                            | Client-side checks |
| Show **clear error messages**       | Better UX                                   | Inline red text |
| Disable button while **loading**    | Prevent multiple submissions                | `disabled` + `ActivityIndicator` |
| **Trim** whitespace                 | Clean data                                  | `.trim()` |
| Use `secureTextEntry`               | Security                                    | For passwords |
| Good **placeholders**               | User guidance                               | Descriptive text |
| `KeyboardAvoidingView` + Dismiss    | Usability                                   | Wrap your form |
| Real-time error clearing            | Smooth experience                           | Clear error on typing |
| Test on **both platforms**          | Consistency                                 | Android + iOS |

---

### **More Best Practices**

#### **1. Always Trim Input**
```jsx
const cleanEmail = email.trim().toLowerCase();
```

#### **2. Debounce Search/Filter Inputs**
```jsx
// Use useEffect with setTimeout for search fields
```

#### **3. Use `returnKeyType`**
```jsx
returnKeyType="next" // or "done", "search", "go"
```

#### **4. Accessibility**
```jsx
accessible={true}
accessibilityLabel="Email input"
```

#### **5. Reset Form After Success**
```jsx
setFormData({ email: '', password: '' });
```
