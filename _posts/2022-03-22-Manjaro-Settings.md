---
layout: post
title: "Basic Settings after Manjaro Installation"
use_math: false
lang: en
tags: notes
desc: This is a record of the basic settings after installing Manjaro, a Linux distribution. 
---

<br>

## 1. Mirrors Selection & System Updation

```
# (1) Select the mirrors by country, and update the system. 
sudo pacman-mirrors --country Singapore

# (2) Update system
sudo pacman -Syyu

# (3) Install basic developing tools
sudo pacman -S base-devel
```

<br>

## 2. Chinese Inputs Configuration

```
# (1) Installation: fcitx5
sudo pacman -S fcitx5-chinese-addons fcitx5-gtk fcitx5-qt
sudo pacman -S fcitx5-configtool

# (2) Configuration
touch ~/.pam_environment
echo 'GTK_IM_MODULE=fcitx5
QT_IM_MODULE=fcitx5
XMODIFIERS=@im=fcitx5' >> ~/.pam_environment
echo fcitx5 configuration Finished
```

<br>

## 3. Desktop Softwares Installation

```
# (1) Use AUR repository
sudo pacman -S yay

# (2) Install signal-desktop (a communication software)
sudo pacman -S signal-desktop
if [ -f "~/.signal_history" ]; then
     rm ~/.signal_history
fi
nohup signal-desktop --start-in-tray --use-tray-icon > ~/.signal_history 2>&1 &

# (3) Other apps: dropbox, zoom, dragon, ......

# (4) Pacman Clean
sudo pacman -Rns $(pacman -Qtdq)
sudo pacman -Scc
```

<br>

## 4. Texlive Environment Configuration

```
## Add to path in /etc/profile (environment variable for Windows 10)
export PATH=$PATH:/usr/local/texlive/20xx/
export PATH=$PATH:/usr/local/texlive/20xx/bin/xxxx
export PATH=$PATH:/usr/local/texlive/20xx/texmf-dist/doc/man
export PATH=$PATH:/usr/local/texlive/20xx/texmf-dist/doc/info
```

<br>

## 5. Github Configuration: SSH Connection

```
# (1) Check current ssh-key
ls -al ~/.ssh
# Now we have private key "id_rsa" and public key "id_rsa.pub"

# (2) Create a key
ssh-keygen -C "zhuanglinsheng@outlook.com"

# (3) Add ssh-key to ssh-agent
## First, start ssh-agent
eval "$(ssh-agent -s)"
# Then, add private key to agent
ssh-add ~/.ssh/id_rsa

# (4) Copy public key to github: Settings > SSH and GPG Keys > SSH Keys
cat ~/.ssh/id_rsa.pub

# (5) Test ssh connection
ssh -T git@github.com

# (6) Sync repository: using git@github.com:user-name/repository-name.git
#     instead of https://github.com/user-name/repository-name.git
```

<br>

## 6. SSHD Configurations

```
# (1) Start ssh service
## Manjaro
sudo systemctl enable sshd.service
sudo systemctl start sshd.service
sudo systemctl status sshd.service
sudo systemctl stop sshd.service

## Ubuntu
sudo systemctl enable ssh
sudo systemctl start ssh
sudo systemctl status ssh
sudo systemctl stop ssh

# (2) Ngrok configurations
## Install Ngrok from AUR:
yay install ngrok

## Verification (login https://ngrok.com/ and find token):
ngrok authtoken 1msZ5i9WIlm8yBDIEVXY07IPeJ5_3XTV6UpTLaMTsBL5pY2fH

## Ngrok proxy (Usages)
if [ -f "~/.nohup_history" ]; then
    rm ~/.nohup_history
fi
nohup ngrok tcp 22 --region ap -log=stdout > ~/.nohup_history 2>&1 &
ps -aux | grep "ngrok"

## Find the ngrok port in '.nohup_history' file (and it shows to be xxxxx = 15432 )
cat ~/.nohup_history | grep "url"

(4) Remote ssh connections (xxxxx stands for the ngrok port)
## General ssh Connection
ssh bob@0.tcp.ap.ngrok.io -p xxxxx

## Jupyter
ssh -N -L localhost:8080:localhost:8888 bob@0.tcp.ap.ngrok.io -p xxxxx
## In browser: localhost: 8888. Type in the default jupyter password. 

## Rstudio-server
ssh -N -L localhost:8181:localhost:8787 bob@0.tcp.ap.ngrok.io -p xxxxx
## In browser: localhost: 8181. Login as bob. 
```

