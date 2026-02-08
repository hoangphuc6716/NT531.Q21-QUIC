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
| 3 | **Connection Migration** | Duy trì kết nối khi đổi IP/network | Demo đổi WiFi → 4G |
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
| 6 | Demo tổng hợp (Topology) | Tất cả features | Video demo |
| 7 | Case Studies & Performance | Google, Cloudflare, Meta | Báo cáo phân tích |
| 8 | Báo cáo & Thuyết trình | Tổng hợp | Báo cáo + Slides |

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
| 2.4 | QUIC 0-RTT Handshake | 0-RTT với PSK | 4 | Sequence diagram + Security analysis |

### Thành viên 2 (15 giờ) - Head-of-Line Blocking

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 2.1 | TCP HOL Blocking | Tại sao HTTP/2 over TCP vẫn bị HOL? | 4 | Diagrams + Explanation |
| 2.2 | QUIC Stream Independence | Mỗi stream độc lập, packet loss không ảnh hưởng stream khác | 5 | Diagrams |
| 2.3 | Bảng so sánh tổng hợp | QUIC vs TCP+TLS: Latency, HOL, Migration, Security | 4 | Comparison table |
| 2.4 | Vẽ infographic | Visual comparison cho báo cáo | 2 | Infographic |

### 📋 Deliverables Tuần 2:
- [ ] 4 Sequence diagrams so sánh handshake (TV1)
- [ ] HOL blocking explanation + diagrams (TV2)
- [ ] Bảng so sánh QUIC vs TCP+TLS (TV2)
- [ ] Infographic tổng hợp (TV2)

### 📊 Bảng So sánh Quan trọng:

| Feature | TCP + TLS 1.2 | TCP + TLS 1.3 | QUIC |
|---------|---------------|---------------|------|
| **New Connection** | 3 RTT | 2 RTT | **1 RTT** |
| **Resumed Connection** | 2 RTT | 1 RTT | **0 RTT** |
| **HOL Blocking** | Yes (TCP level) | Yes (TCP level) | **No** |
| **Connection Migration** | No | No | **Yes** |
| **Built-in Encryption** | Separate (TLS) | Separate (TLS) | **Integrated** |
| **User-space** | No (kernel) | No (kernel) | **Yes** |

---

## 🗓️ TUẦN 3: 0-RTT VÀ 1-RTT HANDSHAKE CHI TIẾT (20 giờ/người)

### Mục tiêu: Hiểu sâu cơ chế handshake - USP lớn nhất của QUIC

### Thành viên 1 (20 giờ) - Handshake Mechanics

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 3.1 | 1-RTT Handshake chi tiết | Initial → Handshake → 1-RTT packets | 5 | Detailed sequence |
| 3.2 | TLS 1.3 Integration | CRYPTO frames, không dùng TLS record layer | 5 | Technical document |
| 3.3 | 0-RTT Early Data | PSK, session tickets, replay attack mitigation | 5 | Security analysis |
| 3.4 | Key Derivation | HKDF, encryption levels, key update | 5 | Crypto document |

### Thành viên 2 (20 giờ) - Packet Protection

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 3.1 | Header Protection | Packet number encryption, why needed | 5 | Document + Diagram |
| 3.2 | Payload Encryption | AEAD (AES-GCM, ChaCha20-Poly1305) | 5 | Technical document |
| 3.3 | Address Validation | Token, Retry packet, amplification attack | 5 | Security document |
| 3.4 | Chuẩn bị Demo handshake | Capture QUIC handshake với Wireshark | 5 | Wireshark screenshots |

### 📋 Deliverables Tuần 3:
- [ ] Chi tiết 1-RTT và 0-RTT handshake (TV1)
- [ ] TLS 1.3 integration document (TV1)
- [ ] Header/Payload protection document (TV2)
- [ ] Wireshark capture của handshake (TV2)

### 🔐 0-RTT Security Considerations:

```
⚠️ 0-RTT Early Data có thể bị REPLAY ATTACK!

Mitigation strategies:
1. Server chỉ accept idempotent requests trong 0-RTT
2. Single-use session tickets
3. Strike register để detect duplicates
4. Application-level replay protection
```

---

## 🗓️ TUẦN 4: STREAM MULTIPLEXING (20 giờ/người)

### Mục tiêu: Hiểu và demo tính năng multiplexing - Giải quyết HOL blocking

