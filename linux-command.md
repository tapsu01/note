1. Remove folder/file use inode number

```sh
# First review the files & inodes
ls -li
# 2: remove the dir via inode
find . -maxdepth 1 -inum 21676512 -exec rm -rf "{}" \;
```

2. Xem thư mục nặng nhất trong /

```sh
sudo du -h --max-depth=1 / | sort -hr
```

3. Xóa binlog trong mysql

```sh
# đăng nhập mysql
mysql -u username -p

# Xoá binlog cũ trước 7 ngày:
PURGE BINARY LOGS BEFORE DATE_SUB(NOW(), INTERVAL 7 DAY);

# Xóa TỚI file cụ thể
PURGE BINARY LOGS TO 'mysql-bin.000120';
```
