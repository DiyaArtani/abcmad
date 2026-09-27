# abcmad
1) Practical 2
Write a dart program to demonstrate variables and datatypes
void main() {
  int age = 20;

  double height = 5.9;

  String name = "Diya";

  bool isStudent = true;

  dynamic value = "Hello";
  value = 100;

  print("Name: $name");
  print("Age: $age");
  print("Height: $height");
  print("Student: $isStudent");
  print("Dynamic Value: $value");
}

if, else if, switch case
void main() {
  int num = 10;

  if (num > 0) {
    print("Positive Number");
  } else {
    print("Negative Number");
  }
}

void main() {
  int marks = 75;

  if (marks >= 90) {
    print("Grade A");
  } else if (marks >= 75) {
    print("Grade B");
  } else if (marks >= 50) {
    print("Grade C");
  } else {
    print("Fail");
  }
}

void main() {
  int day = 3;

  switch (day) {
    case 1:
      print("Monday");
      break;
    case 2:
      print("Tuesday");
      break;
    case 3:
      print("Wednesday");
      break;
    case 4:
      print("Thursday");
      break;
    default:
      print("Invalid Day");
  }
}

for,while,do while
void main() {
  for (int i = 1; i <= 5; i++) {
    print("Iteration: $i");
  }
}

void main() {
  int i = 1;

  while (i <= 5) {
    print("Iteration: $i");
    i++;
  }
}

void main() {
  int i = 1;

  do {
    print("Iteration: $i");
    i++;
  } while (i <= 5);
}

functions
without p and r
void greet() {
  print("Welcome to Dart");
}

void main() {
  greet();
}

with p and without r
void greet(String name) {
  print("Hello, $name");
}

void main() {
  greet("Diya");
}

without p and with r
int getNumber() {
  return 100;
}

void main() {
  int num = getNumber();
  print("Number: $num");
}

 with p and r 
int add(int a, int b) {
  return a + b;
}

void main() {
  int result = add(10, 20);
  print("Sum = $result");
}

lambda 
void main() {
  var square = (int n) => n * n;

  print(square(5));
}

recursive
int factorial(int n) {
  if (n == 0 || n == 1) {
    return 1; // Base case
  }
  return n * factorial(n - 1);
}

void main() {
  int num = 5;
  print("Factorial of $num = ${factorial(num)}");
}

2) Practical 3
Implement any simple class with object utilization and also show the usage of static
member
class Student {
  String name;
  static String schoolName = "Jai Hind college";

  Student(this.name);

  void displayInfo() {
    print('\nStudent Name: $name');
    print('School Name: ${Student.schoolName}');
  }
}

void main() {
  var student1 = Student("Diya ");
  var student2 = Student("Riya");

  student1.displayInfo();
  student2.displayInfo();

  print('\nAfter changing the schoolname');
  Student.schoolName = "KC college";

  student1.displayInfo();
  student2.displayInfo();
}

Implement single inheritance
class Animal {
  String name;

  Animal(this.name);

  void eat() {
    print('$name is eating.');
  }
}

class Dog extends Animal {
  String breed;

  Dog(String name, this.breed) : super(name);

  void bark() {
    print('$name the $breed says: Woof!');
  }
}

void main() {
  var myDog = Dog('Tommy', 'Golden Retriever');
  myDog.eat();
  myDog.bark();
  print('Dog name is: ${myDog.name}');
}

Implement multilevel inheritance
class Animal {
  void eat() {
    print("This animal can eat.");
  }
}

class Mammal extends Animal {
  void breathe() {
    print("This mammal can breathe.");
  }
}

class Dog extends Mammal {
  void bark() {
    print("This dog can bark.");
  }
}

void main() {
  Dog myDog = Dog();
  myDog.eat();
  myDog.breathe();
  myDog.bark();
}

Implement multiple interface
class Flyable {
  void fly() {
    print("Flying in the air...");
  }
}

class Swimmable {
  void swim() {
    print("Swimming in the water...");
  }
}

class Robot implements Flyable, Swimmable {
  String name;
  Robot(this.name);

  @override
  void fly() {
    print('$name is using a jet to fly!');
  }

  void swim() {
    print('$name is using propellers to swim!');
  }
}

void main() {
  var myRobot = Robot("Chiti");
  myRobot.fly();
  myRobot.swim();
}

Implement the concept of mixin
mixin Swimmer {
  void swim() {
    print('I am swimming!');
  }
}

mixin Flyer {
  void fly() {
    print('I am flying!');
  }
}

class Animal {
  String name;
  Animal(this.name);
}

class Duck extends Animal with Swimmer, Flyer {
  Duck(String name) : super(name);
}

class Fish extends Animal with Swimmer {
  Fish(String name) : super(name);
}

void main() {
  print('--- Duck ---');
  var donald = Duck('Donald');
  print('Name: ${donald.name}');
  donald.swim();
  donald.fly();

  print('\n--- Fish ---');
  var nemo = Fish('Nemo');
  print('Name: ${nemo.name}');
  nemo.swim();
}



3) Practical 4 - Calculator
main.dart
class _MyHomePageState extends State<MyHomePage> {
  final TextEditingController _num1Controller = TextEditingController();
  final TextEditingController _num2Controller = TextEditingController();
  String _result = "Result: ";

