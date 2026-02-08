# 🚀 ĐỒ ÁN: NGHIÊN CỨU GIAO THỨC QUIC

## Đề tài: Nghiên cứu và Demo các Đặc điểm Nổi bật của Giao thức QUIC

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò | Trách nhiệm chính |
|-----|-----------|------|---------|-------------------|
| 1 | Thành viên 1 | [MSSV] | Trưởng nhóm | Kiến trúc QUIC, Bảo mật, 0-RTT/1-RTT Handshake |
| 2 | Thành viên 2 | [MSSV] | Thành viên | Stream Multiplexing, Connection Migration, Demo thực hành |

---

## 🎯 Mục tiêu đề tài - Điểm 10/10

### Các đặc điểm nổi bật của QUIC cần nghiên cứu:

| # | Đặc điểm | Tại sao quan trọng? | Output |
|---|----------|---------------------|--------|
| 1 | **0-RTT Handshake** | Giảm latency xuống 0ms cho returning users | So sánh với TCP+TLS (2-3 RTT) |
| 2 | **Multiplexed Streams** | Không có Head-of-Line blocking | Demo nhiều streams đồng thời |
| 3 | **Connection Migration** | Duy trì kết nối khi đổi IP/network | Demo đổi WiFi → Ethernet |
| 4 | **Built-in Encryption** | TLS 1.3 tích hợp, always encrypted | Phân tích bảo mật |
| 5 | **Improved Loss Recovery** | ACK ranges, NACK implicit | So sánh với TCP |
| 6 | **User-space Implementation** | Dễ update, không cần kernel changes | Ưu điểm triển khai |

---

## 📅 Kế hoạch thời gian - 8 tuần

| Tuần | Nội dung chính | Đặc điểm QUIC focus | Output |
|------|----------------|---------------------|--------|
| 1 | Kiến trúc QUIC cơ bản | Protocol Stack, Packet/Frame | Tài liệu kiến trúc |
| 2 | So sánh QUIC vs TCP+TLS | Tại sao QUIC tốt hơn? | Bảng so sánh chi tiết |
| 3 | 0-RTT và 1-RTT Handshake | **Tốc độ kết nối** | Sequence diagrams |
| 4 | Stream Multiplexing | **Không HOL blocking** | Demo + Capture |
| 5 | Connection Migration | **Unique feature** | Demo thực tế |
| 6 | **DEMO TỔNG HỢP** | Tất cả features + Topology | **VIDEO DEMO** |
| 7 | Case Studies & Performance | Google, Cloudflare, Meta | Báo cáo phân tích |
| 8 | Báo cáo & Thuyết trình | Tổng hợp | Báo cáo + Slides |

---

## 🌐 TOPOLOGY DEMO - MÔ PHỎNG THỰC TẾ DUY NHẤT

### Tổng quan Topology

