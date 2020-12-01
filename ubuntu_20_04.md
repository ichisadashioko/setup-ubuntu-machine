# Ubuntu Desktop 20.04

## Modify `.bashrc`

```sh
# shorten bash cwd path
PROMPT_DIRTRIM=1

# make * select dot files
shopt -s dotglob

alias aup="sudo apt update"
alias ll="ls -la"
alias la="ls -a"

# block core-js ads
export ADBLOCK=1
```

## Change timezone

```sh
sudo dpkg-reonfigure tzdata
```

## Install some development packages

- Add the `git` official `ppa` for the latest `git` release

```sh
sudo add-apt-repository ppa:git-core/ppa
```

We will have to press `Enter` to continue.

```sh
sudo apt update
```

```sh
sudo apt install \
git git-lfs \
tmux vim \
curl wget net-tools htop tree dos2unix \
build-essential gcc g++ cmake autoconf
```

- Configure `git` name and email

```sh
git config --global user.name "shioko"
git config --global user.email "ichisadashioko@gmail.com"

git config --global core.editor vim
git config --global core.autocrlf false
git config --global pull.ff only

# cache git credentials
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=1'
```

- `java`

```sh
sudo apt install default-jdk
```

- `nodejs`

Use `nvm-sh` - https://github.com/nvm-sh/nvm

Install `nvm-sh`

```sh
wget -qO- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

The installation script will modify our `.bashrc` file so we need to open a new terminal to reload the `.bashrc` content.
`Ctrl+Alt+T` is faster than `source ~/.bashrc` or `exec $SHELL`.

Install the latest `LTS` version

```sh
nvm install --lts
```

## Change default editor for using in terminal (e.g. `visudo`)

> I hate `nano` interface. It looks so confusing. Why do they use the `^` character for implying `Ctrl` key? Why do I have enter the file path to save file while I opened an existing file.

```sh
export EDITOR=$(which vi)
```

or 

```sh
sudo update-alternatives --config editor
```

and choose `vi` or `vim.basic`

## Install some GUI softwares

- Remote desktop client

```sh
sudo apt-add-repository ppa:remmina-ppa-team/remmina-next
```

Press `Enter` to continue

```sh
sudo apt update
```

```sh
sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret
```

- Archiving and its extensions

```sh
sudo apt install p7zip p7zip-rar unzip zip tar
```

- media player

VLC

```sh
sudo apt install vlc
```

- Disk Usage Analyzer

```sh
sudo apt install baobab
```
