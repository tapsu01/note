# Arch Linux with BSPWM

#### Install browser

```sh
yay -S chromium brave-bin
```

#### Install terminal

```sh
yay -S xfce4-terminal
```

#### Install fonts

```sh
yay -S adobe-source-code-pro-fonts \
  noto-fonts-emoji otf-font-awesome otf-font-awesome-4 ttf-droid \
  ttf-fantasque-sans-mono ttf-jetbrains-mono ttf-jetbrains-mono-nerd siji-ttf
```

#### Install thunar and dependencies

```sh
yay -S thunar thunar-volman tumbler thunar-archive-plugin polkit-gnome xarchiver unzip
```

#### Install audio

```sh
yay -S pulseaudio-ctl pavucontrol pulseaudio
```

#### Install polybar and dmenu

```sh
yay -S polybar dmenu 
```

#### Install vscode

```sh
yay -S visual-studio-code-bin
```

#### Create `.config` folder

```sh
mkdir ~/.config
mkdir ~/.config/bspwm
mkdir ~/.config/sxhkd
```

- Copy `bspwm` and `sxhkd` config file

```sh
cp /usr/share/doc/bspwm/examples/bspwmrc ~/.config/bspwm
cp /usr/share/doc/bspwm/examples/sxhkdrc ~/.config/sxhkd
```

#### Install ibus-bamboo

```sh
bash -c "$(curl -fsSL https://raw.githubusercontent.com/BambooEngine/ibus-bamboo/master/archlinux/install.sh)"
```

Add to `/etc/profile`

```sh
export GTK_IM_MODULE=ibus
export QT_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT4_IM_MODULE=ibus
export CLUTTER_IM_MODULE=ibus
ibus-daemon -drx
```
