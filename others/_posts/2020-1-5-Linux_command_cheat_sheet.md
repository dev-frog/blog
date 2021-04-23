---
layout: post
title: Linux Commands Cheat Sheet.
description: >
  **Linux Commands** are categorized into different sections according to its usage. if you want to Download [Linux Command Cheat Sheet in pdf]() format.
---

# Linux Commands Cheat Sheet.


## What Is The Shell ?
Shell is the textual representation of the operating system. It takes keyboard commands and passes them to the operating system. All Linux distributions came with a Shell program called _BASH_. Which is the acronym for _"Bourne Again Shell."_


## What is Terminal Emulators?

To Interact with the Shell, We need a graphical user interface that can allow the user access to a textual representation of the operating system and its application. Most used terminal emulators on Linux are GNOME Terminal on GNOME and GTK-based environments, Konsole on KDE, and xfce4-terminal on Xfce as well as xterm.

### Help Commands.
> `whatis` : Search whatis database for complete words. used to find short descriptions of system commands. 

```bash
$ whatis ls
$ whatis man
$ whatis cd
$ whatis env
```

>`which` : Show the full path to shell commands.

```bash
$ which ls
$ which cd
$ which man
```

>`whereis` : Locate binary, source and man pages for a command.

```bash
$ whereis cd 
$ whereis ls
$ whereis man
$ whereis pwd
```


>`apropos`: Search through a database of short description to find help and man pages containing certain terms and commands.

```bash
$ apropos man
$ apropos ls
$ apropos cd
$ apropos pwd
```

>`man` : Manual pages for commands.

```bash
$ man ls
$ man cd
$ man pwd
$ man man
```

### Bash Variables.
>`env` : List current environment variables.

```bash
$ env
```

> `echo` : Output value of `$Name` variable. 


```bash
$ echo "Hello World"
$ echo $USER
$ echo $HOSTNAME
$ echo $PATH
$ echo $HOME
$ echo $BASH_VERSION
# Create a Variable
$ MY_VAR='Hello, from Variable'
$ echo $MY_VAR

# Some other command
$ echo {A..Z}
$ echo {1..100}
$ echo {001..15}
$ echo "Hello World !" > README.txt
```

> `export`: Set `$Name` to value in environment.


```bash
$ export MY_VAR="Hello, Centos 8"
#show see
$ env
```

> `$PATH` : Executable search path.


```bash
$ echo $PATH
```
> `$HOME` : Home Directory.


```bash
$ echo $HOME
```
> `$SHELL` : Current Shell.


```bash
$ echo $SHELL
```
### System Commands.
> `uname` : Displays Linux system information.


```bash
$ uname
$ uname --help
# print all infomation
$ uname -a
# print kernel name
$ uname -s
# print the operating system.
$ uname -o
```

> `uptime` : Displays how long the system has been running including load average.


```bash
$ uptime
$ uptime --help
$ uptime -s
$ uptime -p
```

> `hostname` : Shows the system host-name.


```bash
$ hostname
$ hostname --help
$ hostname -a
$ hostname -A
$ hostname -i
$ hostname -I

```

> `last reboot` : Shows system reboot history.


```bash
$ last reboot
```

> `date` : Displays current system date and time.


```bash
$ date 
$ date -u
$ date --date "10 days ago"
$ date +%T
```

> `cal` : Displays the current calendar month and day.


```bash
$ cal 
$ cal --help
$ cal 08 1991

```

> `w` : Displays currently logged in users in the system.


```bash
$ w
$ w -i 
```
> `whoami` : Displays who you are logged in as.


```bash
$ whoami
```
> `id` : prints real user id, and various other details related to the account.
```bash
$ id
$ id root
```


### Directory Operations
> `clear` : clear your terminal.


```bash
$ clear
```

> `pwd`: Print working directory.


```bash
$ pwd
```

> `ls` : prints the names of the files and directories.


```bash
$ ls
$ ls --help
$ ls -a
$ ls -l
$ ls -l -a -h
$ ls -lah
```

> `cd` : Change directory.


```bash
$ cd /etc
$ pwd
$ cd /bin
$ pwd

# This command is used to change directory to the home directory.
$ cd ~

$ cd -
$ cd ..
$ cd ../../
```

> `mkdir`: Create a new  directory.


```bash
$ mkdir MyFolder

$ mkdir -p Folder_1/Floder_A

```
> `rmdir`: Delete an empty directory.


```bash
$ rmdir MyFolder
```

###  File Operations
> `cat`: Concatenate,It reads data from the file and gives their content as output.


```bash
$ cat [file_name]
$ cat README.txt
$ cat /etc/passwd
$ cat /etc/hosts

# Custom end marker and Write Text in File.
$ cat  > longFile.txt << EOF 
> We are Writting in a Long file  
> We can write untile we use wordl of 'EOF'  
> EOF
```

> `less` :Display the contents of a file one pages at a time.


```bash
$ less LongFile.txt
$ less /etc/passwd
```

> `head`: Print the first 10 line of a file.


```bash
$ head /etc/passwd 
$ head longFile.txt 
$ head -3 longFile.txt
```

