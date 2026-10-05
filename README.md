# Báo cáo Bài 4: Quản lý tệp tin bỏ qua (.gitignore) và Sửa lịch sử (Amend)

## 1. Gỡ bỏ file khỏi cache của Git
Để gỡ bỏ file `credentials.txt` đã bị đưa nhầm vào Git mà không làm mất file vật lý trên máy tính, tôi đã sử dụng lệnh:
```bash
git rm --cached credentials.txt
```
Lệnh này xóa file khỏi vùng theo dõi (staging/tracking) của Git nhưng vẫn giữ nguyên file trên đĩa cứng cục bộ.

## 2. Cấu hình file .gitignore
Sau khi gỡ bỏ, tôi tạo file `.gitignore` và thêm tên file vào để Git tự động bỏ qua trong tương lai:
```text
credentials.txt
```
Sau đó tôi đã add file `.gitignore` vào staging:
```bash
git add .gitignore
```

## 3. Sửa thông điệp commit (Amend)
Để ghi đè lên commit lỗi trước đó (xóa `credentials.txt` khỏi lịch sử commit đó và thay bằng `.gitignore`, đồng thời đổi luôn câu message), tôi dùng cờ `--amend`:
```bash
git commit --amend -m "Initial commit: Add gitignore, exclude sensitive data"
```

## 4. Kiểm tra kết quả
Kết quả lệnh `git log -n 1` hiển thị thông điệp đã được sửa đổi thành công:
```text
commit 78a72c72979806dbef1e9b760ab15a8f3cf6fcbc
Author: Duy Ho <duyho@example.com>
Date:   Mon Oct 5 18:42:46 2026 +0700

    Initial commit: Add gitignore, exclude sensitive data
```
Và kết quả `git status` lúc này sẽ báo thư mục làm việc sạch sẽ, bỏ qua hoàn toàn file `credentials.txt`.
