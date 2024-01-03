---
layout: post
title: "Basic Linux Operations, a Memorandum (Manjaro for Example)"
use_math: false
lang: en
tags: notes
desc: This is a record of the basic settings after installing Manjaro, a Linux distribution. 
---

<br><br>

Afrer installation, how to select the mirrors by country and update the system?

```
sudo pacman-mirrors --country Singapore
sudo pacman -Syyu
sudo pacman -S base-devel # Install basic developing tools
```

How to enable Chinese input?

```
sudo pacman -S fcitx5-chinese-addons fcitx5-gtk fcitx5-qt
sudo pacman -S fcitx5-configtool
touch ~/.pam_environment
echo 'GTK_IM_MODULE=fcitx5
QT_IM_MODULE=fcitx5
XMODIFIERS=@im=fcitx5' >> ~/.pam_environment
echo fcitx5 configuration Finished
```

Is there any `pacman` tricks?

```
sudo pacman -S yay  ## Use AUR repository
sudo pacman -Rns $(pacman -Qtdq)  ## Pacman Clean
sudo pacman -Scc
```

How to let software run as backstage process? Signal as an example

```
sudo pacman -S signal-desktop  ## 

if [ -f "~/.signal_history" ]; then
     rm ~/.signal_history
fi
nohup signal-desktop --start-in-tray --use-tray-icon > ~/.signal_history 2>&1 &
```

How to add environment path? Texlive as an example

```
## add to path in /etc/profile
export PATH=$PATH:/usr/local/texlive/20xx/
export PATH=$PATH:/usr/local/texlive/20xx/bin/xxxx
export PATH=$PATH:/usr/local/texlive/20xx/texmf-dist/doc/man
export PATH=$PATH:/usr/local/texlive/20xx/texmf-dist/doc/info
```

How to connect host with SSH? Github as an example

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
# (7) How about SSHD?
sudo systemctl enable sshd.service
sudo systemctl start sshd.service
sudo systemctl status sshd.service
sudo systemctl stop sshd.service
```

How to make your computer a server? Using `ngrok` 

```
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
## General ssh Connection
ssh bob@0.tcp.ap.ngrok.io -p xxxxx
## Jupyter
ssh -N -L localhost:8080:localhost:8888 bob@0.tcp.ap.ngrok.io -p xxxxx
## In browser: localhost: 8888. Type in the default jupyter password. 
## Rstudio-server
ssh -N -L localhost:8181:localhost:8787 bob@0.tcp.ap.ngrok.io -p xxxxx
## In browser: localhost: 8181. Login as bob. 
```

Is there any `pip` tricks?

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

How can I use jupyter remotely?

```
# Install jupyter notebook extensions
pip install jupyter_contrib_nbextensions
jupyter contrib nbextension install --user --skip-running-check
# Basic jupyter environment settings
## Set password (default 958642zls), the same as user password:
jupyter notebook password
# Start Jupyter Service
if [ -f "~/.jupyter_history" ]; then
    rm ~/.jupyter_history
fi
nohup jupyter notebook --no-browser --port=8888 > ~/.jupyter_history 2>&1 &
ps -aux | grep "jupyter"
```

