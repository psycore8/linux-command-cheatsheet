
# Linux Commands Cheatsheet

## Command list

### User Management

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

### File and directory management

| Command | Comment |
|----|----|
| chgrp \<user\> \<datei/ordner\> | Change group |
| chown \<user\> \<datei/ordner\> | Change owner |
| cp -r newdir/\* olddir/ | Copy files recursively |
| 'cp' -rf dir/{\*,.??\*} /dir/ | hidden files and aliased cp -i will be copied |
| du -hs \<dir\> | specify directory size |
| du -h \* \| sort -hr \> /home/user/filelist.txt | File list sorted by size |
| echo bla \> 1.txt | Create file 1.txt with content bla |
| echo blabla \>\> 1.txt | Append blabla to file 1.txt |
| ls | List directory contents |
| ls -la dir | List directory contents with user information |
| ls -lahS $(find / -type f -size +100000k) | search for files \> 100MB |
| pwd | Output working directory |
| tar xfz u-web-my4.tgz | extract file |
| whereis | Output binary directory |

### Package management

| Command                   | Comment                    |
|---------------------------|----------------------------|
| apt-cache search \<pack\> | search for a package       |
| apt-get install \<pack\>  | install pack               |
| apt-get update            | update package cache       |
| apt-get upgrade           | upgrade installed packages |

### System Management

| Command                        | Comment                             |
|--------------------------------|-------------------------------------|
| cat /proc/cpuinfo              | cpuinfo                             |
| cat /proc/meminfo              | RAM Info                            |
| cat /proc/version              | Deb Version                         |
| crontab -e                     | Edit cronjobs                       |
| crontab -l                     | Listen to cronjobs                  |
| date +%s                       | Output Unix time                    |
| date -d @1234631164            | Output Unix time in normal time     |
| df -h                          | free disc space                     |
| dpkg-reconfigure locales -plow | Language settings                   |
| dpkg-reconfigure tzdata        | Time zone settings                  |
| kill -6 \<PID\> [^1]           | SIGABRT - Cancel process            |
| kill -9 \<PID\>                | SIGKILL - Terminate process         |
| kill -15 \<PID\>               | SIGTERM - terminate process cleanly |
| kill -18 \<PID\>               | SIGCONT - Continue process          |
| kill -19 \<PID\>               | SIGSTOP - Stop process              |
| mount -o remount -rw /         | release read-only file system       |
| ps                             | process list                        |
| ps -aux                        | detailed process list               |

### Network Management

| Command | Comment |
|----|----|
| ifconfig | Display IP address and netmask |
| netstat -pantu | Connections/Ports |
| nload -u H | Display bandwidth |
| sh blubb.sh | sh file executen |
| wget <http://www.psoft.net/shiv/HS/u-web-my4.tgz> | gets file |

### shutdown options

| Command        | Comment                 |
|----------------|-------------------------|
| shutdown -s    | Shut down or switch off |
| shutdown -r    | Restart (reboot)        |
| shutdown -l    | User logout             |
| shutdown -s -f | Forced shutdown         |

## change system time

Set the time under Linux. [^2]

### show time

``` bash
timedatectl
```

### change time

Set time zone manually

``` bash
sudo timedatectl set-timezone Europe/Berlin
```

Select time zone

``` bash
sudo dpkg-reconfigure tzdata
```

## Load Apache modules

``` bash
a2enmod modname
```



``` bash
a2dismod modname
```



``` bash
/etc/init.d/apache2 restart
```

## References


[^1]: PID denotes the process ID

[^2]: <https://wiki.ubuntuusers.de/Systemzeit/>