### Thành viên 1 (20 giờ) - Stream Concepts

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 4.1 | Stream Types | Bidirectional vs Unidirectional | 4 | Document |
| 4.2 | Stream ID encoding | Client/Server initiated, Bidi/Uni | 4 | Diagrams |
| 4.3 | Stream States | Ready, Send, Data Sent, Data Recvd, Reset | 5 | State diagrams |
| 4.4 | Flow Control | MAX_DATA, MAX_STREAM_DATA, credit-based | 5 | Technical document |
| 4.5 | Cài đặt quiche | Build từ source, test locally | 2 | Working setup |

### Thành viên 2 (20 giờ) - Demo Multiplexing

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 4.1 | Cài đặt demo environment | quiche-server, quiche-client | 4 | Setup guide |
| 4.2 | Demo multiple streams | 5 concurrent downloads | 5 | Screenshots + Video |
| 4.3 | Demo HOL blocking comparison | TCP vs QUIC với packet loss | 6 | Comparison video |
| 4.4 | Capture với Wireshark | Stream frames, interleaving | 3 | Captures + Analysis |
| 4.5 | Document demo steps | Reproducible demo guide | 2 | Demo guide |

### 📋 Deliverables Tuần 4:
- [ ] Stream types và encoding document (TV1)
- [ ] Flow control mechanism document (TV1)
- [ ] Working demo environment (TV2)
- [ ] Video: Multiple streams + HOL blocking comparison (TV2)

### 🎬 Demo Script - Stream Multiplexing:

```bash
# Terminal 1: Start QUIC Server
./quiche-server --cert cert.pem --key key.pem --root ./www --listen 0.0.0.0:4433

# Terminal 2: Multiple concurrent requests (5 streams)
for i in {1..5}; do
  ./quiche-client --no-verify https://localhost:4433/file$i.bin &
done
wait
echo "All downloads complete!"

# Terminal 3: Wireshark capture
tshark -i lo -f "udp port 4433" -Y "quic.stream" -T fields \
  -e frame.number -e quic.stream.stream_id -e quic.stream.length
```

---

## 🗓️ TUẦN 5: CONNECTION MIGRATION (20 giờ/người)

### Mục tiêu: Hiểu và demo Connection Migration - Unique feature của QUIC

### Thành viên 1 (20 giờ) - Migration Mechanics

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 5.1 | Connection ID concept | Multiple CIDs, rotation, privacy | 5 | Document |
| 5.2 | Path Validation | PATH_CHALLENGE, PATH_RESPONSE | 5 | Sequence diagram |
| 5.3 | NAT Rebinding | Handling NAT timeout | 4 | Technical document |
| 5.4 | Active vs Passive migration | Client-initiated vs Server detection | 4 | Comparison |
| 5.5 | Security aspects | Off-path attack prevention | 2 | Security analysis |

### Thành viên 2 (20 giờ) - Demo Connection Migration

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 5.1 | Setup dual-network environment | WiFi + Ethernet or VMs | 5 | Setup guide |
| 5.2 | Demo migration scenario | Switch network during download | 6 | Video demo |
| 5.3 | Capture PATH frames | Wireshark analysis | 4 | Captures |
| 5.4 | Measure migration time | Downtime measurement | 3 | Performance data |
| 5.5 | Compare với TCP | TCP connection drops, QUIC survives | 2 | Comparison |

### 📋 Deliverables Tuần 5:
- [ ] Connection ID và Path Validation document (TV1)
- [ ] Working migration demo (TV2)
- [ ] Video: Connection migration demo (TV2)
- [ ] Performance comparison: QUIC migration vs TCP reconnect (TV2)

### 🔄 Connection Migration Demo Script:

```bash
# Scenario: Download large file, switch network midway

# Step 1: Start server
./quiche-server --cert cert.pem --key key.pem --root ./www --listen 0.0.0.0:4433

# Step 2: Start download on interface eth0
./quiche-client --no-verify https://server:4433/largefile.bin

# Step 3: During download, disable eth0, enable wlan0
sudo ip link set eth0 down
sudo ip link set wlan0 up
# QUIC connection should survive!

# Step 4: Capture and look for PATH_CHALLENGE/PATH_RESPONSE
tshark -r capture.pcap -Y "quic.frame_type == 0x1a or quic.frame_type == 0x1b"
```

---

## 🗓️ TUẦN 6: DEMO THỰC TẾ VỚI TOPOLOGY (20 giờ/người)

### Mục tiêu: Demo tổng hợp tất cả features trên môi trường thực tế