```
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                    QUIC DEMO TOPOLOGY                                             │
│                        (Ubuntu Server + Multiple Clients + Clear Scenarios)                       │
├──────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                   │
│                              ┌─────────────────────────────────┐                                  │
│                              │      🖥️ UBUNTU SERVER           │                                  │
│                              │        (Local/VPS)               │                                  │
│                              │                                  │                                  │
│                              │   ┌──────────────────────────┐   │                                  │
│                              │   │     QUIC Server          │   │                                  │
│                              │   │     (quiche-server)      │   │                                  │
│                              │   │     Port: 4433/UDP       │   │                                  │
│                              │   │     Public IP            │   │                                  │
│                              │   └──────────────────────────┘   │                                  │
│                              │                                  │                                  │
│                              │   OS: Ubuntu 22.04 LTS          │                                  │
│                              │   RAM: 4GB+                      │                                  │
│                              │   Storage: 20GB+                 │                                  │
│                              └─────────────┬───────────────────┘                                  │
│                                            │                                                      │
│                                            │ INTERNET (QUIC over UDP/4433)                       │
│                     ┌──────────────────────┼──────────────────────┐                              │
│                     │                      │                      │                              │
│                     ▼                      ▼                      ▼                              │
│   ┌─────────────────────────┐  ┌─────────────────────────┐  ┌─────────────────────────┐         │
│   │  ☁️ CLOUD CLIENT        │  │  💻 LOCAL CLIENT        │  │  📱 MOBILE CLIENT       │         │
│   │  (Oracle Cloud Free)    │  │  (Laptop/PC)            │  │  (Optional - Phone)     │         │
│   │                         │  │                         │  │                         │         │
│   │  ┌───────────────────┐  │  │  ┌───────────────────┐  │  │  ┌───────────────────┐  │         │
│   │  │  quiche-client    │  │  │  │  quiche-client    │  │  │  │  HTTP/3 Browser   │  │         │
│   │  │                   │  │  │  │  + Wireshark      │  │  │  │  or curl          │  │         │
│   │  └───────────────────┘  │  │  └───────────────────┘  │  │  └───────────────────┘  │         │
│   │                         │  │                         │  │                         │         │
│   │  Purpose:               │  │  Purpose:               │  │  Purpose:               │         │
│   │  - Latency testing      │  │  - Packet capture       │  │  - Real-world test      │         │
│   │  - Cross-region demo    │  │  - Migration demo       │  │  - Mobile network       │         │
│   │  - 0-RTT testing        │  │  - HOL blocking demo    │  │  - 4G/5G testing        │         │
│   │                         │  │  - Stream multiplexing  │  │                         │         │
│   │  Network: Oracle VCN    │  │  Network: WiFi+Ethernet │  │  Network: WiFi/4G       │         │
│   └─────────────────────────┘  └─────────────────────────┘  └─────────────────────────┘         │
│                                                                                                   │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Chi tiết các thành phần

#### 🖥️ UBUNTU SERVER (QUIC Server)

| Thành phần | Chi tiết |
|------------|----------|
| **Hardware** | Máy tính local hoặc VPS (4GB RAM, 2 CPU) |
| **OS** | Ubuntu 22.04 LTS |
| **Network** | Public IP (hoặc DynDNS nếu IP động) |
| **Port** | 4433/UDP (mở trên firewall/router) |
| **Software** | quiche (Cloudflare), Wireshark, tcpdump |
| **Vai trò** | QUIC Server phục vụ tất cả clients |

#### ☁️ CLOUD CLIENT (Oracle Cloud Free Tier)

| Thành phần | Chi tiết |
|------------|----------|
| **Provider** | Oracle Cloud - **Always Free** (miễn phí vĩnh viễn) |
| **Instance** | VM.Standard.E2.1.Micro (1 OCPU, 1GB RAM) |
| **OS** | Ubuntu 22.04 LTS |
| **Network** | Oracle VCN với Public IP |
| **Software** | quiche-client, tc (traffic control) |
| **Vai trò** | Test latency, 0-RTT, cross-region connection |

#### 💻 LOCAL CLIENT (Laptop/PC)

| Thành phần | Chi tiết |
|------------|----------|
| **Hardware** | Laptop hoặc PC của nhóm |
| **OS** | Ubuntu 22.04 / Windows với WSL2 |
| **Network** | WiFi + Ethernet (dual network cho migration demo) |
| **Software** | quiche-client, Wireshark, tc |
| **Vai trò** | Packet capture, Connection Migration demo, HOL blocking test |

#### 📱 MOBILE CLIENT (Optional)

| Thành phần | Chi tiết |
|------------|----------|
| **Device** | Smartphone Android/iOS |
| **Network** | WiFi + 4G/5G |
| **Software** | Chrome (HTTP/3 enabled) hoặc curl |
| **Vai trò** | Real-world mobile network testing |

---

## 🎬 CÁC KỊCH BẢN DEMO CHI TIẾT

### 📌 Kịch bản 1: So sánh Handshake (0-RTT vs 1-RTT vs TCP+TLS)

**Mục tiêu:** Chứng minh QUIC nhanh hơn TCP+TLS trong connection establishment

**Thiết lập:**
- Server: Ubuntu Server với quiche-server
- Client: Cloud Client (Oracle)

**Các bước thực hiện:**

```bash
# === TRÊN CLOUD CLIENT ===

# Bước 1: Test TCP+TLS connection time (baseline)
echo "=== TCP+TLS Baseline ==="
time curl -o /dev/null -s https://server-ip/index.html

