Linux is basically simple. You got core OS, on which you install apps. Apps come in form of packages, and their dependencies are also packages.
Unlike Windows, Linux makes a difference between small and capital letters, and will return error if not exact.
You can start by downloading a fairly small install file to install over network and end up with system capable of anything:

```
http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/current/legacy-images/netboot/
```

Once you downloaded mini.iso, burn it to usb. On Linux, type this:

```
sudo dd if=pathtoiso of=nameofusbdevice(sdb)
```

I recommend non EFI boot, MBR, go through install process, and when offered additional software, dont pick anything.
After you reboot, you will see a black screen. This is because no desktop is installed. Press ctrl alt F1 to open terminal.
After logging in, you can assing root account password. This account is normally not accessible without a password,
but if you need it, type in:

```
sudo passwd root
```

Now you can download a desktop. There is quite a few of them, so you can type something like this:

```
sudo apt install xfce4
```

You should be getting a prompt about gui manager. If you don't get that prompt, type in:

```
sudo apt install lightdm
```

After that, assign it to run from boot by typing in:

```
sudo dpkg-configure ligthdm
```

Now you can install a browser. Type in:

```
sudo apt install firefox
```

Or:

```
sudo apt install chromium-browser
```

If you need to find gpu drivers packages, type in:

```
sudo apt search nvidia-driver-*
```

To install it, type in:

```
sudo apt install nvidia-driver-435
```

If at any time you need to uninstall an app, type in:

```
sudo apt remove appname
```

You can also use wildcards, like this:

```
sudo apt remove nvidia*
```

If you need to clear your system of dependencies of apps you uninstalled, type in:

```
sudo apt autoremove
```

You need to install software to be able to add additional repositiors. In case you don't have this software, type in:

```
sudo apt install software-properties-common
```

Now to add a new repo, type in:

```
sudo add-apt-repository multiverse
```

Alternative way to above command is to use built in app, called nano editor:

```
sudo nano /etc/apt/sources.list
```

If you need to refresh your system after adding a repo, type in:

```
sudo apt update
```

You can list all packages available in all of repos by typing in:

```
sudo apt list
```

Software is normally installed via apps such as Synaptic or Gnome Software manager. However, if it's not listed, you can install an app to install it, like gdebi:

```
sudo apt install gdebi
```

If you have unmanaged network devices, type in:

```
sudo nano /etc/NetworkManager/NetworkManager.conf
```

And than edit the file with:

```
[keyfile]

unmanaged-devices=none
```

ctro + o is to save, enter for confirmation and ctrl + x to exit. You can restart a service by typing:

```
sudo service network-manager restart
```

Some software is installed via snap:

```
sudo snap install discord
```

You can run it by typing:

```
sudo /snap/bin/discord
```

For music:

```
sudo apt install clementine
```

For videos:

```
sudo snap install vlc
```

For torrents:

```
sudo apt install transmission
```

For archive management:

```
sudo apt install file-roller
```

For RAR files:

```
sudo apt install unrar
```

For managing local drives:

```
sudo apt install gparted
```

For picture editing:

```
sudo apt install gimp
```

For gaming:

```
sudo apt install steam
```

If you need Google Drive, type in next set of commands, just change your username:

```
sudo add-apt-repository ppa:alessandro-strada/ppa
sudo apt install google-drive-ocamlfuse
mkdir /home/username/google-drive
google-drive-ocamlfuse /home/username/google-drive
```

This line will list all users on your drive who aren't system users:

```
sudo awk -F':' '{if ($3 >= 1000 && $3 != 65534) print $1}' /etc/shadow
```

You can type this in to configure security:

```
sudo nano /etc/security/access.conf
```

And edit it with:

```
+:yourusername:LOCAL
+:root:tty1
-:ALL:ALL
```

With above command, you allowed yourself to login locally, root on terminal, and forbid everyone else from everywhere

Now you can type in:

```
reboot
```

Click on white button to select XFCE then login. If you don't like XFCE, add additional ones by typing:

```
sudo apt install kubuntu-desktop
```
