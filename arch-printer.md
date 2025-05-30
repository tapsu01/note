# Setup Canon LBP-6230dn on ArchLinux

0. Install `sudo pacman -S ghostscript`
1. Install `yay -S cups`
2. Enable its service `sudo systemctl enable cups.service`
3. Restart the service `sudo systemctl restart cups.service`
4. Check its status `sudo systemctl status cups.service`
5. Install `sudo pacman -S libxml2-legacy`
6. Install `yay -S cndrvcups-lt cnrdrvcups-lb` 
7. Open `http://localhost:631/` in Chrome.
8. Go to `Administration` and then click on `Add Printer`
