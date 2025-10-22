# Nodejs-Notes

# ========= Ubuntu on Windows =====

## --------- Install nvm command -------------------------
# Step 1 
* update apt
  {
    $sudo apt update && sudo apt upgrade -y
  }
* install package support if not
    $sudo apt install -y build-essential curl
*install nvm
    $curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

# Step 2 – Active nvm in the current session
  $source ~/.bashrc
  $source ~/.zshrc

*Check
  $nvm --version

# Step 3 – Install Nodejs version by nvm

* Ex:
    $nvm install 18
    $nvm use 18

* Set default version
    $nvm alias default 18

# Bước 4 – Manager version Nodejs
* List all version
    $nvm ls-remote

* List installed version

    $nvm ls
* Install version
    $nvm install 20.0.0    

* Switch version
    $nvm use 20.0.0
  
* Set default version
    $nvm alias default 18
    
* Delete version
    $nvm uninstall 18

## ----- End install nvm ---------
## ----- Get Ip ---------

  ip route show default | awk '{print $3}'

## ----- End get Ip -----------

# ===== Config Mongodb for Ubuntu connect to Windows ======
# 1. 🧱 Windows Defender Firewall with Advanced Security

Open "Windows Defender Firewall with Advanced Security"

 "Inbound Rules" => "New Rule...".

  Select Port -> Next.

  set "Specific local ports:" 27017 => Next.

  check "Allow the connection" -> Next.

  check all (Domain, Private, Public) -> Next.

  Set rule name: MongoDB WSL -> Finish.

Run again Nodejs

# 2. ⚙️ Update config bindIp của MongoDB
*Find file mongod.cfg. location: C:\Program Files\MongoDB\Server\<this version>\bin\mongod.cfg

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

*(Note: 0.0.0.0 - "Allow connection from all ips").

Save file and restart MongoDB Service

Open Service.msc on windows
  Restart service name: "MongoDB Server"

# ===== End config connect DB ============
