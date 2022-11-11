---
layout: post
title: Customizing the linux zsh terminal | change the way you use linux 
date: '2022-11-10'
#images: [https://ddewaele.github.io/assets/images/jekyll_docker/logo.png]   
categories: [Linux]
tags: [Linux]
author: piragenth
---

Hi There, As a linux enthusiast i always use terminal but many of the default linux terminals are boring and has no color, shape or functionality
Today we will transform our terminal into wonderful and usable.

>## Setup zsh

```bash
#debian based distro
sudo apt install zsh

#Arch based distro
sudo pacman -S zsh
```

and type 'zsh' to swith the shell

>### Installing oh-my-zsh

```zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

>## [PowerLevel10K](https://github.com/romkatv/powerlevel10k){:target='blank'}

* in the command line 
```bash
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Then you need to enable the theme by typing  
```bash
 nano ~/.zshrc
 #and edit this line line like this
 ZSH_THEME="powerlevel10k/powerlevel10k"
 ```

>### Configure Powerlevel10k

make sure to install [FiraCode NF](https://github.com/ryanoasis/nerd-fonts/raw/master/patched-fonts/FiraCode/Medium/complete/Fira%20Code%20Medium%20Nerd%20Font%20Complete.ttf){:target='blank'} font before starting the process

type 
```bash
source ~/.zshrc
```
to zshrc config file to take effect.
after the at you should promted with powerlevel10k configuration wizard.
if it does not appeat typt "p10k configure".

>### oh-my-zsh plugins

* zsh-syntax-highlighting - It enables highlighting of commands whilst they are typed at a zsh prompt into an interactive terminal. This helps in reviewing commands before running them, particularly in catching syntax errors.

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

* zsh-autosuggestions - It suggests commands as you type based on history and completions.

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
 

>#### ls tools

Colorls:

```bash 
#installing ruby
sudo apt install ruby-full
sudo pacman -S ruby

#installing colorls
sudo gem install colorls
```
some alternative for colorls 
* [LSD](https://github.com/Peltoche/lsd){:target='blank'}
* [exa](https://github.com/ogham/exa){:target='blank'}

>## Activating all the plugins you have installed

In the ~/.zshrc file find the plugins=() to 
```bash
plugins=( git zsh-syntax-highlighting zsh-autosuggestions )
```

To change ls with colorls add this
```bash
if [ -x "$(command -v colorls)" ]; then
    alias ls="colorls"
    alias la="colorls -al"
fi
```
and make sure to uncomment thil line 
```bash 
DISABLE_LS_COLORS="true"
```

type source ~/.zshrc to take effect 
