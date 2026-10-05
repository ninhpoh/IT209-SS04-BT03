# Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub

## 1. Mục tiêu

* Tạo cặp khóa SSH sử dụng thuật toán Ed25519.
* Cấu hình xác thực SSH với GitHub.
* Liên kết repository cục bộ với repository GitHub bằng giao thức SSH.
* Đẩy mã nguồn và lịch sử commit lên GitHub.

## 2. Tạo SSH Key Ed25519

Sử dụng Git Bash để tạo cặp khóa SSH bằng thuật toán Ed25519:

```bash
ssh-keygen -t ed25519 -C "260806tan@gmail.com"
```

Khóa được lưu tại:

```text
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

Trong đó:

* `id_ed25519`: Private Key, không được chia sẻ hoặc đưa lên GitHub.
* `id_ed25519.pub`: Public Key, được sử dụng để xác thực với GitHub.

Kiểm tra Public Key bằng lệnh:

```bash
cat ~/.ssh/id_ed25519.pub
```

Sau đó Public Key được thêm vào GitHub tại:

**Settings → SSH and GPG keys → New SSH key**

## 3. Kiểm tra kết nối SSH với GitHub

Sử dụng lệnh:

```bash
ssh -T git@github.com
```

Kết quả:

```text
Hi ninhpoh! You've successfully authenticated, but GitHub does not provide shell access.
```

Kết quả trên xác nhận máy tính đã xác thực thành công với tài khoản GitHub `ninhpoh` thông qua SSH.

## 4. Khởi tạo Git Repository cục bộ

Di chuyển đến thư mục bài làm:

```bash
cd ~/Desktop/it-209/ss04/bt03
```

Khởi tạo Git Repository:

```bash
git init
```

Repository cục bộ được tạo tại:

```text
C:/Users/PC/Desktop/it-209/ss04/bt03/.git/
```

## 5. Thêm và Commit README.md

Thêm file README vào Git:

```bash
git add README.md
```

Tạo commit:

```bash
git commit -m "Add README for exercise 3"
```

Đổi tên branch chính thành `main`:

```bash
git branch -M main
```

## 6. Liên kết Remote Repository bằng SSH

Repository GitHub được sử dụng:

**IT209-SS04-BT03**

Thêm remote bằng giao thức SSH:

```bash
git remote add origin git@github.com:ninhpoh/IT209-SS04-BT03.git
```

Kiểm tra cấu hình remote:

```bash
git remote -v
```

Kết quả:

```text
origin  git@github.com:ninhpoh/IT209-SS04-BT03.git (fetch)
origin  git@github.com:ninhpoh/IT209-SS04-BT03.git (push)
```

Remote sử dụng giao thức **SSH**, không sử dụng HTTPS.

## 7. Đẩy dự án lên GitHub

Sử dụng lệnh:

```bash
git push -u origin main
```

Sau khi push thành công, mã nguồn và lịch sử commit được lưu trữ trên repository GitHub.

## 8. Thông tin Repository

**GitHub Username:**

```text
ninhpoh
```

**Repository:**

```text
IT209-SS04-BT03
```

**GitHub URL:**

```text
https://github.com/ninhpoh/IT209-SS04-BT03
```

**SSH Remote URL:**

```text
git@github.com:ninhpoh/IT209-SS04-BT03.git
```

## 9. Kết quả kiểm tra

### Kiểm tra SSH

Lệnh:

```bash
ssh -T git@github.com
```

Kết quả:

```text
Hi ninhpoh! You've successfully authenticated, but GitHub does not provide shell access.
```

→ Xác thực SSH với GitHub thành công.

### Kiểm tra Remote

Lệnh:

```bash
git remote -v
```

Remote:

```text
origin  git@github.com:ninhpoh/IT209-SS04-BT03.git (fetch)
origin  git@github.com:ninhpoh/IT209-SS04-BT03.git (push)
```

→ Repository local đã được liên kết với GitHub bằng giao thức SSH.

## 10. Kết luận

Đã hoàn thành cấu hình xác thực SSH bằng thuật toán **Ed25519**, xác thực thành công với tài khoản GitHub `ninhpoh`, liên kết repository local với GitHub bằng giao thức **SSH** và đẩy dự án lên repository:

```text
https://github.com/ninhpoh/IT209-SS04-BT03
```

## 11. Lưu ý bảo mật

Không chia sẻ hoặc upload Private Key:

```text
~/.ssh/id_ed25519
```

Chỉ Public Key được sử dụng để cấu hình xác thực với GitHub:

```text
~/.ssh/id_ed25519.pub
```