# Bước 2: Test QUIC 1-RTT (first connection)
echo "=== QUIC 1-RTT (First Connection) ==="
time ./quiche-client --no-verify https://server-ip:4433/index.html

# Bước 3: Test QUIC 0-RTT (resumed connection)
echo "=== QUIC 0-RTT (Resumed Connection) ==="
time ./quiche-client --no-verify https://server-ip:4433/index.html

# Bước 4: Capture với Wireshark và đếm RTT
tshark -i eth0 -f "udp port 4433" -c 50 -Y "quic" > handshake_capture.txt
```

**Kết quả mong đợi:**

| Connection Type | RTTs | Time (100ms RTT) |
|-----------------|------|------------------|
| TCP + TLS 1.2 | 3 RTT | ~300ms |
| TCP + TLS 1.3 | 2 RTT | ~200ms |
| QUIC 1-RTT | 1 RTT | ~100ms |
| QUIC 0-RTT | 0 RTT | ~0ms + data |

---

### 📌 Kịch bản 2: Stream Multiplexing + HOL Blocking Demo

**Mục tiêu:** Chứng minh QUIC không bị Head-of-Line blocking khi có packet loss

**Thiết lập:**
- Server: Ubuntu Server với 5 files (file1.bin - file5.bin, mỗi file 10MB)
- Client: Local Client với dual terminal

**Các bước thực hiện:**

```bash
# === TRÊN SERVER ===
# Tạo test files
mkdir -p ~/quic-demo/www
for i in {1..5}; do
  dd if=/dev/urandom of=~/quic-demo/www/file$i.bin bs=1M count=10
done

# Start server
./quiche-server --cert cert.pem --key key.pem --root ~/quic-demo/www --listen 0.0.0.0:4433

# === TRÊN LOCAL CLIENT ===

# Terminal 1: Simulate 5% packet loss
sudo tc qdisc add dev wlan0 root netem loss 5% delay 50ms

# Terminal 2: Download 5 files đồng thời với QUIC
echo "=== QUIC với 5% packet loss ==="
time (
  for i in {1..5}; do
    ./quiche-client --no-verify https://server:4433/file$i.bin > /tmp/file$i.bin &
  done
  wait
)

# Terminal 3: Capture stream interleaving
tshark -i wlan0 -f "udp port 4433" -Y "quic.stream" -T fields \
  -e frame.time_relative -e quic.stream.stream_id -e quic.stream.length \
  > stream_interleaving.txt

# So sánh với TCP (HTTP/1.1 sequential)
echo "=== TCP sequential download ==="
time (
  for i in {1..5}; do
    curl -o /tmp/tcp_file$i.bin https://server/file$i.bin
  done
)

# Clear packet loss
sudo tc qdisc del dev wlan0 root
```

**Kết quả mong đợi:**
- QUIC: Tất cả streams hoàn thành gần như đồng thời
- TCP: Mỗi file phải chờ file trước hoàn thành
- Với packet loss: QUIC chỉ ảnh hưởng stream bị mất gói, TCP block tất cả

---

### 📌 Kịch bản 3: Connection Migration Demo

**Mục tiêu:** Chứng minh QUIC duy trì connection khi đổi network

**Thiết lập:**
- Server: Ubuntu Server
- Client: Local Client với WiFi + Ethernet

**Yêu cầu đặc biệt:**
- Laptop phải có cả WiFi và Ethernet
- Cả hai đều kết nối được tới Server

**Các bước thực hiện:**

```bash
# === CHUẨN BỊ ===
# Đảm bảo cả WiFi (wlan0) và Ethernet (eth0) đều active
ip addr show

# === THỰC HIỆN ===

# Terminal 1: Start Wireshark capture
tshark -i any -f "udp port 4433" -w migration_demo.pcap

# Terminal 2: Start download file lớn qua WiFi
# Đảm bảo route qua wlan0
sudo ip route add SERVER_IP/32 dev wlan0
./quiche-client --no-verify https://SERVER_IP:4433/large.bin > /tmp/download.bin

# Terminal 3: TRONG KHI DOWNLOAD - Switch sang Ethernet
sleep 5  # Chờ download bắt đầu
echo "=== Switching to Ethernet ==="
# Setup eth0 route TRƯỚC khi disable wlan0 để minimize downtime
sudo ip link set eth0 up
sudo ip route add SERVER_IP/32 dev eth0
sudo ip link set wlan0 down
sudo ip route del SERVER_IP/32 dev wlan0 2>/dev/null

