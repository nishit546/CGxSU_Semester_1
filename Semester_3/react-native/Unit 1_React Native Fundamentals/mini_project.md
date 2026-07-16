
### **Mini Project 1 — Profile Card App**

### **What We Are Going to Build**
In this mini project, we will create a **beautiful, modern Profile Card** component.  
The final result will be a **centered card** on the screen featuring:

- A circular profile picture
- Name and professional role
- Short bio text
- A "Follow" button with press feedback

This is a very common UI pattern used in social media, networking, and portfolio apps.

---

### **Step 1: Create the Project**

```bash
npx create-expo-app@latest ProfileCardApp
cd ProfileCardApp
```

Start the development server:

```bash
npx expo start
```

Scan the QR code using the **Expo Go** app on your phone.

---

### **Step 2: Install Required Dependencies**

Run the following commands:

```bash
npx expo install react-native-safe-area-context
npx expo install @expo/vector-icons
```

> These two packages are required for safe area handling and icon support in the tab navigation.

---

### **Step 3: Project Folder Structure**

Create the following structure inside your project:

```bash
ProfileCardApp/
├── app/
│   ├── _layout.tsx
│   ├── modal.tsx
│   └── (tabs)/
│       ├── _layout.tsx
│       ├── index.tsx
│       ├── profile.tsx          ← Profile Card Screen
│       └── explore.tsx
└── assets/
    └── images/
        └── icon.png             ← (Place your profile image here)
```

---

### **Step 4: Create Profile Card Screen**

**File:** `app/(tabs)/profile.tsx`

```tsx
import React from "react";
import { View, Text, Image, Pressable, StyleSheet, Alert } from "react-native";
import { SafeAreaView } from "react-native-safe-area-context";

const Profile = () => {
  const handleFollow = () => {
    Alert.alert("Success", "You are now following John Doe!");
  };

  return (
    <SafeAreaView style={styles.container}>
      <View style={styles.card}>
        {/* Profile Image */}
        <Image
          source={require("../../assets/images/icon.png")}
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

        <Pressable
          onPress={handleFollow}
          android_ripple={{
            color: "rgba(55, 255, 0, 0.6)",
            borderless: false,
            foreground: true,
          }}
          style={styles.button}
        >
          <Text style={styles.buttonText}>Follow</Text>
        </Pressable>
      </View>
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f8fafc",
    justifyContent: "center",
    alignItems: "center",
  },
  card: {
    backgroundColor: "#ffffff",
    width: 340,
    borderRadius: 24,
    padding: 32,
    alignItems: "center",
    shadowColor: "#000",
    shadowOffset: { width: 0, height: 12 },
    shadowOpacity: 0.12,
    shadowRadius: 20,
    elevation: 15,
  },
  image: {
    width: 130,
    height: 130,
    borderRadius: 65,
    borderWidth: 5,
    borderColor: "#ffffff",
    marginBottom: 20,
  },
  name: {
    fontSize: 26,
    fontWeight: "bold",
    color: "#1e2937",
    marginBottom: 6,
  },
  role: {
    fontSize: 16,
    color: "#64748b",
    marginBottom: 20,
  },
  bio: {
    fontSize: 15,
    color: "#475569",
    textAlign: "center",
    lineHeight: 23,
    marginBottom: 28,
  },
  button: {
    width: "100%",
    height: 58,
    backgroundColor: "#1976D2",
    borderRadius: 14,
    justifyContent: "center",
    alignItems: "center",
    overflow: "hidden",
    elevation: 6,
  },
  buttonText: {
    color: "#fff",
    fontSize: 18,
    fontWeight: "600",
  },
});

export default Profile;
```

---

### **Step 5: Update Tab Layout**

**File:** `app/(tabs)/_layout.tsx`

```tsx
import { Tabs } from "expo-router";
import React from "react";

import { HapticTab } from "@/components/haptic-tab";
import { IconSymbol } from "@/components/ui/icon-symbol";
import { Colors } from "@/constants/theme";
import { useColorScheme } from "@/hooks/use-color-scheme";
import { Ionicons } from "@expo/vector-icons";

export default function TabLayout() {
  const colorScheme = useColorScheme();

  return (
    <Tabs
      screenOptions={{
        tabBarActiveTintColor: Colors[colorScheme ?? "light"].tint,
        headerShown: false,
        tabBarButton: HapticTab,
      }}
    >
      <Tabs.Screen
        name="index"
        options={{
          title: "Home",
          tabBarIcon: ({ color }) => (
            <IconSymbol size={28} name="house.fill" color={color} />
          ),
        }}
      />
      <Tabs.Screen
        name="explore"
        options={{
          title: "Explore",
          tabBarIcon: ({ color }) => (
            <IconSymbol size={28} name="paperplane.fill" color={color} />
          ),
        }}
      />
      <Tabs.Screen
        name="profile"
        options={{
          title: "Profile",
          tabBarIcon: ({ color }) => (
            <Ionicons name="person" size={24} color={color} />
          ),
        }}
      />
    </Tabs>
  );
}
```

