# Bài 3: Cấu hình xác thực SSH và Đẩy dự án lên GitHub

## 1. Mục tiêu

* Khởi tạo cặp khóa SSH sử dụng thuật toán Ed25519.
* Cấu hình xác thực SSH với GitHub.
* Liên kết repository cục bộ với repository trên GitHub bằng giao thức SSH.
* Đẩy mã nguồn và lịch sử commit lên GitHub.

## 2. Tạo SSH Key Ed25519

Sử dụng Git Bash trên Windows và thực hiện lệnh:

```bash
ssh-keygen -t ed25519 -C "260806tan@gmail.com"
```

Khóa được tạo tại:

```text
~/.ssh/id_ed25519
~/.ssh/id_ed25519.pub
```

Trong đó:

* `id_ed25519` là Private Key, không được chia sẻ hoặc đưa lên GitHub.
* `id_ed25519.pub` là Public Key, được sử dụng để xác thực với GitHub.

Public Key được kiểm tra bằng lệnh:

```bash
cat ~/.ssh/id_ed25519.pub
```

Sau đó Public Key được thêm vào GitHub tại:

**GitHub → Settings → SSH and GPG keys → New SSH key**

## 3. Kiểm tra kết nối SSH với GitHub

Sử dụng lệnh:

```bash
ssh -T git@github.com
```

Kết quả:

```text
Hi ninhpoh! You've successfully authenticated, but GitHub does not provide shell access.
```

Kết quả trên xác nhận máy tính đã xác thực thành công với tài khoản GitHub `ninhpoh` thông qua giao thức SSH.

## 4. Khởi tạo Git Repository cục bộ

Di chuyển đến thư mục bài làm:

```bash
cd ~/Desktop/it-209/ss04/bt03
```

Khởi tạo Git Repository:

```bash
git init
```

Kết quả:

```text
Initialized empty Git repository in C:/Users/PC/Desktop/it-209/ss04/bt03/.git/
```

## 5. Commit mã nguồn

Thêm các file vào Git:

```bash
git add .
```

Tạo commit:

```bash
git commit -m "Complete exercise 3"
```

## 6. Liên kết Remote Repository bằng SSH

Repository GitHub được liên kết bằng giao thức SSH với định dạng:

```text
git@github.com:username/repository.git
```

Thêm remote:

```bash
git remote add origin git@github.com:ninhpoh/REPOSITORY_NAME.git
```

Kiểm tra remote:

```bash
git remote -v
```

Kết quả mong đợi:

```text
origin  git@github.com:ninhpoh/REPOSITORY_NAME.git (fetch)
origin  git@github.com:ninhpoh/REPOSITORY_NAME.git (push)
```

Remote sử dụng giao thức **SSH**, không sử dụng HTTPS.

## 7. Đẩy dự án lên GitHub

Đổi tên branch chính thành `main`:

```bash
git branch -M main
```

Đẩy mã nguồn lên GitHub:

```bash
git push -u origin main
```

Sau khi push thành công, mã nguồn và lịch sử commit đã được lưu trữ trên GitHub.

## 8. Repository GitHub

**Tài khoản GitHub:** `ninhpoh`

**URL Repository:**

```text
https://github.com/ninhpoh/REPOSITORY_NAME
```

**SSH Remote URL:**

```text
git@github.com:ninhpoh/REPOSITORY_NAME.git
```

> Thay `REPOSITORY_NAME` bằng tên repository GitHub thực tế.

## 9. Kết quả kiểm tra

### Kiểm tra SSH

```bash
ssh -T git@github.com
```

Kết quả:

```text
Hi ninhpoh! You've successfully authenticated, but GitHub does not provide shell access.
```

### Kiểm tra Remote

```bash
git remote -v
```

Remote có dạng:

```text
git@github.com:ninhpoh/REPOSITORY_NAME.git
```

### Kết luận

Đã hoàn thành cấu hình xác thực SSH bằng thuật toán **Ed25519**, liên kết repository cục bộ với GitHub bằng giao thức **SSH** và đẩy dự án lên repository GitHub thành công.

## 10. Lưu ý bảo mật

Không đưa Private Key lên GitHub:

```text
~/.ssh/id_ed25519
```

Chỉ Public Key được sử dụng để cấu hình xác thực:

```text
~/.ssh/id_ed25519.pub
```
