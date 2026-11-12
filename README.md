# ⚽ FCO - Dây Mồi Calculator

> **Công cụ tính toán & ước tính tỷ lệ nâng cấp / dây mồi cầu thủ FC Online (FO4)**  
> Ứng dụng web Progressive Web App (PWA) hiện đại, hỗ trợ PC & Mobile, tự động học dữ liệu thực tế và hoạt động 100% offline.

---

## 🌟 Tính Năng Nổi Bật

1. **Phân Tích Dây Mồi Thời Gian Thực**
   - Chọn cấp thẻ mục tiêu (+2 đến +10).
   - Nhập chuỗi phôi mồi (qua bàn phím thường hoặc bàn phím số cảm ứng tích hợp).
   - Phân tích chi tiết:
     - **Tỷ lệ gốc (Base Rate)** của từng mốc nâng cấp.
     - **Điều chỉnh động**: tác động tăng tỷ lệ (phôi 2, 3), giảm tỷ lệ (phôi 5+), giữ nguyên (phôi 4) và mồi 1 (reset tích luỹ).
     - **Đuôi mẫu (Tail Pattern Match)**: Nhận diện các chuỗi dây mồi đẹp kinh điển được cộng đồng đúc kết.
     - **Hệ số giảm chấn (Dampen factor)** tránh ảo tưởng tỷ lệ khi chuỗi mồi quá dài.

2. **Đồng Hồ Đo Tỷ Lệ Động (Gauge Half-Donut 240°)**
   - Vòng cung đổi màu theo tỷ lệ: Đỏ (thấp), Vàng (vừa), Xanh (cao/chín).
   - Hiệu ứng âm thanh rung lắc (haptic vibration) và âm thanh bump/shake bằng Web Audio API không cần nạp file ngoài.

3. **Tự Học & Tối Ưu Hệ Số Từ Dữ Liệu Thực Tế (Self-Calibration)**
   - Sau khi đập thẻ thực tế trong game, đánh dấu kết quả **Thành công (✅)** hoặc **Thất bại (❌)** trong tab Lịch sử.
   - Hệ thống tự động tính toán lại các hệ số `STEP_UP`, `PENALTY_5`, `CAP_BONUS`, `TAIL_SCALE` để ngày càng khớp với vận may và thuật toán thực tế của bạn.
   - Thuật toán quét và phát hiện các mẫu dây mồi đẹp mới dựa trên dữ liệu lịch sử.

4. **Biểu Đồ & Thống Kê Chuyên Sâu**
   - Khoảng tin cậy 95% (Wilson Score) theo từng cấp thẻ.
   - Biểu đồ đường xu hướng so sánh tỷ lệ dự đoán vs tỷ lệ thực tế.
   - Thống kê tỷ lệ thành công của từng loại phôi mồi.

5. **Trải Nghiệm Đỉnh Cao & Đa Nền Tảng (PWA)**
   - **Chế độ PC & Mobile**: Chuyển đổi linh hoạt giữa giao diện Sidebar (máy tính) và Bottom Navigation (điện thoại).
   - **Giao diện**: Hỗ trợ Dark Mode huyền bí và Light Mode trang nhã.
   - **Cài đặt như Native App**: Đã cấu hình đầy đủ `manifest.json`, icon chất lượng cao và `service-worker.js`.
   - **Bảo mật & Riêng tư**: Dữ liệu lưu an toàn trên trình duyệt (`localStorage`), hỗ trợ đăng nhập Google OAuth hoặc chế độ Khách (Guest).

---

## 🚀 Hướng Dẫn Sử Dụng & Triển Khai

### 1. Chạy Trực Tiếp Trên Máy Tính
- **Cách đơn giản nhất**: Nhấp đúp chuột vào file `index.html` để mở ngay trên trình duyệt (Chrome, Edge, Brave, Cốc Cốc, Safari...).
- **Khởi động server cục bộ (để trải nghiệm đầy đủ PWA & Service Worker)**:
  ```bash
  # Mở PowerShell hoặc Terminal tại thư mục này
  python -m http.server 3000
  ```
  Sau đó mở trình duyệt truy cập: `http://localhost:3000`

---

### 2. Triển Khai Miễn Phí Lên Vercel (Giống hệt fcoaibot.vercel.app)

#### Cách 1: Dùng Vercel CLI (Nhanh nhất)
1. Cài đặt Vercel CLI (nếu chưa có):
   ```bash
   npm i -g vercel
   ```
2. Mở terminal tại thư mục `e:\aibot` và chạy:
   ```bash
   vercel
   ```
3. Đăng nhập và làm theo các bước hỏi mặc định (bấm Enter liên tục). Sau 30 giây bạn sẽ có ngay link `https://<ten-app-cua-ban>.vercel.app`.

#### Cách 2: Triển khai qua GitHub
1. Tạo một repository mới trên GitHub (ví dụ: `fco-daymoi-calculator`).
2. Đẩy toàn bộ mã nguồn trong thư mục này lên GitHub:
   ```bash
   git init
   git add .
   git commit -m "Initial commit FCO Dây Mồi Calculator"
   git branch -M main
   git remote add origin https://github.com/<tai-khoan-cua-ban>/fco-daymoi-calculator.git
   git push -u origin main
   ```
3. Truy cập [vercel.com](https://vercel.com), bấm **Add New Project** -> Chọn repository vừa tạo -> Bấm **Deploy**.

---

### 3. Cấu Hình Đăng Nhập Google (Tùy Chọn)
Nếu muốn kích hoạt tính năng đăng nhập Google bằng tài khoản cá nhân:
1. Truy cập [Google Cloud Console Credentials](https://console.cloud.google.com/apis/credentials).
2. Tạo **OAuth 2.0 Client ID** (loại Web Application).
3. Thêm domain của bạn vào **Authorized JavaScript origins** (ví dụ: `https://ten-mien-cua-ban.vercel.app` hoặc `http://localhost:3000`).
4. Mở file `index.html`, tìm biến `GOOGLE_CLIENT_ID` và dán Client ID của bạn vào:
   ```javascript
   const GOOGLE_CLIENT_ID = 'YOUR_CLIENT_ID.apps.googleusercontent.com';
   ```
*(Nếu không cấu hình, bạn vẫn có thể dùng hoàn toàn bình thường ở chế độ Khách / Guest mode).*

---

## 📁 Cấu Trúc Dự Án
```text
e:/aibot/
├── index.html          # Ứng dụng chính (HTML5 + CSS3 + Vanilla JS tự hoàn thiện)
├── manifest.json       # Cấu hình PWA để cài đặt lên Mobile / Desktop
├── service-worker.js   # Bộ nhớ đệm cache offline
├── favicon.ico         # Icon hiển thị trên tab trình duyệt
├── icon-192.png        # Icon ứng dụng kích thước 192x192
├── icon-512.png        # Icon ứng dụng kích thước 512x512
├── vercel.json         # Cấu hình cache và routing cho Vercel
└── README.md           # Tài liệu hướng dẫn sử dụng
```

---

## 💬 Hỗ Trợ & Liên Hệ
- **Zalo**: [https://zalo.me/0365060304](https://zalo.me/0365060304) (SĐT: `0365060304`)

