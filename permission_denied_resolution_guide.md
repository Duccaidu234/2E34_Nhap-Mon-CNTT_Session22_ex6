# 🛠️ Hướng Dẫn Giải Quyết Lỗi Quyền Truy Cập Git (`.git/FETCH_HEAD`)

Tài liệu này tổng hợp kỹ năng viết Prompt AI để chẩn đoán lỗi và mẫu Bug Report chuẩn để gửi Giảng viên/Mentor khi gặp sự cố quyền truy cập hệ thống.

---

## 1. Prompt AI Chẩn Đoán Lỗi (Công thức 3 Thành phần)

Sử dụng cấu trúc 3 phần (**Context + Data + Constraint**) để yêu cầu AI giải thích lỗi bằng ngôn ngữ bình dân, dễ hiểu.

### 📝 Prompt Mẫu:

> **[Context - Ngữ cảnh & Hành động]**  
> Tôi đang dùng Windows 11 và chạy lệnh `git fetch` (hoặc `git pull`) trong VS Code Terminal để đẩy code lên GitHub cho kịp deadline.  
>  
> **[Data - Log lỗi nguyên văn]**  
> `error: open(".git/FETCH_HEAD"): Permission denied`  
>  
> **[Constraint - Yêu cầu & Phong cách giải thích]**  
> Hãy giải thích nguyên nhân gây ra lỗi này theo cách bình dân, dễ hiểu nhất (dùng hình ảnh so sánh thực tế, không dùng thuật ngữ chuyên ngành phức tạp). Sau đó hướng dẫn ngắn gọn các bước khắc phục nhanh nhất.

---

### 💡 Ví dụ Phản hồi Giải thích Bình dân từ AI:

> *"Lỗi này giống như việc tệp file `FETCH_HEAD` trong thư mục ẩn `.git` của bạn đang bị **khóa lại bằng một ổ khóa khác**. Bạn giống như người giữ chìa khóa thường, nhưng file này hiện chỉ mở được bằng **chìa khóa Vạn năng (Quyền Administrator)** hoặc đang bị một chương trình khác (như Antivirus hoặc một tiến trình VS Code ngầm) nắm giữ và không chịu nhả ra."*

---

## 2. Quy Trình Chụp Ảnh Màn Hình Minh Họa Chuyên Nghiệp

Khi thực hiện thao tác **Run as Administrator** theo hướng dẫn của AI, ảnh chụp màn hình gửi kèm báo cáo cần tuân thủ 4 quy tắc vàng:

1. **Ngữ cảnh đầy đủ (Full Context Window):** Chụp rõ thanh tiêu đề (Title bar) hiển thị dòng chữ `Administrator: PowerShell` hoặc `Administrator: VS Code` để chứng minh đã chạy quyền Admin.
2. **Khoanh vùng trọng tâm (Visual Focus):** Dùng khung chữ nhật màu đỏ/cam khoanh tròn lệnh vừa thực hiện và dòng thông báo lỗi `Permission denied`.
3. **Bảo mật thông tin (Privacy Masking):** Che mờ (Blur) hoặc dùng hộp màu đen đè lên các thông tin nhạy cảm:
   * Đường dẫn thư mục cá nhân chứa `Username` (Ví dụ: `C:\Users\TenThatOfBan\...`).
   * Mã Token, SSH Key, hoặc thông tin cấu hình bí mật trong file `.env`.
4. **Độ nét cao:** Export ảnh dạng PNG chất lượng cao, không chụp lại bằng điện thoại.

---

## 3. Mẫu Bug Report Gửi Giảng Viên / Mentor

Nếu đã chạy quyền Administrator và thử các cách cơ bản nhưng vẫn bị chặn, dán mẫu tin nhắn này để gửi nhờ hỗ trợ:

```markdown
Kính gửi Thầy/Cô [Tên Giảng viên],

Em gặp sự cố về quyền truy cập tệp tin `.git` không thể tự khắc phục để push code kịp deadline. Em xin gửi báo cáo chi tiết nhờ Thầy/Cô hỗ trợ:

--- 🐛 BUG REPORT: PERMISSION DENIED (.GIT/FETCH_HEAD) ---

1. Ngữ cảnh (Context):
- Hệ điều hành: Windows 11 Pro (23H2)
- Công cụ: VS Code Terminal / Git Bash v2.43
- Lệnh thực hiện: git pull origin main (hoặc git fetch)

2. Kết quả Kỳ vọng (Expected):
- Git tải thành công metadata từ remote repository và cập nhật tệp `.git/FETCH_HEAD` bình thường.

3. Kết quả Thực tế (Actual):
- Terminal chặn thao tác và trả về lỗi không có quyền ghi:
  error: open(".git/FETCH_HEAD"): Permission denied
  fatal: could not open '.git/FETCH_HEAD' for writing

4. Nhật ký & Các bước đã tự xử lý (Logs & Troubleshooting):
- Step 1 (Googling): Đã tra cứu lỗi permission denied với file FETCH_HEAD.
- Step 2 (Community): Đã kiểm tra thuộc tính file (không bật Read-only) và kiểm tra tiến trình git.exe ngầm.
- Step 3 (AI Diagnosis): Đã thử mở VS Code bằng quyền "Run as Administrator" và cấp lại quyền sở hữu (Take Ownership) nhưng vẫn bị từ chối.

📸 Đính kèm: [Ảnh chụp màn hình đã khoanh vùng lỗi và che mờ thông tin cá nhân]

Em cảm ơn Thầy/Cô ạ!
```