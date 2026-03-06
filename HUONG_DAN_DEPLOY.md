# 🚀 Hướng dẫn Deploy Wave Signal Bot lên Railway

## 📁 Các file cần thiết
```
wave_signal_bot.py   ← bot (đã sửa đọc env vars)
requirements.txt     ← thư viện Python
Procfile             ← lệnh chạy
railway.json         ← cấu hình Railway
```

---

## BƯỚC 1 — Tạo GitHub Repository

1. Vào https://github.com → **New repository**
2. Đặt tên: `wave-signal-bot` → **Create repository**
3. Upload 4 file trên vào repo (kéo thả hoặc dùng GitHub Desktop)

---

## BƯỚC 2 — Tạo tài khoản Railway

1. Vào https://railway.com
2. Nhấn **Login** → chọn **Login with GitHub**
3. Xác nhận quyền truy cập

---

## BƯỚC 3 — Tạo Project mới trên Railway

1. Nhấn **New Project**
2. Chọn **Deploy from GitHub repo**
3. Chọn repo `wave-signal-bot` vừa tạo
4. Railway sẽ tự detect và bắt đầu build

---

## BƯỚC 4 — Cài đặt Biến Môi Trường (BẮT BUỘC)

1. Vào project → tab **Variables**
2. Nhấn **New Variable** → thêm 2 biến:

| Name | Value |
|------|-------|
| `TELEGRAM_TOKEN` | `7xxxxxxxxx:AAF...` (token bot của bạn) |
| `CHAT_ID` | `-100xxxxxxxxxx` hoặc `@channel_name` |

> ⚠️ **Lấy TELEGRAM_TOKEN:** Chat với @BotFather trên Telegram → /newbot
> ⚠️ **Lấy CHAT_ID:** Thêm @userinfobot vào nhóm/channel → nó sẽ báo ID

---

## BƯỚC 5 — Deploy

1. Sau khi thêm variables → Railway tự **Redeploy**
2. Vào tab **Deployments** → xem log build
3. Nếu thấy `🌊 Wave Signal Bot started — quét mỗi 4 giờ` → **THÀNH CÔNG!**

---

## 🔍 Kiểm tra hoạt động

- Tab **Deployments** → click vào deploy mới nhất → xem **Live Logs**
- Bot sẽ gửi tin nhắn Telegram ngay lần đầu khởi động
- Sau đó chạy tự động mỗi 4 giờ: 0h, 4h, 8h, 12h, 16h, 20h UTC

---

## 💰 Chi phí Railway

- **Free tier:** $5 credit miễn phí mỗi tháng
- Bot nhẹ (~$1-2/tháng) → dùng free tier thoải mái
- Không cần nhập thẻ tín dụng cho plan miễn phí

---

## ❗ Lỗi thường gặp

| Lỗi | Cách xử lý |
|-----|-----------|
| `Unauthorized` | Kiểm tra lại TELEGRAM_TOKEN |
| `Chat not found` | Bot chưa được thêm vào group/channel, hoặc CHAT_ID sai |
| `ModuleNotFoundError` | Railway chưa cài xong, chờ build hoàn tất |
| Bot không gửi tin | Kiểm tra bot có quyền post trong channel không |