  void _calculate(String operation) {
    double? num1 = double.tryParse(_num1Controller.text);
    double? num2 = double.tryParse(_num2Controller.text);

    if(num1 == null || num2 == null) {
      setState(() {
        _result = " Please enter Valid number";
      });
      return;
    }

    setState(() {
      switch(operation) {
        case '+':
          _result = "Result: ${num1 + num2}";
          break;
        case '-':
          _result = "Result: ${num1 - num2}";
          break;
        case '*':
          _result = "Result: ${num1 * num2}";
          break;
        case '/':
          if (num2 != 0) {
            _result = "Result: ${num1 / num2}";
          }else {
            _result ="cannot divide ny zero";
          }
          break;
      }
    });
    }
~~
body: Center(
        child: Column(
          mainAxisAlignment: .center,
          children: [
            TextField(
              controller: _num1Controller,
              decoration: const InputDecoration(
                labelText: "First Number"
              ),
            ),
            const SizedBox(),
            TextField(
              controller: _num2Controller,
              decoration: const InputDecoration(
                  labelText: "Second Number"
              ),
            ),
            const SizedBox(),
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceEvenly,
              children: [
                ElevatedButton(
                    onPressed: () => _calculate('+'),
                    child: const Text('+'),),
                ElevatedButton(
                  onPressed: () => _calculate('-'),
                  child: const Text('-'),),
                ElevatedButton(
                  onPressed: () => _calculate('*'),
                  child: const Text('*'),),
                ElevatedButton(
                  onPressed: () => _calculate('/'),
                  child: const Text('/'),),
                ],
            ),
                const SizedBox(),
                Text(
                  _result,
                ),
          ],
        ),
      ),
    );
  }

  @override
  void dispose(){
    _num2Controller.dispose();
    _num2Controller.dispose();
    super.dispose();
  }
}




4) Practical 5 - registration page and login page 
registration 
class _RegistrationPageState extends State<RegistrationPage> {
  final TextEditingController nameController = TextEditingController();
  final TextEditingController emailidController = TextEditingController();
  final TextEditingController mobilenoController = TextEditingController();

  String gender ="Male";

  bool reading = false;
  bool music = false;
  bool sports = false;
  String output ="";

  void submitData(){
    List<String> hobbies =[];
    if (reading) hobbies.add("Reading");
    if (music) hobbies.add("Music");
    if (sports) hobbies.add("Sports");

    setState(() {
      output ='''
      Name: ${nameController.text}
      Email: ${emailidController.text}
      Mobile:${mobilenoController.text}
      Gender: $gender
      Hobbies: ${hobbies.join(",")}
      ''';
    });
  }
~~
body: SingleChildScrollView(
        child: Column(
          crossAxisAlignment:crossAxisAlignment.start,
          children: [
            TextField(
              controller: nameController,
              decoration: InputDecoration(
                labelText: "Name"
              ),
            ),

            SizedBox(height:15),

            TextField(
              controller: emailidController,
              decoration: InputDecoration(
                labelText: "Email",
              ),
            ),

            SizedBox(),

            TextField(
              controller: mobilenoController,
              decoration: InputDecoration(
                labelText: "Mobile no",
              ),
            ),

            SizedBox(),

            Text(
              "Gender"
            ),

            RadioListTile(
              title: Text("Male"),
              value:"Male",
              groupValue: gender,
              onChanged: (value){
                setState(() {
                  gender = value.toString();
                });
              },
            ),

            RadioListTile(
              title: Text("Female"),
              value:"Female",
              groupValue: gender,
              onChanged: (value){
                setState(() {
                  gender = value.toString();
                });
              },
            ),

            SizedBox(),

            Text(
              "Hobbies"
            ),

            CheckboxListTile(
                title:Text("Reading"),
                value: reading,
                onChanged:(value){
                  setState(() {
                    reading = value!;
                  });
                }),

            CheckboxListTile(
                title:Text("Music"),
                value: music,
                onChanged:(value){
                  setState(() {
                    music = value!;
                  });
                }),

            CheckboxListTile(
                title:Text("Sports"),
                value: sports,
                onChanged:(value){
                  setState(() {
                    sports = value!;
                  });
                }),

            SizedBox(),

            Center(
              child:ElevatedButton(
                  onPressed: submitData,
                  child: Text("Submit")),
            ),

            SizedBox(),

            Text(
              "Entered Details",
            ),

            SizedBox(),

            Text(
              output
            )
          ],
        ),
      ),
    );
  }

}


Login Page
without validate
class _RegistrationPageState extends State<RegistrationPage> {
  final TextEditingController usernameController = TextEditingController();
  final TextEditingController passwordController = TextEditingController();

  String message = " ";

  void login(){
    String username = usernameController.text;
    String password = passwordController.text;

    setState(() {
      if(username == "Diya" && password == "123456"){
        message ="Login successful";
      }else{
        message ="Incorrect email or password";
      }
    });
  }
~~
body: Center(
        child: Column(
          mainAxisAlignment: .center,
          children: [
            TextField(
              controller: usernameController,
              decoration: InputDecoration(
                  labelText: "UserName"
              ),
            ),

            SizedBox(),

            TextField(
              controller: passwordController,
              decoration: InputDecoration(
                labelText: "password",
              ),
            ),

            ElevatedButton(
                  onPressed: login,
                  child: Text("Login")
            ),

            Text(
              message,
            ),

          ],
        ),
      ),
    );
  }

}


