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
  use 18.10
```