# Quan sát: Download vẫn tiếp tục!

# Phân tích capture
tshark -r migration_demo.pcap -Y "quic.frame_type == 0x1a" # PATH_CHALLENGE
tshark -r migration_demo.pcap -Y "quic.frame_type == 0x1b" # PATH_RESPONSE
```

**Kết quả mong đợi:**
- Download không bị gián đoạn khi đổi network
- Capture cho thấy PATH_CHALLENGE và PATH_RESPONSE frames
- Downtime: < 500ms

---

### 📌 Kịch bản 4: Multi-Client Concurrent Connections

**Mục tiêu:** Chứng minh Server handle được nhiều clients đồng thời

**Thiết lập:**
- Server: Ubuntu Server
- Clients: Cloud Client + Local Client + Mobile (optional)

**Các bước thực hiện:**

```bash
# === TRÊN SERVER ===
# Monitor connections
watch -n 1 "netstat -anu | grep 4433 | wc -l"

# === TRÊN CLOUD CLIENT ===
echo "=== Cloud Client downloading ==="
./quiche-client --no-verify https://server:4433/medium.bin &

# === TRÊN LOCAL CLIENT ===
echo "=== Local Client downloading ==="
./quiche-client --no-verify https://server:4433/medium.bin &

# === TRÊN MOBILE (nếu có) ===
# Mở Chrome, truy cập https://server:4433/index.html

