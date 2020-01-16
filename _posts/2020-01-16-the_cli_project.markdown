---
layout: post
title:      "The CLI Project"
date:       2020-01-16 05:29:40 -0500
permalink:  the_cli_project
---

The CLI project was a great experience for me and I am very happy with what I was able to accomplish. I also really liked that we had to start from scratch for the first time. Using bundler to install the gem setup and then setting up the environmental dependencies was nice as I had always ignored those files in previous labs and really needed the experience of creating them. It was also the first time I had to use github commands and create and manage a repo. And while I did not find the github commands very intuitive, I was able to get fairly comfortable commiting changes, creating branches, merging branches, and pushing changes to the repo. The other really big change for me was working without tests. I have gotten so used to using rspec --f-f and then fixing that it was strange to code without them. I ended up having to constantly remind myself to slow down and test new code as I went along. Eventually I started to form some new habits when coding, I now commit changes frequently and do most of my coding in a side branch until I get it working and merge it back into the master branch. I also am much better at following my own code as I would try to catch errors or places my code could break/exit before loading the gem and testing it out. Completing the CLI has left me feeling much better about what I have learned and much more confident that I can actually code moving forward.

For the project I decided to work with colors. I wanted to get more familiar with hexadecimal color notation and using color in CSS/html so I originally chose  to scrape a list of the html colors and then return the hex and rgb color values of a chosen color. The scrape was definitely the part that took me the longest and was the part I was least confident in. I spent the first night trying to scrape everything with one pull but ended up having to do three separate scrapes to get all the info I wanted. Once I got all that working my project seemed really boring and not very useful so I decided to start adding more features.

The first feature I wanted to add was I wanted to get more information about each of the colors so I passed each color through an API to grab additional information. I then added the ability to search the API directly for more colors using a hexadecimal code. Connecting to the API was actually really easy and made me regret the hours spent scraping but in the end I am happy that I incorporated both into the project.

The next feature I added was a keyword search that would return a list of colors containing the keyword. The main issues with this one I had to deal with was I wanted to check both the html name and the database name for the color and had to account for the casing of the names. Additionally, since I broke the search section up into parts I needed to use an instance variable for the information to persist from one method to the next.

Lastly, I added a save color feature which allows the user to save a color and then select it later from a list of saved colors. The hardest part of this feature was that I had to incorporate it into existing code as well as new code, which broke my code in a few places but was fairly easy to fix.

Overall, I am happy with what I was able to accomplish in the amount of time I had. Areas I would like to improve upon for next project would be:
1. Starting with a stronger outline of what the project's scope will be.
2. Keeping my code more organized as I build longer programs.
3. Focusing more on the UI of the program
4. I would like to build the next one with the intention of one day publishing it

Until next time. Happy living.




