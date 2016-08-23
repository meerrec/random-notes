## How to sync sublime text settings using Dropbox

To properly sync your installed packages across different machines, you actually do not want to sync the whole Packages/ and Installed Packages/ folders. The reason for this is that some packages have different versions for different operating systems. By syncing the actual package contents across operating systems, you will possibly run into broken packages.

The proper solution is to install Package Control on all machines and then to sync only the Packages/User/ folder. This folder contains the Package Control.sublime-settings file, which includes a list of all installed packages. If this file is copied to another machine, the next time Sublime Text is started, Package Control will install the correct version of any missing packages.

---

### Mac OSX

- First Machine
```
cd ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/
mkdir ~/Dropbox/Sublime
mv User ~/Dropbox/Sublime/
ln -s ~/Dropbox/Sublime/User
```

- Other Machine
```
cd ~/Library/Application\ Support/Sublime\ Text\ 3/Packages/
rm -r User
ln -s ~/Dropbox/Sublime/User
```
---

### Linux

- First Machine
```
cd ~/.config/sublime-text-3/Packages/
mkdir ~/Dropbox/Sublime
mv User ~/Dropbox/Sublime/
ln -s ~/Dropbox/Sublime/User
```

- Other Machine
```
cd ~/.config/sublime-text-3/Packages/
rm -r User
ln -s ~/Dropbox/Sublime/User
```
---
