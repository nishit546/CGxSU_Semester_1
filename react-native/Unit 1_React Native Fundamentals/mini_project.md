
# Mini Project 1 — Profile Card App

### **What We Are Going to Build**

In this mini project, we will create a **beautiful, modern Profile Card** component.  

The final result will be a centered card on the screen featuring:
- A circular profile picture
- Name and professional role
- Short bio text
- A "Follow" button with press feedback

This is a very common UI pattern used in social media, networking, and portfolio apps.

---

### Step 1: Create the Project

Open your terminal and run:

```bash
npx create-expo-app@latest ProfileCardApp
cd ProfileCardApp
code .
```

Start the development server:

```bash
npx expo start
```

Scan the QR code using the **Expo Go** app on your phone.

---

### Step 2: Project Folder Structure

Create the following structure inside your project:

```bash
ProfileCardApp/
├── assets/
│   └── images/
│       └── profile.jpg     # Add your profile picture here
├── components/
│   └── ProfileCard.js
├── App.js
├── app.json
├── package.json
└── babel.config.js
```

---

### Step 3: Create ProfileCard Component

Create file: **`components/ProfileCard.js`**

```jsx
import React from 'react';
import { View, Text, Image, Pressable, StyleSheet, Alert } from 'react-native';

const ProfileCard = () => {
  const handleFollow = () => {
    Alert.alert('Success', 'You are now following John Doe!');
  };

  return (
    <View style={styles.card}>
      {/* Profile Image */}
      <Image
        source={require('../assets/images/profile.jpg')}
        style={styles.image}
      />

      {/* Name */}
      <Text style={styles.name}>John Doe</Text>

      {/* Role */}
      <Text style={styles.role}>React Native Developer</Text>

      {/* Bio */}
      <Text style={styles.bio}>
        Passionate about building beautiful and performant mobile applications 
        using React Native and Expo. Love turning ideas into reality.
      </Text>

      {/* Follow Button */}
      <Pressable style={styles.button} onPress={handleFollow}>
        <Text style={styles.buttonText}>Follow</Text>
      </Pressable>
    </View>
  );
};

const styles = StyleSheet.create({
  card: {
    backgroundColor: '#ffffff',
    width: 340,
    borderRadius: 24,
    padding: 24,
    alignItems: 'center',
    shadowColor: '#000',
    shadowOffset: { width: 0, height: 10 },
    shadowOpacity: 0.1,
    shadowRadius: 15,
    elevation: 10, // For Android shadow
  },
  image: {
    width: 130,
    height: 130,
    borderRadius: 65,
    borderWidth: 4,
    borderColor: '#f8fafc',
    marginBottom: 16,
  },
  name: {
    fontSize: 26,
    fontWeight: 'bold',
    color: '#1e2937',
    marginBottom: 4,
  },
  role: {
    fontSize: 16,
    color: '#64748b',
    marginBottom: 16,
  },
  bio: {
    fontSize: 15,
    color: '#475569',
    textAlign: 'center',
    lineHeight: 22,
    marginBottom: 24,
  },
  button: {
    backgroundColor: '#0ea5e9',
    paddingVertical: 14,
    paddingHorizontal: 48,
    borderRadius: 12,
    marginTop: 8,
  },
  buttonText: {
    color: 'white',
    fontSize: 17,
    fontWeight: 'bold',
  },
});

export default ProfileCard;
```

---

### Step 4: Update App.js

Replace the content of **`App.js`** with:

```jsx
import { SafeAreaView, StatusBar, StyleSheet } from 'react-native';
import ProfileCard from './components/ProfileCard';

export default function App() {
  return (
    <SafeAreaView style={styles.container}>
      <StatusBar barStyle="dark-content" backgroundColor="#f8fafc" />
      <ProfileCard />
    </SafeAreaView>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#f1f5f9',
    justifyContent: 'center',
    alignItems: 'center',
    padding: 20,
  },
});
```