with validate
class _RegistrationPageState extends State<RegistrationPage> {
  final formKey = GlobalKey<FormState>();
  final TextEditingController usernameController = TextEditingController();
  final TextEditingController passwordController = TextEditingController();

  void login(){
    if(formKey.currentState!.validate()) {
      String message;
      if(usernameController.text == "Diya" && passwordController.text == "123456"){
        message ="Login successful";
      }else{
        message ="Incorrect email or password";
      }
      ScaffoldMessenger.of(context).showSnackBar(
          SnackBar(content: Text(message)),
    );
  }
    }
~~
body: Center(
        child: Column(
          mainAxisAlignment: .center,
          children: [
            TextFormField(
              controller: usernameController,
              decoration: InputDecoration(
                  labelText: "UserName",
              ),
              validator :(value) {
                if (value == null || value.isEmpty){
                  return"Enter username";
              }
                return null;
              },
            ),

            SizedBox(),

            TextFormField(
              controller: passwordController,
              decoration: InputDecoration(
                labelText: "password",
              ),
              validator :(value) {
                if (value == null || value.isEmpty){
                  return"Enter password";
                }
                return null;
              },
            ),

            ElevatedButton(
                onPressed: login,
                child: Text("Login")
            ),
          ],
        ),
      ),
    );
  }

}




5) Practical 6 - Navigation
same as prac 5 
import 'registrationpage.dart'
just change this in login
void login(){
    if(formKey.currentState!.validate()) {
      String message;
      if(usernameController.text == "Diya" && passwordController.text == "123456"){
        message ="Login successful";
	Navigator.push(
	  context,
	  MaterialPageRoute(builder: (context)=>RegistrationPage()),
	  );
      }else{
        message ="Incorrect email or password";
      }
      ScaffoldMessenger.of(context).showSnackBar(
          SnackBar(content: Text(message)),
    );
  }
    }

6) Practical 7 - Smart Device Controller 
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: SmartDeviceController(),
    );
  }
}

class SmartDeviceController extends StatefulWidget {
  const SmartDeviceController({super.key});

  @override
  State<SmartDeviceController> createState() =>
      _SmartDeviceControllerState();
}

class _SmartDeviceControllerState extends State<SmartDeviceController> {
  final List<String> devices = [
    "Living Room Light",
    "Bedroom Lamp",
    "Smart TV",
    "Air Conditioner",
  ];

  String selectedDevice = "Living Room Light";
  bool isOn = false;
  double brightness = 50;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Smart Device Controller"),
        centerTitle: true,
      ),
      body: Padding(
        padding: const EdgeInsets.all(20),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            const Text(
              "Select Device",
              style: TextStyle(
                fontSize: 18,
                fontWeight: FontWeight.bold,
              ),
            ),

            const SizedBox(height: 10),

            DropdownButton<String>(
              value: selectedDevice,
              isExpanded: true,
              items: devices.map((device) {
                return DropdownMenuItem<String>(
                  value: device,
                  child: Text(device),
                );
              }).toList(),
              onChanged: (value) {
                setState(() {
                  selectedDevice = value!;
                });
              },
            ),

            const SizedBox(height: 30),

            Row(
              mainAxisAlignment: MainAxisAlignment.spaceBetween,
              children: [
                const Text(
                  "Power",
                  style: TextStyle(fontSize: 18),
                ),
                Switch(
                  value: isOn,
                  onChanged: (value) {
                    setState(() {
                      isOn = value;
                    });
                  },
                ),
              ],
            ),

            // Show brightness only when power is ON
            if (isOn) ...[
              const SizedBox(height: 20),

              const Text(
                "Brightness",
                style: TextStyle(fontSize: 18),
              ),

              Slider(
                value: brightness,
                min: 0,
                max: 100,
                divisions: 100,
                label: "${brightness.round()}%",
                onChanged: (value) {
                  setState(() {
                    brightness = value;
                  });
                },
              ),

              Center(
                child: Text(
                  "${brightness.round()}%",
                  style: const TextStyle(
                    fontSize: 18,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ),
            ],

            const SizedBox(height: 30),

            Center(
              child: ElevatedButton(
                onPressed: () {
                  String powerStatus = isOn ? "ON" : "OFF";

                  String message =
                      "Device: $selectedDevice\n"
                      "Power: $powerStatus";

                  if (isOn) {
                    message +=
                        "\nBrightness: ${brightness.round()}%";
                  }

                  print(message);

                  showDialog(
                    context: context,
                    builder: (context) => AlertDialog(
                      title: const Text("Device Settings"),
                      content: Text(message),
                      actions: [
                        TextButton(
                          onPressed: () => Navigator.pop(context),
                          child: const Text("OK"),
                        ),
                      ],
                    ),
                  );
                },
                child: const Text("Submit"),
              ),
            ),
          ],
        ),
      ),
    );
  }
}




7) Practical 8 - Url Naviagtion
import 'package:flutter/material.dart';
import 'package:url_launcher/url_launcher.dart';

void main() {
  runApp(
    const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: HomePage(),
    ),
  );
}

class HomePage extends StatelessWidget {
  const HomePage({super.key});

