# Real Estate IT Management System

Website quản trị hệ thống CNTT cho công ty bất động sản, gồm frontend React/Vite, backend Node.js/Express và SQL Server schema/seed.

## Tài khoản demo

| Username | Password | Vai trò |
| --- | --- | --- |
| admin | 123456 | Admin IT |
| manager | 123456 | Manager |
| broker | 123456 | Môi giới |
| marketing | 123456 | Marketing |
| accountant | 123456 | Kế toán |
| legal | 123456 | Pháp lý |

## Chạy local

Backend:

```bash
cd backend
cp .env.example .env
npm install
npm run dev
```

Frontend:

```bash
cd frontend
cp .env.example .env
npm install
npm run dev
```

Mở `http://localhost:5173`.

## Thứ tự triển khai đầy đủ

1. Tạo database trên Windows Server 2025.
2. Import `backend/database/schema.sql`.
3. Import `backend/database/seed.sql`.
4. Cấu hình backend `.env`.
5. Chạy backend bằng Node.js hoặc PM2.
6. Build frontend bằng `npm run build`.
7. Cấu hình Nginx với `deployment/nginx-real-estate.conf`.
8. Kiểm tra truy cập từ Windows Client.
9. Đăng nhập bằng `admin / 123456`.
10. Kiểm tra dashboard và các module.

## Tài liệu

- `deployment/DEPLOYMENT.md`: hướng dẫn deploy Ubuntu App Server `192.168.1.151`.
- `deployment/SQL_SETUP.md`: hướng dẫn SQL Server `192.168.1.101`.
- `deployment/TESTING.md`: checklist test backend, frontend, database.
- `deployment/REPORT_NOTES.md`: nội dung đưa vào báo cáo.
