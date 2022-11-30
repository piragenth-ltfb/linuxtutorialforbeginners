---
author: piragenth
categories:
- Fix
date: "2022-08-12"
title: How to Fix No Audio Issue In Kali Linux
url: /post/How-to-Fix-No-Audio-Issue-In-Kali-Linux/
---

In this post i am going to show the fix for the no audio problem in kali linux  


```bash
sudo apt install pulseaudio -y
systemctl --user enable pulseaudio
systemctl --user start pulseaudio
```


Install pulseaudio and start the pulseaudio

Make sure NOT to start pulseaudio using sudo 

---
In my this command works when command runs after a reboot i need to start pulseaudio mannualy

SO  

We are going to make this command at the boot  


To run command at the boot

![img](https://raw.githubusercontent.com/piragenthnetlify/ltfb.github.io/master/assets/Pictures/Screenshot_2022-08-12_08-29-42.png)
=======


Under the Application and Autostart  
Click add and enter name,description    
For the command type 

```bash
systemctl --user start pulseaudio
```
---

and click ok then reboot 
It should work now!
