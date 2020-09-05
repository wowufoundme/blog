---
layout: post
title: Fix audio errors in Ubuntu 18.04 with alsamixer
thumbnail: https://thepracticaldev.s3.amazonaws.com/i/ngrqy7f6orzk8hgo4r93.png
theme: tile-dark
---

Recently I installed Ubuntu 18.04 on my laptop having an SSD and an internal HDD. Soon after fixing a lot of issues, I encountered through this one and thought maybe a lot of people are going through this. So,why not write about it?

![Sound panel in Ubuntu 18.04](https://thepracticaldev.s3.amazonaws.com/i/ngrqy7f6orzk8hgo4r93.png)

Sometimes it happens that all the audio controls and volume are full and you stilll don't hear any volume coming out of those speakers. I researched a lot and found out that there maybe a problem with the mixer control. And here is what I found out. I ran `alsamixer` in terminal and checked if all the volumes are full or not.

![Alsamixer](https://thepracticaldev.s3.amazonaws.com/i/d7zjho3ux37iriic17i2.png)

The 'Headphone' volume was mute even though the 'Master' one was full. And this small thing was the issue. The fix? Simple use arrow keys (left/right) to highlight the headphones tab (it turns red as master is in the above photo). Then use arrow keys(up/down) to increase/decrease the volume. Exit the interface by tapping the Esc key.

You can also use the terminal commands to adjust the volume:

```bash
amixer set Headphone 50%
```
To set volume level for Master  
```bash
amixer set Master 80%
```

![Command Line Editing](https://thepracticaldev.s3.amazonaws.com/i/f5pjfsmcmsueg5iizcce.png)


This finally helped me figure out the issue with the audio.
