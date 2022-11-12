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
and make sure to uncomment This line 
```bash 
DISABLE_LS_COLORS="true"
```

type source ~/.zshrc to take effect 

>## More Tools for your Terminal


>## rip

rip is an improved version of the rm command. It is faster, safer, and user-friendly. rip sends deleted files to a temp location so they can be recovered using rip -u. I really like the simplicity and the revert feature, as I don't have to worry about accidentally deleting something using rm. While rip can be aliased to replace rm, the creators advise not doing that as you might get used to it and do rm on other systems where you cannot revert the delete.

>### Installation

```bash
# Arch Linux
yay -S rm-improved
# Fedora/CentOS/Debian/Ubuntu
# Install from binary or build locally using Cargo
# macOS Homebrew
brew install rm-improved
# Cargo
cargo install rm-improved
```

>## xcp

xcp is a partial clone of the cp command. It is faster and more user-friendly with progress bars, parallel copying, .gitignore support, and so on. I like its simplicity and developer experience, especially the progress bars. I have aliased cp to xcp so I can use it everywhere.


>### Installation

```bash
# Arch Linux
yay -S xcp
# Fedora/CentOS/Debian/Ubuntu/macOS
# Install from binary or build locally using Cargo
# Cargo
cargo install xcp

# Alias cp to xcp
alias cp='xcp'
```
>## zoxide

zoxide is a smarter cd replacement. It remembers the directories you visit, and you can jump to them without providing a full path. You can provide partial paths or even a word from the path. When there are similar paths, zoxide offers an interactive selection using fzf. It is super fast and works with all major shells. I like how it works, and I have aliased cd to z so I can use it everywhere.


>### Installation

```bash
# Arch Linux
yay -S zoxide
# Fedora/CentOS
dnf install zoxide
# Debian/Ubuntu
apt install zoxide
# macOS/Linux Homebrew
brew install zoxide
# macOS MacPorts
port install zoxide
# Windows Scoop
scoop install zoxide
# Cargo
cargo install zoxide --locked
Once installed, you must add the following to your shell config file. For other shells, refer the docs
# bash (~/.bashrc)
eval "$(zoxide init bash)"
# zsh (~/.zshrc)
eval "$(zoxide init zsh)"
# fish (~/.config/fish/config.fish)
zoxide init fish | source
# Alias cd to z
alias cd='z'
```

>## dust

Dust is an alternative for the du command. It is fast and has a better UX with nice visualization for disk usage.


>### Installation

```bash 
# Arch Linux
yay -S dust
# Fedora/CentOS
# Install binary from https://github.com/bootandy/dust/releases
# Debian/Ubuntu
deb-get install du-dust
# macOS Homebrew
brew install dust
# macOS MacPorts
port install dust
# Windows Scoop
scoop install dust
# Cargo
cargo install du-dust
```

>## ripgrep

ripgrep (rg) is a line-oriented search tool that recursively searches your current directory for a regex pattern. It is faster than grep and has many features like compressed files search, colorized output, smart case, file type filtering, multi-threading, and so on. It understands .gitignore files and skips hidden and ignored files. Here is a feature comparison with other similar tools, and yes, it is faster than all the other tools in the list.


>### Installation

```bash 
# Arch Linux
yay -S ripgrep
# Fedora/CentOS
dnf install ripgrep
# Debian/Ubuntu
apt-get install ripgrep
# macOS/Linux Homebrew
brew install ripgrep
# macOS MacPorts
port install ripgrep
# Windows Scoop
scoop install ripgrep
# Cargo
cargo install ripgrep
```

>## fd

fd is a simpler alternative to find. It is more intuitive to use and comes with sensible defaults. It is extremely fast due to parallel traversing and shows a modern colorized output and supports patterns and regex, parallel commands, smart case, understands .gitignore files, and so on. I have aliased find to fd as I could never remember what options to pass to get a basic find command working.


>### Installation

```bash
# Arch Linux
yay -S fd
# Fedora/CentOS
dnf install fd-find
# Debian/Ubuntu
apt install fd-find
# macOS Homebrew
brew install fd
# macOS MacPorts
port install fd
# Windows Scoop
scoop install fd
# Cargo
cargo install fd-find
```

>## sd

sd is a find-and-replace CLI, and you can use it as a replacement for sed and awk. It is way more user-friendly and modern. It is also magnitudes faster than sed.

>### Installation

```bash
# Arch Linux
yay -S sd
# Fedora/CentOS
dnf install sd
# Debian/Ubuntu
# Install binary from the release page
# macOS Homebrew
brew install sd
# Windows Scoop
choco install sd-cli
# Cargo
cargo install sd
```

>## procs

procs is a ps replacement. It provides colorized human-readable output, multi-column search, more information than ps, docker support, paging, watch mode, and tree view. It is a much more user-friendly and modern alternative to ps. You can filter by name and PID and use logical and/or operators to combine multiple filters. It also has a tree view which is very useful for seeing the process hierarchy. It can also show docker container names for the process running docker containers.


>### Installation

```bash
# Arch Linux
yay -S procs
# Fedora/CentOS
dnf install procs
# Debian/Ubuntu
# Install binary from the release page
# macOS Homebrew
brew install procs
# macOS MacPorts
port install procs
# Windows Scoop
scoop install procs
# Cargo
cargo install procs
```

>## bottom

bottom is a top replacement with a nice terminal UI. It's quite feature-rich and customizable.


>### Installation

```bash
# Arch Linux
yay -S bottom
# Fedora/CentOS
dnf copr enable atim/bottom -y
dnf install bottom
# Debian/Ubuntu
dpkg -i bottom_0.6.8_amd64.deb
# macOS Homebrew
brew install bottom
# macOS MacPorts
port install bottom
# Windows Scoop
scoop install bottom
# Cargo
cargo install bottom --locked
```

>## Topgrade

Topgrade is a fantastic utility if you prefer to keep your system up-to-date, like me. It detects most of the package managers on your system and triggers updates. It is configurable, so you can configure it to ignore certain package managers. On my system, it detected pacman, SDKMAN, Flatpak, snap, Homebrew, rustup, Linux firmware, Pip, and so on. Topgrade is cross-platform; you can use it on Windows, macOS, and Linux.


>### Installation

```bash
# Arch Linux
yay -S topgrade
# Fedora/CentOS/Debian/Ubuntu/Windows
# Install binary from the release page
# macOS Homebrew
brew install topgrade
# macOS MacPorts
port install topgrade
# Cargo
cargo install topgrade --locked
```

>## Broot

Broot is a tree alternative with a better user experience, and you can use it to navigate a file structure. It's fast and respects .gitignore. You can cd into a directory from the tree view, open sub-directories in a panel, and even preview files. It has excellent keyboard navigation as well. It has many more features.


>### Installation

```bash
# Arch Linux
yay -S broot
# Fedora/CentOS/Debian/Ubuntu/Windows
# Install binary from release page https://dystroy.org/broot/install/
# macOS Homebrew
brew install broot
# macOS MacPorts
port install broot
# Cargo
cargo install broot --locked
```

>## Tokei

Tokei is a nice utility to count lines and stats of code. It is very fast, accurate, and has a nice output. It supports over 150 languages and can output in JSON, YAML, CBOR, and human-readable tables.


>### Installation

```bash
# Arch Linux
yay -S tokei
# Fedora/CentOS
dnf install tokei
# Debian/Ubuntu
# Install binary from the release page
# macOS Homebrew
brew install tokei
# macOS MacPorts
port install tokei
# Windows Scoop
scoop install tokei
# Cargo
cargo install tokei
```