  Future<void> openGoogle() async {
    final Uri url = Uri.parse("https://www.google.com/");

    await launchUrl(
      url,
      mode: LaunchMode.externalApplication,
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("URL Navigation"),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: openGoogle,
          child: const Text("Open Google"),
        ),
      ),
    );
  }
}




8) Practical 9 - Validation
import 'package:flutter/material.dart';

void main() {
  runApp(const MaterialApp(home: RegistrationPage()));
}

class RegistrationPage extends StatefulWidget {
  const RegistrationPage({super.key});

  @override
  State<RegistrationPage> createState() => _RegistrationPageState();
}

class _RegistrationPageState extends State<RegistrationPage> {
  final formKey = GlobalKey<FormState>();

  final nameController = TextEditingController();
  final emailController = TextEditingController();
  final mobileController = TextEditingController();
  final passwordController = TextEditingController();
  final confirmPasswordController = TextEditingController();

  void submit() {
    if (formKey.currentState!.validate()) {
      ScaffoldMessenger.of(context).showSnackBar(
        const SnackBar(content: Text('Registration successful!')),
      );
    }
  }

  @override
  void dispose() {
    nameController.dispose();
    emailController.dispose();
    mobileController.dispose();
    passwordController.dispose();
    confirmPasswordController.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Registration Page')),
      body: SingleChildScrollView(
        padding: const EdgeInsets.all(20),
        child: Form(
          key: formKey,
          child: Column(
            children: [
              TextFormField(
                controller: nameController,
                decoration: const InputDecoration(labelText: 'Name'),
                validator: (value) {
                  if (value == null || value.trim().isEmpty) {
                    return 'Enter your name';
                  }
                  return null;
                },
              ),

              TextFormField(
                controller: emailController,
                decoration: const InputDecoration(labelText: 'Email'),
                validator: (value) {
                  if (value == null || value.trim().isEmpty) {
                    return 'Enter your email';
                  }
                  if (!value.contains('@') || !value.contains('.')) {
                    return 'Enter a valid email';
                  }
                  return null;
                },
              ),

              TextFormField(
                controller: mobileController,
                decoration: const InputDecoration(labelText: 'Mobile Number'),
                keyboardType: TextInputType.phone,
                validator: (value) {
                  if (value == null || !RegExp(r'^\d{10}$').hasMatch(value)) {
                    return 'Enter a 10-digit mobile number';
                  }
                  return null;
                },
              ),

              TextFormField(
                controller: passwordController,
                decoration: const InputDecoration(labelText: 'Password'),
                obscureText: true,
                validator: (value) {
                  if (value == null || value.length < 6) {
                    return 'Password must have at least 6 characters';
                  }
                  return null;
                },
              ),

              TextFormField(
                controller: confirmPasswordController,
                decoration: const InputDecoration(
                  labelText: 'Confirm Password',
                ),
                obscureText: true,
                validator: (value) {
                  if (value != passwordController.text) {
                    return 'Passwords do not match';
                  }
                  return null;
                },
              ),

              const SizedBox(height: 20),

              ElevatedButton(
                onPressed: submit,
                child: const Text('Submit'),
              ),
            ],
          ),
        ),
      ),
    );
  }
}




9) Practical 10 - Authetication
create flutter project
create firebase project 
authentication enable with email and password
create a andriod app with same project name -com.example.packages
Download the json file and add it to your project in src folder
Add this in the pubspec.yaml
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^4.1.0
  firebase_auth: ^6.0.2
create web app
copy api keys
create dart file in lib firebase_options.dart
import 'package:firebase_core/firebase_options.dart';
class DefaultFirebaseOptions{
  static FirebaseOptions get currentPlatform{
    return const FirebaseOptions(
        apiKey: "AIzaSyApk4N2BDH9IweyRn4_Z7LRpaRza95j81s",
        authDomain: "project-9b2e8.firebaseapp.com",
        projectId: "project-9b2e8",
        storageBucket: "project-9b2e8.firebasestorage.app",
        messagingSenderId: "728739034827",
        appId: "1:728739034827:web:a5d8589b4e75ceb7948d4e",
        measurementId: "G-90C22SFTCD"
    );
  }
}
Add the following code in build.gradle.kts(outside)
buildscript {
    repositories {
        google()
        mavenCentral()
    }
    dependencies {
        classpath("com.android.tools.build:gradle:7.4.2")
        classpath("com.google.gms:google-services:4.3.15")
    }
}
Add the following code in build.gradle.kts
plugins {
    id("com.android.application")
    // The Flutter Gradle Plugin must be applied after the Android plugin.
    id("dev.flutter.flutter-gradle-plugin")
    id("com.google.gms.google-services")
}
Create a dart file(login.dart)
import 'package:databaseprac/main.dart';
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'package:firebase_auth/firebase_auth.dart';
import 'firebase_options.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Firebase Demo',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: const AuthScreen(),
    );
  }
}

class AuthScreen extends StatefulWidget {
  const AuthScreen({super.key});

  @override
  State<AuthScreen> createState() => _AuthScreenState();
}

class _AuthScreenState extends State<AuthScreen> {
  final _emailController = TextEditingController();
  final _passwordController = TextEditingController();
  bool isLogin = true;

