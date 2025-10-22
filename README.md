# Nodejs-Notes

# ========= Ubuntu on Windows =====

## --------- Install nvm command -------------------------
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
## ----- End install nvm ---------
## ----- Get Ip ---------

  ip route show default | awk '{print $3}'

## ----- End get Ip -----------

# ===== Cấu hình Mongodb ubuntu connect to windows ======
Lỗi MongooseServerSelectionError: connection timed out có nghĩa là ứng dụng Node.js của bạn (chạy trong WSL) đã tìm thấy địa chỉ IP của máy Windows (172.24.176.1), nhưng khi nó cố gắng kết nối đến cổng 27017 tại đó, nó không nhận được phản hồi cho đến khi hết thời gian.

Đây gần như chắc chắn là một trong hai vấn đề:

Tường lửa (Firewall) của Windows đang chặn kết nối.

Cấu hình MongoDB trên Windows không cho phép kết nối từ bên ngoài.

#Hãy kiểm tra từng bước sau:

#1. 🧱 Tường lửa Windows (Lý do phổ biến nhất)
Tường lửa của Windows đang coi kết nối từ WSL (Ubuntu) là một kết nối "từ bên ngoài" và đang chặn nó.

Cách sửa: Bạn phải tạo một "Inbound Rule" (Luật cho kết nối đến) để cho phép cổng 27017.

Trên Windows, mở "Windows Defender Firewall with Advanced Security" (bạn có thể tìm nó trong Start Menu).

Ở cột bên trái, nhấn vào "Inbound Rules".

Ở cột bên phải, nhấn vào "New Rule...".

Một cửa sổ mới sẽ hiện ra:

Chọn Port -> Next.

Chọn TCP và điền vào "Specific local ports:" là 27017 -> Next.

Chọn "Allow the connection" -> Next.

Để nguyên 3 ô (Domain, Private, Public) được tick -> Next.

Đặt tên cho nó (ví dụ: MongoDB WSL) và nhấn Finish.

Thử chạy lại ứng dụng Node.js của bạn.

#2. ⚙️ Cấu hình bindIp của MongoDB
Nếu Tường lửa đã mở mà vẫn lỗi, thì do MongoDB trên Windows được cấu hình chỉ nghe kết nối từ localhost của Windows (127.0.0.1).

Cách sửa: Bạn cần sửa file cấu hình của MongoDB để nó chấp nhận kết nối từ mọi IP.

Tìm file mongod.cfg. Vị trí phổ biến nhất là: C:\Program Files\MongoDB\Server\<phiên-bản-của-bạn>\bin\mongod.cfg

Mở file này bằng một trình soạn thảo (ví dụ: Notepad) với quyền Administrator (Quản trị viên).

Tìm đến mục net:, nó sẽ trông như thế này:

YAML

net:
  port: 27017
  bindIp: 127.0.0.1 
Sửa bindIp từ 127.0.0.1 thành 0.0.0.0:

YAML

net:
  port: 27017
  bindIp: 0.0.0.0  # Sửa dòng này
(Lưu ý: 0.0.0.0 nghĩa là "chấp nhận kết nối từ bất kỳ địa chỉ IP nào").

Lưu file lại.

Rất quan trọng: Khởi động lại dịch vụ MongoDB.

Mở Services trên Windows (tìm trong Start Menu).

Tìm dịch vụ tên là "MongoDB Server".

Nhấn chuột phải vào nó và chọn Restart.

Sau khi MongoDB khởi động lại, thử chạy lại ứng dụng Node.js của bạn.

# ===== End config connect DB ============
