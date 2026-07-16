
### **Mini Project 2 — Student Management App**


## Objective
Create a React Native application that allows users to manage students, fetch data from an API, and navigate between different screens using **Bottom Tabs** and **Drawer Navigation**.

---

### 1. Home Screen
- Use `View`, `Text` and `Button`.
- Show a welcome message and a button to navigate to **Students** screen.

### 2. Students Screen
- Use `FlatList`, `Pressable` and `useState`.
- Display a list of students.
- On pressing **Select**, display the selected student's name.

### 3. API Screen
- Fetch data from `https://jsonplaceholder.typicode.com/users`.
- Display **Name**, **Email** and **Phone** using `FlatList`.
- Show **"Loading..."** while fetching.

### 4. Profile Screen
- Display **Student Name**, **Course** and **College**.
- Include an **Edit Profile** button.
- On click, show an alert: `'Profile Updated'`.

---

## Navigation
- **Bottom Tab Navigation**: Home, Students, API
- **Drawer Navigation**: Home, Students, API, Profile

---

### Install the package

Run this command in your terminal:

```bash

npm install @react-navigation/drawer

```

---

## Folder Structure

```bash
Student_Management_App/
├── app/
│   ├── _layout.tsx                 # Root Layout
│   ├── modal.tsx                   # Modal Screen
│   ├── (drawer)/                   # Drawer Group
│   │   ├── _layout.tsx             # Drawer Layout
│   │   ├── (tabs)/                 # Tabs Group (Nested inside Drawer)
│   │   │   ├── _layout.tsx         # Bottom Tabs Layout
│   │   │   ├── index.tsx           # Home Screen
│   │   │   ├── students.tsx        # Students Screen
│   │   │   ├── api.tsx             # API Screen
│   │   │   └── about.tsx           # (if any)
│   │   ├── profile.tsx             # Profile Screen
│   │   └── setting.tsx             # Settings Screen
│   └── +not-found.tsx              # (Optional)
├── assets/
│   └── images/
├── components/
├── constants/
├── hooks/
├── node_modules/
├── scripts/
├── .gitignore
├── app.json
├── package.json
├── tsconfig.json
└── README.md
```

---

## Key Code Files

### 1. `app/_layout.tsx`

```tsx
import { Stack } from "expo-router";
import { StatusBar } from "expo-status-bar";

export default function RootLayout() {
  return (
    <>
      <Stack screenOptions={{ headerShown: false }}>
        <Stack.Screen name="(drawer)" />
      </Stack>
      <StatusBar style="auto" />
    </>
  );
}
```

---

### 2. `app/(drawer)/(tabs)/_layout.tsx`

```tsx
import { Tabs } from "expo-router";
import { Ionicons } from "@expo/vector-icons";

export default function TabLayout() {
  return (
    <Tabs
      screenOptions={{
        headerShown: false,
        tabBarActiveTintColor: "#2563eb",
        tabBarInactiveTintColor: "gray",
      }}
    >
      <Tabs.Screen
        name="index"
        options={{
          title: "Home",
          tabBarIcon: ({ color, size }) => (
            <Ionicons name="home" size={size} color={color} />
          ),
        }}
      />
      <Tabs.Screen
        name="students"
        options={{
          title: "Students",
          tabBarIcon: ({ color, size }) => (
            <Ionicons name="people" size={size} color={color} />
          ),
        }}
      />
      <Tabs.Screen
        name="api"
        options={{
          title: "API",
          tabBarIcon: ({ color, size }) => (
            <Ionicons name="cloud-download" size={size} color={color} />
          ),
        }}
      />
      <Tabs.Screen
        name="about"
        options={{
          title: "About",
          tabBarIcon: ({ color, size }) => (
            <Ionicons name="information-circle" size={size} color={color} />
          ),
        }}
      />
    </Tabs>
  );
}
```

---

### 3. `app/(drawer)/(tabs)/index.tsx` (Home Screen)