  Future<void> _authAction() async {
    try {
      if (isLogin) {
        final userCredential =
            await FirebaseAuth.instance.signInWithEmailAndPassword(
          email: _emailController.text.trim(),
          password: _passwordController.text.trim(),
        );

        if (userCredential.user != null) {
          Navigator.pushReplacement(
            context,
            MaterialPageRoute(builder: (context) => const WelcomePage()),
          );
        }
      } else {
        await FirebaseAuth.instance.createUserWithEmailAndPassword(
          email: _emailController.text.trim(),
          password: _passwordController.text.trim(),
        );

        ScaffoldMessenger.of(context).showSnackBar(
          const SnackBar(content: Text('Registration successful! Please login')),
        );

        setState(() {
          isLogin = true;
        });
      }
    } catch (e) {
      ScaffoldMessenger.of(context).showSnackBar(
        SnackBar(content: Text('Error: $e')),
      );
    }
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text(isLogin ? 'Login' : 'Sign UP ')),
      body: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            TextField(
              controller: _emailController,
              decoration: const InputDecoration(labelText: 'Email'),
            ),
            TextField(
              controller: _passwordController,
              obscureText: true,
              decoration: const InputDecoration(labelText: 'Password'),
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _authAction,
              child: Text(isLogin ? 'Login' : 'Sign Up'),
            ),
            TextButton(
              onPressed: () => setState(() => isLogin = !isLogin),
              child: Text(
                isLogin ? 'Create an account' : 'Already have an account? login',
              ),
            ),
          ],
        ),
      ),
    );
  }
}

class WelcomePage extends StatelessWidget {
  const WelcomePage({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Welcome'),
        actions: [
          IconButton(
            icon: const Icon(Icons.logout),
            onPressed: () async {
              await FirebaseAuth.instance.signOut();
              Navigator.pushReplacement(
                context,
                MaterialPageRoute(builder: (context) => const AuthScreen()),
              );
            },
          ),
        ],
      ),
      body: const Center(
        child: Text(
          'Welcome! You are logged in.',
          style: TextStyle(fontSize: 20),
        ),
      ),
    );
  }
}



10) Practical 11 - Firestore
firestore database in test mode
Add this in the pubspec.yaml
dependencies:
  flutter:
    sdk: flutter
  firebase_core: ^4.1.0
  firebase_auth: ^6.0.2
  cloud_firestore :^6.0.1
Create a dart file and add the following code (firestorex.dart)
import 'package:databaseprac/main.dart';
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';
import 'package:cloud_firestore/cloud_firestore.dart';
import 'firebase_options.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  await Firebase.initializeApp(
    options: DefaultFirebaseOptions.currentPlatform,
  );
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Firebase Demo',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: AddStudentPage(),
    );
  }
}

class AddStudentPage extends StatefulWidget {
  const AddStudentPage({super.key});

  @override
  State<AddStudentPage> createState() => _AddStudentPageState();
}

class _AddStudentPageState extends State<AddStudentPage> {
  final _nameController = TextEditingController();
  final _ageController = TextEditingController();

  Future<void> _addStudent() async {
    try {
      String name1 = _nameController.text.trim();
      int age = int.tryParse(_ageController.text.trim()) ?? 0;

      if (name1.isEmpty || age <= 0) {
        _showAlert("Error", "Please enter a valid name and age");
        return;
      }

      await FirebaseFirestore.instance.collection("students").add({
        'name': name1,
        'age': age,
        'createAt': FieldValue.serverTimestamp(),
      });

      _showAlert("Success", "Student added successfully");
      _nameController.clear();
      _ageController.clear();
    } catch (e) {
      _showAlert('Error', e.toString());
    }
  }

  void _showAlert(String title, String message) {
    showDialog(
      context: context,
      builder: (context) => AlertDialog(
        title: Text(title),
        content: Text(message),
        actions: [
          TextButton(
            onPressed: () => Navigator.pop(context),
            child: const Text("OK"),
          ),
        ],
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text("Add student")),
      body: Padding(
        padding: const EdgeInsets.all(16),
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            TextField(
              controller: _nameController,
              decoration: const InputDecoration(labelText: 'Student Name'),
            ),
            TextField(
              controller: _ageController,
              keyboardType: TextInputType.number,
              decoration: const InputDecoration(labelText: 'Age'),
            ),
            const SizedBox(height: 20),
            ElevatedButton(
              onPressed: _addStudent,
              child: const Text("Add Student"),
            ),
          ],
        ),
      ),
    );
  }
}



11) Practical 12 - Gestures
import 'package:flutter/material.dart';

void main() {
  runApp(const GestureApp());
}

class GestureApp extends StatelessWidget {
  const GestureApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: GestureDemo(),
    );
  }
}

class GestureDemo extends StatefulWidget {
  const GestureDemo({super.key});

  @override
  State<GestureDemo> createState() => _GestureDemoState();
}

class _GestureDemoState extends State<GestureDemo> {
  double left = 100;
  double top = 200;