# === TRÊN SERVER ===
# Observe: Tất cả clients nhận data đồng thời
tcpdump -i eth0 udp port 4433 -c 100 | grep -E "length [0-9]+"
```

---

## 🗓️ TUẦN 1: KIẾN TRÚC QUIC CƠ BẢN (15 giờ/người)

### Mục tiêu: Hiểu cấu trúc và các thành phần của QUIC

### Thành viên 1 (15 giờ) - Protocol Stack & History

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 1.1 | Lịch sử QUIC | gQUIC (2012) → IETF QUIC (2021) → RFC 9000 | 3 | Timeline document |
| 1.2 | QUIC Protocol Stack | Application → QUIC → TLS 1.3 → UDP → IP | 4 | Sơ đồ kiến trúc |
| 1.3 | Connection & Stream concepts | Connection ID, Stream ID, multiplexing | 4 | Tài liệu khái niệm |
| 1.4 | Đọc RFC 9000 (Sections 1-10) | Overview, Streams, Flow Control | 4 | Ghi chú tóm tắt |

### Thành viên 2 (15 giờ) - Packet & Frame Structure

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 1.1 | Packet Types | Long Header (Initial, Handshake) vs Short Header (1-RTT) | 4 | Diagrams |
| 1.2 | Frame Types | STREAM, ACK, CRYPTO, MAX_DATA, PATH_CHALLENGE | 5 | Bảng tổng hợp |
| 1.3 | Packet Number Spaces | Initial, Handshake, Application Data | 3 | Tài liệu |
| 1.4 | Đọc RFC 9000 (Sections 11-22) | Frames, Packets, Error Codes | 3 | Ghi chú |

### 📋 Deliverables Tuần 1:
- [ ] Sơ đồ QUIC Protocol Stack (TV1)
- [ ] Bảng tổng hợp Frame Types (TV2)
- [ ] Tài liệu Connection/Stream concepts (TV1)
- [ ] Diagrams Packet Structure (TV2)

---

## 🗓️ TUẦN 2: SO SÁNH QUIC vs TCP+TLS (15 giờ/người)

### Mục tiêu: Hiểu rõ tại sao QUIC tốt hơn TCP+TLS

### Thành viên 1 (15 giờ) - Connection Establishment

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 2.1 | TCP + TLS 1.2 Handshake | 3-RTT (TCP SYN + TLS Full) | 4 | Sequence diagram |
| 2.2 | TCP + TLS 1.3 Handshake | 2-RTT (TCP SYN + TLS 1-RTT) | 3 | Sequence diagram |
| 2.3 | QUIC 1-RTT Handshake | 1-RTT (Combined transport + crypto) | 4 | Sequence diagram |
| 2.4 | QUIC 0-RTT Handshake | 0-RTT với PSK, replay attack analysis | 4 | Sequence diagram + Security analysis |

### Thành viên 2 (15 giờ) - Head-of-Line Blocking

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 2.1 | TCP HOL Blocking | Tại sao HTTP/2 over TCP vẫn bị HOL? | 4 | Diagrams |
| 2.2 | QUIC Stream Independence | Mỗi stream độc lập, packet loss không ảnh hưởng stream khác | 5 | Diagrams |
| 2.3 | Bảng so sánh tổng hợp | QUIC vs TCP+TLS: Latency, HOL, Migration, Security | 4 | Comparison table |
| 2.4 | Vẽ infographic | Visual comparison cho báo cáo | 2 | Infographic |

### 📊 Bảng So sánh:

| Feature | TCP + TLS 1.2 | TCP + TLS 1.3 | QUIC |
|---------|---------------|---------------|------|
| **New Connection** | 3 RTT | 2 RTT | **1 RTT** |
| **Resumed Connection** | 2 RTT | 1 RTT | **0 RTT** |
| **HOL Blocking** | Yes (TCP level) | Yes (TCP level) | **No** |
| **Connection Migration** | No | No | **Yes** |
| **Built-in Encryption** | Separate | Separate | **Integrated** |

---

## 🗓️ TUẦN 3: 0-RTT VÀ 1-RTT HANDSHAKE (20 giờ/người)

### Mục tiêu: Hiểu sâu cơ chế handshake - USP lớn nhất của QUIC

### Thành viên 1 (20 giờ) - Handshake Mechanics

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 3.1 | 1-RTT Handshake chi tiết | Initial → Handshake → 1-RTT packets | 5 | Detailed sequence |
| 3.2 | TLS 1.3 Integration | CRYPTO frames, encryption levels | 5 | Technical document |
| 3.3 | 0-RTT Early Data | PSK, replay attack mitigation | 5 | Security analysis |
| 3.4 | Key Derivation | HKDF, key update | 5 | Crypto document |

### Thành viên 2 (20 giờ) - Security & Protection

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 3.1 | Header Protection | Packet number encryption | 5 | Document |
| 3.2 | Payload Encryption | AEAD algorithms | 5 | Technical document |
| 3.3 | Address Validation | Token, Retry packet | 5 | Security document |
| 3.4 | Setup demo environment | Cài đặt quiche trên Server | 5 | Working server |

### 📋 Deliverables Tuần 3:
- [ ] Chi tiết 1-RTT và 0-RTT handshake (TV1)
- [ ] Security analysis document (TV1)
- [ ] Header/Payload protection document (TV2)
- [ ] Working QUIC Server (TV2)

---

## 🗓️ TUẦN 4: STREAM MULTIPLEXING (20 giờ/người)

### Mục tiêu: Hiểu và chuẩn bị demo tính năng multiplexing

### Thành viên 1 (20 giờ) - Stream Concepts

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 4.1 | Stream Types | Bidirectional vs Unidirectional | 4 | Document |
| 4.2 | Stream ID encoding | Client/Server initiated | 4 | Diagrams |
| 4.3 | Stream States | State machine | 5 | State diagrams |
| 4.4 | Flow Control | MAX_DATA, MAX_STREAM_DATA | 5 | Technical document |
| 4.5 | Loss Recovery | ACK ranges, retransmission | 2 | Document |

### Thành viên 2 (20 giờ) - Chuẩn bị Demo

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 4.1 | Setup Cloud Client | Oracle Cloud VM | 5 | Working client |
| 4.2 | Setup Local Client | Laptop với dual network | 4 | Working client |
| 4.3 | Test Kịch bản 1 | Handshake comparison | 4 | Test results |
| 4.4 | Test Kịch bản 2 | Stream multiplexing | 4 | Test results |
| 4.5 | Document test steps | Reproducible guide | 3 | Guide |

### 📋 Deliverables Tuần 4:
- [ ] Stream types document (TV1)
- [ ] Flow control document (TV1)
- [ ] Working Cloud Client (TV2)
- [ ] Working Local Client (TV2)
- [ ] Test results cho Kịch bản 1 & 2 (TV2)

---

## 🗓️ TUẦN 5: CONNECTION MIGRATION (20 giờ/người)

### Mục tiêu: Hiểu và chuẩn bị demo Connection Migration

### Thành viên 1 (20 giờ) - Migration Mechanics

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 5.1 | Connection ID concept | Multiple CIDs, rotation | 5 | Document |
| 5.2 | Path Validation | PATH_CHALLENGE, PATH_RESPONSE | 5 | Sequence diagram |
| 5.3 | NAT Rebinding | Handling NAT timeout | 4 | Technical document |
| 5.4 | Active vs Passive migration | Comparison | 4 | Document |
| 5.5 | Security aspects | Off-path attack prevention | 2 | Security analysis |

### Thành viên 2 (20 giờ) - Test Migration

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 5.1 | Setup dual-network | WiFi + Ethernet trên laptop | 4 | Setup guide |
| 5.2 | Test Kịch bản 3 | Connection Migration | 6 | Test results |
| 5.3 | Capture PATH frames | Wireshark analysis | 4 | Captures |
| 5.4 | Test Kịch bản 4 | Multi-client | 4 | Test results |
| 5.5 | Document demo steps | Migration guide | 2 | Guide |

### 📋 Deliverables Tuần 5:
- [ ] Connection Migration document (TV1)
- [ ] Path Validation sequence diagram (TV1)
- [ ] Working migration demo (TV2)
- [ ] Multi-client test results (TV2)
- [ ] All 4 scenarios tested (TV2)

---

## 🗓️ TUẦN 6: DEMO TỔNG HỢP + QUAY VIDEO (20 giờ/người)

### Mục tiêu: Thực hiện và ghi hình tất cả demo scenarios

### Thành viên 1 (20 giờ) - Server Management & Recording

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 6.1 | Chuẩn bị Server | Ensure stability | 3 | Stable server |
| 6.2 | Quay Kịch bản 1 | Handshake comparison | 4 | Video 1 |
| 6.3 | Quay Kịch bản 2 | Stream multiplexing | 4 | Video 2 |
| 6.4 | Quay Kịch bản 3 | Connection Migration | 5 | Video 3 |
| 6.5 | Quay Kịch bản 4 | Multi-client | 2 | Video 4 |
| 6.6 | Edit video tổng hợp | Combine all scenarios | 2 | Final video |

### Thành viên 2 (20 giờ) - Client Operations & Documentation

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 6.1 | Thực hiện Kịch bản 1 | Handshake từ Cloud | 4 | Data + Screenshots |
| 6.2 | Thực hiện Kịch bản 2 | Multiplexing từ Local | 4 | Data + Screenshots |
| 6.3 | Thực hiện Kịch bản 3 | Migration từ Local | 5 | Data + Screenshots |
| 6.4 | Thực hiện Kịch bản 4 | Multi-client | 3 | Data + Screenshots |
| 6.5 | Screenshot compilation | All captures | 2 | Screenshot document |
| 6.6 | Demo documentation | Step-by-step guide | 2 | Demo guide |

### 📋 Deliverables Tuần 6:
- [ ] Video Demo hoàn chỉnh (5-10 phút) (TV1)
- [ ] Screenshots tất cả scenarios (TV2)
- [ ] Demo guide có thể reproduce (TV2)
- [ ] Raw data và captures (TV2)

---

## 🗓️ TUẦN 7: CASE STUDIES & PERFORMANCE ANALYSIS (15 giờ/người)

### Thành viên 1 (15 giờ) - Performance Analysis

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 7.1 | Tổng hợp demo metrics | Latency, throughput | 4 | Performance report |
| 7.2 | So sánh với TCP | Same tests với TCP | 4 | Comparison data |
| 7.3 | Case Study: Google | YouTube, Search | 3 | Analysis |
| 7.4 | Case Study: Cloudflare | Edge network | 2 | Analysis |
| 7.5 | Case Study: Meta | Facebook/Instagram | 2 | Analysis |

### Thành viên 2 (15 giờ) - Future & Extensions

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 7.1 | QUIC v2 (RFC 9369) | Improvements | 3 | Document |
| 7.2 | Multipath QUIC | Overview | 3 | Document |
| 7.3 | Other QUIC applications | DNS, WebTransport | 3 | Use cases |
| 7.4 | Adoption challenges | UDP blocking | 3 | Analysis |
| 7.5 | Visual summary | Infographics | 3 | Visuals |

### 📋 Deliverables Tuần 7:
- [ ] Performance comparison report (TV1)
- [ ] Case studies document (TV1)
- [ ] QUIC extensions overview (TV2)
- [ ] Visual assets (TV2)

---

## 🗓️ TUẦN 8: BÁO CÁO VÀ THUYẾT TRÌNH (20 giờ/người)

### Thành viên 1 (20 giờ) - Viết báo cáo

| STT | Công việc | Giờ | Output |
|-----|-----------|-----|--------|
| 8.1 | Chương 1: Giới thiệu | 2 | Introduction |
| 8.2 | Chương 2: Kiến trúc QUIC | 4 | Architecture |
| 8.3 | Chương 3: Các đặc điểm nổi bật | 5 | Features |
| 8.4 | Chương 4: Demo thực hành | 4 | Demo documentation |
| 8.5 | Chương 5: Case Studies | 2 | Analysis |
| 8.6 | Chương 6: Kết luận | 1 | Conclusion |
| 8.7 | Review và edit | 2 | Final review |

### Thành viên 2 (20 giờ) - Slides

| STT | Công việc | Giờ | Output |
|-----|-----------|-----|--------|
| 8.1 | Slide: Introduction (5 slides) | 2 | Slides |
| 8.2 | Slide: Architecture (8 slides) | 3 | Slides |
| 8.3 | Slide: Features (10 slides) | 4 | Slides |
| 8.4 | Slide: Demo (5 slides + embed video) | 5 | Slides |
| 8.5 | Slide: Case Studies (4 slides) | 2 | Slides |
| 8.6 | Slide: Conclusion (3 slides) | 1 | Slides |
| 8.7 | Review slides | 3 | Final review |

### 📋 Deliverables Tuần 8:
- [ ] Báo cáo hoàn chỉnh (25-30 trang) (TV1)
- [ ] Slide thuyết trình (35 slides) (TV2)
- [ ] Demo video embedded trong slides (TV2)

### 📑 Cấu trúc Báo cáo:

```
Chương 1: Giới thiệu (2 trang)
├── 1.1 Đặt vấn đề
├── 1.2 Mục tiêu
└── 1.3 Phạm vi

