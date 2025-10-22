# Nodejs-Notes

# ========= Ubuntu on Windows =====

## --------- Install nvm command -------------------------
# Step 1 
* update apt
  ```bash
    sudo apt update && sudo apt upgrade -y
  
* install package support if not
    ```bash
    sudo apt install -y build-essential curl
  
* install nvm
  ```bash
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

# Step 2 – Active nvm in the current session

```bash
  source ~/.bashrc
```bash
  source ~/.zshrc

* Check

  ```bash
  nvm --version

# Step 3 – Install Nodejs version by nvm

* Ex:

    ```bash
    nvm install 18
    ```bash
    nvm use 18

* Set default version

    ```bash
    nvm alias default 18

# Bước 4 – Manager version Nodejs
* List all version
    ```bash
    nvm ls-remote

* List installed version

    ```bash
    nvm ls
  
* Install version

```bash
  nvm install 20.0.0    

* Switch version
  
    ```bash
  nvm use 20.0.0
  
* Set default version
  
    ```bash
  nvm alias default 18
    
* Delete version
  
    ```bash
  nvm uninstall 18

## ----- End install nvm ---------
## ----- Get Ip ---------

  ```bash
  ip route show default | awk '{print $3}'

## ----- End get Ip -----------

# ===== Config Mongodb for Ubuntu connect to Windows ======
# 1. 🧱 Windows Defender Firewall with Advanced Security

* Open "Windows Defender Firewall with Advanced Security"

   "Inbound Rules" => "New Rule...".
  
    Select Port -> Next.
  
    set "Specific local ports:" 27017 => Next.
  
    check "Allow the connection" -> Next.
  
    check all (Domain, Private, Public) -> Next.
  
    Set rule name: MongoDB WSL -> Finish.
  
  Run again Nodejs

# 2. ⚙️ Update config bindIp của MongoDB
* Find file mongod.cfg. location: C:\Program Files\MongoDB\Server\<this version>\bin\mongod.cfg

  Open this file:
  
  find to item net:
  
  YAML
  
  net:
    port: 27017
    bindIp: 127.0.0.1 
  
  update bindIp from 127.0.0.1 to 0.0.0.0:
  
  YAML
  
  net:
    port: 27017
    bindIp: 0.0.0.0  # update line

  (Note: 0.0.0.0 - "Allow connection from all ips").

  Save file and restart MongoDB Service
* Restart service
  
  Open Service.msc on windows
    Restart service name: "MongoDB Server"

# ===== End config connect DB ============
