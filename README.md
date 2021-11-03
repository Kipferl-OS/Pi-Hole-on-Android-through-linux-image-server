#  [Pi-Hole-on-Android-through-linux-image-server](https://github.com/Kipferl-OS/Pi-Hole-on-Android-through-linux-image-server)

## Disclaimer 
The following guide does not contain **ANY resources** that I personally own or have created so far, for which the contents should **rather be seen as a collection of various projects/documentation I have used myself in order to better compile a straightforward set of instructions** that would specifically and (almost) exclusively describe how an old android phone can be used to act as a Pi-hole server that can efficiently mitigate and get rid of most of website's ads. Not only, custom website block lists can be created with the purpose of filtering and getting rid of most commonly accessed fake news/misinformation websites (I do not own the block lists either). Ultimately, the whole project can turn in a very nice "aesthetic" (for whoever would take it as that) setup with the help of few nice apps available on A**ndroid** and **Linux** :) (you can get these working on Windows as well, but I won't get into details about that). 

**Note**: There is no endorsement or partnership between this page and [Pi-hole© LLC](https://pi-hole.net/). They deserve [your support](https://pi-hole.net/donate/) if you find this useful. Same applies for **ALL the following resources belonging to their each and every author**:

 - https://github.com/DesktopECHO/Pi-hole-for-Android
 - https://github.com/blchinezu/rolist-hosts
 - https://github.com/tcptomato/ROad-Block
 - https://github.com/Swordfish90/cool-retro-term
 - Any other resource(s) I will be further mentioning throughout the guide.


## Introduction
Quick and relatively convenient solution of running Pi-hole via a typical android device (although must be **ARMv7** - 2011 and newer) without the hassle of getting a raspberry-pi with the sole purpose of eradicating internet ads. 

Through this brief guide I will show the main steps I have done in order to get an old Xiaomi phone I had around run a custom Linux server image that contains Pi-hole preinstalled and can thus emulate the Pi-hole environment. Most of the changes can be easily done via a SSH terminal (either via a computer terminal or by installing a 3rd party terminal on the same android phone). 

Additionally, I have added in this guide few "tweaks" regarding battery management that can be applied on the phone itself if chosen to have it run 24/7 (must be rooted), as well as few ideas that I personally used to make the whole setup look "futuristic". Basic terminal, networking, phone debugging knowledge would be useful to have (I am not fully knowledgeable either), but the guide shouldn't be difficult to read through. 


## Prerequisities

 - Working **ROOTED** Android device (must be **ARMv7; 2011 and newer**, other specs don't really matter).
 - Internet router that supports **DNS-forwarding**
 - Terminal environment for **SSH** (for Linux & Android) // **PuTTY** if Windows is used
 - **Any Linux distribution (for obtaining the "aesthetic" terminal dashboard look, pretty much optional)*

## Instructions

[Getting Pi-hole running on Android]
As long as the phone has already been rooted, please regard the installing instructions from the following page: https://github.com/DesktopECHO/Pi-hole-for-Android
