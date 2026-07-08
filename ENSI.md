# HỆ THỐNG MẠNG VÀ MÁY CHỦ DOANH NGHIỆP BẤT ĐỘNG SẢN

## Giới thiệu

Đây là bài tập lớn môn **Cài đặt và cấu hình máy chủ, mạng và triển khai ứng dụng**.

Đề tài tập trung vào việc xây dựng và triển khai hạ tầng công nghệ thông tin cho doanh nghiệp kinh doanh bất động sản trên môi trường ảo hóa VMware Workstation. Hệ thống được thiết kế theo mô hình doanh nghiệp thực tế với các dịch vụ quản trị tập trung, bảo mật mạng, quản lý dữ liệu và truy cập từ xa.

---

# Mục tiêu

- Xây dựng mô hình mạng doanh nghiệp hoàn chỉnh.
- Triển khai hệ thống máy chủ trên môi trường ảo hóa.
- Quản lý người dùng tập trung bằng Active Directory.
- Cấu hình DNS và DHCP Server.
- Xây dựng Website quản lý bất động sản.
- Triển khai cơ sở dữ liệu MariaDB.
- Thực hiện sao lưu dữ liệu bằng MariaDB Replication.
- Cung cấp truy cập từ xa thông qua OpenVPN.
- Kiểm tra và đánh giá hệ thống bằng Kali Linux.

---

# Mô hình hệ thống

## Môi trường triển khai

- VMware Workstation
- pfSense CE
- Windows Server 2025
- Windows 11
- Ubuntu Server
- Kali Linux

---

# Danh sách máy chủ

| STT | Máy chủ | Hệ điều hành | Địa chỉ IP | Chức năng |
|------|---------|-------------|------------|------------|
| 1 | pfSense | pfSense CE | 192.168.10.1 | Firewall, Router, VPN |
| 2 | Windows Server | Windows Server 2025 | 192.168.10.10 | AD DS, DNS, DHCP, Website |
| 3 | Ubuntu Master | Ubuntu Server | 192.168.10.5 | MariaDB Master |
| 4 | Ubuntu Slave | Ubuntu Server | 192.168.10.6 | MariaDB Slave |
| 5 | Windows 11 Client | Windows 11 | DHCP | Máy trạm |
| 6 | Kali Linux | Kali Linux | DHCP | Kiểm thử bảo mật |

---

# Thông tin Domain

| Thành phần | Giá trị |
|------------|---------|
| Domain | batdongsan.local |
| DNS Server | 192.168.10.10 |
| Gateway | 192.168.10.1 |
| VPN Network | 10.8.0.0/24 |

---

# Các dịch vụ triển khai

## 1. pfSense Firewall

### Chức năng

- Firewall
- Router
- NAT
- ACL
- OpenVPN Server
- Gateway hệ thống

### Địa chỉ

```text
192.168.10.1
```

### Các chức năng đã cấu hình

- LAN Interface
- WAN Interface
- Firewall Rules
- OpenVPN Server
- NAT Rules

---

## 2. Active Directory Domain Services

### Máy chủ

```text
192.168.10.10
```

### Domain

```text
batdongsan.local
```

### Chức năng

- Quản lý người dùng
- Quản lý máy tính
- Xác thực tập trung
- Hỗ trợ Group Policy

---

## 3. DNS Server

### Máy chủ

```text
192.168.10.10
```

### Chức năng

- Phân giải tên miền nội bộ
- Hỗ trợ Active Directory
- Quản lý Forward Lookup Zone

Ví dụ:

```text
batdongsan.local
```

---

## 4. DHCP Server

### Máy chủ

```text
192.168.10.10
```

### Chức năng

- Cấp phát địa chỉ IP tự động
- Quản lý dải IP tập trung
- Cấp Gateway và DNS tự động

---

## 5. Website Quản lý Bất động sản

### Máy chủ

```text
192.168.10.10
```

### Công nghệ sử dụng

Frontend:

- ReactJS
- HTML
- CSS
- JavaScript

Backend:

- NodeJS
- ExpressJS

### Chức năng

- Đăng nhập hệ thống
- Quản lý bất động sản
- Quản lý khách hàng
- Quản lý giao dịch
- Quản lý người dùng

---

## 6. MariaDB Master

### Máy chủ

```text
192.168.10.5
```

### Database

```sql
bds_abc
```

### Chức năng

- Lưu trữ dữ liệu hệ thống
- Ghi nhận thay đổi dữ liệu
- Cung cấp Binary Log cho Replication

### Kiểm tra

```sql
SHOW DATABASES;
SHOW MASTER STATUS;
```

---

## 7. MariaDB Slave

### Máy chủ

```text
192.168.10.6
```

### Chức năng

- Đồng bộ dữ liệu từ Master
- Dự phòng cơ sở dữ liệu
- Tăng tính sẵn sàng của hệ thống

### Kiểm tra

```sql
SHOW SLAVE STATUS\G
```

hoặc

```sql
SHOW REPLICA STATUS\G
```

---

## 8. OpenVPN

### Máy chủ

```text
192.168.10.1
```

### Thông số

```text
Protocol : UDP
Port     : 1194
Network  : 10.8.0.0/24
```

### Chức năng

- Truy cập từ xa
- Kết nối an toàn qua Internet
- Hỗ trợ quản trị hệ thống từ bên ngoài

---

## 9. Kali Linux

### Chức năng

- Kiểm tra kết nối mạng
- Kiểm tra DNS
- Quét dịch vụ
- Đánh giá bảo mật hệ thống

Ví dụ:

```bash
ping 192.168.10.10

nslookup batdongsan.local

nmap -sV 192.168.10.10
```

---

# Kiểm tra hệ thống

## Kiểm tra Domain

Windows 11 đã tham gia Domain:

```text
batdongsan.local
```

---

## Kiểm tra DNS

```bash
nslookup batdongsan.local
```

---

## Kiểm tra DHCP

```cmd
ipconfig /all
```

---

## Kiểm tra Database

Master:

```sql
SHOW MASTER STATUS;
```

Slave:

```sql
SHOW SLAVE STATUS\G
```

---

## Kiểm tra Website

Truy cập Website từ máy Client.

---

## Kiểm tra VPN

Kết nối thành công từ OpenVPN Client.

---