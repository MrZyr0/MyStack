# MacOS tweaks

## Use TouchID for sudo in terminal

1. From Finter, click on “Go” in the menu navigate down to “Go to Folder”. Paste the following into the Go To Folder popup: `/etc/pam.d/`
2. One click on the file named `sudo` to highlight it and press CMD + I
3. Expend "Sharing & Permission" and click on the padlock to temporarily change the file permissions.
4. Change the privileges of `system` to "Read & Write".
5. Open the sudo file in VIM (or equivalent) and replace the third param on the ligne 2 by `pam_tid.so` to get this `auth sufficient pam_tid.so`.
6. Save, exit and close your terminal
7. Revert the original permission before close the finder window and try to use `sudo` in a new terminal window.

Or do it in one command line with : `sudo echo " auth       sufficient     pam_tid.so" >> /etc/pam.d/sudo`


## Speed up dock animations

_You can control that with [Dockey](https://dockey.publicspace.co) software if you prefer_
1. Disable display delay : `defaults write com.apple.dock autohide-delay -float 0`
2. Reduce hiding delay : `defaults write com.apple.dock autohide-time-modifier -float 0.5`
3. Restart the dock : `killall Dock`
