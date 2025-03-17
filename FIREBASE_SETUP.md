# Firebase Setup Guide for IISMA LMS

This guide will help you set up Firebase Firestore for your IISMA LMS application. The app has been refactored to use Firestore instead of localStorage for data persistence.

## Step 1: Create a Firebase Project

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Click "Add Project" and follow the prompts to create a new Firebase project
3. Give your project a name (e.g., "IISMA-LMS")
4. Choose whether to enable Google Analytics (recommended but optional)
5. Complete the project creation process

## Step 2: Create a Firestore Database

1. In your Firebase project, navigate to the "Firestore Database" section in the left sidebar
2. Click "Create database"
3. Choose "Start in production mode" (recommended)
4. Select a location that's closest to your users (e.g., "asia-south1" for India)
5. Click "Enable"

## Step 3: Set Up Firestore Security Rules

1. Go to the "Rules" tab in the Firestore Database section
2. Replace the default rules with the following (for development purposes):

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

**Note:** These rules allow anyone to read and write to your database. For production, you should implement proper authentication rules.

## Step 4: Get Your Firebase Configuration

1. Click on the gear icon (⚙️) next to "Project Overview" in the left sidebar
2. Select "Project settings"
3. Scroll down to the "Your apps" section
4. Click on the web app icon (</>) to add a web app if you haven't already
5. Register your app with a nickname (e.g., "IISMA LMS Web")
6. Copy the Firebase configuration object (it looks like this):

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

## Step 5: Update Your Application with Firebase Config

1. Open the file `src/lib/firebase.js` in your project
2. Replace the placeholder Firebase configuration with your actual configuration:

```javascript
// Your web app's Firebase configuration
const firebaseConfig = {
  apiKey: "YOUR_API_KEY", // Replace with your actual API key
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com", // Replace
  projectId: "YOUR_PROJECT_ID", // Replace
  storageBucket: "YOUR_PROJECT_ID.appspot.com", // Replace
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID", // Replace
  appId: "YOUR_APP_ID" // Replace
};
```

## Step 6: Run Your Application

1. Start your development server:
```
npm run dev
```

2. The application will now use Firestore for data storage instead of localStorage

## Important Notes

### Data Initialization

The first time you run the application with Firebase:

- The system will automatically create default admin and manager users in Firestore
- Sample leads will be added if the leads collection is empty
- You'll be able to log in with the default credentials:
  - Admin: username `admin`, password `admin123`
  - Manager: username `manager`, password `manager123`

### Deployment to Production

For a production deployment, you should:

1. Update the Firestore security rules to be more restrictive
2. Consider implementing Firebase Authentication for more secure user management
3. Set up Firebase hosting for easy deployment:

```
npm install -g firebase-tools
firebase login
firebase init hosting
firebase deploy
```

### Advantages of Using Firestore

- Data is now stored in the cloud, not just in the browser
- Multiple users can access and update the data simultaneously
- Data persists across devices and browsers
- Better scalability for larger datasets
- Built-in security and access controls

### Backup and Migration

If you had important data in your localStorage version:

1. Export your localStorage data from the browser's developer tools
2. Contact the developer for assistance in importing this data to Firestore

## Troubleshooting

If you encounter any issues:

1. Check the browser console for error messages
2. Verify your Firebase configuration is correct
3. Ensure your Firebase project has Firestore enabled
4. Make sure your security rules allow read/write operations during development 