<br>

## 7. Python Setup

```
# (1) Install packages
sudo pacman -S python-pip
pip3 install numpy scipy pandas matplotlib

# (2) pip installed packages' location:
# ~/.local/lib/python3.8/site-packages/ 

# (3) pip operations: list outdated
pip list -o

# (4) pip operations: updated outdated
pip list -o -f=freeze | grep -v '^\-e' | cut -d = -f 1 | xargs -n1 pip install -U
```

<br>

## 8. Jupyter Configurations & SSH Connection

```
# (1) Installation
sudo pacman -S jupyter

# Install jupyter notebook extensions
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user --skip-running-check

# (2) Basic jupyter environment settings:
## Set password (default 958642zls), the same as user password:
jupyter notebook password

## Jupyter for MATLAB: install Python-MATLAB API
pip install matlab_kernel

## Jupyter for gnuplot
pip install gnuplot_kernel
python -m gnuplot_kernel install --user

# (3) Start Jupyter Service
if [ -f "~/.jupyter_history" ]; then
    rm ~/.jupyter_history
fi
nohup jupyter notebook --no-browser --port=8888 > ~/.jupyter_history 2>&1 &
ps -aux | grep "jupyter"
```

<br>

## 9. Rstudio-Server Setup

```
# (1) Reference: 
## https://aur.archlinux.org/packages/rstudio-server-bin/

# (2) Installation
sudo pacman -S r
yay rstudio-server-bin

# (3) Enable service
## The default port is 8787
sudo useradd --system rstudio-server
sudo systemctl enable rstudio-server
sudo systemctl start rstudio-server
```

<br>

## 10. Matlab Configurations

```
# (1) MATLAB extern engines
## Python
cd /opt/MATLAB/R2020b/extern/engines/python
sudo python ./setup.py install
cd ~

## Java
cd /opt/MATLAB/R2020b/extern/engines/java/jar
javac -classpath engine.jar MyJavaCode.java
java -classpath .;engine.jar MyJavaCode
cd ~
```

<br>

## 11. IRC Configurations & Operations

```
# (1) Basic Infos:
## server: chat.freenode.net -p 6667 (no SSL) / 6697 (SSL)
## channel: ##toy-solvers
## nick: bobantbeejjjjj

# (2) create or join a channel
/join ##toy-solvers

# (3) Register
/NickServ REGISTER 5795867960 bobantbeej@outlook.com 

# (4) To complete the registration, we need email verification
/msg NickServ VERIFY REGISTER bobantbeej vyiweyrzfwgy

# (5) Register for Linsheng_Zhuang (in Office's network)
/msg NickServ REGISTER 5795867960 zhuanglinsheng@outlook.com
/msg NickServ VERIFY REGISTER Linsheng_Zhuang wpeheejbtqam

# (6) Type in the password within 60 seconds
/pass 5795867960

# (7) Check passwords for all guests, and kill the one with same nick as me
/ns set kill on

# (8) Change nick name
/nick newname

# (9) Ignore someone who is annoying
/Ignore nickname

# (10) Change topic
/topic ##channel newtopic

# (11) Check someone
/whois xxxxx

# (12) Private chat with someone
/msg nickname messages

# (13) Leave for some time
/away reasons for leaving

# (14) Leave the channel
/part ##toy-solvers reasons for leaving

# (15) Leave the server
/quit reasons for leaving
```