```tsx
import { View, Text, StyleSheet, Button } from "react-native";
import { router } from "expo-router";
import { Ionicons } from "@expo/vector-icons";

export default function HomeScreen() {
  return (
    <View style={styles.container}>
      <Text style={styles.title}>Student Management App</Text>
      <Text style={styles.subtitle}>
        Welcome to the React Native Assignment
      </Text>

      <View style={styles.card}>
        <View style={styles.row}>
          <Ionicons name="layers-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>View</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="text-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>Text</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="radio-button-on-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>Button</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="list-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>FlatList</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="hand-left-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>Pressable</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="refresh-circle-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>useState</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="cloud-download-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>API Fetching</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="grid-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>Bottom Tab Navigation</Text>
        </View>
        <View style={styles.row}>
          <Ionicons name="menu-outline" size={22} color="#2563eb" />
          <Text style={styles.text}>Drawer Navigation</Text>
        </View>
      </View>

      <View style={styles.buttonContainer}>
        <Button
          title="Go To Students"
          onPress={() => router.push("/(drawer)/(tabs)/students")}
        />
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 20,
    justifyContent: "center",
    backgroundColor: "#f5f5f5",
  },
  title: {
    fontSize: 28,
    fontWeight: "bold",
    color: "#2563eb",
    textAlign: "center",
    marginBottom: 10,
  },
  subtitle: {
    textAlign: "center",
    fontSize: 16,
    marginBottom: 25,
    color: "#555",
  },
  card: {
    backgroundColor: "#fff",
    padding: 20,
    borderRadius: 10,
    elevation: 4,
    marginBottom: 30,
  },
  row: {
    flexDirection: "row",
    alignItems: "center",
    marginVertical: 8,
  },
  text: {
    fontSize: 17,
    marginLeft: 10,
  },
  buttonContainer: {
    marginTop: 10,
  },
});
```

---

### 4. `app/(drawer)/(tabs)/students.tsx`

```tsx
import React, { useState } from "react";
import {
  View,
  Text,
  FlatList,
  Pressable,
  StyleSheet,
} from "react-native";

export default function StudentsScreen() {
  const [students] = useState([
    { id: "1", name: "Rahul Sharma", course: "React Native" },
    { id: "2", name: "Amit Kumar", course: "Flutter" },
    { id: "3", name: "Priya Singh", course: "Android" },
    { id: "4", name: "Sneha Patel", course: "iOS" },
    { id: "5", name: "Rohan Verma", course: "Java Full Stack" },
  ]);

  const [selectedStudent, setSelectedStudent] = useState("");

  const renderItem = ({ item }: { item: typeof students[0] }) => (
    <View style={styles.card}>
      <Text style={styles.name}>{item.name}</Text>
      <Text style={styles.course}>Course: {item.course}</Text>
      <Pressable
        style={styles.button}
        onPress={() => setSelectedStudent(item.name)}
      >
        <Text style={styles.buttonText}>Select</Text>
      </Pressable>
    </View>
  );

  return (
    <View style={styles.container}>
      <Text style={styles.heading}>Student List</Text>

      {selectedStudent !== "" && (
        <View style={styles.selectedCard}>
          <Text style={styles.selectedTitle}>Selected Student</Text>
          <Text style={styles.selectedName}>{selectedStudent}</Text>
        </View>
      )}

      <FlatList
        data={students}
        keyExtractor={(item) => item.id}
        renderItem={renderItem}
        showsVerticalScrollIndicator={false}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f2f2f2",
    padding: 15,
  },
  heading: {
    fontSize: 28,
    fontWeight: "bold",
    color: "#2563eb",
    marginBottom: 15,
    textAlign: "center",
  },
  selectedCard: {
    backgroundColor: "#dbeafe",
    padding: 15,
    borderRadius: 10,
    marginBottom: 20,
  },
  selectedTitle: {
    fontSize: 18,
    fontWeight: "bold",
  },
  selectedName: {
    fontSize: 20,
    color: "#2563eb",
    marginTop: 5,
  },
  card: {
    backgroundColor: "#fff",
    padding: 18,
    borderRadius: 10,
    marginBottom: 15,
    elevation: 3,
  },
  name: {
    fontSize: 20,
    fontWeight: "bold",
  },
  course: {
    fontSize: 16,
    marginTop: 8,
    color: "#555",
  },
  button: {
    marginTop: 15,
    backgroundColor: "#2563eb",
    padding: 12,
    borderRadius: 8,
    alignItems: "center",
  },
  buttonText: {
    color: "#fff",
    fontWeight: "bold",
    fontSize: 16,
  },
});
```

---

### 5. `app/(drawer)/(tabs)/api.tsx`

