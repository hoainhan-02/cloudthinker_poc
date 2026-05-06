# 🩺 Health Check API với Node.js

Tài liệu này hướng dẫn bạn tạo một API **health check** đơn giản باستخدام Node.js. API này thường dùng để kiểm tra xem server có đang hoạt động bình thường hay không.

---

## 📦 Yêu cầu

* Node.js >= 14
* npm hoặc yarn

---

## 🚀 Khởi tạo project

```bash
mkdir health-check-api
cd health-check-api
npm init -y
```

Cài đặt thư viện cần thiết:

```bash
npm install express
```

---

## 📁 Cấu trúc project

```
health-check-api/
│── index.js
│── package.json
└── README.md
```

---

## 🧑‍💻 Viết code API

Tạo file `index.js`:

```js
const express = require('express');

const app = express();
const PORT = process.env.PORT || 3000;

// Health check endpoint
app.get('/health', (req, res) => {
  res.status(200).json({
    status: 'OK',
    uptime: process.uptime(),
    timestamp: Date.now()
  });
});

app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```

---

## ▶️ Chạy ứng dụng

```bash
node index.js
```

---

## 🔍 Kiểm tra API

Mở trình duyệt hoặc dùng curl:

```bash
curl http://localhost:3000/health
```

Kết quả trả về:

```json
{
  "status": "OK",
  "uptime": 12.345,
  "timestamp": 1710000000000
}
```

---

## ⚙️ Mở rộng (tuỳ chọn)

Bạn có thể cải thiện health check bằng cách:

* Kiểm tra kết nối database
* Kiểm tra Redis / cache
* Thêm trạng thái chi tiết:

```js
{
  status: "OK",
  database: "connected",
  memoryUsage: process.memoryUsage()
}
```

---

## 📌 Ghi chú

* Endpoint `/health` thường được dùng bởi:

  * Load balancer
  * Kubernetes (liveness/readiness probe)
  * Monitoring tools

---

## 🧾 License

MIT
