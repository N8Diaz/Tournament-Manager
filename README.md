# Tournament-Manager
A tournament system
CnCNet AI Command | Tactical Interface

Version: 1.0 
Type: Single-File Web Application (SPA)

📋 Overview

CnCNet AI Command is a tactical, cyberpunk-styled tournament management system designed to run entirely within a web browser. It serves as a comprehensive tool for organising gaming tournaments, specifically tailored for Command & Conquer but adaptable to any competitive game.

The application leverages Firebase Firestore for real-time data persistence and utilises CryptoJS to implement a client-side AES encryption layer for channel access.

✨ Key Features

🎮 Tournament Management

Flexible Formats: Supports Single Elimination and Group Stage (Round Robin) formats.

Team Sizes: Configurable for 1v1 and 2v2 matches.

Dynamic Brackets: Automatically generates visual bracket trees and group standings tables.

Real-Time Sync: Match results and bracket updates propagate instantly to all connected clients.

🏆 Hall of Fame

Live Leaderboards: Rankings are calculated dynamically from the entire match history in the database.

Deep Stats: Tracks ELO, Win/Loss ratios, and Tournament Wins.

Sorting & Filtering: * Filter by Game (e.g., Red Alert, Tiberian Sun).

Filter by Year.

Sort by any column (Rank, Name, Wins, ELO) by clicking the headers.

🗄️ Archive & Export

Historical Viewer: Browse detailed records of every tournament ever played.

PDF Export: Generate high-quality, printable PDF reports of tournament brackets and results using html2canvas and jsPDF.

🔒 Security (AES Layer)

Encrypted Access: Channel passwords are encrypted using AES-256 before being sent to the database.

Auto-Migration: The system detects legacy plaintext passwords and automatically upgrades them to encrypted hashes upon the first successful login.

Input Sanitization: Built-in protection against Cross-Site Scripting (XSS) in player names.

🚀 Installation & Setup

This application is a standalone HTML file. To make it functional, you must link it to a Firebase project.

1. Prerequisites

A Google Account.

A modern web browser (Chrome, Firefox, Edge).

2. Firebase Configuration

Go to the Firebase Console.

Create a new project.

Database: Navigate to Build > Cloud Firestore and create a database. (Start in Test Mode for initial setup).

Auth: Enable Authentication and turn on Anonymous sign-in provider.

Keys: Go to Project Settings > General, scroll to "Your apps", select Web </>, and copy the firebaseConfig object.

3. Edit the Code

Open program in a text editor.

Step A: Insert API Keys
Locate the firebaseConfig variable (approx. line 570) and paste your keys:

const firebaseConfig = { 
    apiKey: "YOUR_API_KEY_HERE", 
    authDomain: "YOUR_PROJECT.firebaseapp.com", 
    projectId: "YOUR_PROJECT_ID", 
    storageBucket: "YOUR_PROJECT.firebasestorage.app", 
    messagingSenderId: "...", 
    appId: "..." 
};


Step B: Set Your Secret Key
Locate the APP_SECRET variable just below the config. Change this to a unique, random string.
Note: Anyone you share this file with must have the same secret key to access the same encrypted channels.

const APP_SECRET = "MY_CUSTOM_SECRET_KEY_2025"; 


4. Run

Simply double-click the .html file to open it. No web server or installation is required.

🎨 Customization

Logo: The logo uses a fixed aspect ratio container. To update it, search for the <img> tag inside the <nav> block and replace the src URL.

Current Asset: https://i.imgur.com/QUmxZKB.png

Colors: The theme is built with Tailwind CSS. You can adjust the color palette (Titanium, Tactical Green, Gold) in the tailwind.config script block at the top of the file.

⚠️ Security Notice

This application uses Client-Side Encryption.

Protection Level: It protects channel passwords from being read by casual users browsing the database or "shoulder surfing."

Limitations: The APP_SECRET is stored in the source code. Advanced users can extract this key. This tool is designed for community gaming contexts and should not be used to store sensitive personal information.

📦 Dependencies (CDN)

Tailwind CSS: Styling engine.

FontAwesome 6: Icons.

Google Fonts: Inter, Orbitron, JetBrains Mono.

Firebase SDK (v10.13.1): Database backend.

CryptoJS (v4.1.1): Encryption standards.

html2canvas & jsPDF: Rendering engine for exports.
