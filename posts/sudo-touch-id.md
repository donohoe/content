# sudo make me a sandwich 
#### February 15th 2021

My usage of sudo has gone down over the last couple of years, but enabling Touch ID on my Mac for use with `sudo` has been a huge win. Yes, you have to take your fingers off the keyboard for this so that might put off many folk.

```
# Open sudo
sudo vi /etc/pam.d/sudo

# Add this as the very first line
auth sufficient pam_tid.so
```

This is terribly amazing until you do a system update and it becomes disabled :(

To get around that you might consider adding it to your `.bash_profile`. It is a hidden file and usually located in your home folder:

```
~/.bash_profile
```
  
Open it and add this...

```
enable-sudo-touchid() {
  sudo sed -i -e '1s;^;auth       sufficient     pam_tid.so\n;' /etc/pam.d/sudo
}
```

Now the warning. It evaluates this every time you create a new shell or tab, which for me is not very frequently but [your mileage may vary](https://xkcd.com/149/).
