# PHÂN CÔNG CÔNG VIỆC VÀ THỜI GIAN THỰC HIỆN

## Đề tài: Tìm hiểu về thiết kế và đánh giá hiệu năng của QUIC

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò | Trách nhiệm chính |
|-----|-----------|------|---------|-------------------|
| 1 | Thành viên 1 | [MSSV] | Trưởng nhóm | Kiến trúc QUIC, Connection, Handshake |
| 2 | Thành viên 2 | [MSSV] | Thành viên | Thử nghiệm hiệu năng, Phân tích dữ liệu |

---

## 🎯 Mục tiêu đề tài

1. **Nghiên cứu kiến trúc QUIC** - Hiểu rõ thiết kế và các thành phần của giao thức
2. **Đánh giá hiệu năng QUIC** - Thử nghiệm trong các điều kiện mạng khác nhau
3. **So sánh với HTTP/2** - Phân tích ưu nhược điểm của QUIC so với HTTP/2
4. **Đưa ra khuyến nghị** - Kết luận về việc áp dụng QUIC trong thực tế

---

## 📅 Kế hoạch thời gian tổng quan

| Giai đoạn | Nội dung | Thời gian | Số tuần | Giờ/tuần/người |
|-----------|----------|-----------|---------|----------------|
| 1 | Nghiên cứu lý thuyết về QUIC | Tuần 1-2 | 2 tuần | 15 giờ |
| 2 | Triển khai và thử nghiệm | Tuần 3-4 | 2 tuần | 20 giờ |
| 3 | Phân tích kết quả và so sánh | Tuần 5-6 | 2 tuần | 15 giờ |
| 4 | Viết báo cáo và hoàn thiện | Tuần 7 | 1 tuần | 20 giờ |
| **TỔNG** | | **7 tuần** | | **~120 giờ/người** |

---

## 📝 CHI TIẾT PHÂN CÔNG CÔNG VIỆC THEO TUẦN

---

## 🗓️ TUẦN 1: TỔNG QUAN VỀ QUIC (15 giờ/người)

### Thành viên 1 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 1.1 | Tìm hiểu lịch sử phát triển QUIC | - Đọc tài liệu về gQUIC (Google QUIC 2012-2015)<br>- Nghiên cứu quá trình chuẩn hóa IETF (2016-2021)<br>- Tìm hiểu sự khác biệt gQUIC vs IETF QUIC | 4 | Tài liệu 2-3 trang |
| 1.2 | Nghiên cứu kiến trúc tổng quan | - Vẽ sơ đồ các lớp protocol (QUIC, TLS, UDP, IP)<br>- Mô tả Connection, Stream, Frame, Packet<br>- So sánh với TCP/IP stack | 5 | Sơ đồ kiến trúc + mô tả |
| 1.3 | Đọc RFC 9000 (Sections 1-5) | - Giới thiệu và tổng quan<br>- Stream States<br>- Frame Types | 4 | Ghi chú tóm tắt |
| 1.4 | Tổng hợp tài liệu tham khảo | - Thu thập RFC 9000, 9001, 9002<br>- Tìm papers liên quan (Google Scholar) | 2 | Danh sách 10-15 tài liệu |

### Thành viên 2 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 1.1 | Nghiên cứu TCP và vấn đề của nó | - Phân tích TCP handshake (3-way)<br>- Vấn đề Head-of-Line blocking<br>- Hạn chế với TLS riêng biệt | 4 | Tài liệu 2-3 trang |
| 1.2 | So sánh QUIC với TCP/UDP | - Tại sao QUIC chạy trên UDP<br>- Bảng so sánh chi tiết các đặc điểm<br>- Ưu điểm QUIC so với TCP | 5 | Bảng so sánh chi tiết |
| 1.3 | Đọc RFC 9000 (Sections 6-10) | - Connections<br>- Version Negotiation<br>- Cryptographic Handshake | 4 | Ghi chú tóm tắt |
| 1.4 | Tìm hiểu HTTP/3 | - Quan hệ QUIC và HTTP/3<br>- Sự khác biệt với HTTP/2 | 2 | Tài liệu tóm tắt |

### 📋 Deliverables cuối Tuần 1:
> **Ghi chú:** TV1 = Thành viên 1, TV2 = Thành viên 2

