# Nodejs-Notes

# ====================== Ubuntu on Windows ================================

# --------- Install nvm command -------------------------
Bước 1 
# update apt
sudo apt update && sudo apt upgrade -y
# install package support if not
sudo apt install -y build-essential curl
# install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
# Script sẽ thêm vào file ~/.bashrc hoặc ~/.zshrc các dòng như:
{
  export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
  [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
}
Bước 2 – Kích hoạt nvm trong session hiện tại
# Nạp lại cấu hình shell
source ~/.bashrc
# hoặc nếu dùng zsh
# source ~/.zshrc

# Kiểm tra
nvm --version

Bước 3 – Cài Node bằng nvm

# Ví dụ bạn muốn cài Node 18 LTS:

nvm install 18
nvm use 18


# Bạn có thể kiểm tra: node -v, npm -v.

# Để mặc định mỗi khi mở terminal dùng version này:

nvm alias default 18

🔁 Bước 4 – Quản lý nhiều version Node
# Liệt kê các bản có thể cài: rất dài

nvm ls-remote

# Liệt kê các bản đã cài:

nvm ls


# Cài thêm một bản khác, ví dụ Node 20:

nvm install 20


# Chuyển phiên bản:

nvm use 20


# Xóa bản không dùng:

nvm uninstall 18

🎛️ Bước 5 – Gắn với dự án Angular

# Trong thư mục dự án Angular của bạn (ví dụ ~/projects/angular15):

cd ~/projects/angular15
nvm use 18   # nếu dự án phù hợp Node 18
node -v      # kiểm tra
npm install  # sử dụng Node 18 và npm tương ứng
npm run start


