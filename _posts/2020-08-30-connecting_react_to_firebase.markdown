---
layout: post
title:      "Connecting React to Firebase"
date:       2020-08-30 09:02:46 +0000
permalink:  connecting_react_to_firebase
---


Since graduating from the bootcamp I attended, I have done a few tutorials on React and a couple of those connected React to a Firebase backend. Firebase is Google’s web application platform and is a nice option for developers looking to create a quick and simple backend for their projects. 

Google has made creating a Firebase project super simple. To start a project a user can go to firebase.google.com and make sure they are signed into a google account.  Here are the steps to setting up the store …

Once signed in. click on the ‘go to console’ link in the header.
In the console, click on the link to start a new project.
Then a pop-up will appear where you can name the project then accept the terms and conditions.
Google will then create the Firebase project and take you to its dashboard.
From the dashboard start by clicking the ‘Project Overview Link’.
Click the web icon in the pop-up, then register the app with a nickname.
It will then give you a code snippet, we are going to copy the FirebaseConfig Object.

The next steps will be done inside the React app.

Install Firebase into the React project with: yarn add firebase
Inside the project’s src folder create a firebase directory.
Then create a firebase.utils.js file inside of that directory.
In the file: import firebase from ‘firebase/app’ followed by ...
 import ‘firebase/firestore’ and import ‘firebase/auth’
Save the FirebaseConfig Object as: const config 
Then call: firebase.initializeApp(config) afterwards
Call: export const auth = firebase.auth() and export const firestore = firebase.firestore()
To set up Google auth add: const provider = new firebase.auth.GoogleAuthProvider()
 And: export const signInWithGoogle = () => auth.signInWithPopup(provider)
And: export default firebase

Here is a copy of the code up until this point.

<<<<<<<<<<<<<<

import firebase from 'firebase/app'
import 'firebase/firestore';
import 'firebase/auth';
 
const config = {
   apiKey: "xxxxx",
   authDomain: "xoxoxoxoxox",
   databaseURL: "https://1111.firebaseio.com",
   projectId: "1111",
   storageBucket: "1111.appspot.com",
   messagingSenderId: "12345",
   appId: "1:1212313:web:2131312",
   measurementId: "afadlfa;"
};
 
 
firebase.initializeApp(config)
 
export const auth = firebase.auth()
export const firestore = firebase.firestore()
 
const provider = new firebase.auth.GoogleAuthProvider()
 
export const signInWithGoogle = () => auth.signInWithPopup(provider)
 
export default firebase

<<<<<<<<<

Now our app can speak to firebase. In my next post we will look at how to add Authentication and pass data to and from the firebase store. 

In conclusion, Firebase is a nice platform for developers looking to add a simple backend to their projects. It only requires a little configuration to set up and then it is good to go. Currently we have managed to connect our project to firebase and will, in the next post look at adding authentication to the application.

