
#  [Pi-Hole-on-Android-through-linux-image-server](https://github.com/Kipferl-OS/Pi-Hole-on-Android-through-linux-image-server)

![Final result of the project!](https://i.imgur.com/FtYouRB.jpeg)

![And there goes another one!](https://user-images.githubusercontent.com/92034177/148465734-f7880ce4-d6e5-4bfb-a91e-1b2edbd09490.GIF)

## Disclaimer 

The following guide does not contain **ANY resources** that I own or have created so far, for which the contents should **rather be seen as a collection of various projects/documentation/tests that I have used myself to better compile a custom set of instructions**. The overall purpose would specifically and (almost) exclusively be to describe how an old android phone can be used to act as a Pi-hole server that can efficiently mitigate and get rid of most website's ads. Moreover, custom website blocklists can be created with the purpose of filtering and getting rid of most commonly accessed fake news/misinformation websites (I do not own the blocklists either). Ultimately, the whole project can turn in a very nice "aesthetic" (for whoever would take it like that) setup with the help of a few nice apps available on **Android** and **Linux** :) (you can get these working on Windows as well, although there is no official way available yet, so I won't get into details about that). 

**Note**: There is no endorsement or partnership between this page and [**Pi-hole© LLC**](https://pi-hole.net/). They deserve [**your support**](https://pi-hole.net/donate/) if you find this useful. Same applies for **ALL the following resources belonging to their each and every author**:

 - **https://github.com/DesktopECHO/Pi-hole-for-Android**
 - **https://github.com/blchinezu/rolist-hosts**
 - **https://github.com/tcptomato/ROad-Block**
 - **https://github.com/Swordfish90/cool-retro-term**
 - Any other resource(s) I will be further mentioning throughout the guide.


## Introduction

Quick and relatively convenient solution of running Pi-hole via a typical Android device (although must be **ARMv7** - 2011 and newer) without the hassle of getting a Raspberry Pi with the sole purpose of eradicating internet ads. 

Through this brief guide, I will be showing the main steps to get an old **Xiaomi** phone I had around (but you can try on any other compatible device) run a custom Linux server image that contains Pi-Hole preinstalled and can thus emulate its environment. Most of the changes can be easily done via an SSH terminal (either via a computer terminal or by installing a 3rd party terminal on the same android phone). 

Additionally, I have added in this guide a few "tweaks" regarding battery management that can be applied on the phone itself, if chosen to have it run 24/7 (must be rooted), as well as some other ideas that I used, to make the whole setup look *futuristic*. Basic terminal, networking, phone debugging knowledge would be useful to have (I am not fully knowledgeable either), but the guide shouldn't be difficult to read through. 


## Prerequisities
 - Working **ROOTED** Android device (must be **ARMv7; 2011 and newer**, other specs don't really matter);
 - Internet router that supports assigning a custom **DHCP Server**;
 - Terminal environment for **SSH** (for Linux & Android) // **PuTTY** if Windows is used. **Powershell** should do just fine too;
 - *Any common Linux distribution (for obtaining the *aesthetic* terminal dashboard look, pretty much **optional**).

## Instructions

**[Getting Pi-hole running on Android]**

As long as the phone has already been rooted, please regard the installing instructions from the [**original guide**](https://github.com/DesktopECHO/Pi-hole-for-Android). Whereas I have also attempted to **rewrite** or add some additional details/supporting recorded examples to make the whole set of instructions even more user-friendly, I still find the original guide to be straightforward enough. You can very well make use of the way I have listed the installation steps. However, as I have also stated before, I am not the original creator of these particular resources, therefore I could only borrow and adapt the guide to this separate fork project. Now, given everything's clear enough, to shortly sum up the steps, you would have to do & ensure of the following:

![Main installation steps](https://svgshare.com/i/dL8.svg)

**[Summary of the overall installation steps]**

Download Linux Deploy APK on your chosen device. While it's officially available on the Play Store (or any safe 3rd APP store - I strongly suggest giving **Aurora Store** a go). Alternatively, it can be downloaded from the original GitHub sources:

  - Latest version: **https://github.com/meefik/linuxdeploy/releases**
  - For android 4.x older devices: **https://github.com/meefik/linuxdeploy/releases/tag/2.5.1**

Download the **Pi-hole for Android disk image**: (**v1.4 / December 23, 2021**)

   - **http://desktopecho.com/p4a14.tar.gz** (MD5: be609fbadbc1bcc3e0d5e46a2ca521d8)\

Open **Linux Deploy** and have the options from the screenshots below manually changed **only** so that they match (apart from the SSH login credentials):

Insert screenhost 1 & 2

Go back to the main window, click **Options** Menu (three dots type of menu, should be located at the top right of the screen), and click **Install**:

Insert screenshot 3

If installation turns to be complete & successful, the Linux Deploy console window will show this (or similar) console output: 

        `````[HH:mm:ss] >>> :: Configuring core/profile ...`````
        
        `````[HH:mm:ss] >>> :: Configuring core/sudo ...`````
        
        `````[HH:mm:ss] >>> :: Configuring core/unchroot ...`````
        
        `````[HH:mm:ss] >>> deploy`````
        
If any Linux Deploy Console error messages occur, the most common solution would be to first check whether the location of **p4a14.tar.gz** is correctly listed in the app itself (meaning you would have to use a file manager and make sure you got the file's location correctly. The default one should be fine as long as you've placed the archive in the phone's internal memory). I am specifically stating this because it would be expected to get rather confused about how the storage allocation works on an android phone. This piece of answer should though clarify the way it works:

> *Basically, there are two types of external storage. One is the popular form of external memory that most smartphone users understand i.e. SD card, also known as memory cards that is the secondary external storage and the other one built-in external storage which is known as primary external storage. A **Primary External Storage** is one that is accessible by the user but still part of the built-in memory. All your media files, documents, and pictures are stored on this primary storage and this is when you don’t have a physical external storage device such as an SD Card.* > [**Source article here**](https://www.cashify.in/what-is-the-difference-between-external-storage-and-internal-storage-cashify-explains) <

By knowing this, it would be more than correct to assume that **${EXTERNAL_STORAGE}** does not imply the need to use an external SD card (nor have I mentioned at the beginning of the guide!). However, you may be free to use whichever location inside the built-in storage itself :grin:.


If you still have trouble installing the image in Linux Deploy, it could also be because of the SELinux mode that is "engraved" by default on your device. The original creator of the guide also provides the following link, being quite useful in terms of understanding the processes behind [**post on XDA**](https://forum.xda-developers.com/t/app-tool-2-0-official-the-selinux-switch.3656502/). It contains an APK that will allow changing SELinux modes without writing permanent changes to the boot script files.

Lastly, open the 'Hamburger menu' (Three dashes at top left) and press on **Settings**:

 - [x]  Mark the **Lock Wi-Fi** option as checked (If your device has Wi-Fi)
 - [x]  Mark the **Autostart** option

Touch the **[ ▸ START ]** button and confirm. 

Insert screenshot 4 & 5 

*Voilà!* You've just got your old Android 'pal up and running with Pi-Hole! Turns out it's the coolest phone out there in the neighbourhood :sunglasses:!

**[Interacting with Pi-Hole via terminal]**

Your Android device's IP will be shown right at the top of the Linux Deploy the main window. Out of the most common ways to interact with Pi-Hole, these two are the most common ones:

 - Open a web browser to the Android device's IP address **-->**   
```http://<IP_ADDPRESS_OF_YOUR_PI_HOLE>/admin/```
```http:/pi.hole/admin (when using Pi-hole as your DNS server)```
```http://pi.hole/ (when using Pi-hole as your DNS server)```

 - SSH to the instance on port 22 **-->** ```ssh android@IP_ADDPRESS_OF_YOUR_PI_HOLE>```

The original creator of the guide has also provided a third alternative of getting an easier grip on the Pi-Hole SSH session running directly on your Android device (assuming it has a working display) through the use of an **RDP** (remote desktop protocol) software. However, what I found to be slightly more applicable and independent from any external devices, would simply be to run a terminal instance directly from the phone itself! No worries, I will be mentioning this right after we jump on the "aesthetic" part of the guide :smile:! Before that, you may have a look at the optional info section.


## Optional stuff/Worth information to take into consideration
There's an additional info section provided by the [**original guide**](https://github.com/DesktopECHO/Pi-hole-for-Android) that you should check out first!

**[Playing cautiously with your device's battery]**

I think that we can all be very well aware of the fact that a considerable advantage in terms of safety of using an original RaspberryPi device over a simple custom-configured Android phone would be the lack of an internal battery. Moreover, the battery itself is not even made to be run as an idle device under continuous charge! While the whole content does not encompass more of a prototype/project attempt of running a Pi-Hole instance on an old phone (and give it almost the same functionality), the idea itself should not under any circumstance be commercialized as a plug-and-play/good-to-go device. The [**original creator**](https://github.com/DesktopECHO/Pi-hole-for-Android) states something similar too:

>**If your Android device has a battery and was unused for months or years, replace its battery.** Old, worn, or abused Li-ion batteries can fail when pushed back into service. Failure appears as a bulge in the battery, "thermal event" or worse. A new battery makes an excellent [UPS](https://en.wikipedia.org/wiki/Uninterruptible_power_supply) for the tiny Linux box you just provisioned! 

In such circumstances, I considered that there are two aspects that can be further done to reduce the risk of worn/overheated batteries (including new ones), as much as possible:

 - [x] Using a debloated/completely clean custom Android image/ROM on your device. This is something that unfortunately would be too extensive to talk about and cover as a sidenote for this guide only. The reality is that each device requires different prerequisites and files to be able to unlock the phone's bootloader and flash a new & custom Android system that would contain only basic apps (not even Google services), thus the objecting of using as few resources as possible & avoid usual overheating. 
 - [x] Take advantage of **[AccA - Advanced Charging Controller](https://github.com/VR-25/acc)** (all credits go to the creators of the app): A completely configurable tool that allows controlling how your device charges. Some various settings and tweaks can be accessed to obtain the best performance out of the battery usage & have the phone run in safe conditions. 
 In the case of deploying Pi-Hole, I chose to use the default **Cool down after 60%** custom profile, which does not let the phone jump over 80% of charged battery (very "healthy" for the Li-Ion type of batteries. And, while plugged in, the phone will freeze the charging at 60%, take a short break, go under a slow charge cycle that prevents overheating until 70%, and, finally, the cycle would go back to normal until it reaches 80% again. Surely, there are much more settings to play around with, and, especially thanks to the flexibility of this app, you may very well achieve even better results & ways of preserving the battery in good condition. Here's how the profile looks within the APP:

Insert screenshot 6

**[Expanding Pi-Hole functionality and defending yourself from the toxic online media envinronment]**

For this particular guide, I chose to take Romania as an example, considering that the misinformation phenomenon is quite active recently, if not at its worst in terms of the impact through which people are hit day by day. While Pi-Hole cannot do its magic without being aware of the hosts it's required to stop from attacking us, blacklists are the firsthand solution through which custom lists of websites (flooded with poisonous and mostly lying or fraudulent news or similar content) can be easily added. Fortunately, ads are less of a headache, as settings out-of-the-box work well enough, but for a more specific way of targeting the current spread fake content, I managed to find two hosts lists that were reviewed as practical enough for also adding a pinch of safety when it comes to the concept of surfing the internet: 

 1. > **https://github.com/tcptomato/ROad-Block**
 2. > **https://github.com/blchinezu/rolist-hosts**

The installation steps are super easy and are described on each GitHub page (credit goes fully to both the creators for providing these resources).
Apart from that, I strongly recommend to my **fellow Romanians** to check the following additional resources that describe amazingly well what the consequences of falling into the traps of adware & misinformation can lead at a broader social level. I chose to talk about this as Pi-Hole could also serve as a good tool for reducing the overall exposure, on the condition of occasionally being on track with the main hosts/websites the malicious content or disinformation comes from. The following sources contain a clear & objective overview of the given case scenario, but please bear in mind that this more or less goes out of this guide's main scope, so I will choose to stop adding more details about this particular part of it:

**[Uriașa escrocherie a suplimentelor alimentare: milioane de euro din minciuni care împânzesc internetul - Recorder.ro](https://recorder.ro/uriasa-escrocherie-a-suplimentelor-alimentare-milioane-de-euro-din-minciuni-care-impanzesc-internetul/)** - fantastic article showing how a fraudulent chain of medical supplements ads has been running and flooding most of the websites known for showing very striking adware content around the webpage. 

**[Anti-Western Propaganda Report - FunkyCitizens - funky.ong](https://funky.ong/wp-content/uploads/2021/12/Anti-Western-Propaganda-Report-by-Funky-Citizens.pdf)**  - a truly elaborate report on how political and social anti-western propaganda has been functioning, as well as shaping for the recent years in Romania, if not most of the surrounding Eastern European part. 

**[Stopfals.md](https://stopfals.md/ro/category/21)** - another great Moldavian website solely dedicated to detecting & debunking various fake news found across the internet. Contains an additional list of recently updated hosts which were categorized as containing misinformation.


As an ending note, I have also tried comparing the results in terms of intentionally going through the fraudulent ads which are shown on a typical Romanian news website (among the ones which are categorized as clickbait titles, misleading data or politically affiliated) that is known to be funded by these specific hosts:

> **1st Instance**, accessing the website through another phone while being connected on a common SIM data network:

Insert screenshot iphone1

> **2nd Instance**, to be noted that some of the ads may still show as clickable, but in the end, the connection routes to "nowhere", simply becoming inaccessible.

Insert screenshot iphone2


**[Time for some fun: adding a pinch of a nice looking terminal for both your desktop & Pi-Hole device]**

You may have most probably already got to see the picture at the very beginning of this guide, and while I do agree it looks sort of *kitschy* (the picture is also older than the guide itself), there is a different terminal GUI used on my Linux main desktop, plus an APK that offers some pretty nice customization in terms of running custom terminal sessions via your own Android device. I did mention I'll let you know the way I configured both platforms a little bit while ago :). Let's have a look together:

 1. Grab your Android device and through whichever application store, go get [**Termux**](https://termux.com/) (I do not own this app either).

You can check its official guide, but essentially the APP simply works as a very intuitive and customizable interface for running a terminal session directly from your phone. Once you're in, you may deploy a new SSH connection to your Android's internal IP address (SSH connectivity is by default enabled in this APP) and enter in the Pi-Hole environment. ~~After that, we will have to install [**PADD**](https://github.com/pi-hole/PADD) to obtain the more expansive version of the original **chronometer.sh** that is included with [**Pi-Hole**](https://pi-hole.net).~~ > I just found out that with the recent available version, PADD comes installed automatically along the whole** Pi-Hole set up, thumbs up for having to go through even less hassle :smiley:! Here's an example of how it should be run:

Insert first gif/video recorded from terminal

2. Now that the whole environment is ready to go, the only thing left for achieving our *kitschy* futuristic look, is to go back on our Linux desktop (assuming you're using one; MacOS has installation support too, but AFAIK,  I am sorry for the sole users of Windows, it's not really available there), and grab a copy of [**cool-retro-term**](https://github.com/Swordfish90/cool-retro-term). I won't get into details about the installation steps here, considering that there's a specific way of having it on each available distribution. Believe me, it will not take you more than 2-3 terminal commands to have it up and running! Here's a quick self-recorded demonstration from which you will be convinced how easy it is to get it:

Insert second gif/video recorded from terminal

**[That's it :smiley:!]**

You're good to go with anything related to running Pi-Hole on your Android device, having a load of resources worth checking out to better defend yourself from the informational dangers across the internet & undoubtedly, you can do it in a *futuristic* way so that you'll be even cooler throughout your adventure! Don't forget to play around with the settings on the main Pi-Hole's web panel, it would make things so much easier rather than having to do everything via terminal (unless something goes wrong). 

If you managed to read through all this stuff, I can only congratulate you and sincerely thank you for all the efforts made! And, of course, huge thanks to all the creators of the resources that I have collected so far to make this guide! 

**Keep an eye from time to time, as I'm sure there are gaps or text mistakes that might still lie around here. I will be actively updating the contents whenever there's a major update or I find anything that should be changed, but until then, feel free to let me know if you found anything too! Cheers.**
