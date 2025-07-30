---
layout: post
title: Turning my A5 into an MP3 Player
categories: [misc]
tags: [project]    
---

Consider this a short write-up, not to showcase my potential, but simply because I’m excited to document my process. I bought this cracked Android A5 several years ago as a backup phone, and since then, it’s mostly been collecting dust in a drawer. Recently, I found blogs hosting tracks and albums from long-lost MySpace-era bands I wanted to preserve and listen to.

## Why?

I enjoy listening to obscure bands that were once active on MySpace. This is the stuff that you can't find on Spotify anymore. Some of these songs were never uploaded there in the first place, and when they are, they’re often pulled down or re-uploaded under someone else’s account just to be monetised. To ease these issues, I decided to make them locally available, offline and untouched, in an environment dedicated entirely to music. This also means no ads or noise. Again, a lot of the songs that I tend to find a lot on archive blogs and most recently, Soulseek.

I will take this as a chance to collect other songs.

My A5 still works fine, has a headphone jack, and a storage of 32GB, which is enough to handle a solid music library. It's also compact and light. While it's definitely dated, it’s surprisingly clean out of the box compared to most modern Android phones. Debloating it was easy because there wasn’t much bloat to begin with. I did try going the custom OS route, but even two years ago, the bootloader was region-locked. I gave up trying to bypass it even after searching the XDA forums for hours on end.

## Debloating process

I factory-reset my A5 to begin the debloating process from scratch without pre-existing issues and enabled USB debugging in the developer options so my A5 could communicate with my laptop. I double-checked to see if I still had *Android Debug Bridge* installed somewhere on my laptop to access features that a normal user usually couldn't without root permission. The debloating could be done in various ways; I could manually uninstall the packages via the `adb` command, use a GUI if I can't handle command-line operations such as the Universal Android Debloater, and Canta with Shizuku; however Canta requires Android 9.0 which my phone lacks.

But in this case, I'll be using the traditional UAD which I've had no issues with for the many times I had to use it. For it to work, I need to make sure that `adb` actually recognises my device. I can check this by running `adb devices`, which will list connected USB devices.

![ADB devices list screenshot](assets/img/adb-devices-screenshot.png)

I should see my device on the list. Now that `adb` recognises the device, I can basically proceed to the debloating process which is straightforward and fast. I'll be using a GUI version of the [Universal Android Debloater](https://github.com/0x192/universal-android-debloater) which I can find on GitHub. There's also forks available that I could use but I'll be using this one exactly. Note that UAD doesn't remove everything, like some system apps on the `/SYSTEM` partition that require root. Instead, it freezes these apps to prevent them running.

With the core use-case explained, I installed it from GitHub and dragged the `universal-android-debloater.exe` to the folder (platform-tools) that also has `adb.exe` for the UAD to recognise the device faster.

![UAD running screenshot](assets/img/uad-running-screenshot.png)

My device was recognised, along with a list of installed packages. While more packages are available, the list was filtered to only show those "*Recommended*" for safe debloating. If there are any apps I'd like to keep, I can simply scroll through the list and uncheck them before proceeding. If I feel like I made a mistake, I can also restore apps. Once I checked the apps I'd like to get rid of, there should be a couple of buttons on the bottom right.

I would probably recommend you keep Chrome installed so you could install the later APKs from there instead of the Play Store. Don't worry, you can delete it later, even without the debloater.

![UAD uninstall selection screenshot](assets/img/uad-uninstall-selection.png)

I tapped "Uninstall selection", and I saw the number of installed apps gradually decrease. Once the process is complete, it's best to reboot the phone to finalise the changes. When it powers back on, the phone should be officially debloated!

![Debloated phone screenshot](assets/img/debloated-phone.png)

By now, the A5 should be debloated, with only the essential apps remaining. To summarise, I used ADB on my laptop to send system commands to the A5. It’s a straightforward and rewarding process that frees your phone from bloatware.

## Device settings

I've briefly covered the debloating process. I'll keep this section short since there's not too much to cover here. Now, I'll go through the A5's settings to disable or enable certain options to maximise performance. I'll tackle the options in the developer options first:

![Developer options screenshot](assets/img/developer-options.png)

Window animation scale, transition animation scale, and animator duration scale should all be turned off. Disabling these will remove animations throughout the phone’s interface such as UI transitions and sliding effects, making interactions feel faster and more responsive.

![Limit background processes screenshot](assets/img/limit-background-processes.png)

I scrolled all the way down until I found "*Limit background processes*", which will show me a list of options. This setting varies depending on my needs. The default limit is usually 20 background processes, way too many for a dated phone like this. Since I'm using the A5 primarily as a music player, I'm setting the limit to just 3 processes, for my music application and Tailscale; which I'll discuss later.

Additionally, there are a few power-saving options I can use. Medium Power Saving Mode lets me lower the screen brightness, cap the CPU performance to 70%, and disable background network activity like Wi-Fi and mobile data, which is perfect since I’m turning this into an offline MP3 player anyway.

![Medium Power Saving Mode screenshot](assets/img/medium-power-saving.png)

If I really want to stretch the battery life, Maximum Power Saving Mode goes even further. It limits background activity, restricts most apps, and simplifies the home screen to the bare essentials. It’s a bit overkill for casual use, but useful if I’m out for hours and want to keep the music going.

## A music player

With the A5 finally debloated, I started looking for offline music players that don’t bombard you with ads and respect your privacy. Honestly, you don’t even need to install a new one if you’re fine using the default music player that comes with the phone since it still gets the job done.

That said, here's some great options if you want something better:

- **VLC** - reliable, lightweight, and supports just about every audio format.  
- **Foobar2000** - A classic and minimalist music player that also supports every audio format and makes transferring music easier.  
- **Musicolet** - one of the best ad-free offline music players with powerful queue and folder-based playback.  
- **retroPod** – if you’re feeling nostalgic and want that classic iPod interface.

Of course, I wouldn’t recommend installing these through the Play Store, since that requires signing in with a Google account. Instead, you can grab the APKs from trusted repositories like F-Droid.

I'll be using Foobar2000 because I have a bit of experience with it.

## Where to get your music from?

Anywhere, honestly. This write-up focuses more on turning your phone into an MP3 player rather than walking you through where to get your music. Personally, I’ve already downloaded a bunch of tracks from various blogs over time, they’re just sitting on my laptop now, waiting to be transferred. I will however use this time to give credits to the fantastic blogs for their preservation efforts:

- [Lost Songs](https://lostsongshc.blogspot.com/)  
- [Angry Emo Nerd](https://angryemonerd.blogspot.com/)  
- [Capital Loss](https://canadianwastelandarchives.blogspot.com/)  
- [Myspace Archive Project](https://archive.org/details/myspace-Music)

That said, I **highly recommend** Soulseek. And if you’re going to use it to download music from others, I absolutely suggest sharing a folder of your own collection too; it’s only fair. Just make sure you don’t accidentally share your entire drive. Instead, create a dedicated folder specifically for the music you want to share.