### 🌐 TOPOLOGY DEMO

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│                           QUIC DEMO TOPOLOGY                                         │
│                     (Free Cloud + Local Ubuntu Server)                               │
├─────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                      │
│   ┌──────────────────────────────┐              ┌──────────────────────────────┐    │
│   │     🖥️ UBUNTU SERVER         │              │     ☁️ FREE CLOUD CLIENT     │    │
│   │        (Local/VPS)           │              │   (Oracle Cloud Free Tier)    │    │
│   │                              │              │                              │    │
│   │   ┌────────────────────┐    │              │   ┌────────────────────┐    │    │
│   │   │   QUIC Server      │    │    QUIC     │   │   QUIC Client      │    │    │
│   │   │   (quiche-server)  │◄───┼──────────────┼───│   (quiche-client)  │    │    │
│   │   │   Port: 4433/UDP   │    │   over      │   │                    │    │    │
│   │   └────────────────────┘    │  Internet   │   └────────────────────┘    │    │
│   │                              │              │                              │    │
│   │   OS: Ubuntu 22.04 LTS      │              │   OS: Ubuntu 22.04 LTS      │    │
│   │   IP: Public IP / DynDNS    │              │   IP: Oracle Cloud IP       │    │
│   │   Software:                  │              │   Software:                  │    │
│   │   - quiche (Cloudflare)     │              │   - quiche (Cloudflare)     │    │
│   │   - Wireshark               │              │   - curl with HTTP/3        │    │
│   │   - tcpdump                 │              │   - tc (traffic control)    │    │
│   └──────────────────────────────┘              └──────────────────────────────┘    │
│                                                                                      │
│   ┌──────────────────────────────────────────────────────────────────────────────┐  │
│   │                            NETWORK CONDITIONS                                 │  │
│   │   • Real Internet latency: 50-200ms RTT (depending on location)              │  │
│   │   • Simulated packet loss: 0.1% - 5% using tc netem                          │  │
│   │   • Bandwidth: Varies (can be limited for testing)                           │  │
│   └──────────────────────────────────────────────────────────────────────────────┘  │
│                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────┘
```

### ☁️ Tại sao chọn Oracle Cloud Free Tier?

| Cloud Provider | Free Tier | Specs | Lý do chọn/không chọn |
|----------------|-----------|-------|----------------------|
| **Oracle Cloud** ✅ | **Always Free** | 2 VMs, 1GB RAM each, 50GB storage | ✅ **CHỌN** - Miễn phí vĩnh viễn, đủ specs |
| Google Cloud | $300 credit (90 days) | Expired after trial | ❌ Hết hạn sau 90 ngày |
| AWS | 12 months free | t2.micro only | ❌ Hết hạn sau 1 năm |
| Azure | $200 credit (30 days) | Limited time | ❌ Quá ngắn |

### 🖥️ Server Setup (Ubuntu Local/VPS)

**Yêu cầu:**
- Ubuntu 22.04 LTS
- Public IP hoặc DynDNS
- Mở port 4433/UDP trên router/firewall

### Thành viên 1 (20 giờ) - Server Setup

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 6.1 | Setup Ubuntu Server | Install OS, configure network | 4 | Working server |
| 6.2 | Install quiche | Build từ source | 3 | quiche installed |
| 6.3 | Generate certificates | Self-signed for demo | 2 | cert.pem, key.pem |
| 6.4 | Configure firewall | UFW, port forwarding | 3 | Accessible from internet |
| 6.5 | Create test content | Various file sizes | 2 | Test files |
| 6.6 | Setup monitoring | Wireshark, tcpdump | 3 | Monitoring ready |
| 6.7 | Document setup | Step-by-step guide | 3 | Setup guide |

### Thành viên 2 (20 giờ) - Cloud Client Setup

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 6.1 | Register Oracle Cloud | Create free account | 1 | Account ready |
| 6.2 | Create VM instance | Ubuntu 22.04, Always Free | 2 | VM running |
| 6.3 | Install quiche client | Build từ source | 3 | Client ready |
| 6.4 | Configure network | Security list, ingress rules | 2 | Network configured |
| 6.5 | Test connectivity | Ping, basic connection | 2 | Connection working |
| 6.6 | Run all demos | Handshake, multiplexing, migration | 6 | Demo videos |
| 6.7 | Record demo video | Screen record with explanation | 4 | Final demo video |

### 📋 Deliverables Tuần 6:
- [ ] Working Server với public access (TV1)
- [ ] Working Cloud Client (TV2)
- [ ] Demo videos cho tất cả scenarios (TV2)
- [ ] Setup guides cho cả Server và Client (Cả 2)

### 📝 Setup Scripts

#### setup_server.sh (Ubuntu Server)
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
echo "<h1>QUIC Demo Server</h1><p>Connection successful!</p>" > ~/quic-demo/www/index.html
dd if=/dev/urandom of=~/quic-demo/www/small.bin bs=1K count=100      # 100KB
dd if=/dev/urandom of=~/quic-demo/www/medium.bin bs=1M count=10      # 10MB  
dd if=/dev/urandom of=~/quic-demo/www/large.bin bs=1M count=100      # 100MB

# Configure firewall
sudo ufw allow 4433/udp
sudo ufw reload

echo "=== Server Setup Complete ==="
echo ""
echo "Start server with:"
echo "cd ~/quiche && ./target/release/examples/quiche-server \\"
echo "  --cert ~/quic-demo/certs/cert.pem \\"
echo "  --key ~/quic-demo/certs/key.pem \\"
echo "  --root ~/quic-demo/www \\"
echo "  --listen 0.0.0.0:4433"
```