> `tail`: print the last 10 line of a file


```bash
$ tail /etc/passwd 
$ tail longFile.txt 
$ tail -3 longFile.txt

```

> `touch` : Create an empty file,


```bash
$ touch file1
$ touch file2 file3 file4
```

> `cp` : copy directory and files.


```bash
$ cp file1 copy_file
$ cp file1 [directory_path]
$ cp -r [directory] [copy_directory_path]
```

> `mv`: Move directory and files.


```bash
$ mv file1 New_file
$ mv file1 [directory_path]
$ mv -r [directory] [copy_directory_path]
```

> `rm` : Remove directory and files.


```bash
$ rm MyFile.txt 
$ rm README.txt

$ rm -r MyFloder 
$ rm -r Directory
```
> `file`: The file utility determines the file type.


```bash
$ file /dev/sda 
$ file File.png 
$ file /proc/cpuinfo
```




> `wc` : count the number of words or characters in a file.


```bash
$ wc randomFile.txt
$ wc -l /etc/passwd
$ wc --help
```

> `stat` : Display file system status.


```bash
$ stat file.txt
$ stat /etc/passwd
$ stat /var/log/audit/
```


> `cut` : Removes sections from lines of input.


```bash
$ cut -d ":" -f 1 /etc/passwd

```

### Search Files
> `grep` : Search text files for lines containing a matching pattern.


```bash
$ grep [word] [fileName]
$ grep root /etc/passwd
```

> `locate` : Find files by matching the whole path name.


```bash
$ locate [fileName]
$ locate shadow
```

> `find` : Search fir files in a directory hierarchy. 


```bash
# $ find [location/directory] -type [file type] -name [Name of the file
$ find / -type f -name passwd 
$ find /etc -type -f -name apache2
```

### Commands to know
> `sudo` : Execute a command as another user,usually with higher permissions.


```bash
$ sudo  ls /root 
$ sudo burpsuite

```
> `adduser` : To add/create a new user.


```bash
$ sudo adduser cent
```
> `passwd` : change password of a user.


```bash
$ sudo passwd cent
```

> `su` : Run a shell as another user or Change the user


```bash
$ su cent
```

> `shutdown` : Bring the system down in a safe way.


```bash
$ shutdown -h now

# Will shutdown in 5 minit
$ shutdown -h +5
# Will restart in 5 minit
$ shutdown -r +5
```
> `poweroff` : Turn off the system.


```bash
$ poweroff
```
 

> `init 6` : This command gracefully reboots the system.


```bash
$ init 6
	or
$ reboot
```



### Partitions and Disk Management.
> `df` : Report file system disk space usage.


```bash
$ df -h
```

> `fdisk `: lists all the partitions of all the drives


```bash
$ fdisk -l
```

>`lsblk`: It is similar to the output from `fdisk-l`, but it will also display devices with multiple partitions in a kind of tree


```bash
$ lsblk

```

> `lsof`: Established connections


```bash
$ lsof -i
```

### Process Management
> `ps` : Report on current processes


```bash
$ ps 
$ ps x 
$ ps aux

```

> `top` : Show real time processes.


```bash
$ top
```

> `kill` : Terminate a process by PID.


```bash
$ kill -9 [PID]
```


> `pkill` : Lookup of signal processes based on same and other attributes. 


```bash
$ pkill [service_name]
```

> `pgrep` : Grep for process information.


```bash
$ pgrep [service_name]
$ pgrep sshd
$ pgrep firewalld
```

> `jobs` : Display all jobs.


```bash
$ jobs
```


### Networking
> `ifconfig` : Configure network interface.


```bash
# intall net-tools
$ yum install net-tools

$ ifconfig 
$ ifconfig eth0 down 
$ ifconfig eth0 192.168.0.120 netmask 255.255.255.0 broadcast 192.168.0.255 
$ route add defult gw 192.168.0.1 
$ ifconfig eth0 hw ether 00:11:22:33:44:55 
$ ifconfig eth0 up
```

> `route` : Show/Manipulate the IP routing table.


```bash
$ route
# To display routing table in full numeric form.
$ route -n

# To add a default gateway.
$ sudo route add default gw 169.254.0.0
#To reject routing to a particular host or network.
$ sudo route add -host 192.168.1.51 reject
# To delete the default gateway.
$ route del default
```

> `ip` :   Show/M­ani­pulate routing, devices, policy and tunnels; replaces ifconfig, arp, and route.


```bash
$ ip a 
	or
$ ip addr

# Only show ipv4
$ ip -4 addr

# Only show ipv6
$ ip -6 addr

# Only show running interfaces.
$ ip link ls up

# Adding an IPv4 address
$ ip addr add 192.168.0.120/24 dev esp0s3

# Delete IP address to interface
$ ip addr del 192.168.0.120/24 dev esp0s3

```

> `ifup` :    Bring network interface up.


```bash
$ ifup enp0s3

```

> `ifdown` : Bring network interface down.


```bash
$ ifdown enp0s3
```

> `ping` : Send ICMP ECHO_R­EQUEST to network hosts


```bash

$ ping google.com
$ ping -c 3 google.com

```