Chương 2: Kiến trúc QUIC (6 trang)
├── 2.1 Protocol Stack
├── 2.2 Connection và Stream
├── 2.3 Packet và Frame Types
└── 2.4 So sánh với TCP+TLS

Chương 3: Các đặc điểm nổi bật (10 trang)
├── 3.1 0-RTT và 1-RTT Handshake
├── 3.2 Stream Multiplexing
├── 3.3 Connection Migration
├── 3.4 Built-in Security
└── 3.5 Loss Recovery

Chương 4: Demo thực hành (5 trang)
├── 4.1 Topology
├── 4.2 Kịch bản 1: Handshake
├── 4.3 Kịch bản 2: Stream Multiplexing
├── 4.4 Kịch bản 3: Connection Migration
└── 4.5 Kịch bản 4: Multi-client

Chương 5: Case Studies (3 trang)
├── 5.1 Google
├── 5.2 Cloudflare
└── 5.3 Meta

Chương 6: Kết luận (2 trang)
├── 6.1 Tổng kết
├── 6.2 Hạn chế
└── 6.3 Hướng phát triển
```

---

## 📝 SETUP SCRIPTS

### setup_server.sh (Ubuntu Server)
```bash
#!/bin/bash
echo "=== Setting up QUIC Server on Ubuntu ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    wireshark tshark tcpdump curl git

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