#### setup_client.sh (Oracle Cloud VM)
```bash
#!/bin/bash
echo "=== Setting up QUIC Client on Oracle Cloud ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    curl git iproute2

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

# Create test script
cat > ~/test_quic.sh << 'EOF'
#!/bin/bash
SERVER_IP="${1:-YOUR_SERVER_IP}"
PORT="${2:-4433}"

echo "Testing QUIC connection to $SERVER_IP:$PORT"

# Test 1: Simple connection
echo "=== Test 1: Simple Connection ==="
./quiche/target/release/examples/quiche-client \
  --no-verify https://$SERVER_IP:$PORT/index.html

# Test 2: Download speed test
echo "=== Test 2: Download Test (10MB) ==="
time ./quiche/target/release/examples/quiche-client \
  --no-verify https://$SERVER_IP:$PORT/medium.bin > /dev/null

# Test 3: Multiple streams
echo "=== Test 3: Multiple Streams ==="
for i in {1..3}; do
  ./quiche/target/release/examples/quiche-client \
    --no-verify https://$SERVER_IP:$PORT/small.bin &
done
wait
echo "All streams complete!"
EOF
chmod +x ~/test_quic.sh

echo "=== Client Setup Complete ==="
echo ""
echo "Test connection with:"
echo "~/test_quic.sh YOUR_SERVER_IP 4433"
```

### 🎬 Demo Scenarios

#### Demo 1: 0-RTT vs 1-RTT Handshake
```bash
# First connection (1-RTT) - measure time
time ./quiche-client --no-verify https://server:4433/index.html

# Second connection (0-RTT) - should be faster
time ./quiche-client --no-verify https://server:4433/index.html
```

#### Demo 2: Stream Multiplexing
```bash
# Server đã có multiple files

# Download 5 files đồng thời
for i in small medium large; do
  ./quiche-client --no-verify https://server:4433/$i.bin &
done
wait

# So sánh với TCP sequential
```

#### Demo 3: Packet Loss Resilience
```bash
# Simulate 5% packet loss
sudo tc qdisc add dev eth0 root netem loss 5%

# Test QUIC - should still work
./quiche-client --no-verify https://server:4433/medium.bin

# Clear
sudo tc qdisc del dev eth0 root
```

---

## 🗓️ TUẦN 7: PHÂN TÍCH HIỆU NĂNG & CASE STUDIES (15 giờ/người)

### Thành viên 1 (15 giờ) - Performance Analysis

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 7.1 | Tổng hợp demo metrics | Latency, throughput, loss recovery | 4 | Performance report |
| 7.2 | So sánh với TCP baseline | Same tests với TCP | 4 | Comparison data |
| 7.3 | Case Study: Google | YouTube, Google Search QUIC deployment | 3 | Analysis |
| 7.4 | Case Study: Cloudflare | Edge network QUIC rollout | 2 | Analysis |
| 7.5 | Case Study: Meta | Facebook/Instagram QUIC usage | 2 | Analysis |

### Thành viên 2 (15 giờ) - Future & Extensions