  void showSnackBar(String message) {
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        content: Text(message),
        duration: const Duration(seconds: 1),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Gesture Demo"),
        centerTitle: true,
      ),
      body: Stack(
        children: [
          Positioned(
            left: left,
            top: top,
            child: GestureDetector(
              onTap: () {
                showSnackBar("Single Tap Detected!");
              },
              onDoubleTap: () {
                showSnackBar("Double Tap Detected!");
              },
              onLongPress: () {
                showSnackBar("Long Press Detected!");
              },

              // Move the container anywhere
              onPanUpdate: (details) {
                setState(() {
                  left += details.delta.dx;
                  top += details.delta.dy;
                });
              },

              child: Container(
                width: 150,
                height: 150,
                alignment: Alignment.center,
                decoration: BoxDecoration(
                  color: Colors.blue,
                  borderRadius: BorderRadius.circular(15),
                ),
                child: const Text(
                  "Tap / Move Me",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    color: Colors.white,
                    fontSize: 20,
                  ),
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }
}




12) Practical 13 - Animations
implicit animation
import 'package:flutter/material.dart';

void main() {
  runApp(const GestureApp());
}

class GestureApp extends StatelessWidget {
  const GestureApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: GestureDemo(),
    );
  }
}

class GestureDemo extends StatefulWidget {
  const GestureDemo({super.key});

  @override
  State<GestureDemo> createState() => _GestureDemoState();
}

class _GestureDemoState extends State<GestureDemo> {
  double left = 100;
  double top = 200;

  void showSnackBar(String message) {
    ScaffoldMessenger.of(context).showSnackBar(
      SnackBar(
        content: Text(message),
        duration: const Duration(seconds: 1),
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text("Gesture Demo"),
        centerTitle: true,
      ),
      body: Stack(
        children: [
          Positioned(
            left: left,
            top: top,
            child: GestureDetector(
              onTap: () {
                showSnackBar("Single Tap Detected!");
              },
              onDoubleTap: () {
                showSnackBar("Double Tap Detected!");
              },
              onLongPress: () {
                showSnackBar("Long Press Detected!");
              },

              // Move the container anywhere
              onPanUpdate: (details) {
                setState(() {
                  left += details.delta.dx;
                  top += details.delta.dy;
                });
              },

              child: Container(
                width: 150,
                height: 150,
                alignment: Alignment.center,
                decoration: BoxDecoration(
                  color: Colors.blue,
                  borderRadius: BorderRadius.circular(15),
                ),
                child: const Text(
                  "Tap / Move Me",
                  textAlign: TextAlign.center,
                  style: TextStyle(
                    color: Colors.white,
                    fontSize: 20,
                  ),
                ),
              ),
            ),
          ),
        ],
      ),
    );
  }
}

tween animation 
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatefulWidget {
  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _sizeAnimation;
  late Animation<Color?> _colorAnimation;

  @override
  void initState() {
    super.initState();

    _controller = AnimationController(
      vsync: this,
      duration: Duration(seconds: 1),
    );

    _sizeAnimation = Tween<double>(
      begin: 100,
      end: 200,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );

    _colorAnimation = ColorTween(
      begin: Colors.blue,
      end: Colors.red,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );
  }

  void _changeBox() {
    if (_controller.status == AnimationStatus.completed) {
      _controller.reverse();
    } else {
      _controller.forward();
    }
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Tween Animation'),
        ),
        body: Center(
          child: AnimatedBuilder(
            animation: _controller,
            builder: (context, child) {
              return Container(
                width: _sizeAnimation.value,
                height: _sizeAnimation.value,
                color: _colorAnimation.value,
              );
            },
          ),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: _changeBox,
          child: Icon(Icons.play_arrow),
        ),
        floatingActionButtonLocation:
            FloatingActionButtonLocation.centerFloat,
      ),
    );
  }
}

explicit animation
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatefulWidget {
  @override
  State<MyApp> createState() => _MyAppState();
}

class _MyAppState extends State<MyApp>
    with SingleTickerProviderStateMixin {
  late AnimationController _controller;
  late Animation<double> _buttonWidth;

  @override
  void initState() {
    super.initState();

    _controller = AnimationController(
      duration: Duration(seconds: 1),
      vsync: this,
    );

    _buttonWidth = Tween<double>(
      begin: 100,
      end: 300,
    ).animate(
      CurvedAnimation(
        parent: _controller,
        curve: Curves.easeInOut,
      ),
    );
  }

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Explicit Animation'),
        ),
        body: Center(
          child: AnimatedBuilder(
            animation: _controller,
            builder: (context, child) {
              return SizedBox(
                width: _buttonWidth.value,
                height: 50,
                child: ElevatedButton(
                  onPressed: () {
                    _controller.forward();
                  },
                  child: Text('Click Me'),
                ),
              );
            },
          ),
        ),
      ),
    );
  }

  @override
  void dispose() {
    _controller.dispose();
    super.dispose();
  }
}




13) Practical 14 - Packages
run on cmd - Flutter create --template=package my_calculator
open folder in android studio
lib/my_calculator.dart 
library my_calculator;

export 'src/calculator.dart';

lib/src/calculator.dart
class Calculator{
  int add(int a, int b) => a+b;
  int sub(int a, int b) => a-b;
  int multiply(int a, int b) => a*b;
  double division(int a, int b){
    if (b == 0) throw ArgumentError("Cannot divide by 0");
    return a/b;
  }

}

test/my_calculator_test.dart
import 'package:flutter_test/flutter_test.dart';

import 'package:my_calculator/my_calculator.dart';

void main() {
  final calculator = Calculator();

  test('addition',(){
    expect(calculator.add(2,1),3);
  });

  test('subtraction',(){
    expect(calculator.sub(2,1),1);
  });

  test('multiplication',(){
    expect(calculator.multiply(2,1),2);
  });

  test('division',(){
    expect(calculator.division(6,2),3);
  });

}

