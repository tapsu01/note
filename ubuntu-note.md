In Ubuntu 20.04 LTS and Ubuntu 20.10, I removed snapd following this steps:

# stop snapd services
sudo systemctl stop snapd && sudo systemctl disable snapd
# purge snapd
sudo apt purge snapd
# remove no longer needed folders
rm -rf ~/snap
sudo rm -rf /snap /var/snap /var/lib/snapd /var/cache/snapd /usr/lib/snapd
Then, to avoid that other applications may reinstall it (chromium-browser is an example of application that restores snapd even if installed via apt) you can create a file no-snap.pref by issuing:

sudo -H gedit /etc/apt/preferences.d/no-snap.pref

and then copying the following content in it:

# To install snapd, specify its version with 'apt install snapd=VERSION'
# where VERSION is the version of the snapd package you want to install.
Package: snapd
Pin: release a=*
Pin-Priority: -10
