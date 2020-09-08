1. iTerm2 auto login

    - iTerm2 / preferences / profiles / Command input:

      ```none
      login -pfq {username} /usr/local/bin/zsh -il
      ```
2. iTerm2 & zsh login slow
    - Run command:
      ```none
      sudo rm -rf /private/var/log/asl/*.asl
      ```
