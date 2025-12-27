---
title: "Fix ET Legacy using a 32 bit mod on Flatpak"
date: 2025-12-25 14:49:00 -0800
categories: [Blogging]
tags: [ET Legacy, Enemy Territory, Linux]
---



## Fixing the dreaded "VM creation on cgame failed make sure that cgame.mp.i386.so exists in the mod's folder you're trying to run" Error in Fedora


So if you are like me and still like to play Enemy Territory just like the good old days and are using Linux like I am, you may have ran into this error:

```
VM creation on cgame failed make sure that cgame.mp.i386.so exists in the mod's folder you're trying to run
```

Now, I'm using the Flatpak version of ET Legacy so if you are using the downloaded version, you will need to adjust the fix. So the issue is basically that I'm using a specific mod for the game, Silent Mod, which is 32 bit. If you check the logs on the game you will see the error is in trying to load a shared object file ui.mp.i386.so. To get around this, we can force the game to load in Wayland using the X11 compatibility mode. 

To do this simply run this command with sudo priveledges:

``` 
flatpak override --system --socket=x11 --nosocket=wayland com.etlegacy.ETLegacy

```
After that the game should run fine. I'd also recommend putting an alias to the app in your bashrc or zshrc:

```
alias etl="flatpak run com.etlegacy.ETLegacy +connect 69.164.251.155:27960"

```
That connects to my favorite server and you can also append other options, like passwords if needed too.