```tsx
import React, { useEffect, useState } from "react";
import {
  View,
  Text,
  FlatList,
  StyleSheet,
  ActivityIndicator,
} from "react-native";

type User = {
  id: number;
  name: string;
  email: string;
  phone: string;
};

export default function ApiScreen() {
  const [users, setUsers] = useState<User[]>([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then((response) => response.json())
      .then((data) => {
        setUsers(data);
        setLoading(false);
      })
      .catch((error) => {
        console.error(error);
        setLoading(false);
      });
  }, []);

  if (loading) {
    return (
      <View style={styles.loadingContainer}>
        <ActivityIndicator size="large" color="#2563eb" />
        <Text style={styles.loadingText}>Loading...</Text>
      </View>
    );
  }

  const renderItem = ({ item }: { item: User }) => (
    <View style={styles.card}>
      <Text style={styles.name}>{item.name}</Text>
      <Text style={styles.label}>Email:</Text>
      <Text style={styles.value}>{item.email}</Text>
      <Text style={styles.label}>Phone:</Text>
      <Text style={styles.value}>{item.phone}</Text>
    </View>
  );

  return (
    <View style={styles.container}>
      <Text style={styles.heading}>API Data</Text>
      <FlatList
        data={users}
        keyExtractor={(item) => item.id.toString()}
        renderItem={renderItem}
        showsVerticalScrollIndicator={false}
      />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f2f2f2",
    padding: 15,
  },
  heading: {
    fontSize: 28,
    fontWeight: "bold",
    textAlign: "center",
    color: "#2563eb",
    marginBottom: 20,
  },
  loadingContainer: {
    flex: 1,
    justifyContent: "center",
    alignItems: "center",
  },
  loadingText: {
    marginTop: 15,
    fontSize: 18,
  },
  card: {
    backgroundColor: "#fff",
    padding: 18,
    borderRadius: 10,
    marginBottom: 15,
    elevation: 3,
  },
  name: {
    fontSize: 20,
    fontWeight: "bold",
    color: "#2563eb",
    marginBottom: 10,
  },
  label: {
    fontWeight: "bold",
    fontSize: 16,
    marginTop: 5,
  },
  value: {
    fontSize: 15,
    color: "#555",
    marginBottom: 5,
  },
});
```

---

### 6. `app/(drawer)/(tabs)/about.tsx`

*(Already well formatted — minor cleanup)*

```tsx
import { View, Text, StyleSheet } from "react-native";

export default function AboutScreen() {
  return (
    <View style={styles.container}>
      <Text style={styles.heading}>About</Text>
      <View style={styles.card}>
        <Text style={styles.title}>Student Management App</Text>
        <Text style={styles.text}>
          This application is developed as a React Native Assignment.
        </Text>
        <Text style={styles.text}>It demonstrates the following concepts:</Text>
        
        <Text style={styles.list}>• View</Text>
        <Text style={styles.list}>• Text</Text>
        <Text style={styles.list}>• Button</Text>
        <Text style={styles.list}>• Pressable</Text>
        <Text style={styles.list}>• FlatList</Text>
        <Text style={styles.list}>• useState</Text>
        <Text style={styles.list}>• useEffect</Text>
        <Text style={styles.list}>• API Fetching</Text>
        <Text style={styles.list}>• Bottom Tab Navigation</Text>
        <Text style={styles.list}>• Drawer Navigation</Text>

        <Text style={styles.version}>Version : 1.0</Text>
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f2f2f2",
    padding: 20,
  },
  heading: {
    fontSize: 28,
    fontWeight: "bold",
    color: "#2563eb",
    textAlign: "center",
    marginBottom: 20,
  },
  card: {
    backgroundColor: "#fff",
    borderRadius: 10,
    padding: 20,
    elevation: 4,
  },
  title: {
    fontSize: 22,
    fontWeight: "bold",
    color: "#2563eb",
    marginBottom: 15,
  },
  text: {
    fontSize: 16,
    marginBottom: 10,
    lineHeight: 24,
  },
  list: {
    fontSize: 16,
    marginVertical: 4,
  },
  version: {
    marginTop: 20,
    fontSize: 18,
    fontWeight: "bold",
    color: "#2563eb",
  },
});
```

---

### 7. `app/(drawer)/_layout.tsx`

