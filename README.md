# 404-found-us
sehet_imaan_adventure/
├── lib/
│   ├── main.dart
│   ├── screens/
│   │   ├── splash_screen.dart
│   │   ├── onboarding_screen.dart
│   │   ├── login_screen.dart
│   │   ├── home_screen.dart
│   │   ├── habit_tracker_screen.dart
│   │   ├── story_screen.dart
│   │   ├── dua_screen.dart
│   │   └── rewards_screen.dart
│   └── widgets/
│       ├── custom_button.dart
│       └── habit_card.dart
├── pubspec.yaml
└── assets/
    ├── images/
    └── audio/
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^1.10.6
  firebase_auth: ^3.3.6
  cloud_firestore: ^3.1.5
  firebase_storage: ^10.2.3
  provider: ^6.1.3
  flutter_localizations:
    sdk: flutter
import 'package:firebase_core/firebase_core.dart';
import 'package:flutter/material.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp();
  runApp(MyApp());
}
import 'package:firebase_auth/firebase_auth.dart';

Future<User?> signInWithEmailPassword(String email, String password) async {
  try {
    final UserCredential userCredential = await FirebaseAuth.instance.signInWithEmailAndPassword(
      email: email,
      password: password,
    );
    return userCredential.user;
  } catch (e) {
    print("Error: $e");
    return null;
  }
}
import 'package:cloud_firestore/cloud_firestore.dart';

Future<void> createUserProfile(String userId, String name) async {
  await FirebaseFirestore.instance.collection('users').doc(userId).set({
    'name': name,
    'createdAt': Timestamp.now(),
  });
}
import 'package:flutter/material.dart';

class SplashScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(child: Text('Sehet & Imaan Adventure')),
    );
  }
}
import 'package:flutter/material.dart';

class OnboardingScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return PageView(
      children: [
        OnboardingPage(title: 'Learn Sunnah Habits', description: 'Description here'),
        OnboardingPage(title: 'Track Your Health', description: 'Description here'),
        OnboardingPage(title: 'Collect Stars', description: 'Description here'),
      ],
    );
  }
}

class OnboardingPage extends StatelessWidget {
  final String title;
  final String description;

  OnboardingPage({required this.title, required this.description});

  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text(title),
        Text(description),
      ],
    );
  }
}
import 'package:flutter/material.dart';

class LoginScreen extends StatelessWidget {
  final TextEditingController emailController = TextEditingController();
  final TextEditingController passwordController = TextEditingController();

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          TextField(controller: emailController),
          TextField(controller: passwordController),
          ElevatedButton(
            onPressed: () async {
              final user = await signInWithEmailPassword(
                emailController.text,
                passwordController.text,
              );
              if (user != null) {
                Navigator.pushReplacementNamed(context, '/home');
              }
            },
            child: Text('Login'),
          ),
        ],
      ),
    );
  }
}
import 'package:flutter/material.dart';

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Column(
        children: [
          Text('Welcome to Sehet & Imaan Adventure'),
          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(context, '/habitTracker');
            },
            child: Text('Habit Tracker'),
          ),
          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(context, '/story');
            },
            child: Text('Islamic Stories'),
          ),
          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(context, '/dua');
            },
            child: Text('Daily Duas'),
          ),
          ElevatedButton(
            onPressed: () {
              Navigator.pushNamed(context, '/rewards');
            },
            child: Text('My Rewards'),
          ),
        ],
      ),
    );
  }
}
import 'package:flutter/material.dart';

class HabitTrackerScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView(
        children: [
          HabitCard(habit: 'Brush Teeth'),
          HabitCard(habit: 'Say Bismillah'),
          HabitCard(habit: 'Sleep Early'),
        ],
      ),
    );
  }
}

class HabitCard extends StatelessWidget {
  final String habit;

  HabitCard({required this.habit});

  @override
  Widget build(BuildContext context) {
    return ListTile(
      title: Text(habit),
      trailing: Icon(Icons.check_box_outline_blank),
    );
  }
}
import 'package:flutter/material.dart';

class StoryScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: ListView(
        children: [
          StoryCard(title: 'Story 1', content: 'Content here'),
          StoryCard(title: 'Story 2', content: 'Content here'),
        ],
      ),
    );
  }
}

class StoryCard extends StatelessWidget {
  final String title;
  final String content;

  StoryCard({required this.title, required this.content});

  @override
  Widget build(BuildContext context) {
    return Card(
      child: ListTile(
        title: Text(title),
        subtitle: Text(content),
      ),
    );
  }
}
import 'package:flutter/material.dart';

class DuaScreen extends StatelessWidget {
  @override
 
::contentReference[oaicite:12]{index=12}
 

Sehet &amp; Imaan Adventure An engaging mobile app that teaches Islamic habits, health, and character to cp's core values: le
