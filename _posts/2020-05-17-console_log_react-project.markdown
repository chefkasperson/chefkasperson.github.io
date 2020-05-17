---
layout: post
title:      "console.log(React-project)"
date:       2020-05-17 13:22:00 +0000
permalink:  console_log_react-project
---


It is hard to believe that the end is already here, well more like the preparation for a new beginning has come to an end. For this project I wanted to make an app that could keep the score of a family card game I play with my parents when they come to town. It is a pretty simple card game involving betting and playing hands with a few things like sets and moon bids. I wanted the backend to handle all of the game logic so I ended up doing quite a bit of coding in Ruby, which was odd after spending the past couple months in Javascript and React. I kept trying to invoke methods and found myself using this instead of self on a few occasions. That being said I was able to get a working version of the game up an running fairly quickly and switched over to React.

The React and Redux make working in Javascript much more intuitive for me. Breaking up the dom into components, was how I tried to approach my Javascript project so I was happy when I discovered that is exactly what React-Redux does, only way better. The syntaxes for both were a bit difficult for me to learn, so I spent a good while debugging errors that were syntactical in nature. What I really liked about working with React is how easy it is to make items dynamic and how their values will change without a full refresh. For example in my project I have a form that uses select boxes for adding players and the dealer. I decided that for a better user experience I would add the new player form to the same page as the new game form and was pleased to see that once working the new player would be added to the select boxes without refreshing the form itself. That way the user would not have to reset the players he or she already had chosen. I then tied the dealer select options to the state of the player's names so that when a player was chosen for player one the dealer option for player one would be that player's name instead of just 'player 1'. Also props are the bee's knees. I really liked being able to do all my logic in the component that is connected directly to state and then be able to pass whatever logic I needed to as props to the others.

I feel a little sad that my time at school is coming to an end but I feel like it has given me the tools I need to continue my studies alone from here and to transition myself into a new career that will hopefully be a big positive change for myself and my family. 
