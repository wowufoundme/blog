---
layout: post
title: Serverless or Debug APK for React Native Development
thumbnail: https://cdn-images-1.medium.com/max/800/1*wyxuq21keffc5b0d_lMkUw.jpeg
---

So I have been working on React Native for a long time, now and no one actually asked me this till I actually asked myself, “So every time, I have to create a signed APK to test it on another device?”. 

And as usual, I started googling but came up with a lot of results but none of them actually worked for all the apps that I created or worked with. Eventually, I came up with a solution to build a complete, working serverless APK that runs without the `npm` packager.

![Photo by [Artem Sapegin](https://unsplash.com/photos/ZMraoOybTLQ?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)](https://cdn-images-1.medium.com/max/800/1*wyxuq21keffc5b0d_lMkUw.jpeg)

Basically, the process is very easy. Open a terminal/command prompt inside the root directory of your project and run the following commands:

1\.  Start the node packaging bundler:

```bash
npm start
```

2\. When the terminal shows: “Loading dependency graphs….”, open a new terminal in the same directory and now run the following to create a new directory inside the app to store the assets:

```bash
mkdir -p android/app/src/main/assets
```

3\. Use react-native’s bundle to bundle the assets in the directory created above:

```bash
react-native bundle --platform android --dev false --entry-file index.js --bundle-output android/app/src/main/assets/index.android.bundle --assets-dest android/app/src/main/res
```

4\. Curl the .js files created to the index.android.bundle:

```bash
curl "http://localhost:8081/index.bundle?platform=android" -o "android/app/src/main/assets/index.android.bundle"
```

5\. Change to _/android_ directory and run _gradlew_ to build the APK:

```bash
cd android && ./gradlew clean assembleDebug
```

Well, that’s it. Easy, peasy! After everything is done and it shows “Build successful”, your APK will be present in the folder

```bash
<project>/android/app/build/outputs/apk/debug
```