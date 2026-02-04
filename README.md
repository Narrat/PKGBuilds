# PKGBUILDs
A bunch of PKGBuilds and patches for those.  
The _Patches directory contains patches for PKGBUILDs from the Repos and the AUR which are themselves git repos.  
The PKGBUILDS included here are the ones I maintain on the AUR (with some exceptions).  

## AUR4
Because of the changes AUR4 introduced made this repo mostly useless.
It still exists, but because I didn't track .SRCINFO back then and didn't knew about interactive rebase, I couldn't import this history into the AUR4 Repos.
So all the stuff I maintain on the AUR will be added as subtrees and main changes will be made there.

Dunno at the moment how to handle PRs.

## ToDo
Subtrees are kinda suboptimal.
If there is a conflict (which should never happen, but does so) files that are created are put into the top level and not into the respective folder.
Additionally the additional steps made me kinda ignore updating the contained subtrees.  
Ideally I could use this monorepo for all maintenance and push only the relevant history to the respective upstream repos.
While having all files available without switching branches.
Possible methods:
* Subtree
* Separate branches with no common history (with or without `git-worktree`)
* Submodules

Submodules are still kinda the least favourite option, as it makes the webviewer useless.
Keeping everything in separate branches plus making use of `git-worktree` fits more or less nicely in the current structure.
One place with the main repo and a separate folder with all the respective ones.
Maintenance could be a hassle though.  
Subtrees itself I need to test with more.
I have a shell script which does things to add a foreign repo and that's it.
Never tested what happens if a subtree is pushed back with updates.
Especially what history it creates.
If the combined history cannot be split out cleanly and contains wrong references pushing to the aurweb will be impossible.