# Create directories
mkdir -p ~/quic-demo/{certs,www,captures}

# Generate certificates
openssl req -x509 -newkey rsa:2048 \
  -keyout ~/quic-demo/certs/key.pem \
  -out ~/quic-demo/certs/cert.pem \
  -days 365 -nodes \
  -subj "/CN=quic-demo-server"

# Create test files
echo "<h1>QUIC Demo Server</h1>" > ~/quic-demo/www/index.html
dd if=/dev/urandom of=~/quic-demo/www/small.bin bs=100K count=1     # 100KB
dd if=/dev/urandom of=~/quic-demo/www/medium.bin bs=1M count=10     # 10MB
dd if=/dev/urandom of=~/quic-demo/www/large.bin bs=1M count=100     # 100MB

# Multiple files for multiplexing test
for i in {1..5}; do
  dd if=/dev/urandom of=~/quic-demo/www/file$i.bin bs=1M count=10
done

# Configure firewall
sudo ufw allow 4433/udp
sudo ufw reload

echo "=== Server Setup Complete ==="
echo "Start server: cd ~/quiche && ./target/release/examples/quiche-server \\"
echo "  --cert ~/quic-demo/certs/cert.pem --key ~/quic-demo/certs/key.pem \\"
echo "  --root ~/quic-demo/www --listen 0.0.0.0:4433"
```

### setup_cloud_client.sh (Oracle Cloud)
```bash
#!/bin/bash
echo "=== Setting up QUIC Client on Oracle Cloud ==="

sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential cmake pkg-config libssl-dev curl git iproute2

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

echo "=== Client Setup Complete ==="
echo "Test: ./target/release/examples/quiche-client --no-verify https://YOUR_SERVER:4433/index.html"
```

### setup_local_client.sh (Laptop)
```bash
#!/bin/bash
echo "=== Setting up QUIC Client on Local Machine ==="

sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    curl git iproute2 wireshark tshark

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

echo "=== Local Client Setup Complete ==="
echo "Ensure you have both WiFi and Ethernet for migration demo"
```

---

## ✅ CHECKLIST TIẾN ĐỘ

### Tuần 1-2: Lý thuyết
- [ ] Protocol Stack diagram (TV1)
- [ ] Packet/Frame structure (TV2)
- [ ] So sánh handshake (TV1)
- [ ] HOL blocking explanation (TV2)

### Tuần 3-4: Cơ chế + Setup
- [ ] 0-RTT/1-RTT document (TV1)
- [ ] Server setup complete (TV2)
- [ ] Cloud Client setup (TV2)
- [ ] Local Client setup (TV2)

### Tuần 5-6: Demo
- [ ] All 4 scenarios tested ✓
- [ ] Video demo recorded ✓
- [ ] Screenshots collected ✓
- [ ] Demo guide written ✓

### Tuần 7-8: Report
- [ ] Performance report (TV1)
- [ ] Case studies (TV1)
- [ ] Final report 25-30 pages (TV1)
- [ ] Slides 35 slides (TV2)

---

## 🔧 Công cụ sử dụng

| Công cụ | Mục đích | Link |
|---------|----------|------|
| quiche | QUIC implementation | https://github.com/cloudflare/quiche |
| Wireshark | Packet analysis | https://wireshark.org |
| Oracle Cloud | Free cloud VM | https://oracle.com/cloud/free |
| OBS Studio | Screen recording | https://obsproject.com |
| draw.io | Diagrams | https://app.diagrams.net |

## 📚 Tài liệu tham khảo

| Tài liệu | Mô tả |
|----------|-------|
| RFC 9000 | QUIC Transport Protocol |
| RFC 9001 | Using TLS to Secure QUIC |
| RFC 9002 | QUIC Loss Detection and Congestion Control |
| RFC 9114 | HTTP/3 |
| RFC 9369 | QUIC Version 2 |

---

## 🎯 Tiêu chí đạt điểm 10

| Tiêu chí | Yêu cầu | ✓ |
|----------|---------|---|
| **Nội dung đầy đủ** | Bao quát tất cả đặc điểm QUIC | |
| **Demo thực tế** | 4 kịch bản demo với video | |
| **Topology rõ ràng** | Server + 3 clients với scenarios cụ thể | |
| **So sánh data** | QUIC vs TCP+TLS với số liệu thực | |
| **Hiểu sâu** | Giải thích WHY, không chỉ WHAT | |
| **Trình bày đẹp** | Diagrams, slides chuyên nghiệp | |
| **Demo live** | Có thể demo trực tiếp + video backup | |

---

*Cập nhật lần cuối: 08/02/2026*