new project 
pubspec.yaml
dev_dependencies:
  flutter_test:
    sdk: flutter
  my_calculator:
    path: ../my_calculator

main.dart
import 'package:flutter/material.dart';
import 'package:my_calculator/my_calculator.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    final calculator = Calculator();
    final result = calculator.sub(20, 3);

    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(title: const Text("Calculator demo")),
        body: Center(child: Text("20 - 3 = $result")),
      ),
    );
  }
}



14) Alert dialog box
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: AlertDialogExample(),
    );
  }
}

class AlertDialogExample extends StatelessWidget {
  void _showAlertDialog(BuildContext context) {
    showDialog(
      context: context,
      //barrierDismissible: false,
      builder: (BuildContext context) {
        return AlertDialog(
          title: Text('Alert'),
          content: Text('This is a simple alert dialog.'),
          actions: [
            TextButton(
              child: Text('Cancel'),
              onPressed: () {
                // Perform some action
                Navigator.of(context).pop(); // Dismiss the dialog
              },
            ),
            ElevatedButton(
              child: Text('OK'),
              onPressed: () {
                // Perform some action
                print("You pressed OK");
                Navigator.of(context).pop();
              },
            ),
          ],
        );
      },
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('AlertDialog Demo')),
      body: Center(
        child: ElevatedButton(
          child: Text('Show Alert'),
          onPressed: () => _showAlertDialog(context),
        ),
      ),
    );
  }
}



15) checkbox
   children: [
                Checkbox(
                  value: isChecked,
                  onChanged: (bool? value) {
                    setState(() {
                      isChecked = value!;
                    });
                  },
                ),
                Text('Accept Terms'),
              ],



16) listsingleselection
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: SingleSelectionListScreen(),
    );
  }
}

class SingleSelectionListScreen extends StatefulWidget {
  @override
  _SingleSelectionListScreenState createState() => _SingleSelectionListScreenState();
}

class _SingleSelectionListScreenState extends State<SingleSelectionListScreen> {
  final List<String> items = [
    'Item A',
    'Item B',
    'Item 3',
    'Item 4',
    'Item 5',
  ];

  int? selectedIndex; // null initially — no selection

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Single Selection List')),
      body: ListView.builder(
        itemCount: items.length,
        itemBuilder: (context, index) {
          return RadioListTile<int>(
            title: Text(items[index]),
            value: index,
            groupValue: selectedIndex,
            onChanged: (int? value) {
              setState(() {
                selectedIndex = value;
                print(selectedIndex);
              });
            },
          );
        },
      ),
    );
  }
}



17) list with images
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: ImageListSelectionScreen(),
    );
  }
}

class ImageListSelectionScreen extends StatefulWidget {
  @override
  _ImageListSelectionScreenState createState() => _ImageListSelectionScreenState();
}

class _ImageListSelectionScreenState extends State<ImageListSelectionScreen> {
  final List<String> items = [
    'Apple',
    'Banana',
    'Cherry',
    'Grapes',
    'Orange',
  ];

  final List<String> imagePaths = [
    'assets/images/apple.jpeg',
    'assets/images/banana.jpeg',
    'assets/images/cherry.jpeg',
    'assets/images/grapes.jpeg',
    'assets/images/orange.jpeg',
  ];

  final Set<int> selectedIndexes = {};
  String selectedItemsText = '';

  void _updateSelectedItemsText() {
    final selectedItems = selectedIndexes.map((i) => items[i]).toList();
    setState(() {
      selectedItemsText = selectedItems.join(', ');
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('Local Image List with Selection')),
      body: Column(
        children: [
          Expanded(
            child: ListView.builder(
              itemCount: items.length,
              itemBuilder: (context, index) {
                return CheckboxListTile(
                  secondary: Image.asset(
                    imagePaths[index],
                    //width: 50,
                    //height: 50,
                    fit: BoxFit.cover,
                  ),
                  title: Text(items[index]),
                  value: selectedIndexes.contains(index),
                  onChanged: (bool? value) {
                    setState(() {
                      if (value == true) {
                        selectedIndexes.add(index);
                      } else {
                        selectedIndexes.remove(index);
                      }
                      _updateSelectedItemsText();
                    });
                  },
                );
              },
            ),
          ),
          Padding(
            padding: const EdgeInsets.all(16.0),
            child: Text(
              selectedItemsText.isEmpty
                  ? 'No items selected.'
                  : 'Selected: $selectedItemsText',
              style: TextStyle(fontSize: 16),
            ),
          ),
        ],
      ),
    );
  }
}


18) Listbox multiple
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
     // title: 'List Box Example with Multiple selection',
      home: ListBoxScreen(),
    );
  }
}

class ListBoxScreen extends StatefulWidget {
  @override
  _ListBoxScreenState createState() => _ListBoxScreenState();
}

class _ListBoxScreenState extends State<ListBoxScreen> {
  final List<String> items = List.generate(10, (i) => 'Item ${i + 1}');
  final Set<int> selectedIndexes = {};

