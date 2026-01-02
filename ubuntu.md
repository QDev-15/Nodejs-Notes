# Notejs 18.10

## Step 1: insall nvm - install nodejs version 18.10
### update apt install nvm prerequisites
```bash
  sudo apt update
  sudo apt install -y curl build-essential
```
### Install nvm 
```bash
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
### After it finishes, reload your shell:
```bash
  source ~/.bashrc
```
### Verify NVM is installed:
```bash
  nvm --version

  You should see something like ==> 0.39.7
```

## Step 2: Install Node.js using NVM
### Install Node 18.10
```bash
  nvm install 18.10
```
### Use node 18
```bash
  nvm use 18.10
```

## Step 3: Create folder and Clone from Github 
### create folder
```bash
  mkdir Projects
```
### Check and add ssh-key if not exists 
```bash 
  ssh-keygen -t ed25519 -C "your_email_github@example.com"
```
### Copy SSH public key
```bash
  cat ~/.ssh/id_ed25519.pub
```
-> Copy all start width:
```bash
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAI...
```
### Add SSH key to GitHub
  1. Open link (logined GitHub):
    👉 https://github.com/settings/ssh/new

  2. Set:

    Title: Ubuntu WSL or Office Laptop

    Key type: Authentication Key

    Key: paste public key coped

  3. Click Add SSH key

    ✔ Done add key to GitHub
### Test SSH
```bash
  ssh -T git@github.com
```
Result:
```bash
Hi quynhvp90! You've successfully authenticated, but GitHub does not provide shell access.
```

### If Test Error => Copy all and paste to command
```bash
  mkdir -p ~/.ssh
  chmod 700 ~/.ssh

  touch ~/.ssh/known_hosts
  chmod 600 ~/.ssh/known_hosts

  ssh-keyscan -t ed25519 github.com >> ~/.ssh/known_hosts
```
### If remove key on github and add again
```bash
  cat ~/.ssh/id_ed25519.pub
```
-> Copy all start width:
```bash
  ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAI...
```
* and back to step: * Add SSH key to GitHub *

### Get source from github
```bash
  git clone git@github.com:quynhvp90/webclient-ngx.git
```
```bash
  cd webclient-ngx
```
## Install packages
```bash
  npm i --force
```
