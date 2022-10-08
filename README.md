# PKGBUILDs
A bunch of PKGBuilds and patches for those.  
The _Patches directory contains patches for PKGBUILDs from the Repos and the AUR which are themselves git repos.  
The PKGBUILDS included here are the ones I maintain on the AUR (with some exceptions).  

## AUR4
Because of the changes AUR4 introduced made this repo mostly useless.
It still exists, but because I didn't track .SRCINFO back then I couldn't import this history into the AUR4 Repos.
So all the stuff I maintain on the AUR will be added as subtrees and main changes will be made there.

Dunno at the moment how to handle PRs.

## ToDo
Subtrees are suboptimal.
If there is a conflict (which should never happen, but does so) files that are created are put into the top level and not into the respective folder.
Maybe I will switch to submodules, which makes the webviewer kinda useless, but whatever.
