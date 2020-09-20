---
layout: post
title:      "Getting Started with React Native"
date:       2020-09-20 10:56:58 +0000
permalink:  getting_started_with_react_native
---


Welcome everybody, this is meant to be a quick beginners guide to React Native and will briefly cover what it is, how to install, and how to get coding. I am still new to React Native myself and hope writing this blog will also be a good resource for myself going forward as well.

So what is React Native? React Native allows users to use the React library to create mobile apps in both Android and IOS. It is a great choice for developers like me who are already familiar with React for web and want to try out mobile development. With React Native you create an app by building a component tree. React Native comes with some basic components like Text and View to build the mobile apps with and also includes styling which was designed to simulate CSS. It should be noted that neither Android or IOS phones are able to understand JavaScript and CSS so React converts the code into widgets that the phones are able to understand. 

Getting started..

The first thing we need to get started is to make sure node is installed on the computer. Additionally, if you want to preview the code on the computer and not your phone we can download Android Studio. This will let us create simulations of actual phones where we can run and test our app. If instead, we want to just use our cell phone to try out the app we can download Expo Client to our phone and then scan the barcode once we get the app up and running. Additionally, a text editor can be used to write the code itself. I use VSCode for this.

To build an App with React native we have two options: Expo CLI and React Native CLI. It is recommended to beginners to use Expo as it has a few more things preloaded in the code base to make getting started easier. It also makes it easy to connect a phone to the app. To install Expo CLI just type => npm install expo-cli --global //  in the console. Once the Expo CLI has been installed we can begin our project with => expo init project-title //. Next we change directories into the project ant type npm start. Once everything is installed we can begin writing our own code and we will most likely begin with some of the pre built components given to us with React Native. 

The first such component to learn is the View component. View works very much like div does for html and creates a section of code where one can add styles to and add touch events if needed.

Next to learn is the Text component. Anytime we would like some words displayed on the screen we will be using a Text component.

Others include Image for displaying images, Textinput for getting information from the user, Scrollview to allow components to be scrolled, Flaltlist for creating lists of items, and Button for attaching buttons to the app. 

A more complete list of the components can be found at https://reactnative.dev/docs/components-and-apis.

Creating the app with Expo should have given us a bunch of files including an App.js file. At first it is good to practice with the components already given to us and seeing how the app changes. We should also make sure we have a phone connected to the app. A nice part of React Native is that any time a save is made, the app will refresh itself and update so that the changes can be viewed.

From here we can just build out an app similar to how we would build one with React for web. We create some components and then connect them together in the app. Happy coding.