```tsx
import { Drawer } from "expo-router/drawer";
import { Ionicons } from "@expo/vector-icons";

export default function DrawerLayout() {
  return (
    <Drawer
      screenOptions={{
        headerStyle: { backgroundColor: "#2563eb" },
        headerTintColor: "#fff",
        drawerActiveTintColor: "#2563eb",
      }}
    >
      <Drawer.Screen
        name="(tabs)"
        options={{
          title: "Home",
          drawerIcon: ({ color, size }) => (
            <Ionicons name="home" size={size} color={color} />
          ),
        }}
      />
      <Drawer.Screen
        name="profile"
        options={{
          title: "Profile",
          drawerIcon: ({ color, size }) => (
            <Ionicons name="person" size={size} color={color} />
          ),
        }}
      />
      <Drawer.Screen
        name="setting"
        options={{
          title: "Settings",
          drawerIcon: ({ color, size }) => (
            <Ionicons name="settings" size={size} color={color} />
          ),
        }}
      />
    </Drawer>
  );
}
```

---

### 8. `app/(drawer)/profile.tsx`

```tsx
import React from "react";
import { View, Text, StyleSheet, Button, Alert } from "react-native";

export default function ProfileScreen() {
  const handleEditProfile = () => {
    Alert.alert("Profile Updated", "Your profile has been updated successfully.");
  };

  return (
    <View style={styles.container}>
      <Text style={styles.heading}>Student Profile</Text>
      <View style={styles.card}>
        <Text style={styles.label}>Student Name</Text>
        <Text style={styles.value}>Rahul Sharma</Text>

        <Text style={styles.label}>Course</Text>
        <Text style={styles.value}>React Native</Text>

        <Text style={styles.label}>College</Text>
        <Text style={styles.value}>ABC Institute of Technology</Text>

        <View style={styles.buttonContainer}>
          <Button
            title="Edit Profile"
            onPress={handleEditProfile}
            color="#2563eb"
          />
        </View>
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f2f2f2",
    padding: 20,
  },
  heading: {
    fontSize: 28,
    fontWeight: "bold",
    textAlign: "center",
    color: "#2563eb",
    marginBottom: 25,
  },
  card: {
    backgroundColor: "#fff",
    borderRadius: 12,
    padding: 20,
    elevation: 4,
  },
  label: {
    fontSize: 16,
    fontWeight: "bold",
    color: "#555",
    marginTop: 15,
  },
  value: {
    fontSize: 18,
    color: "#000",
    marginTop: 5,
  },
  buttonContainer: {
    marginTop: 30,
  },
});
```

---

### 9. `app/(drawer)/setting.tsx`

```tsx
import React from "react";
import { View, Text, StyleSheet } from "react-native";
import { Ionicons } from "@expo/vector-icons";

export default function SettingScreen() {
  return (
    <View style={styles.container}>
      <Text style={styles.heading}>Settings</Text>
      <View style={styles.card}>
        <View style={styles.item}>
          <Ionicons name="notifications" size={24} color="#2563eb" />
          <Text style={styles.text}>Notifications</Text>
        </View>
        <View style={styles.item}>
          <Ionicons name="lock-closed" size={24} color="#2563eb" />
          <Text style={styles.text}>Privacy Policy</Text>
        </View>
        <View style={styles.item}>
          <Ionicons name="help-circle" size={24} color="#2563eb" />
          <Text style={styles.text}>Help & Support</Text>
        </View>
        <View style={styles.item}>
          <Ionicons name="information-circle" size={24} color="#2563eb" />
          <Text style={styles.text}>About Application</Text>
        </View>
        <View style={styles.item}>
          <Ionicons name="phone-portrait" size={24} color="#2563eb" />
          <Text style={styles.text}>App Version : 1.0.0</Text>
        </View>
      </View>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#f2f2f2",
    padding: 20,
  },
  heading: {
    fontSize: 28,
    fontWeight: "bold",
    textAlign: "center",
    color: "#2563eb",
    marginBottom: 20,
  },
  card: {
    backgroundColor: "#fff",
    borderRadius: 12,
    padding: 20,
    elevation: 4,
  },
  item: {
    flexDirection: "row",
    alignItems: "center",
    paddingVertical: 18,
    borderBottomWidth: 1,
    borderBottomColor: "#ddd",
  },
  text: {
    marginLeft: 15,
    fontSize: 18,
    color: "#333",
  },
});
```
