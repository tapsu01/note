1. Remove folder/file use inode number

```sh
# First review the files & inodes
ls -li
# 2: remove the dir via inode
find . -maxdepth 1 -inum 21676512 -exec rm -rf "{}" \;
```