- [ ] Tài liệu lịch sử QUIC (TV1)
- [ ] Sơ đồ kiến trúc QUIC (TV1)
- [ ] Bảng so sánh QUIC vs TCP/UDP (TV2)
- [ ] Danh sách tài liệu tham khảo (Cả 2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 1

#### Task 1.1 (TV1): Tìm hiểu lịch sử phát triển QUIC

**Bước 1: Tìm nguồn tài liệu (30 phút)**
- Truy cập https://www.chromium.org/quic/ để đọc tài liệu gốc của Google
- Tìm blog posts từ Google về gQUIC (2013-2015)
- Tìm IETF mailing list archives về QUIC standardization

**Bước 2: Đọc và ghi chép về gQUIC (1 giờ)**
- Đọc paper "The QUIC Transport Protocol: Design and Internet-Scale Deployment" (Google, 2017)
- Ghi chú các đặc điểm của gQUIC:
  - Năm bắt đầu phát triển (2012)
  - Mục tiêu ban đầu (giảm latency cho Google services)
  - Các phiên bản gQUIC (Q043, Q046, etc.)

**Bước 3: Nghiên cứu quá trình chuẩn hóa IETF (1.5 giờ)**
- Đọc timeline từ IETF QUIC Working Group
- Ghi chú các milestones:
  - 2016: IETF bắt đầu làm việc với QUIC
  - 2018: Draft versions
  - 2021: RFC 9000 được publish

**Bước 4: So sánh gQUIC vs IETF QUIC (1 giờ)**
- Lập bảng so sánh:
  - Crypto handshake: gQUIC (custom) vs IETF (TLS 1.3)
  - Header format: khác nhau
  - Version negotiation: khác nhau
  - Packet number encoding

**Bước 5: Viết tài liệu tổng hợp (30 phút)**
- Viết 2-3 trang tổng hợp
- Thêm timeline diagram
- Cite nguồn tài liệu

#### Task 1.2 (TV1): Nghiên cứu kiến trúc tổng quan

**Bước 1: Đọc RFC 9000 Section 2 - Overview (1 giờ)**
- Hiểu khái niệm Connection
- Hiểu khái niệm Stream
- Hiểu khái niệm Packet và Frame

**Bước 2: Vẽ sơ đồ Protocol Stack (1 giờ)**
- Sử dụng draw.io hoặc Lucidchart
- Vẽ các layers:
  ```
  +------------------+
  |    HTTP/3        |
  +------------------+
  |    QUIC          |
  +------------------+
  |    TLS 1.3       | (integrated)
  +------------------+
  |    UDP           |
  +------------------+
  |    IP            |
  +------------------+
  ```
- So sánh với TCP/IP stack

**Bước 3: Mô tả các thành phần (2 giờ)**
- **Connection**: Connection ID, state machine
- **Stream**: Stream ID, bidirectional/unidirectional, states
- **Frame**: STREAM, ACK, CRYPTO, PADDING, etc.
- **Packet**: Long header vs Short header

**Bước 4: Viết mô tả chi tiết (1 giờ)**
- Giải thích từng component
- Thêm ví dụ cụ thể
- Export sơ đồ dạng PNG/SVG

#### Task 1.1 (TV2): Nghiên cứu TCP và vấn đề

**Bước 1: Review TCP handshake (1 giờ)**
- Vẽ sequence diagram của 3-way handshake
- Tính toán: Client → SYN → Server → SYN-ACK → Client → ACK
- = 1.5 RTT trước khi gửi data

**Bước 2: Thêm TLS handshake (1 giờ)**
- TLS 1.2: thêm 2 RTT
- TLS 1.3: thêm 1 RTT
- Tổng: TCP + TLS 1.3 = 2-3 RTT

**Bước 3: Phân tích Head-of-Line blocking (1 giờ)**
- Giải thích vấn đề HOL blocking trong TCP
- Vẽ diagram: khi packet 1 bị mất, packets 2,3,4 phải chờ
- Impact đến HTTP/2 multiplexing

**Bước 4: Viết tài liệu (1 giờ)**
- Tổng hợp các vấn đề của TCP
- Giải thích tại sao cần protocol mới
- Thêm diagrams vào tài liệu

#### Task 1.2 (TV2): So sánh QUIC với TCP/UDP

**Bước 1: Lập bảng so sánh features (1.5 giờ)**
```
| Feature           | TCP      | UDP      | QUIC     |
|-------------------|----------|----------|----------|
| Connection-oriented| Yes      | No       | Yes      |
| Reliable          | Yes      | No       | Yes      |
| Ordered           | Yes      | No       | Per-stream|
| Multiplexing      | No       | No       | Yes      |
| Encryption        | Optional | No       | Built-in |
| Handshake RTT     | 1-3      | 0        | 1 (0-RTT)|
```

**Bước 2: Giải thích tại sao QUIC chạy trên UDP (1.5 giờ)**
- UDP không có HOL blocking
- UDP có thể deploy dễ hơn (user-space)
- Middleboxes không can thiệp

**Bước 3: Phân tích ưu điểm QUIC (1.5 giờ)**
- Faster connection establishment
- No HOL blocking
- Connection migration
- Built-in encryption

**Bước 4: Viết tài liệu (0.5 giờ)**
- Format bảng so sánh đẹp
- Thêm giải thích cho từng row

---

## 🗓️ TUẦN 2: CHI TIẾT THIẾT KẾ QUIC (15 giờ/người)

### Thành viên 1 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 2.1 | Nghiên cứu Connection Establishment | - Phân tích 1-RTT handshake chi tiết<br>- Vẽ sequence diagram<br>- So sánh với TCP+TLS (3-RTT) | 5 | Sơ đồ + tài liệu |
| 2.2 | Nghiên cứu 0-RTT Resumption | - Cơ chế hoạt động 0-RTT<br>- Session ticket và PSK<br>- Rủi ro replay attack | 4 | Tài liệu kỹ thuật |
| 2.3 | Nghiên cứu Stream Multiplexing | - Cách QUIC xử lý nhiều streams<br>- Không có HOL blocking giữa streams<br>- Stream ID và prioritization | 4 | Tài liệu + sơ đồ |
| 2.4 | Nghiên cứu Connection Migration | - Khả năng đổi IP/port mà không mất kết nối<br>- Connection ID và vai trò của nó<br>- Use case: Mobile handoff | 2 | Tài liệu |

### Thành viên 2 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 2.1 | Nghiên cứu TLS 1.3 trong QUIC | - Cách QUIC tích hợp TLS 1.3<br>- Encryption levels (Initial, Handshake, 1-RTT)<br>- Key derivation | 5 | Tài liệu bảo mật |
| 2.2 | Nghiên cứu Packet Protection | - Header protection<br>- Payload encryption<br>- AEAD algorithm | 3 | Tài liệu |
| 2.3 | Nghiên cứu Loss Detection (RFC 9002) | - Packet number encoding<br>- ACK mechanism<br>- Loss detection algorithm | 4 | Tài liệu kỹ thuật |
| 2.4 | Nghiên cứu Congestion Control | - QUIC congestion control<br>- So sánh với TCP (NewReno, CUBIC)<br>- Pacing | 3 | Tài liệu |

### 📋 Deliverables cuối Tuần 2:
- [ ] Sơ đồ Handshake 1-RTT và 0-RTT (TV1)
- [ ] Tài liệu Stream Multiplexing (TV1)
- [ ] Tài liệu bảo mật QUIC (TV2)
- [ ] Tài liệu Loss Detection & Congestion Control (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 2

#### Task 2.1 (TV1): Nghiên cứu Connection Establishment

**Bước 1: Đọc RFC 9000 Section 7 (1 giờ)**
- Hiểu Initial packets
- Hiểu Handshake packets
- Hiểu 1-RTT packets

**Bước 2: Vẽ 1-RTT Handshake Sequence Diagram (1.5 giờ)**
```
Client                                    Server
  |                                         |
  |--- Initial[CRYPTO: ClientHello] ------->|
  |<-- Initial[CRYPTO: ServerHello] --------|
  |<-- Handshake[CRYPTO: EncryptedExt] -----|
  |<-- Handshake[CRYPTO: Certificate] ------|
  |<-- Handshake[CRYPTO: CertVerify] -------|
  |<-- Handshake[CRYPTO: Finished] ---------|
  |--- Handshake[CRYPTO: Finished] -------->|
  |<========== 1-RTT Data =================>|
```

**Bước 3: So sánh với TCP+TLS (1.5 giờ)**
- TCP: 1.5 RTT (SYN, SYN-ACK, ACK)
- TLS 1.3: 1 RTT (ClientHello, ServerHello+data)
- Tổng TCP+TLS: 2 RTT (có thể 3 RTT với TLS 1.2)
- QUIC: 1 RTT (combined)

**Bước 4: Viết tài liệu (1 giờ)**
- Export diagram
- Giải thích từng bước
- Highlight advantages

#### Task 2.2 (TV1): Nghiên cứu 0-RTT Resumption

**Bước 1: Hiểu cơ chế 0-RTT (1.5 giờ)**
- Đọc RFC 9001 Section 4.6
- Hiểu Early Data
- Hiểu Pre-Shared Key (PSK)

**Bước 2: Vẽ 0-RTT Diagram (1 giờ)**
```
Client                                    Server
  |                                         |
  |--- Initial[CRYPTO: ClientHello] ------->|
  |--- 0-RTT[STREAM: Request Data] -------->|  <- Data sent immediately!
  |<-- Initial[CRYPTO: ServerHello] --------|
  |<-- Handshake[...] ----------------------|
  |<========== 1-RTT Data =================>|
```

**Bước 3: Phân tích Replay Attack risk (1 giờ)**
- 0-RTT data có thể bị replay
- Server phải có cơ chế anti-replay
- Chỉ nên dùng cho idempotent requests

**Bước 4: Viết tài liệu (0.5 giờ)**
- Giải thích mechanism
- List use cases phù hợp
- Security considerations

#### Task 2.3 (TV1): Nghiên cứu Stream Multiplexing

**Bước 1: Hiểu Stream concept (1 giờ)**
- Đọc RFC 9000 Section 2.1
- Stream ID format: 2 bits cho type, còn lại cho sequence
- Types: Client-initiated bidirectional, Server-initiated, Unidirectional

**Bước 2: Vẽ diagram Stream Independence (1.5 giờ)**
```
QUIC Connection
├── Stream 0 (Control)
├── Stream 4 (Request 1) ─────> [Packet lost, retransmit]
├── Stream 8 (Request 2) ─────> [Continue normally!]  <- No HOL blocking
└── Stream 12 (Request 3) ────> [Continue normally!]
```

**Bước 3: So sánh với HTTP/2 (1 giờ)**
- HTTP/2: tất cả streams share 1 TCP connection
- Khi packet bị mất → tất cả streams bị block
- QUIC: mỗi stream độc lập

**Bước 4: Viết tài liệu (0.5 giờ)**

#### Task 2.1 (TV2): Nghiên cứu TLS 1.3 trong QUIC

**Bước 1: Đọc RFC 9001 (1.5 giờ)**
- Hiểu cách QUIC integrate TLS 1.3
- Không dùng TLS record layer
- CRYPTO frames carry TLS messages

**Bước 2: Hiểu Encryption Levels (1.5 giờ)**
```
Level 0: Initial (derived from connection ID)
Level 1: Handshake (derived from handshake secrets)
Level 2: 1-RTT (derived from handshake)
Level 3: 0-RTT (derived from PSK)
```

**Bước 3: Hiểu Key Derivation (1.5 giờ)**
- HKDF-Extract và HKDF-Expand-Label
- Separate keys cho client và server
- Separate keys cho header protection

**Bước 4: Viết tài liệu (0.5 giờ)**

#### Task 2.3 (TV2): Nghiên cứu Loss Detection

**Bước 1: Đọc RFC 9002 (1.5 giờ)**
- Packet Number Space
- ACK-based detection
- Time-based detection (PTO)

**Bước 2: Hiểu ACK mechanism (1.5 giờ)**
```
- Packet numbers monotonically increasing
- ACK frames carry ranges of received packets
- ACK Delay field cho RTT calculation
- Ví dụ: ACK[1-5, 7-10] = received 1,2,3,4,5,7,8,9,10 (missing 6)
```

**Bước 3: Hiểu Loss Detection algorithm (1 giờ)**
- Packet Threshold: 3 packets (like TCP FACK)
- Time Threshold: 9/8 * max(smoothed_rtt, latest_rtt)
- Probe Timeout (PTO)

**Bước 4: Viết tài liệu (0.5 giờ)**

---

## 🗓️ TUẦN 3: THIẾT LẬP MÔI TRƯỜNG THỬ NGHIỆM (20 giờ/người)

### Thành viên 1 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 3.1 | Cài đặt QUIC server (quiche) | - Clone repo quiche từ Cloudflare<br>- Cài đặt Rust và build quiche<br>- Tạo certificate cho QUIC server<br>- Test server hoạt động | 8 | Server QUIC chạy được |
| 3.2 | Tạo test files | - Tạo files với kích thước: 1KB, 10KB, 100KB, 1MB, 10MB<br>- Đặt files vào thư mục server | 2 | Test files |
| 3.3 | Viết script đo Handshake | - Script đo thời gian connection establishment<br>- Chạy 100 lần để lấy trung bình<br>- Ghi log kết quả ra file CSV | 5 | Script + template CSV |
| 3.4 | Viết script đo Latency | - Script đo TTFB (Time To First Byte)<br>- Test với các điều kiện mạng khác nhau<br>- Output ra CSV | 5 | Script + template CSV |

### Thành viên 2 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 3.1 | Cài đặt HTTP/2 server (nginx) | - Cài nginx với HTTP/2 support<br>- Cấu hình SSL/TLS<br>- Enable HTTP/2 trong config<br>- Test server hoạt động | 6 | Server HTTP/2 chạy được |
| 3.2 | Thiết lập Network Emulation | - Cài đặt tc/netem<br>- Tạo script cho các điều kiện mạng:<br>  + Normal (0ms delay, 0% loss)<br>  + High latency (50ms, 100ms, 200ms)<br>  + Packet loss (1%, 5%, 10%)<br>  + Jitter (20ms variation) | 8 | Scripts network emulation |
| 3.3 | Cài đặt công cụ benchmark | - Cài curl với HTTP/3 support<br>- Cài h2load cho HTTP/2<br>- Cài Wireshark để capture packets | 3 | Công cụ sẵn sàng |
| 3.4 | Viết script đo Throughput | - Script download files và đo tốc độ<br>- Test với các file size khác nhau<br>- Output ra CSV | 3 | Script + template CSV |

### 📋 Deliverables cuối Tuần 3:
- [ ] QUIC server hoạt động (TV1)
- [ ] HTTP/2 server hoạt động (TV2)
- [ ] Scripts network emulation (TV2)
- [ ] Scripts benchmark cơ bản (Cả 2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 3

#### Task 3.1 (TV1): Cài đặt QUIC server (quiche)

**Bước 1: Cài đặt prerequisites (1 giờ)**
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env

# Install dependencies
sudo apt install -y cmake build-essential pkg-config libssl-dev
```

**Bước 2: Clone và build quiche (2 giờ)**
```bash
# Clone repository
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche

# Build
cargo build --release --examples

# Verify build
ls -la target/release/examples/
# Should see: quiche-server, quiche-client
```

**Bước 3: Tạo SSL certificate (1 giờ)**
```bash
# Create certs directory
mkdir -p ~/quic-test/certs
cd ~/quic-test/certs

# Generate self-signed certificate
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes \
  -subj "/C=VN/ST=HCMC/L=HCMC/O=UIT/CN=localhost"

# Verify certificate
openssl x509 -in cert.pem -text -noout
```

**Bước 4: Tạo thư mục content (30 phút)**
```bash
mkdir -p ~/quic-test/www

# Create index.html
echo "<html><body><h1>QUIC Test Server</h1></body></html>" > ~/quic-test/www/index.html
```

**Bước 5: Chạy và test server (1.5 giờ)**
```bash
# Start server
cd ~/quiche
./target/release/examples/quiche-server \
  --cert ~/quic-test/certs/cert.pem \
  --key ~/quic-test/certs/key.pem \
  --root ~/quic-test/www \
  --listen 0.0.0.0:4433

# Test với quiche-client (terminal khác)
./target/release/examples/quiche-client \
  --no-verify \
  https://localhost:4433/index.html
```

**Bước 6: Viết startup script (1 giờ)**
```bash
#!/bin/bash
# File: ~/quic-test/start_quic_server.sh

QUICHE_DIR=~/quiche
CERT_DIR=~/quic-test/certs
WWW_DIR=~/quic-test/www

$QUICHE_DIR/target/release/examples/quiche-server \
  --cert $CERT_DIR/cert.pem \
  --key $CERT_DIR/key.pem \
  --root $WWW_DIR \
  --listen 0.0.0.0:4433 \
  2>&1 | tee ~/quic-test/server.log
```

**Bước 7: Document và troubleshoot (1 giờ)**
- Ghi chú các issues gặp phải
- Test từ máy khác (nếu có)
- Verify port 4433 UDP mở

#### Task 3.1 (TV2): Cài đặt HTTP/2 server (nginx)

**Bước 1: Cài đặt nginx với HTTP/2 support (1 giờ)**
```bash
# Install nginx
sudo apt install -y nginx

# Verify HTTP/2 support
nginx -V 2>&1 | grep -o 'http_v2_module'
```

**Bước 2: Tạo SSL certificate (30 phút)**
```bash
sudo mkdir -p /etc/nginx/ssl
sudo openssl req -x509 -newkey rsa:4096 \
  -keyout /etc/nginx/ssl/key.pem \
  -out /etc/nginx/ssl/cert.pem \
  -days 365 -nodes \
  -subj "/C=VN/ST=HCMC/L=HCMC/O=UIT/CN=localhost"
```

**Bước 3: Cấu hình nginx cho HTTP/2 (2 giờ)**
```nginx
# File: /etc/nginx/sites-available/http2-test
server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    
    server_name localhost;
    
    ssl_certificate /etc/nginx/ssl/cert.pem;
    ssl_certificate_key /etc/nginx/ssl/key.pem;
    
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers HIGH:!aNULL:!MD5;
    
    root /var/www/html;
    index index.html;
    
    location / {
        try_files $uri $uri/ =404;
    }
}
```

**Bước 4: Enable và restart (30 phút)**
```bash
sudo ln -s /etc/nginx/sites-available/http2-test /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl restart nginx
```

**Bước 5: Test HTTP/2 (1 giờ)**
```bash
# Test với curl
curl -I --http2 -k https://localhost/

# Verify HTTP/2
curl -I --http2 -k https://localhost/ 2>&1 | grep HTTP/2

# Test với nghttp
sudo apt install -y nghttp2-client
nghttp -v https://localhost/
```

**Bước 6: Tạo test content (1 giờ)**
```bash
# Copy test files to web root
sudo cp ~/quic-test/www/* /var/www/html/
```

#### Task 3.2 (TV2): Thiết lập Network Emulation

**Bước 1: Hiểu tc/netem (1 giờ)**
- Đọc man page: `man tc-netem`
- Hiểu các options: delay, loss, duplicate, corrupt

**Bước 2: Tạo script cho network conditions (3 giờ)**
```bash
#!/bin/bash
# File: ~/quic-test/network_emulation.sh

IFACE="lo"  # hoặc eth0

case "$1" in
  "normal")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    echo "Network: Normal (no emulation)"
    ;;
  "delay50")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem delay 50ms
    echo "Network: 50ms delay"
    ;;
  "delay100")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem delay 100ms
    echo "Network: 100ms delay"
    ;;
  "delay200")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem delay 200ms
    echo "Network: 200ms delay"
    ;;
  "loss1")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem loss 1%
    echo "Network: 1% packet loss"
    ;;
  "loss5")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem loss 5%
    echo "Network: 5% packet loss"
    ;;
  "loss10")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem loss 10%
    echo "Network: 10% packet loss"
    ;;
  "jitter20")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem delay 50ms 20ms
    echo "Network: 50ms delay with 20ms jitter"
    ;;
  "mobile4g")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    sudo tc qdisc add dev $IFACE root netem delay 50ms 10ms loss 0.5%
    echo "Network: Simulated 4G (50ms delay, 10ms jitter, 0.5% loss)"
    ;;
  "clear")
    sudo tc qdisc del dev $IFACE root 2>/dev/null
    echo "Network emulation cleared"
    ;;
  *)
    echo "Usage: $0 {normal|delay50|delay100|delay200|loss1|loss5|loss10|jitter20|mobile4g|clear}"
    ;;
esac
```

**Bước 3: Test từng condition (2 giờ)**
```bash
chmod +x ~/quic-test/network_emulation.sh

# Test delay
./network_emulation.sh delay100
ping localhost  # Verify ~100ms RTT
./network_emulation.sh clear
```

**Bước 4: Document (1 giờ)**
- Ghi chú cách sử dụng
- List all conditions
- Note: cần sudo

#### Task 3.3 (TV1): Viết script đo Handshake

**Bước 1: Tạo script template (2 giờ)**
```bash
#!/bin/bash
# File: ~/quic-test/measure_handshake.sh

OUTPUT_FILE="handshake_results.csv"
ITERATIONS=100
QUIC_SERVER="localhost:4433"
HTTP2_SERVER="localhost:443"

echo "protocol,iteration,handshake_time_ms" > $OUTPUT_FILE

# Measure QUIC handshake
for i in $(seq 1 $ITERATIONS); do
  START=$(date +%s%N)
  ~/quiche/target/release/examples/quiche-client \
    --no-verify \
    https://$QUIC_SERVER/ \
    > /dev/null 2>&1
  END=$(date +%s%N)
  TIME_MS=$(( ($END - $START) / 1000000 ))
  echo "quic,$i,$TIME_MS" >> $OUTPUT_FILE
done

# Measure HTTP/2 handshake
for i in $(seq 1 $ITERATIONS); do
  START=$(date +%s%N)
  curl -s -o /dev/null -w "%{time_connect}" --http2 -k https://$HTTP2_SERVER/
  END=$(date +%s%N)
  TIME_MS=$(( ($END - $START) / 1000000 ))
  echo "http2,$i,$TIME_MS" >> $OUTPUT_FILE
done

echo "Results saved to $OUTPUT_FILE"
```

**Bước 2: Test và validate script (2 giờ)**
```bash
chmod +x ~/quic-test/measure_handshake.sh
./measure_handshake.sh

# Verify output
head -20 handshake_results.csv
```

**Bước 3: Tạo phiên bản với different network conditions (1 giờ)**

---

## 🗓️ TUẦN 4: THỬ NGHIỆM HIỆU NĂNG CƠ BẢN (20 giờ/người)

### Thành viên 1 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 4.1 | Đo Handshake Time - QUIC | - Đo 1-RTT handshake time<br>- Chạy 100 lần mỗi điều kiện<br>- Điều kiện: Normal, 50ms, 100ms, 200ms delay | 6 | Data CSV |
| 4.2 | Đo Handshake Time - HTTP/2 | - Đo TCP+TLS handshake time<br>- Cùng điều kiện với QUIC<br>- Chạy 100 lần mỗi điều kiện | 4 | Data CSV |
| 4.3 | Đo Latency (TTFB) | - Đo TTFB cho cả QUIC và HTTP/2<br>- File 1KB để minimize transfer time<br>- Các điều kiện: Normal, 50ms, 100ms, 200ms | 6 | Data CSV |
| 4.4 | Kiểm tra 0-RTT (QUIC) | - Test 0-RTT resumption<br>- So sánh với new connection<br>- Ghi nhận improvement | 4 | Data CSV + notes |

### Thành viên 2 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 4.1 | Đo Throughput - Small files | - File 1KB, 10KB<br>- QUIC vs HTTP/2<br>- Điều kiện: Normal, 50ms, 100ms delay | 5 | Data CSV |
| 4.2 | Đo Throughput - Medium files | - File 100KB, 1MB<br>- QUIC vs HTTP/2<br>- Cùng điều kiện | 5 | Data CSV |
| 4.3 | Đo Throughput - Large files | - File 10MB<br>- QUIC vs HTTP/2<br>- Test với bandwidth limiting | 5 | Data CSV |
| 4.4 | Tổng hợp dữ liệu Tuần 4 | - Merge tất cả CSV files<br>- Kiểm tra data consistency<br>- Backup dữ liệu | 5 | Master spreadsheet |

### 📋 Deliverables cuối Tuần 4:
- [ ] Data Handshake time QUIC vs HTTP/2 (TV1)
- [ ] Data Latency QUIC vs HTTP/2 (TV1)
- [ ] Data Throughput các file sizes (TV2)
- [ ] Master spreadsheet với tất cả data (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 4

#### Task 4.1 (TV1): Đo Handshake Time - QUIC

**Bước 1: Chuẩn bị test matrix (30 phút)**
```
Network Conditions:
- Normal (0ms delay)
- 50ms delay
- 100ms delay  
- 200ms delay

Iterations: 100 per condition
Total measurements: 400
```

**Bước 2: Chạy tests với từng condition (4 giờ)**
```bash
#!/bin/bash
# Run for each condition

CONDITIONS=("normal" "delay50" "delay100" "delay200")

for cond in "${CONDITIONS[@]}"; do
  echo "Testing condition: $cond"
  ~/quic-test/network_emulation.sh $cond
  sleep 2
  
  for i in $(seq 1 100); do
    # Measure QUIC new connection handshake
    START=$(date +%s%N)
    ~/quiche/target/release/examples/quiche-client \
      --no-verify \
      https://localhost:4433/index.html \
      > /dev/null 2>&1
    END=$(date +%s%N)
    TIME_MS=$(( ($END - $START) / 1000000 ))
    echo "quic,new,$cond,$i,$TIME_MS" >> handshake_quic.csv
  done
  
  ~/quic-test/network_emulation.sh clear
done
```

**Bước 3: Validate data (1 giờ)**
- Check cho outliers
- Verify số lượng measurements
- Tính mean, median, std dev

**Bước 4: Document findings (0.5 giờ)**
- Note bất kỳ issues
- Record test environment details

#### Task 4.2 (TV1): Đo Handshake Time - HTTP/2

**Bước 1: Chạy tương tự cho HTTP/2 (3 giờ)**
```bash
#!/bin/bash

CONDITIONS=("normal" "delay50" "delay100" "delay200")

for cond in "${CONDITIONS[@]}"; do
  echo "Testing condition: $cond"
  ~/quic-test/network_emulation.sh $cond
  sleep 2
  
  for i in $(seq 1 100); do
    # Measure HTTP/2 connection time (TCP + TLS)
    TIME=$(curl -s -o /dev/null -w "%{time_connect},%{time_appconnect}" \
      --http2 -k https://localhost/)
    echo "http2,$cond,$i,$TIME" >> handshake_http2.csv
  done
  
  ~/quic-test/network_emulation.sh clear
done
```

**Bước 2: Parse curl output (1 giờ)**
- time_connect: TCP handshake
- time_appconnect: TCP + TLS
- Calculate total

#### Task 4.3 (TV1): Đo Latency (TTFB)

**Bước 1: Tạo script đo TTFB (2 giờ)**
```bash
#!/bin/bash
# Measure Time To First Byte

FILE="index.html"  # Small file

CONDITIONS=("normal" "delay50" "delay100" "delay200")

for cond in "${CONDITIONS[@]}"; do
  ~/quic-test/network_emulation.sh $cond
  sleep 2
  
  for i in $(seq 1 100); do
    # QUIC TTFB
    START=$(date +%s%N)
    ~/quiche/target/release/examples/quiche-client \
      --no-verify \
      https://localhost:4433/$FILE 2>&1 | head -1 > /dev/null
    END=$(date +%s%N)
    QUIC_TTFB=$(( ($END - $START) / 1000000 ))
    
    # HTTP/2 TTFB
    HTTP2_TTFB=$(curl -s -o /dev/null -w "%{time_starttransfer}" \
      --http2 -k https://localhost/$FILE)
    HTTP2_TTFB_MS=$(echo "$HTTP2_TTFB * 1000" | bc)
    
    echo "$cond,$i,$QUIC_TTFB,$HTTP2_TTFB_MS" >> ttfb_results.csv
  done
  
  ~/quic-test/network_emulation.sh clear
done
```

**Bước 2: Chạy tests (3 giờ)**
**Bước 3: Validate và document (1 giờ)**

#### Task 4.1-4.3 (TV2): Đo Throughput

**Bước 1: Tạo test files (30 phút)**
```bash
cd ~/quic-test/www

# Small files
dd if=/dev/urandom of=1KB.bin bs=1K count=1
dd if=/dev/urandom of=10KB.bin bs=1K count=10

# Medium files
dd if=/dev/urandom of=100KB.bin bs=1K count=100
dd if=/dev/urandom of=1MB.bin bs=1M count=1

# Large file
dd if=/dev/urandom of=10MB.bin bs=1M count=10

# Copy to nginx
sudo cp *.bin /var/www/html/
```

**Bước 2: Tạo script đo throughput (2 giờ)**
```bash
#!/bin/bash
# File: measure_throughput.sh

FILES=("1KB.bin" "10KB.bin" "100KB.bin" "1MB.bin" "10MB.bin")
CONDITIONS=("normal" "delay50" "delay100")
ITERATIONS=50

echo "protocol,file,condition,iteration,time_ms,throughput_mbps" > throughput_results.csv

for file in "${FILES[@]}"; do
  for cond in "${CONDITIONS[@]}"; do
    ~/quic-test/network_emulation.sh $cond
    sleep 2
    
    # Get file size in bytes
    FILESIZE=$(stat -c%s "/var/www/html/$file")
    
    for i in $(seq 1 $ITERATIONS); do
      # QUIC throughput
      START=$(date +%s%N)
      ~/quiche/target/release/examples/quiche-client \
        --no-verify \
        https://localhost:4433/$file \
        > /tmp/download 2>/dev/null
      END=$(date +%s%N)
      TIME_MS=$(( ($END - $START) / 1000000 ))
      THROUGHPUT=$(echo "scale=2; $FILESIZE * 8 / $TIME_MS / 1000" | bc)
      echo "quic,$file,$cond,$i,$TIME_MS,$THROUGHPUT" >> throughput_results.csv
      
      # HTTP/2 throughput
      START=$(date +%s%N)
      curl -s -o /tmp/download --http2 -k https://localhost/$file
      END=$(date +%s%N)
      TIME_MS=$(( ($END - $START) / 1000000 ))
      THROUGHPUT=$(echo "scale=2; $FILESIZE * 8 / $TIME_MS / 1000" | bc)
      echo "http2,$file,$cond,$i,$TIME_MS,$THROUGHPUT" >> throughput_results.csv
    done
    
    ~/quic-test/network_emulation.sh clear
  done
done
```

**Bước 3: Chạy tests (10 giờ)**
- Small files: nhanh hơn, chạy nhiều iterations
- Large files: lâu hơn, có thể giảm iterations

**Bước 4: Tổng hợp dữ liệu (5 giờ)**
- Import vào spreadsheet (Google Sheets/Excel)
- Tính mean, median, std dev cho mỗi combination
- Kiểm tra data consistency

---

## 🗓️ TUẦN 5: PHÂN TÍCH DỮ LIỆU (15 giờ/người)

### Thành viên 1 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 5.1 | Phân tích Handshake Time | - Tính mean, median, std deviation<br>- So sánh QUIC 1-RTT vs TCP+TLS<br>- Phân tích improvement % | 4 | Báo cáo phân tích |
| 5.2 | Phân tích 0-RTT | - So sánh 0-RTT vs 1-RTT<br>- Tính improvement %<br>- Phân tích use cases | 3 | Báo cáo phân tích |
| 5.3 | Phân tích Latency | - So sánh TTFB theo điều kiện mạng<br>- Phân tích tác động của RTT<br>- QUIC vs HTTP/2 comparison | 4 | Báo cáo phân tích |
| 5.4 | Phân tích Throughput | - Phân tích throughput patterns<br>- So sánh QUIC vs HTTP/2<br>- Impact of file sizes | 4 | Báo cáo phân tích |

### Thành viên 2 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 5.1 | Xử lý và làm sạch dữ liệu | - Remove outliers (>3 std dev)<br>- Handle missing data<br>- Validate data ranges | 3 | Clean dataset |
| 5.2 | Tạo biểu đồ Handshake & Latency | - Bar chart: Handshake time comparison<br>- Line chart: Latency vs RTT<br>- Annotate key findings | 4 | 3-4 biểu đồ |
| 5.3 | Tạo biểu đồ Throughput | - Line chart: Throughput vs file size<br>- Bar chart: Throughput comparison<br>- Impact of network conditions | 4 | 3-4 biểu đồ |
| 5.4 | Phân tích Throughput comparison | - Analyze throughput patterns<br>- Compare QUIC vs HTTP/2<br>- Document findings | 4 | Báo cáo phân tích |

### 📋 Deliverables cuối Tuần 5:
- [ ] Báo cáo phân tích Handshake & Latency (TV1)
- [ ] Báo cáo phân tích Throughput (TV1)
- [ ] Tất cả biểu đồ (TV2)
- [ ] Báo cáo phân tích Throughput (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 5

#### Task 5.1 (TV1): Phân tích Handshake Time

**Bước 1: Import data vào Python/R (30 phút)**
```python
import pandas as pd
import numpy as np

# Load data
df = pd.read_csv('handshake_results.csv')

# Separate by protocol
quic_data = df[df['protocol'] == 'quic']
http2_data = df[df['protocol'] == 'http2']
```

**Bước 2: Tính statistics (1 giờ)**
```python
# Group by condition
stats = df.groupby(['protocol', 'condition']).agg({
    'handshake_time_ms': ['mean', 'median', 'std', 'min', 'max']
}).round(2)

print(stats)
```

**Bước 3: Tính improvement percentage (1 giờ)**
```python
# Calculate QUIC improvement over HTTP/2
for condition in df['condition'].unique():
    quic_mean = quic_data[quic_data['condition'] == condition]['handshake_time_ms'].mean()
    http2_mean = http2_data[http2_data['condition'] == condition]['handshake_time_ms'].mean()
    improvement = ((http2_mean - quic_mean) / http2_mean) * 100
    print(f"{condition}: QUIC is {improvement:.1f}% faster")
```

**Bước 4: Viết analysis report (1.5 giờ)**
```markdown
## Handshake Time Analysis

### Key Findings:
1. QUIC 1-RTT handshake consistently faster than TCP+TLS
2. Improvement increases with higher latency:
   - Normal: X% faster
   - 100ms delay: Y% faster
   - 200ms delay: Z% faster

### Explanation:
- TCP requires 1.5 RTT + TLS requires 1 RTT = 2.5 RTT minimum
- QUIC combines transport + crypto in 1 RTT
- At higher latency, RTT savings more significant
```

#### Task 5.2 (TV2): Tạo biểu đồ

**Bước 1: Setup Python environment (30 phút)**
```python
import matplotlib.pyplot as plt
import seaborn as sns

plt.style.use('seaborn-v0_8')
sns.set_palette("husl")
```

**Bước 2: Tạo Handshake Time Bar Chart (1 giờ)**
```python
fig, ax = plt.subplots(figsize=(10, 6))

# Data
conditions = ['Normal', '50ms', '100ms', '200ms']
quic_times = [df_stats for QUIC]
http2_times = [df_stats for HTTP/2]

x = np.arange(len(conditions))
width = 0.35

bars1 = ax.bar(x - width/2, quic_times, width, label='QUIC', color='#2ecc71')
bars2 = ax.bar(x + width/2, http2_times, width, label='HTTP/2', color='#3498db')

ax.set_xlabel('Network Condition')
ax.set_ylabel('Handshake Time (ms)')
ax.set_title('QUIC vs HTTP/2: Handshake Time Comparison')
ax.set_xticks(x)
ax.set_xticklabels(conditions)
ax.legend()

# Add value labels
for bar in bars1 + bars2:
    height = bar.get_height()
    ax.annotate(f'{height:.1f}',
                xy=(bar.get_x() + bar.get_width() / 2, height),
                ha='center', va='bottom')

plt.tight_layout()
plt.savefig('handshake_comparison.png', dpi=300)
```

**Bước 3: Tạo Throughput Line Chart (1.5 giờ)**
```python
fig, ax = plt.subplots(figsize=(10, 6))

file_sizes = ['1KB', '10KB', '100KB', '1MB', '10MB']
quic_throughput = [...]
http2_throughput = [...]

ax.plot(file_sizes, quic_throughput, 'o-', label='QUIC', linewidth=2)
ax.plot(file_sizes, http2_throughput, 's-', label='HTTP/2', linewidth=2)

ax.set_xlabel('File Size')
ax.set_ylabel('Throughput (Mbps)')
ax.set_title('Throughput vs File Size')
ax.legend()
ax.grid(True, alpha=0.3)

plt.savefig('throughput_comparison.png', dpi=300)
```

**Bước 4: Export tất cả charts (1 giờ)**
- Save as PNG (300 dpi for print)
- Save as SVG (for editing)
- Create chart index

#### Task 5.3 (TV1): Phân tích Throughput

**Bước 1: Analyze throughput data (1 giờ)**
```python
# Calculate throughput statistics by protocol and file size
throughput_stats = df.groupby(['protocol', 'file_size']).agg({
    'throughput': ['mean', 'std', 'median']
}).round(3)

print("Throughput Analysis:")
print(throughput_stats)
```

**Bước 2: Compare QUIC vs HTTP/2 throughput (1.5 giờ)**
```python
# Calculate improvement percentage
for size in ['1KB', '10KB', '100KB', '1MB', '10MB']:
    quic_avg = df[(df['protocol']=='quic') & (df['file_size']==size)]['throughput'].mean()
    http2_avg = df[(df['protocol']=='http2') & (df['file_size']==size)]['throughput'].mean()
    
    improvement = ((quic_avg - http2_avg) / http2_avg) * 100
    print(f"File {size}: QUIC {'faster' if improvement > 0 else 'slower'} by {abs(improvement):.1f}%")
```

**Bước 3: Viết analysis report (1.5 giờ)**
```markdown
## Throughput Analysis

### Key Findings:
1. Performance comparison across file sizes
2. For small files (1KB, 10KB):
   - QUIC advantage: X%
   - Reason: Lower handshake overhead
3. For large files (1MB, 10MB):
   - Performance comparison: X%
   - Reason: TCP congestion control differences

### Explanation:
- QUIC benefits more for small files due to faster handshake
- For large files, throughput converges
- Network conditions affect both protocols similarly
```

---

## 🗓️ TUẦN 6: SO SÁNH VÀ ĐÁNH GIÁ (15 giờ/người)

### Thành viên 1 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 6.1 | Lập bảng so sánh tổng hợp | - So sánh QUIC vs HTTP/2 theo metrics<br>- Handshake, Latency, Throughput<br>- Thêm data thực tế từ experiments | 5 | Bảng so sánh chi tiết |
| 6.2 | Đánh giá ưu điểm của QUIC | - Liệt kê các ưu điểm với evidence<br>- Faster handshake, 0-RTT, etc.<br>- Quantify improvements | 4 | Báo cáo ưu điểm |
| 6.3 | Phân tích scenarios phù hợp | - Mobile applications<br>- High latency networks<br>- Lossy networks<br>- Streaming applications | 4 | Recommendations |
| 6.4 | Review findings với TV2 | - Thảo luận kết quả<br>- Validate conclusions<br>- Resolve disagreements | 2 | Agreed conclusions |

### Thành viên 2 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 6.1 | Đánh giá hạn chế của QUIC | - UDP blocking by firewalls<br>- CPU overhead<br>- Deployment complexity<br>- Middleware issues | 5 | Báo cáo hạn chế |
| 6.2 | So sánh với real-world data | - Tìm benchmarks từ Google, Cloudflare<br>- So sánh với kết quả của mình<br>- Validate findings | 4 | Comparison report |
| 6.3 | Tổng hợp khuyến nghị | - Khi nào nên dùng QUIC<br>- Khi nào nên giữ HTTP/2<br>- Migration considerations | 4 | Recommendations |
| 6.4 | Chuẩn bị outline báo cáo | - Outline 5 chương<br>- Phân chia nội dung<br>- Timeline viết báo cáo | 2 | Report outline |

### 📋 Deliverables cuối Tuần 6:
- [ ] Bảng so sánh QUIC vs HTTP/2 (TV1)
- [ ] Báo cáo ưu điểm QUIC (TV1)
- [ ] Báo cáo hạn chế QUIC (TV2)
- [ ] Khuyến nghị sử dụng (Cả 2)
- [ ] Outline báo cáo (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 6

#### Task 6.1 (TV1): Lập bảng so sánh tổng hợp

**Bước 1: Tạo template bảng (1 giờ)**
```markdown
| Metric | QUIC | HTTP/2 | Winner | Improvement |
|--------|------|--------|--------|-------------|
| **Connection Establishment** |
| Handshake Time (Normal) | Xms | Yms | QUIC | Z% |
| Handshake Time (100ms RTT) | Xms | Yms | QUIC | Z% |
| 0-RTT Support | Yes | No | QUIC | - |
| **Latency** |
| TTFB (Normal) | Xms | Yms | QUIC | Z% |
| TTFB (High Latency) | Xms | Yms | QUIC | Z% |
| **Throughput** |
| Small files (1KB) | X Mbps | Y Mbps | ? | ? |
| Large files (10MB) | X Mbps | Y Mbps | ? | ? |
```

**Bước 2: Điền data từ experiments (2 giờ)**
- Pull numbers từ analysis reports
- Verify calculations
- Double-check với raw data

**Bước 3: Calculate winners và improvements (1 giờ)**
- Cho mỗi metric, xác định protocol tốt hơn
- Tính improvement percentage
- Note ties hoặc inconclusive results

**Bước 4: Format và finalize (1 giờ)**
- Highlight key findings
- Add footnotes cho context
- Export as Markdown và PNG

#### Task 6.2 (TV1): Đánh giá ưu điểm QUIC

**Bước 1: List all advantages (1 giờ)**
```markdown
## QUIC Advantages

### 1. Faster Connection Establishment
- 1-RTT handshake vs 2-3 RTT for TCP+TLS
- **Evidence**: Our tests show X% improvement
- **Impact**: Critical for short-lived connections, API calls

### 2. 0-RTT Resumption
- Can send data immediately on reconnection
- **Evidence**: X% reduction in latency for returning users
- **Use case**: Mobile apps, frequent reconnects

### 3. Built-in Encryption
- Always encrypted, no downgrade attacks
- Simpler deployment (no separate TLS config)

### 4. Connection Migration (Theoretical)
- Can survive IP changes
- **Use case**: Mobile networks, WiFi-cellular handoff
```

**Bước 2: Add evidence từ experiments (1.5 giờ)**
- Link mỗi advantage với data
- Quote specific numbers
- Reference relevant charts

**Bước 3: Viết detailed analysis (1.5 giờ)**
- Giải thích why each advantage matters
- Discuss real-world impact
- Provide recommendations

#### Task 6.1 (TV2): Đánh giá hạn chế QUIC

**Bước 1: Research known limitations (1.5 giờ)**
```markdown
## QUIC Limitations

### 1. UDP Blocking
- Some firewalls/networks block UDP
- Corporate networks often restrict
- **Impact**: May need fallback to TCP

### 2. CPU Overhead
- User-space implementation = more CPU
- Encryption/decryption overhead
- **Evidence**: Need to measure if significant

### 3. Deployment Complexity
- Newer protocol, less tooling
- Fewer debugging tools
- Middleware may not support

### 4. Middlebox Issues
- NAT traversal challenges
- Load balancers may not support
- CDN support varies

### 5. Maturity
- Less battle-tested than TCP
- Potential undiscovered bugs
- Smaller community
```

**Bước 2: Validate với real-world reports (2 giờ)**
- Search Google, Cloudflare, Facebook reports
- Check adoption statistics
- Note any issues reported

**Bước 3: Document mitigations (1.5 giờ)**
- Fallback mechanisms
- Deployment best practices
- When HTTP/2 is better choice

#### Task 6.3 (TV2): Tổng hợp khuyến nghị

**Bước 1: Create recommendation matrix (1.5 giờ)**
```markdown
## When to Use QUIC

| Scenario | Recommendation | Reason |
|----------|---------------|--------|
| Mobile apps | **QUIC** | Connection migration, 0-RTT |
| High latency networks | **QUIC** | Faster handshake |
| Lossy networks | **QUIC** | Better loss recovery |
| Streaming | **QUIC** | No HOL blocking |
| Enterprise internal | **Consider HTTP/2** | UDP may be blocked |
| Legacy systems | **HTTP/2** | Better compatibility |
| High-throughput bulk | **Either** | Similar performance |
```

**Bước 2: Write detailed recommendations (1.5 giờ)**
```markdown
### Recommendation 1: Prefer QUIC for Mobile Applications
- Mobile networks have variable latency and loss
- Connection migration handles network switches
- 0-RTT benefits returning users

### Recommendation 2: Use HTTP/2 as Fallback
- Always implement HTTP/2 fallback
- Some networks block UDP
- Graceful degradation important

### Recommendation 3: Consider Hybrid Approach
- Use QUIC where supported
- Fall back to HTTP/2
- Monitor and compare performance
```

**Bước 3: Discuss migration considerations (1 giờ)**
- Steps to migrate from HTTP/2
- Testing requirements
- Rollout strategy

#### Task 6.4 (TV2): Chuẩn bị outline báo cáo

**Bước 1: Draft outline (1 giờ)**
```markdown
# Báo cáo: Đánh giá hiệu năng QUIC

## Chương 1: Giới thiệu (TV1)
1.1 Đặt vấn đề
1.2 Mục tiêu nghiên cứu
1.3 Phạm vi và giới hạn

## Chương 2: Cơ sở lý thuyết (TV1)
2.1 Tổng quan về QUIC
2.2 Kiến trúc QUIC
2.3 Các cơ chế chính
2.4 So sánh với HTTP/2

## Chương 3: Phương pháp thử nghiệm (TV2)
3.1 Môi trường thử nghiệm
3.2 Các test cases
3.3 Metrics và phương pháp đo lường

## Chương 4: Kết quả và phân tích (TV2)
4.1 Handshake time
4.2 Latency
4.3 Throughput

## Chương 5: Kết luận (TV1)
5.1 Tóm tắt kết quả
5.2 Khuyến nghị
5.3 Hướng phát triển
```

**Bước 2: Phân chia pages và timeline (1 giờ)**
- Ch1: 2-3 pages (TV1, Day 1-2)
- Ch2: 8-10 pages (TV1, Day 1-3)
- Ch3: 5-6 pages (TV2, Day 1-2)
- Ch4: 10-12 pages (TV2, Day 2-4)
- Ch5: 2-3 pages (TV1, Day 3-4)
- Total: 30-35 pages

---

## 🗓️ TUẦN 7: VIẾT BÁO CÁO VÀ HOÀN THIỆN (20 giờ/người)

### Thành viên 1 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 7.1 | Viết Chương 1: Giới thiệu | - Đặt vấn đề (500 từ)<br>- Mục tiêu nghiên cứu<br>- Phạm vi và giới hạn | 3 | Chương 1 (2-3 trang) |
| 7.2 | Viết Chương 2: Kiến trúc QUIC | - Lịch sử phát triển<br>- Kiến trúc tổng quan<br>- Các cơ chế chính (từ Tuần 1-2) | 6 | Chương 2 (8-10 trang) |
| 7.3 | Viết Chương 5: Kết luận | - Tóm tắt kết quả<br>- Đóng góp của nghiên cứu<br>- Hướng phát triển | 3 | Chương 5 (2-3 trang) |
| 7.4 | Thiết kế Slide thuyết trình | - 15-20 slides<br>- Key findings<br>- Demo screenshots | 5 | Slide deck |
| 7.5 | Review và chỉnh sửa | - Review Chương 3-4 của TV2<br>- Sửa lỗi, format<br>- Kiểm tra references | 3 | Final review |

### Thành viên 2 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 7.1 | Viết Chương 3: Phương pháp | - Mô tả môi trường thử nghiệm<br>- Các test cases<br>- Tools và setup | 5 | Chương 3 (5-6 trang) |
| 7.2 | Viết Chương 4: Kết quả | - Trình bày tất cả kết quả<br>- Biểu đồ và bảng số liệu<br>- Phân tích và thảo luận | 8 | Chương 4 (10-12 trang) |
| 7.3 | Format báo cáo | - Thống nhất format<br>- Mục lục, danh mục hình<br>- Tài liệu tham khảo | 3 | Formatted document |
| 7.4 | Review và chỉnh sửa | - Review Chương 1, 2, 5 của TV1<br>- Cross-check data<br>- Final proofreading | 4 | Final review |

### 📋 Deliverables cuối Tuần 7:
- [ ] Báo cáo hoàn chỉnh (30-35 trang)
- [ ] Slide thuyết trình (15-20 slides)
- [ ] Source code và scripts
- [ ] Raw data và processed data

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 7

#### Task 7.1 (TV1): Viết Chương 1 - Giới thiệu

**Bước 1: Viết phần Đặt vấn đề (1 giờ)**
```markdown
## 1.1 Đặt vấn đề

Trong bối cảnh Internet ngày càng phát triển, nhu cầu về tốc độ và 
độ tin cậy của các ứng dụng web ngày càng tăng. Giao thức HTTP/2, 
mặc dù đã cải thiện đáng kể so với HTTP/1.1, vẫn còn những hạn chế 
do phụ thuộc vào TCP...

[Trình bày vấn đề của TCP: HOL blocking, handshake chậm]
[Giới thiệu QUIC như giải pháp]
[Nêu tầm quan trọng của việc đánh giá hiệu năng]
```

**Bước 2: Viết Mục tiêu nghiên cứu (1 giờ)**
```markdown
## 1.2 Mục tiêu nghiên cứu

Nghiên cứu này hướng đến các mục tiêu sau:
1. Tìm hiểu kiến trúc và các cơ chế hoạt động của QUIC
2. Thiết lập môi trường thử nghiệm để đánh giá hiệu năng
3. So sánh QUIC với HTTP/2 trên nhiều tiêu chí
4. Đưa ra khuyến nghị về việc áp dụng QUIC trong thực tế
```

**Bước 3: Viết Phạm vi và giới hạn (1 giờ)**
```markdown
## 1.3 Phạm vi và giới hạn

### Phạm vi:
- Đánh giá QUIC (IETF RFC 9000)
- So sánh với HTTP/2 over TLS 1.3
- Các metrics: handshake, latency, throughput

### Giới hạn:
- Môi trường thử nghiệm: localhost/LAN
- Không test trên production traffic
- Không đánh giá security aspects deeply
```

#### Task 7.2 (TV1): Viết Chương 2 - Kiến trúc QUIC

**Bước 1: Viết Overview (2 giờ)**
- Copy và edit từ tài liệu Tuần 1-2
- Thêm citations
- Ensure flow logic

**Bước 2: Viết chi tiết các cơ chế (3 giờ)**
- Connection Establishment (với diagrams)
- Stream Multiplexing (với diagrams)
- Loss Detection
- Congestion Control

**Bước 3: Review và polish (1 giờ)**
- Check terminology consistency
- Verify diagrams are clear
- Add cross-references

#### Task 7.3 (TV1): Viết Chương 5 - Kết luận

**Bước 1: Tóm tắt findings (1 giờ)**
```markdown
## 5.1 Tóm tắt kết quả

Nghiên cứu đã cho thấy QUIC có nhiều ưu điểm so với HTTP/2:

1. **Handshake nhanh hơn**: QUIC 1-RTT nhanh hơn X% so với TCP+TLS
2. **0-RTT**: Giảm latency Z% cho returning connections
3. **Built-in encryption**: Đơn giản hóa deployment
```

**Bước 2: Viết Khuyến nghị (1 giờ)**
- Synthesize từ Tuần 6
- Add actionable recommendations

**Bước 3: Viết Hướng phát triển (1 giờ)**
```markdown
## 5.3 Hướng phát triển

1. Mở rộng thử nghiệm trên real-world networks
2. Đánh giá QUIC v2 (RFC 9369)
3. So sánh các implementations (quiche, msquic, etc.)
4. Nghiên cứu HTTP/3 performance
```

#### Task 7.1 (TV2): Viết Chương 3 - Phương pháp

**Bước 1: Mô tả môi trường (2 giờ)**
```markdown
## 3.1 Môi trường thử nghiệm

### Hardware:
- CPU: ...
- RAM: ...
- Network: ...

### Software:
- OS: Ubuntu 22.04
- QUIC Server: quiche v0.x
- HTTP/2 Server: nginx v1.x
- Network Emulation: tc/netem

### Test Files:
| Size | Purpose |
|------|---------|
| 1KB  | Latency testing |
| 100KB| Medium transfer |
| 10MB | Throughput testing |
```

**Bước 2: Mô tả test cases (2 giờ)**
- List all test scenarios
- Explain methodology
- Describe metrics collected

**Bước 3: Viết về measurement methodology (1 giờ)**
- How measurements were taken
- Number of iterations
- Statistical methods used

#### Task 7.2 (TV2): Viết Chương 4 - Kết quả

**Bước 1: Structure kết quả (1 giờ)**
```markdown
## 4.1 Handshake Time
### 4.1.1 Results
[Table with numbers]
[Chart]

### 4.1.2 Analysis
[Explanation of findings]

## 4.2 Latency (TTFB)
[Similar structure]

## 4.3 Throughput
[Similar structure]
```

**Bước 2: Insert all charts và tables (3 giờ)**
- Copy từ Tuần 5 analysis
- Ensure high-quality images
- Add proper captions

**Bước 3: Write analysis cho từng section (3 giờ)**
- Explain what numbers mean
- Compare with expectations
- Discuss implications

**Bước 4: Write summary (1 giờ)**
```markdown
## 4.6 Tổng hợp kết quả

| Metric | QUIC | HTTP/2 | Improvement |
|--------|------|--------|-------------|
| Handshake (100ms RTT) | X | Y | Z% |
| Throughput (1MB) | X | Y | Z% |
```

#### Task 7.4 (TV1): Thiết kế Slide

**Bước 1: Create slide structure (1 giờ)**
```
Slide 1: Title
Slide 2: Agenda
Slide 3-4: Introduction/Problem
Slide 5-7: QUIC Architecture
Slide 8-9: Methodology
Slide 10-14: Results (charts)
Slide 15-16: Comparison
Slide 17: Recommendations
Slide 18: Conclusion
Slide 19: Future Work
Slide 20: Q&A
```

**Bước 2: Design slides (3 giờ)**
- Use consistent template
- Insert key charts
- Keep text minimal

**Bước 3: Review và polish (1 giờ)**
- Check flow
- Ensure readability
- Practice timing

#### Task 7.3-7.4 (TV2): Format và Review

**Bước 1: Compile document (1 giờ)**
- Merge all chapters
- Check page breaks
- Ensure consistent formatting

**Bước 2: Create Table of Contents (30 phút)**
- Auto-generate if using Word/LaTeX
- Verify page numbers

**Bước 3: Create List of Figures/Tables (30 phút)**
- List all figures with captions
- List all tables

**Bước 4: Format References (1 giờ)**
- Use consistent citation style (IEEE)
- Verify all references cited
- Check URLs still work

**Bước 5: Final proofreading (1 giờ)**
- Grammar check
- Spelling check
- Number consistency

---

## 📊 BẢNG TỔNG HỢP PHÂN CÔNG THEO THÀNH VIÊN

### Thành viên 1 - Trưởng nhóm (Kiến trúc QUIC, Connection, Handshake)

| Tuần | Công việc chính | Giờ |
|------|----------------|-----|
| 1 | Lịch sử QUIC + Kiến trúc tổng quan + RFC 9000 (1-5) | 15 |
| 2 | Connection Establishment + 0-RTT + Stream Multiplexing + Migration | 15 |
| 3 | Cài đặt QUIC server + Scripts đo Handshake/Latency | 20 |
| 4 | Đo Handshake QUIC/HTTP/2 + Latency + 0-RTT test | 20 |
| 5 | Phân tích Handshake + 0-RTT + Latency | 15 |
| 6 | Bảng so sánh + Ưu điểm QUIC + Scenarios | 15 |
| 7 | Chương 1, 2, 5 + Slide + Review | 20 |
| **TỔNG** | | **120 giờ** |

### Thành viên 2 (Thử nghiệm hiệu năng, Phân tích dữ liệu)

| Tuần | Công việc chính | Giờ |
|------|----------------|-----|
| 1 | TCP analysis + So sánh QUIC/TCP/UDP + RFC 9000 (6-10) + HTTP/3 | 15 |
| 2 | TLS 1.3 + Packet Protection + Loss Detection + Congestion Control | 15 |
| 3 | Cài đặt HTTP/2 + Network Emulation + Benchmark tools | 20 |
| 4 | Đo Throughput (all sizes) + Tổng hợp data | 20 |
| 5 | Xử lý data + Biểu đồ + Phân tích Throughput | 15 |
| 6 | Hạn chế QUIC + Real-world comparison + Khuyến nghị + Outline | 15 |
| 7 | Chương 3, 4 + Format + Review | 20 |
| **TỔNG** | | **120 giờ** |

---

## 📈 Biểu đồ Gantt chi tiết

```
Tuần        1         2         3         4         5         6         7
           |---------|---------|---------|---------|---------|---------|---------|
TV1        [Lý thuyết][Thiết kế][Setup   ][Test    ][Phân    ][So sánh ][Báo cáo ]
           [QUIC    ][QUIC    ][QUIC    ][cơ bản  ][tích    ][đánh giá][Ch1,2,5 ]
           |---------|---------|---------|---------|---------|---------|---------|
TV2        [TCP/UDP ][Security][Setup   ][Thrput  ][Biểu đồ][Hạn chế ][Báo cáo ]
           [Compare ][Loss Det][HTTP/2  ][test    ][Thrput  ][Khuyến  ][Ch3,4   ]
           |---------|---------|---------|---------|---------|---------|---------|
Chung      [Tài liệu]         [Tools   ]         [Review  ][Bảng SS ][Review  ]
           |---------|---------|---------|---------|---------|---------|---------|
```

---

## ✅ CHECKLIST TIẾN ĐỘ CHI TIẾT

### Tuần 1: Tổng quan QUIC
- [ ] Tài liệu lịch sử QUIC (TV1)
- [ ] Sơ đồ kiến trúc QUIC (TV1)
- [ ] Tài liệu TCP analysis (TV2)
- [ ] Bảng so sánh QUIC/TCP/UDP (TV2)
- [ ] Danh sách tài liệu tham khảo (Cả 2)

### Tuần 2: Chi tiết thiết kế
- [ ] Sơ đồ Handshake 1-RTT, 0-RTT (TV1)
- [ ] Tài liệu Stream Multiplexing (TV1)
- [ ] Tài liệu Connection Migration (TV1)
- [ ] Tài liệu TLS 1.3 integration (TV2)
- [ ] Tài liệu Loss Detection & Congestion Control (TV2)

### Tuần 3: Setup môi trường
- [ ] QUIC server (quiche) hoạt động (TV1)
- [ ] HTTP/2 server (nginx) hoạt động (TV2)
- [ ] Scripts network emulation (TV2)
- [ ] Scripts benchmark (Cả 2)
- [ ] Test files ready (TV1)

### Tuần 4: Thử nghiệm cơ bản
- [ ] Data Handshake time QUIC vs HTTP/2 (TV1)
- [ ] Data 0-RTT test (TV1)
- [ ] Data Latency TTFB (TV1)
- [ ] Data Throughput small/medium/large files (TV2)
- [ ] Master spreadsheet (TV2)

### Tuần 5: Phân tích
- [ ] Báo cáo phân tích Handshake & 0-RTT (TV1)
- [ ] Báo cáo phân tích Latency (TV1)
- [ ] Clean dataset (TV2)
- [ ] Tất cả biểu đồ (TV2)
- [ ] Báo cáo phân tích Throughput (TV2)

### Tuần 6: So sánh và đánh giá
- [ ] Bảng so sánh QUIC vs HTTP/2 (TV1)
- [ ] Báo cáo ưu điểm QUIC (TV1)
- [ ] Báo cáo hạn chế QUIC (TV2)
- [ ] Khuyến nghị sử dụng (Cả 2)
- [ ] Outline báo cáo (TV2)

### Tuần 7: Báo cáo
- [ ] Chương 1: Giới thiệu (TV1)
- [ ] Chương 2: Kiến trúc QUIC (TV1)
- [ ] Chương 3: Phương pháp (TV2)
- [ ] Chương 4: Kết quả (TV2)
- [ ] Chương 5: Kết luận (TV1)
- [ ] Slide thuyết trình (TV1)
- [ ] Format và review (TV2)
- [ ] Nộp báo cáo (Cả 2)

---

## 🔧 Công cụ sử dụng

| Công cụ | Mục đích | Link |
|---------|----------|------|
| quiche | QUIC server implementation | https://github.com/cloudflare/quiche |
| nginx | HTTP/2 server | https://nginx.org |
| tc/netem | Network emulation | https://man7.org/linux/man-pages/man8/tc-netem.8.html |
| Wireshark | Packet capture | https://wireshark.org |
| curl | HTTP client testing | https://curl.se |
| h2load | HTTP/2 benchmarking | https://nghttp2.org |

## 📚 Tài liệu tham khảo chính

| Tài liệu | Mô tả |
|----------|-------|
| RFC 9000 | QUIC: A UDP-Based Multiplexed and Secure Transport |
| RFC 9001 | Using TLS to Secure QUIC |
| RFC 9002 | QUIC Loss Detection and Congestion Control |
| RFC 7540 | HTTP/2 specification |

---

*Cập nhật lần cuối: 30/01/2026*