  void _showSelectedItems() {
    final selectedItems = selectedIndexes.map((i) => items[i]).toList();

    showDialog(
        context: context,
        builder: (BuildContext context) {
          return AlertDialog(
              title: Text('Selected Items'),
              content: SingleChildScrollView(
                  child: ListBody(
                    children: selectedItems.map((item) => Text(item)).toList(),
                  ),
              ),
            actions: [
              TextButton(
                onPressed: () {
                  Navigator.of(context).pop();
                },
                child: Text('OK'),
              )
            ],
          );
        },
    );
  }
  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(title: Text('List Box Example with Multiple selection')),
        body: Column(
            children: [
        Expanded(
        child: ListView.builder(
        itemCount: items.length,
            itemBuilder: (context, index) {
              return CheckboxListTile(
                  title: Text(items[index]),
                  value: selectedIndexes.contains(index),
                  onChanged: (bool? value) {
                    setState(() {
                      if (value == true) {
                        selectedIndexes.add(index);
                      } else {
                        selectedIndexes.remove(index);
                      }
                    });
                  },
              );
            },
        ),
    ),
              Padding(
                padding: const EdgeInsets.all(16.0),
                child: ElevatedButton(
                  onPressed: _showSelectedItems,
                  child: Text('Show Selected Items')
                  ),
                ),

            ],
        ),
    );
  }
}


19) listbox multiple1
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
     // title: 'List Box Example with Multiple selection',
      home: ListBoxScreen(),
    );
  }
}

class ListBoxScreen extends StatefulWidget {
  @override
  _ListBoxScreenState createState() => _ListBoxScreenState();
}

class _ListBoxScreenState extends State<ListBoxScreen> {
  final List<String> items = List.generate(10, (i) => 'Item ${i + 1}');
  final Set<int> selectedIndexes = {};
  String selectedItemsText = '';

  void _showSelectedItems() {
    final selectedItems = selectedIndexes.map((i) => items[i]).toList();
    setState(() {
      selectedItemsText = selectedItems.join(', ');
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(title: Text('List Box Example with Multiple selection')),
        body: Column(
            children: [
        Expanded(
        child: ListView.builder(
        itemCount: items.length,
            itemBuilder: (context, index) {
              return CheckboxListTile(
                  title: Text(items[index]),
                  value: selectedIndexes.contains(index),
                  onChanged: (bool? value) {
                    setState(() {
                      if (value == true) {
                        selectedIndexes.add(index);
                      } else {
                        selectedIndexes.remove(index);
                      }
                    });
                  },
              );
            },
        ),
    ),
              Padding(
                padding: const EdgeInsets.all(16.0),
                child: ElevatedButton(
                  onPressed: _showSelectedItems,
                  child: Text('Show Selected Items')
                  ),
                ),
              Padding(
                padding: const EdgeInsets.all(16.0),
                child: Text(
                  selectedItemsText.isEmpty
                      ? 'No items selected.'
                      : 'Selected: $selectedItemsText',
                  style: TextStyle(fontSize: 16),
                ),
              ),
            ],
        ),
    );
  }
}



20) listbox multiple 2
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
     // title: 'List Box Example with Multiple selection',
      home: ListBoxScreen(),
    );
  }
}

class ListBoxScreen extends StatefulWidget {
  @override
  _ListBoxScreenState createState() => _ListBoxScreenState();
}

class _ListBoxScreenState extends State<ListBoxScreen> {
  final List<String> items = List.generate(10, (i) => 'Item ${i + 1}');
  final Set<int> selectedIndexes = {};
  String selectedItemsText = '';

  void _showSelectedItems() {
    final selectedItems = selectedIndexes.map((i) => items[i]).toList();
    setState(() {
      selectedItemsText = selectedItems.join(', ');
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
        appBar: AppBar(title: Text('List Box Example with Multiple selection')),
        body: Column(
            children: [
        Expanded(
        child: ListView.builder(
        itemCount: items.length,
            itemBuilder: (context, index) {
              return CheckboxListTile(
                  title: Text(items[index]),
                  value: selectedIndexes.contains(index),
                  onChanged: (bool? value) {
                    setState(() {
                      if (value == true) {
                        selectedIndexes.add(index);
                      } else {
                        selectedIndexes.remove(index);
                      }
                      _showSelectedItems();
                    });
                  },
              );
            },
        ),
    ),

              Padding(
                padding: const EdgeInsets.all(16.0),
                child: Text(
                  selectedItemsText.isEmpty
                      ? 'No items selected.'
                      : 'Selected: $selectedItemsText',
                  style: TextStyle(fontSize: 16),
                ),
              ),
            ],
        ),
    );
  }
}



21) listview
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'List Box Example',
      home: ListBoxScreen(),
    );
  }
}

class ListBoxScreen extends StatefulWidget {
  @override
  _ListBoxScreenState createState() => _ListBoxScreenState();
}

class _ListBoxScreenState extends State<ListBoxScreen> {
  // Sample list of items
  final List<String> items = List.generate(5, (index) => 'Item ${index + 1}');
  int? selectedIndex;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: Text('List Box Example')),
      body: ListView.builder(
        itemCount: items.length,
        itemBuilder: (context, index) {
          bool isSelected = selectedIndex == index;
         return ListTile(
           title: Text(items[index]),
           tileColor: isSelected ? Colors.blue :Colors.yellow,
            //selected: isSelected,
            onTap: () {
              setState(() {
                selectedIndex = index;
                print("Selected index: $selectedIndex"); // Debug print
              });
            },
         );
        },
      ),
    );
  }
}
