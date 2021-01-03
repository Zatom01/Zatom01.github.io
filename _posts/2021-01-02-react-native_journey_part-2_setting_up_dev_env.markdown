---
layout: post
title:      "React-Native Journey Part-2 (Setting up dev env)"
date:       2021-01-03 03:31:11 +0000
permalink:  react-native_journey_part-2_setting_up_dev_env
---



There are basically two CLIs for running react native apps ; Expo CLI and React native CLI. If you have prior knowledge on mobile development, react native CLI is the way to go. Since, I do not have any prior experience I installed Expo CLI.
Expo CLI gives us lots of native features. 

Here are the steps for setting up the development environment:
1. I made sure my Node version was 12 and up. I checked mine by "node -v" and found out that it was version 15.4.0, so it was all good to start.
2. I then installed Expo CLI globally by "npm i -g expo-cli"
3. For code editor, I already have vscode.
4. I installed some extensions like React native tools, React-native/react/redux  for debugging the code in vscode. 
5. I made sure Prettier extension was also installed 
6. I then installed Material-icon theme extension that provides nice icons for our projects

I created the project by "expo init project-name". There were multiple workflow template to choose from. I went ahead and chose the basic blank managed workflow template. I opened the code in vscode by code. . I did npm start and in my case, it opened in the port 19002. I saw there was assets folder for all the icons, images and videos that we can bundle with the project. App.js looked pretty familiar with the functional component. We could've made it a class component, but functional component are preferred. There were components like View ( like div ) and Text ( to display text on screen ) imported from the React-native. Functional component returns JSX element just like in our React project. When you run the project, you will see Metro Bundler on the main page, which is a Javascript compiler. It compiles all of our javascript files in to single file. Also, there was multiple links to share the project so that we could run it in our personal devices like android/ios devices.

I then downloaded iOS simulator tool called Xcode. It is a Apple's IDE used for producing software on Mac platforms.

 

