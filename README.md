# Linux-Commands

A Linux command cheat sheet.

Let's get started

## Command to work with directories

1. go to root directory

```
cd ~
```

2. Print To Screen

```
echo hi
```

2. list of files and folders

```
ls
```

3. change directory

```
cd Desktop
```

4. Present working directory

```
pwd
```

5. Make directory

```
mkdir new_directory
```

6. Run multiple commands

```
cd new_directory; mkdir src; cd src; pwd
```

7. make directory hierarchy

```
mkdir -p /app/src/assets/images
```

8. Remove directory

```
rm -r /tmp/my_dir1
```

9. copy directory

```
cp -r my_dir1 /tmp/my_dir1
```

## Commands to work with File

1. Create a new file with no content

```
touch test.txt
```

2. Add content to the file

```
cat > test.txt
__enter your text
```

- press `ctrl+D` to save the file

3. view the content of the file

```
cat test.txt
```

4. copy file

```
cp test.txt copy.txt
```

5. move a file

```
mv copy.txt move.txt
```

- Used to rename the file

5. Delete a file

```
rm copy.txt
```

## User Accounts

1. Which user you are

```
whoami
```

2. For more info use id

```
id
```

3. switch one user to another

```
su siya
```

- password: \***\*\*\*\***
- then siya is the user

4. Regular user can not perform task in root directory so to acess the root directory root user provide sudo priviledge to regular user so that regular user can perform some specific task which is not directly perfoemed

```
ls /root
```

: ls: error permission denied

- to acess use sudo priviledge provided by root

```
sudo ls /root
```

- This command will work for the regular user not for the user you created

## Download files from internet

```
curl https://www.cyberciti.biz/files/sticker/sticker_book.pdf -o output.pdf
```

There are many other methods too [read more](https://www.tecmint.com/linux-command-line-tools-for-downloading-files/)

## Check OS version

- Check release

```
ls /etc/*release*
----------------------
/etc/lsb-release  /etc/os-release

/etc/upstream-release:
lsb-release
```

- More detailed view

```
cat /etc/*release*
------------------
My Output:
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=20.1
DISTRIB_CODENAME=ulyssa
DISTRIB_DESCRIPTION="Linux Mint 20.1 Ulyssa"
NAME="Linux Mint"
VERSION="20.1 (Ulyssa)"
ID=linuxmint
ID_LIKE=ubuntu
PRETTY_NAME="Linux Mint 20.1"
VERSION_ID="20.1"
HOME_URL="https://www.linuxmint.com/"
SUPPORT_URL="https://forums.linuxmint.com/"
BUG_REPORT_URL="http://linuxmint-troubleshooting-guide.readthedocs.io/en/latest/"
PRIVACY_POLICY_URL="https://www.linuxmint.com/"
VERSION_CODENAME=ulyssa
UBUNTU_CODENAME=focal
cat: /etc/upstream-release: Is a directory
```

## Package Manager in Linux

Package manager allows us to install various software into linux system.

Linux mint uses Apt and Snap

Red hat uses YUM

## Services

Any software that runs as a service in background is ninstalled such as database server or devops tools like docker they are automatically considered as service in a system.

1. Start a service docker

```
systemctl start docker
```

2. Stop a service

```
systemctl stop docker
```

3. Check the status of service

```
systemctl status docker
```

4. Configure Docker to start at startup

```
systemctl enable docker
```

5. Configure docker not to start at statup

```
systemctl disable docker
```

## How do we configure a software or a program as sefrvice

For Example We have a simple pyhon program

```
/usr/bin/python3 /Desktop/test/manage.py
```

Say this is a server running at

- Server running on http://127.0.0.1:8000

To get response

```
curl http://127.0.0.1:8000
```

Now we want that our server automatically restart when we start the system and auto restart in case of crash

- We must configure our program as systemd service
- Systemd service is configured using a service unit file these files are located at **/etc/systemd/system**

- let's create a unit file
- file must be named as your flie name
- manage.service

```service
#allow others to understand
[Unit]
Description=My django web application

# application as service
[Service]
ExecStart= python3 manage.py runserver

# comand to run before the execution
[ExecStartPre]=python3 manage.py makemigrations

# command after execution
[ExecStartPost] = python3 manage.py migrate

#to restart the applicationa utomatically
Restart=always
# this will allow to run during startup
[install]=multi-user.target
```

then let systemctl to know our new sevice

```
systemctl daemon-reload
```

Then start the service

```
systemctl  start manage
```

Check the status of your service

```
systemctl status manage
```

Enabele your service to start on startup

```
shystemctl enable manage
```

## Vi Editor

1. Vi editor have two mode

- Command Mode - press `esc` to switch in command mode
- Insert Mode - press `i` to swich in insert mode

2. To move around

- up - `k` , `arraow-up`
- down - `j` , `arrow-down`
- left - `h`, `arraow-left`
- right - `l`, `arraow-right`

3. Delete

- `x` - delete a carecter
- `dd` - delete entire line

3. Copy a line and paste

- copy - `yy`
- paster - `p`

4. Scroll page up and down

- up - `ctrl + u`
- down - `ctrl + d`

5. Commands

- before starting command - `:`
- save - `:w`
- save with file name - `:w filename`
- quit wirhout save - `:q`
- save changes and quit - `:wq`
- Find the word - `/of`
- to move cusor to all occurances of the word - `n`
