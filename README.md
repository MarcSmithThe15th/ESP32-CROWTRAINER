# Ball Counter Project with ESP32 and Firebase 
**This repo is under construction, might be almost blank if you land on it (2024-11-25).
**The README.md document has been written by ChatGPT, might contain errors
## Table of Contents 
- [Introduction](#introduction)
- [Features](#features)
- [Hardware Requirements](#hardware-requirements)
- [Software Requirements](#software-requirements)
- [Circuit Diagram](#circuit-diagram)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Web Application](#web-application)
- [Firebase Setup](#firebase-setup)
- [Acknowledgments](#acknowledgments)
- [License](#license)

## Introduction 

This project is a ball counting system using an ESP32 microcontroller and Firebase Realtime Database. The ESP32 counts the number of balls detected by a sensor and sends the data to Firebase. A web application retrieves this data in real-time and displays it to the user. Everytime a ball is detected, a signal is sent to a linear actuator to open a door for a certain period of time and the door is than closed. The system also includes controls to open and close a door using buttons connected to the ESP32.

## Features 
 
- **Real-time Ball Counting** : Counts balls passing through a sensor and updates the count in real-time.
 
- **Firebase Integration** : Sends data to Firebase Realtime Database for storage and retrieval.
 
- **Web Application** : Displays the ball count and system status on a web page.
 
- **Door Control** : Allows manual opening and closing of a door via connected buttons.
 
- **ESP32-Based** : Utilizes the powerful ESP32 microcontroller with Wi-Fi capabilities.

## Hardware Requirements 
 
- **ESP32 Development Board**
 
- **Ball Detection Sensor**  (e.g., IR sensor, photodiode) connected to GPIO pin 13
 
- **Open Door Button**  connected to GPIO pin 27
 
- **Close Door Button**  connected to GPIO pin 14
 
- **Door Control Outputs** :
  - Open Signal: GPIO pin 25

  - Close Signal: GPIO pin 26
 
- **LED Indicator**  (optional) connected to GPIO pin 33
 
- **Power Supply**  for the ESP32
 
- **Breadboard and Jumper Wires**  for connections

## Software Requirements 
 
- **Visual Studio Code**  with **PlatformIO**  extension
 
- **Firebase ESP32 Client Library**  by Mobizt
 
- **Firebase Account**  with Realtime Database enabled
 
- **Web Hosting Service**  (optional, Firebase Hosting can be used)
 
- **Web Browser**  for accessing the web application

## Circuit Diagram 
*(Insert circuit diagram image here if available)*
## Installation 

### 1. Set Up Hardware 

- Connect the ball detection sensor to GPIO pin 13.

- Connect the open door button to GPIO pin 27.

- Connect the close door button to GPIO pin 14.

- Connect the door control outputs to GPIO pins 25 (open signal) and 26 (close signal).

- Connect the LED indicator to GPIO pin 33 (optional).

- Power the ESP32 using a suitable power source.

### 2. Install Visual Studio Code and PlatformIO 
 
- Download and install [Visual Studio Code](https://code.visualstudio.com/) .
 
- Install the [PlatformIO IDE extension]()  for VSCode.

### 3. Install Required Libraries 

- Open VSCode and start PlatformIO.

- Open the project or create a new one for the ESP32.
 
- Install the **Firebase ESP32 Client**  library: 
  - Open the **PlatformIO Library Manager** .
 
  - Search for **"Firebase ESP32 Client"**  by **Mobizt** .
 
  - Click **Add to Project**  and select your project.

## Configuration 

### 1. Configure Wi-Fi Credentials 
In the main `.cpp` file of your PlatformIO project, update the following lines with your Wi-Fi network's SSID and password:

```cpp
const char* ssid = "YOUR_WIFI_SSID";
const char* password = "YOUR_WIFI_PASSWORD";
```

### 2. Configure Firebase Credentials 

Set your Firebase project credentials in the code:


```cpp
#define FIREBASE_HOST "YOUR_FIREBASE_PROJECT_ID.firebaseio.com"
#define FIREBASE_API_KEY "YOUR_FIREBASE_API_KEY"
```
 
- Replace `YOUR_FIREBASE_PROJECT_ID` with your actual Firebase project ID.
 
- Replace `YOUR_FIREBASE_API_KEY` with your Firebase Web API Key found in the project settings.

### 3. Update Database Rules (For Testing) 

For testing purposes, you may set your Firebase Realtime Database rules to allow public read and write access:


```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```
**Note** : This setting is not secure. Ensure you update the rules to secure your database in a production environment.
## Usage 

### 1. Build and Upload the Firmware 

- Connect your ESP32 to the computer via USB.

- In VSCode, select the correct serial port for your ESP32.
 
- Build and upload the project using PlatformIO's controls (e.g., click on **PlatformIO: Upload** ).

### 2. Run the System 

- Power on the ESP32 if not already powered via USB.

- The ESP32 will connect to the configured Wi-Fi network and initialize Firebase.

- When a ball is detected by the sensor, the counter increments, and data is sent to Firebase.

- Use the open and close door buttons to control the door mechanism.

### 3. Monitor via Web Application 

- Access the web application through your hosting service or Firebase Hosting URL.

- The web app will display the current ball count and system status in real-time.

## Web Application 

### Features 

- Displays the number of balls counted.

- Shows the last reset time and build date (if provided).

- Automatically refreshes data every few seconds.

### Setup 
 
1. **Configure Firebase in Web App** In your `index.html` file, update the Firebase configuration:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_FIREBASE_API_KEY",
  authDomain: "YOUR_FIREBASE_PROJECT_ID.firebaseapp.com",
  databaseURL: "https://YOUR_FIREBASE_PROJECT_ID.firebaseio.com",
  projectId: "YOUR_FIREBASE_PROJECT_ID",
  storageBucket: "YOUR_FIREBASE_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```
 
2. **Deploy the Web App** 
  - Use Firebase Hosting or another web hosting service to deploy your web application.
 
  - Follow Firebase Hosting setup instructions [here]() .

## Firebase Setup 

### 1. Create a Firebase Project 
 
- Go to [Firebase Console]()  and create a new project.

### 2. Enable Realtime Database 
 
- In your Firebase project, navigate to **Database**  > **Realtime Database** .
 
- Click on **Create Database**  and select your preferred location.

- Choose the appropriate security rules.

### 3. Obtain Firebase Configuration 
 
- In the Firebase Console, go to **Project Settings** .
 
- Under **Your Apps** , select **Web App**  and register an app if you haven't already.

- Copy the Firebase configuration object to use in your web app and ESP32 code.

## Acknowledgments 
 
- **Firebase ESP32 Client Library**  by Mobizt
 
- **Firebase**  for providing the Realtime Database and hosting services
 
- **PlatformIO**  and **Visual Studio Code**  for their development tools
 
- **Arduino Community**  for extensive resources and support

## License 
This project is licensed under the MIT License - see the [LICENSE]()  file for details.

---

**Disclaimer** : Ensure you secure your Firebase Realtime Database by updating the security rules before deploying this project in a production environment. Replace all placeholder values with your actual configuration details.

---

You can now copy and paste this text into your `README.md` file. The markdown formatting should be preserved, and all code snippets are properly formatted.
Let me know if you need any further assistance!
