# 🚀 HTML Games Collection - APK Build Guide

**Complete Guide to Build Android APK from HTML Games**

## 🎯 Overview

This guide will help you build an Android APK from the HTML/CSS/JavaScript games collection. The APK will contain all 30 games in a single mobile app.

## 📋 Prerequisites

### Required Software
- **Node.js** (v14 or higher) - [Download](https://nodejs.org/)
- **Java JDK 11** - [Download](https://adoptium.net/temurin/releases/)
- **Android Studio** (with SDK) - [Download](https://developer.android.com/studio)
- **Git** - [Download](https://git-scm.com/)

### Environment Variables
Set these environment variables:
```bash
# Windows
set ANDROID_HOME=C:\Users\YourUser\AppData\Local\Android\Sdk
set JAVA_HOME=C:\Program Files\Java\jdk-11
set PATH=%PATH%;%ANDROID_HOME%\platform-tools;%ANDROID_HOME%\tools

# Linux/Mac
export ANDROID_HOME=$HOME/Android/Sdk
export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export PATH=$PATH:$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools
```

## 🛠️ Step-by-Step Build Process

### Step 1: Clone the Repository
```bash
git clone https://github.com/bijaykumarceh-dev/webgame.git
cd webgame
```

### Step 2: Install Cordova (if not already installed)
```bash
npm install -g cordova
```

### Step 3: Navigate to Android App Directory
```bash
cd android-app
```

### Step 4: Install Dependencies
```bash
npm install
```

### Step 5: Build the APK
```bash
# For debug APK (recommended for testing)
cordova build android

# For release APK (signed)
cordova build android --release
```

## 📱 APK Location

After successful build, find your APK at:
```
android-app/platforms/android/app/build/outputs/apk/debug/app-debug.apk
```

For release build:
```
android-app/platforms/android/app/build/outputs/apk/release/app-release-unsigned.apk
```

## 🔐 Signing the Release APK (Optional)

### Step 1: Generate Keystore
```bash
keytool -genkey -v -keystore my-release-key.keystore -alias alias_name -keyalg RSA -keysize 2048 -validity 10000
```

### Step 2: Sign the APK
```bash
jarsigner -verbose -sigalg SHA1withRSA -digestalg SHA1 -keystore my-release-key.keystore app-release-unsigned.apk alias_name
```

### Step 3: Optimize the APK
```bash
zipalign -v 4 app-release-unsigned.apk HTML-Games-Collection.apk
```

## 🖥️ Alternative: Online APK Builders

If you don't want to set up the development environment, use these online services:

### 1. **BuildPhoneGap** (Free)
- Go to: https://build.phonegap.com/
- Upload the `android-app/www` folder
- Build APK online

### 2. **Cordova Build** (Free)
- Go to: https://cordova.apache.org/docs/en/latest/guide/cli/index.html
- Use PhoneGap Build service

### 3. **Appy Pie** (Free Trial)
- Go to: https://www.appypie.com/
- Upload HTML files
- Convert to APK

### 4. **Convert HTML to APK Online Tools**
- Search for "HTML to APK converter online"
- Upload the `www` folder content

## 🐛 Troubleshooting

### Common Issues

#### 1. "Android SDK not found"
```bash
# Install Android SDK via Android Studio
# Or download command line tools:
# https://developer.android.com/studio#command-tools
```

#### 2. "Java JDK not found"
```bash
java -version  # Should show JDK 11+
# Download from: https://adoptium.net/
```

#### 3. "Cordova command not found"
```bash
npm install -g cordova
```

#### 4. Build fails with Gradle errors
```bash
# Clean and rebuild
cordova clean android
cordova build android
```

#### 5. WebView not loading games
- Check that all game files are in `www/` folder
- Ensure `index.html` exists in `www/`
- Check WebView permissions in `config.xml`

## 📱 Testing the APK

### On Android Device
1. **Enable Developer Options**
   - Go to Settings > About Phone
   - Tap "Build Number" 7 times

2. **Enable USB Debugging**
   - Settings > Developer Options > USB Debugging

3. **Install APK**
   ```bash
   adb install app-debug.apk
   ```

### Using Android Emulator
```bash
# Start emulator
emulator -avd Your_AVD_Name

# Install APK
adb install app-debug.apk
```

## 🎨 Customizing the App

### Change App Name
Edit `android-app/config.xml`:
```xml
<name>HTML Games Collection</name>
```

### Change App Icon
Replace files in `android-app/res/drawable/` and `android-app/res/mipmap-*/`

### Add New Games
1. Create new folder in `android-app/www/`
2. Add HTML/CSS/JS files
3. Update `index.html` to include the new game

## 📊 APK Information

- **Package Name**: `com.example.htmlgames`
- **Min Android Version**: API 21 (Android 5.0)
- **Target Android Version**: API 36 (Android 15)
- **App Size**: ~5-10 MB (depending on games)
- **Permissions**: Internet access (for WebView)

## 🚀 Publishing to Play Store

### Step 1: Sign the APK
Follow the signing steps above

### Step 2: Create Play Store Listing
- Go to: https://play.google.com/console/
- Create new app
- Upload signed APK
- Add screenshots, description, etc.

### Step 3: Publish
- Set pricing (Free)
- Choose countries
- Publish app

## 📞 Support

If you encounter issues:
1. Check the Cordova documentation: https://cordova.apache.org/docs/
2. Android Developer Guide: https://developer.android.com/
3. Create an issue on GitHub

## 🎯 Quick Commands Summary

```bash
# Clone repo
git clone https://github.com/bijaykumarceh-dev/webgame.git
cd webgame/android-app

# Install dependencies
npm install

# Build debug APK
cordova build android

# Find APK
ls platforms/android/app/build/outputs/apk/debug/
```

---

**🎮 Happy APK Building!**