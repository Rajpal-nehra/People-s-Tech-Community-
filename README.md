// Project: The People's Tech Community (React Native + Firebase)

// --- File: App.js --- import React from 'react'; import { NavigationContainer } from '@react-navigation/native'; import { createNativeStackNavigator } from '@react-navigation/native-stack'; import LoginScreen from './screens/LoginScreen'; import SignupScreen from './screens/SignupScreen'; import HomeScreen from './screens/HomeScreen'; import ProfileScreen from './screens/ProfileScreen'; import TasksScreen from './screens/TasksScreen';

const Stack = createNativeStackNavigator();

export default function App() { return ( <NavigationContainer> <Stack.Navigator initialRouteName="Login"> <Stack.Screen name="Login" component={LoginScreen} /> <Stack.Screen name="Signup" component={SignupScreen} /> <Stack.Screen name="Home" component={HomeScreen} /> <Stack.Screen name="Profile" component={ProfileScreen} /> <Stack.Screen name="Tasks" component={TasksScreen} /> </Stack.Navigator> </NavigationContainer> ); }

// --- File: screens/TasksScreen.js --- import React, { useState } from 'react'; import { View, Text, TextInput, Button, FlatList } from 'react-native';

const mockTasks = [ { id: '1', title: 'Create a tech meme', reward: '100 pts + medal' }, { id: '2', title: 'Write a beginner guide to Python', reward: '200 pts + medal' }, ];

export default function TasksScreen({ navigation }) { return ( <View style={{ padding: 20 }}> <Text style={{ fontSize: 24, marginBottom: 20 }}>Community Tasks</Text> <FlatList data={mockTasks} keyExtractor={item => item.id} renderItem={({ item }) => ( <View style={{ marginBottom: 20 }}> <Text style={{ fontSize: 18 }}>{item.title}</Text> <Text style={{ color: 'gray' }}>Reward: {item.reward}</Text> <Button title="Mark as Complete" onPress={() => alert('Submitted for review')} /> </View> )} /> </View> ); }

// --- File: screens/HomeScreen.js --- import React from 'react'; import { View, Text, Button } from 'react-native';

const currentUser = { email: 'you@example.com', role: 'superadmin', };

const getBadge = (role) => { switch (role) { case 'team': return '⭐'; case 'admin': return '⭐⭐'; case 'superadmin': return '⭐⭐⭐'; default: return ''; } };

export default function HomeScreen({ navigation }) { const isAdmin = currentUser.role === 'admin' || currentUser.role === 'superadmin'; const isSuperAdmin = currentUser.role === 'superadmin';

return ( <View style={{ padding: 20 }}> <Text>Welcome to The People's Tech Community!</Text> <Text>{getBadge(currentUser.role)} {currentUser.email}</Text>

<Button title="Go to Profile" onPress={() => navigation.navigate('Profile')} />
<Button title="Go to Tasks" onPress={() => navigation.navigate('Tasks')} />

{isAdmin && (
<View style={{ marginTop: 20 }}>
<Text style={{ fontWeight: 'bold' }}>Admin Panel</Text>
<Text>- Pin or unpin posts</Text>
<Text>- Delete posts</Text>
<Text>- Assign community tasks</Text>
</View>
)}

{isSuperAdmin && (
<View style={{ marginTop: 20 }}>
<Text style={{ fontWeight: 'bold' }}>Super Admin Controls</Text>
<Text>- Promote or demote administrators</Text>
</View>
)}
</View>

); }

// --- File: screens/ProfileScreen.js --- import React from 'react'; import { View, Text, Button } from 'react-native';

const user = { name: 'Your Name', email: 'you@example.com', role: 'superadmin', bio: 'Super admin of The People's Tech Community', score: 4400, medals: 4, followers: 397, following: 17, likes: 14870, coins: 115306, };

const getBadge = (role) => { switch (role) { case 'team': return '⭐'; case 'admin': return '⭐⭐'; case 'superadmin': return '⭐⭐⭐'; default: return ''; } };

export default function ProfileScreen({ navigation }) { return ( <View style={{ padding: 20 }}> <Text style={{ fontSize: 24 }}>{user.name}</Text> <Text>{getBadge(user.role)} {user.role}</Text> <Text>{user.email}</Text> <Text>{user.bio}</Text> <View style={{ marginTop: 20 }}> <Text>🎖️ Medals: {user.medals}</Text> <Text>📈 Score: {user.score}</Text> <Text>👥 Followers: {user.followers}</Text> <Text>➡️ Following: {user.following}</Text> <Text>❤️ Likes: {user.likes}</Text> <Text>🪙 Coins: {user.coins}</Text> </View> <Button title="Back to Home" onPress={() => navigation.navigate('Home')} /> </View> ); }



