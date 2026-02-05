# PKGBUILDs
A bunch of PKGBuilds and patches for those.  
The _Patches directory contains patches for PKGBUILDs from the Repos and the AUR which are themselves git repos.  
The PKGBUILDS included here are the ones I maintain on the AUR (with some exceptions).  

## AUR4
Because of the changes AUR4 introduced made this repo mostly useless.
It still exists, but because I didn't track .SRCINFO back then and didn't knew about interactive rebase, I couldn't import this history into the AUR4 Repos.
So all the stuff I maintain on the AUR will be added as subtrees and main changes will be made there.

Dunno at the moment how to handle PRs.

## Setup

This repo makes use of the `git`-contrib script [`subtree`](https://github.com/git/git/blob/master/contrib/subtree/git-subtree.adoc) (not the [merge-strategy](https://www.kernel.org/pub/software/scm/git/docs/howto/using-merge-subtree.html) with the same name).

### Commands

Add remote (nothing fancy; the usual stuff):  
```bash
$ git remote add <name> <url>
```
  
Add repo as subtree:  
```bash
$ REPO=<name> git subtree --prefix $REPO/ add <remote> <branch>
```
  
Fetch changes (nothing fancy; the usual stuff):  
```bash
$ git fetch --prune --all
```
  
Merge changes:  
```fish
REPO=<name> git subtree --prefix $REPO/ merge $(string join '-' $REPO 'aur') master -m "$(string join '' $(date --rfc-3339=date) ": Merge updates for " $REPO )"
```
Add least this the canonical merge.
Regular merges work fine too. Didn't cause any issue when extracting the subtree.  
Alternative to merge is the use of `subtree pull`.
  
Push subtree to another remote (origin repo or a new one):
```bash
$ REPO=<name> git subtree --prefix $REPO/ push <remote> <branch>
```
  
There is also a [script](https://github.com/Narrat/Scripts/blob/master/subtupd.sh) I assembled in a very crude and hackish way (and with lot of copy and paste).
Isn't the prettiest and also on the ToDo for a rework, but it did its job.

## Alternatives
* Keeping every repo in a separate branch (with or without `git-worktree` to see more than one at a time)
* Submodules
  * Not my favourite although in theory interesting
  * Webview not working
* [`git-subrepo`](https://github.com/ingydotnet/git-subrepo)
  * Need to take a deeper look
  * Theoretically keeps the benefits of `subtree` while reducing the irks
* Merge-strategy `subtree`
  * Not really able to push changes back?