| STT | Công việc | Chi tiết | Giờ | Output |
|-----|-----------|----------|-----|--------|
| 7.1 | QUIC v2 (RFC 9369) | What's new, improvements | 3 | Document |
| 7.2 | Multipath QUIC | Multiple paths simultaneously | 3 | Technical overview |
| 7.3 | QUIC for other protocols | DNS over QUIC, WebTransport | 3 | Use cases |
| 7.4 | Adoption challenges | UDP blocking, middleboxes | 3 | Analysis |
| 7.5 | Tạo visual summary | Infographics cho báo cáo | 3 | Visuals |

### 📋 Deliverables Tuần 7:
- [ ] Performance comparison report (TV1)
- [ ] Case studies document (TV1)
- [ ] QUIC extensions overview (TV2)
- [ ] Visual assets cho báo cáo (TV2)

### 📈 Performance Metrics to Report:

| Metric | Expected QUIC | Expected TCP | Improvement |
|--------|---------------|--------------|-------------|
| New Connection Setup | ~1 RTT (50-100ms) | ~2-3 RTT (100-200ms) | **50% faster** |
| Resumed Connection | ~0 RTT | ~1-2 RTT | **100% faster** |
| HOL Blocking Impact | None | Significant with loss | **Eliminated** |
| Network Switch Recovery | <500ms | Connection dropped | **Seamless** |

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

### Thành viên 2 (20 giờ) - Slides và Demo Video

| STT | Công việc | Giờ | Output |
|-----|-----------|-----|--------|
| 8.1 | Slide: Introduction (5 slides) | 2 | Slides |
| 8.2 | Slide: Architecture (8 slides) | 3 | Slides |
| 8.3 | Slide: Features (10 slides) | 4 | Slides |
| 8.4 | Slide: Demo (5 slides + video) | 4 | Slides + Video |
| 8.5 | Slide: Conclusion (3 slides) | 1 | Slides |
| 8.6 | Edit demo video | 4 | Final video |
| 8.7 | Review slides | 2 | Final review |

### 📋 Deliverables Tuần 8:
- [ ] Báo cáo hoàn chỉnh (25-30 trang) (TV1)
- [ ] Slide thuyết trình (30-35 slides) (TV2)
- [ ] Demo video (5-10 phút) (TV2)

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
├── 3.2 Stream Multiplexing (No HOL)
├── 3.3 Connection Migration
├── 3.4 Built-in Security
└── 3.5 Loss Recovery

Chương 4: Demo thực hành (5 trang)
├── 4.1 Topology
├── 4.2 Demo scenarios
├── 4.3 Kết quả
└── 4.4 Screenshots

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

## ✅ CHECKLIST TIẾN ĐỘ

### Tuần 1-2: Lý thuyết cơ bản
- [ ] Protocol Stack diagram (TV1)
- [ ] Packet/Frame structure (TV2)
- [ ] So sánh handshake (TV1)
- [ ] HOL blocking explanation (TV2)

### Tuần 3-4: Cơ chế chi tiết
- [ ] 0-RTT/1-RTT document (TV1)
- [ ] Handshake Wireshark capture (TV2)
- [ ] Stream multiplexing demo (TV2)
- [ ] Flow control document (TV1)

### Tuần 5-6: Demo thực hành
- [ ] Server setup complete (TV1)
- [ ] Client setup complete (TV2)
- [ ] All demo videos recorded (TV2)
- [ ] Setup guides written (Cả 2)

### Tuần 7-8: Báo cáo
- [ ] Performance report (TV1)
- [ ] Case studies (TV1)
- [ ] Final report (TV1)
- [ ] Slides + Video (TV2)

---

## 🔧 Công cụ sử dụng

| Công cụ | Mục đích | Link |
|---------|----------|------|
| quiche | QUIC implementation | https://github.com/cloudflare/quiche |
| Wireshark | Packet analysis | https://wireshark.org |
| Oracle Cloud | Free cloud VM | https://oracle.com/cloud/free |
| draw.io | Diagrams | https://app.diagrams.net |
| OBS Studio | Screen recording | https://obsproject.com |

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
| **Nội dung đầy đủ** | Bao quát tất cả đặc điểm quan trọng của QUIC | |
| **Demo thực tế** | Có topology hoạt động, video demo | |
| **So sánh rõ ràng** | QUIC vs TCP+TLS với data cụ thể | |
| **Hiểu sâu** | Giải thích được WHY, không chỉ WHAT | |
| **Trình bày đẹp** | Diagrams, infographics, slides chuyên nghiệp | |
| **Thuyết trình tốt** | Demo live + video backup | |

---

*Cập nhật lần cuối: 08/02/2026*
