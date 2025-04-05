# Linux / Debian Command-Cheatsheet

## 1.0 User Management

| Command | Comment |
|----|----|
| /usr/bin/ftptop | Display information about ProFTPd |
| adduser \<username\> | create user with additional information incl. homedir |
| passwd \<username\> | Change password |
| su \<user\> | set user |
| sudo -u www-data command | Execute command as user www-data |
| useradd -d \<homedir\> \<username\> | create user with home dir |
| userdel \<username\> | delete user |
| whoami | Output current user |

## 2.0 File and Directory Management

| Command                                         | Comment                                       |
| ----------------------------------------------- | --------------------------------------------- |
| cat textfile.txt \| awk '{print $1}'            | returns column 1 from textfile                |
| chgrp \<user\> \<datei/ordner\>                 | Change group                                  |
| chown \<user\> \<datei/ordner\>                 | Change owner                                  |
| cp -r newdir/\* olddir/                         | Copy files recursively                        |
| 'cp' -rf dir/{\*,.??\*} /dir/                   | hidden files and aliased cp -i will be copied |
| du -hs \<dir\>                                  | specify directory size                        |
| du -h \* \| sort -hr \> /home/user/filelist.txt | File list sorted by size                      |
| echo bla \> 1.txt                               | Create file 1.txt with content bla            |
| echo blabla \>\> 1.txt                          | Append blabla to file 1.txt                   |
| `find /directory -type d -exec chmod 755 {} \;` | Set permissions for folder recursive          |
| `find /directory -type f -exec chmod 644 {} \;` | Set permissions for files recursive           |
| ls                                              | List directory contents                       |
| ls -la dir                                      | List directory contents with user information |
| ls -lahS $(find / -type f -size +100000k)       | search for files \> 100MB                     |
| pwd                                             | Output working directory                      |
| tree                                            | list (Sub)-Directories in a tree view         |
| whereis                                         | Output binary directory                       |

### 2.1 File Compression

###### tar
- Compress: `tar cfv [Filename].tar [Directory1] [Directory2] [File1] [File2]`
- Decompress: `tar xfv [Filename].tar`
- List: `tar tfv [Filename].tar`

###### gz
- Compress: `tar cfvz [Filename].tar.gz [Directory1] [file1]`
- Decompress: `tar xfvz [Filename].tar.gz`

###### bz2
- Compress: `tar cfvj [Filename].tar.bz2 [Directory1] [file1]`
- Decompress: `tar xfvj [Filename].tar.bz2`

###### zip
- Compress files: `zip [Filename].zip [file1] [file2]`
- Compress directory: `zip -r [Filename].zip [directory1]`
- Decompress: `unzip [Filename].zip`
- Decompress and Overwrite: `unzip -o [Filename].zip -d dir/`

## 3.0 Log Management

### 3.1 Debian 12

- `journalctl`: komplettes Systemprotokoll
- `journalctl -f`: Protokoll in Echtzeit
- `jounalctl -u servicename`: Protokoll für einen bestimmten Dienst
- `journalctl -b`: Protokoll des letzten Boots
- `journalctl --since=yesterday`: Protokoll seit gestern
- `journalctl --since=Sep 05 12:00:00`: Protokoll ab Zeitvorgabe

## 4.0 Package management

| Command                   | Comment                    |
|---------------------------|----------------------------|
| apt-cache search \<pack\> | search for a package       |
| apt-get install \<pack\>  | install pack               |
| apt-get update            | update package cache       |
| apt-get upgrade           | upgrade installed packages |

## 5.0 System Management

| Command                         | Comment                                                                                                                                                                  |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| cat /proc/cpuinfo               | cpuinfo                                                                                                                                                                  |
| cat /proc/meminfo               | RAM Info                                                                                                                                                                 |
| cat /proc/version               | Deb Version                                                                                                                                                              |
| crontab -e                      | Edit cronjobs                                                                                                                                                            |
| crontab -l                      | Listen to cronjobs                                                                                                                                                       |
| date +%s                        | Output Unix time                                                                                                                                                         |
| date -d @1234631164             | Output Unix time in normal time                                                                                                                                          |
| df -h                           | free disc space                                                                                                                                                          |
| dpkg-reconfigure locales -plow  | Language settings                                                                                                                                                        |
| dpkg-reconfigure tzdata         | Time zone settings                                                                                                                                                       |
| kill -(6\|9\|15\|18\|19) <PID\> | 6: SIGABRT - Cancel process<br>9: SIGKILL - Terminate process<br>15: SIGTERM - terminate process cleanly<br>18: SIGCONT - Continue process<br>19: SIGSTOP - Stop process |
| mount -o remount -rw /          | release read-only file system                                                                                                                                            |
| ps                              | process list                                                                                                                                                             |
| ps -aux                         | detailed process list                                                                                                                                                    |
| sh file.sh                      | Shell file execute                                                                                                                                                       |

### 5.1 Shutdown Options

| Command        | Comment                 |
| -------------- | ----------------------- |
| shutdown -s    | Shut down or switch off |
| shutdown -r    | Restart (reboot)        |
| shutdown -l    | User logout             |
| shutdown -s -f | Forced shutdown         |

### 5.2 Change System Time

Set the time under Linux. [^2]

###### Show time
``` bash
timedatectl
```

#### Change time

###### Set time zone manually
``` bash
sudo timedatectl set-timezone Europe/Berlin
```

###### Select time zone with assistance
``` bash
sudo dpkg-reconfigure tzdata
```

## 6.0 Network Management

| Command                                           | Comment                        |
| ------------------------------------------------- | ------------------------------ |
| ip address                                        | Display IP address and netmask |
| ss -lpt                                           | Connections/Ports              |
| nload -u H                                        | Display bandwidth              |
| wget <http://www.psoft.net/shiv/HS/u-web-my4.tgz> | gets file                      |

## 7.0 Apache modules

###### Enable Module
``` bash
a2enmod modname
```

###### Disable Module
``` bash
a2dismod modname
```

###### Restart Apache
``` bash
service apache2 restart
```

----
## References


[^1]: PID denotes the process ID

[^2]: <https://wiki.ubuntuusers.de/Systemzeit/>
