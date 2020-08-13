## Install Sublime Text 3 - Version 3.2.2, Build 3211 On Ubuntu 20.04



1. Install the GPG key:

   `wget -qO - https://download.sublimetext.com/sublimehq-pub.gpg | sudo apt-key add -`

2. Ensure apt is set up to work with https sources:

   `sudo apt-get install apt-transport-https`

3. Select the channel to use:

   - **Stable**

     ```none
     echo "deb https://download.sublimetext.com/ apt/stable/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
     ```

   - **Dev**

     ```none
     echo "deb https://download.sublimetext.com/ apt/dev/" | sudo tee /etc/apt/sources.list.d/sublime-text.list
     ```

4. Update apt sources and install Sublime Text

   ```none
   sudo apt-get update
   sudo apt-get install sublime-text
   ```



___



## Install Package Control

1. Open the `Tools` menu
2. Select `Install Package Control…`



## Install Packages For PHP development

1. *`ctrl+shift+p`*
2. Type `Install Package Control`, press `enter`
3. Search and Install
   - `SublimeLinter`: The code linting framework for Sublime Text 3
   -  `SublimeLinter-php`: SublimeLinter 3 plugin for PHP, using php-l.



## Themes

1. Dracula
