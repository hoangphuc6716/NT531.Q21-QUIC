# 🚀 ĐỒ ÁN: NGHIÊN CỨU TOÀN DIỆN GIAO THỨC QUIC

## Đề tài: Nghiên cứu và Demo các Đặc điểm Nổi bật của Giao thức QUIC

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò | Thiết bị |
|-----|-----------|------|---------|----------|
| 1 | Thành viên 1 | [MSSV] | Trưởng nhóm | Ubuntu PC 1 (Server + Client) |
| 2 | Thành viên 2 | [MSSV] | Thành viên | Ubuntu PC 2 (Client + Analysis) |
| - | Cả 2 | - | Cùng quản lý | ☁️ Oracle Cloud VM (Remote testing) |

---

## 📑 MỤC LỤC CÔNG VIỆC

### PHẦN A: LÝ THUYẾT VÀ NGHIÊN CỨU

| Chương | Nội dung | Thành viên | Trang |
|--------|----------|------------|-------|
| **A1** | [Tổng quan về QUIC](#a1-tổng-quan-về-quic) | TV1 + TV2 | [↓](#a1-tổng-quan-về-quic) |
| **A2** | [Kiến trúc QUIC Protocol](#a2-kiến-trúc-quic-protocol) | TV1 | [↓](#a2-kiến-trúc-quic-protocol) |
| **A3** | [Packet và Frame Structure](#a3-packet-và-frame-structure) | TV2 | [↓](#a3-packet-và-frame-structure) |
| **A4** | [Connection Establishment (0-RTT/1-RTT)](#a4-connection-establishment-0-rtt1-rtt) | TV1 | [↓](#a4-connection-establishment-0-rtt1-rtt) |
| **A5** | [Stream Multiplexing](#a5-stream-multiplexing) | TV2 | [↓](#a5-stream-multiplexing) |
| **A6** | [Connection Migration](#a6-connection-migration) | TV1 | [↓](#a6-connection-migration) |
| **A7** | [Flow Control](#a7-flow-control) | TV2 | [↓](#a7-flow-control) |
| **A8** | [Loss Detection & Congestion Control](#a8-loss-detection--congestion-control) | TV1 | [↓](#a8-loss-detection--congestion-control) |
| **A9** | [Security (TLS 1.3 Integration)](#a9-security-tls-13-integration) | TV2 | [↓](#a9-security-tls-13-integration) |
| **A10** | [HTTP/3 over QUIC](#a10-http3-over-quic) | TV1 | [↓](#a10-http3-over-quic) |
| **A11** | [So sánh QUIC vs TCP+TLS](#a11-so-sánh-quic-vs-tcptls) | TV1 + TV2 | [↓](#a11-so-sánh-quic-vs-tcptls) |

### PHẦN B: THỰC HÀNH VÀ DEMO

| Chương | Nội dung | Thành viên | Trang |
|--------|----------|------------|-------|
| **B1** | [Setup Topology](#b1-setup-topology) | TV1 + TV2 | [↓](#b1-setup-topology) |
| **B2** | [Demo 1: Handshake Comparison](#b2-demo-1-handshake-comparison) | TV1 | [↓](#b2-demo-1-handshake-comparison) |
| **B3** | [Demo 2: Stream Multiplexing](#b3-demo-2-stream-multiplexing) | TV2 | [↓](#b3-demo-2-stream-multiplexing) |
| **B4** | [Demo 3: Connection Migration](#b4-demo-3-connection-migration) | TV1 | [↓](#b4-demo-3-connection-migration) |
| **B5** | [Demo 4: Packet Loss Recovery](#b5-demo-4-packet-loss-recovery) | TV2 | [↓](#b5-demo-4-packet-loss-recovery) |
| **B6** | [Demo 5: Multi-client Stress Test](#b6-demo-5-multi-client-stress-test) | TV1 + TV2 | [↓](#b6-demo-5-multi-client-stress-test) |
| **B7** | [Wireshark Analysis](#b7-wireshark-analysis) | TV2 | [↓](#b7-wireshark-analysis) |

### PHẦN C: PHÂN TÍCH VÀ BÁO CÁO

| Chương | Nội dung | Thành viên | Trang |
|--------|----------|------------|-------|
| **C1** | [Performance Analysis](#c1-performance-analysis) | TV1 | [↓](#c1-performance-analysis) |
| **C2** | [Case Studies](#c2-case-studies) | TV2 | [↓](#c2-case-studies) |
| **C3** | [QUIC v2 và Future](#c3-quic-v2-và-future) | TV1 | [↓](#c3-quic-v2-và-future) |
| **C4** | [Viết báo cáo](#c4-viết-báo-cáo) | TV1 | [↓](#c4-viết-báo-cáo) |
| **C5** | [Làm slides thuyết trình](#c5-làm-slides-thuyết-trình) | TV2 | [↓](#c5-làm-slides-thuyết-trình) |
| **C6** | [Quay video demo](#c6-quay-video-demo) | TV1 + TV2 | [↓](#c6-quay-video-demo) |

---

## 🎯 Mục tiêu đề tài - Điểm 10/10

### Các đặc điểm nổi bật của QUIC cần nghiên cứu:

| # | Đặc điểm | Tại sao quan trọng? | Output |
|---|----------|---------------------|--------|
| 1 | **0-RTT/1-RTT Handshake** | Giảm latency từ 2-3 RTT xuống 0-1 RTT | So sánh với TCP+TLS |
| 2 | **Stream Multiplexing** | Không có Head-of-Line blocking | Demo nhiều streams |
| 3 | **Connection Migration** | Duy trì kết nối khi đổi network | Demo đổi WiFi↔Ethernet |
| 4 | **Built-in Encryption** | TLS 1.3 tích hợp, always encrypted | Phân tích bảo mật |
| 5 | **Flow Control** | Connection + Stream level | Demo flow control |
| 6 | **Loss Detection & Recovery** | ACK ranges, improved recovery | Demo packet loss |
| 7 | **Congestion Control** | CUBIC, BBR support | Phân tích throughput |
| 8 | **HTTP/3** | Application layer trên QUIC | Demo HTTP/3 requests |
| 9 | **QUIC v2** | RFC 9369, improvements | Tài liệu tóm tắt |

---

## 🌐 TOPOLOGY DEMO - 2 UBUNTU PCs + CLOUD

### Sơ đồ Topology

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                    QUIC DEMO TOPOLOGY                                                │
│                        (2 Ubuntu PCs + Cloud - Hybrid Network)                                       │
├─────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                      │
│                                    ☁️ ORACLE CLOUD (Free Tier)                                       │
│                              ┌──────────────────────────────────────┐                                │
│                              │     QUIC SERVER / CLIENT (Remote)    │                                │
│                              │     (quiche-server / quiche-client)  │                                │
│                              │     Public IP: x.x.x.x               │                                │
│                              │     Port: 4433/UDP                   │                                │
│                              │                                      │                                │
│                              │     OS: Ubuntu 22.04 LTS             │                                │
│                              │     VM.Standard.E2.1.Micro (Free)    │                                │
│                              │     1 OCPU, 1GB RAM                  │                                │
│                              └──────────────┬───────────────────────┘                                │
│                                             │                                                        │
│                                             │ INTERNET                                               │
│                                             │ (Real latency testing)                                 │
│                                             │                                                        │
│   ┌─────────────────────────────────────────┴─────────────────────────────────────────┐              │
│   │                                      ROUTER                                        │              │
│   │                              (NAT / Port Forwarding)                               │              │
│   │                              Public IP: y.y.y.y                                    │              │
│   └───────────────────────────────────┬───────────────────────────────────────────────┘              │
│                                       │                                                              │
│                                       │ LAN (192.168.1.0/24)                                         │
│                    ┌──────────────────┴──────────────────┐                                           │
│                    │                                     │                                           │
│   ┌────────────────┴────────────────────┐  ┌────────────┴─────────────────────────┐                 │
│   │   🖥️ UBUNTU PC 1 (Thành viên 1)      │  │   🖥️ UBUNTU PC 2 (Thành viên 2)      │                 │
│   │                                      │  │                                      │                 │
│   │   ┌────────────────────────────┐    │  │   ┌────────────────────────────┐    │                 │
│   │   │    QUIC SERVER (Local)     │    │  │   │    QUIC CLIENT             │    │                 │
│   │   │    (quiche-server)         │    │  │   │    (quiche-client)         │    │                 │
│   │   │    Port: 4433/UDP          │◄───┼──┼───│                            │    │                 │
│   │   │    IP: 192.168.1.100       │    │  │   │    IP: 192.168.1.101       │    │                 │
│   │   └────────────────────────────┘    │  │   └────────────────────────────┘    │                 │
│   │                                      │  │                                      │                 │
│   │   ┌────────────────────────────┐    │  │   ┌────────────────────────────┐    │                 │
│   │   │    QUIC CLIENT             │    │  │   │    Wireshark               │    │                 │
│   │   │    (quiche-client)         │    │  │   │    tcpdump                 │    │                 │
│   │   │    (Self-test + Cloud)     │    │  │   │    tc (traffic control)    │    │                 │
│   │   └────────────────────────────┘    │  │   └────────────────────────────┘    │                 │
│   │                                      │  │                                      │                 │
│   │   OS: Ubuntu 22.04 LTS              │  │   OS: Ubuntu 22.04 LTS              │                 │
│   │   RAM: 4GB+ (khuyến nghị 8GB)       │  │   RAM: 4GB+ (khuyến nghị 8GB)       │                 │
│   │   Network: Ethernet + WiFi          │  │   Network: Ethernet + WiFi          │                 │
│   └──────────────────────────────────────┘  └──────────────────────────────────────┘                 │
│                                                                                                      │
│   ┌──────────────────────────────────────────────────────────────────────────────────────────────┐   │
│   │                                    DEMO SCENARIOS                                             │   │
│   │                                                                                               │   │
│   │   🔹 LOCAL DEMOS (Low latency, controlled environment):                                      │   │
│   │      ├── PC1 (Server) ↔ PC2 (Client): Stream multiplexing, HOL blocking                     │   │
│   │      ├── PC1 ↔ PC2: Connection migration (WiFi ↔ Ethernet)                                  │   │
│   │      └── PC1 ↔ PC2: Packet loss simulation với tc netem                                     │   │
│   │                                                                                               │   │
│   │   🔹 CLOUD DEMOS (Real-world latency, 0-RTT benefits):                                       │   │
│   │      ├── PC1/PC2 → Cloud Server: 0-RTT vs 1-RTT handshake (thấy rõ latency)                 │   │
│   │      ├── Cloud Server → PC1/PC2: Cross-network QUIC connection                              │   │
│   │      └── Multi-path: Local + Cloud simultaneous testing                                     │   │
│   │                                                                                               │   │
│   │   🔹 HYBRID DEMOS:                                                                           │   │
│   │      ├── PC1 as Server: Cloud VM + PC2 connect cùng lúc (multi-client)                      │   │
│   │      └── Failover testing: Local ↔ Cloud switching                                          │   │
│   └──────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Chi tiết các thành phần

#### 🖥️ Ubuntu PC 1 (Thành viên 1 - Server + Client)

| Thành phần | Chi tiết |
|------------|----------|
| **Hardware** | PC/Laptop với Ubuntu 22.04 |
| **RAM** | 4GB+ (khuyến nghị 8GB) |
| **Network** | Ethernet + WiFi (cho migration demo) |
| **IP** | 192.168.1.100 (LAN) |
| **Software** | quiche (server+client), Wireshark, tcpdump, tc |
| **Vai trò** | QUIC Server local + Client để test với Cloud |
| **Người phụ trách** | **Thành viên 1** |

#### 🖥️ Ubuntu PC 2 (Thành viên 2 - Client + Analysis)

| Thành phần | Chi tiết |
|------------|----------|
| **Hardware** | PC/Laptop với Ubuntu 22.04 |
| **RAM** | 4GB+ |
| **Network** | Ethernet + WiFi (cho migration demo) |
| **IP** | 192.168.1.101 (LAN) |
| **Software** | quiche-client, Wireshark, tcpdump, tc |
| **Vai trò** | QUIC Client + Packet analysis + Test với Cloud |
| **Người phụ trách** | **Thành viên 2** |

#### ☁️ Oracle Cloud VM (Free Tier - Cả 2 cùng quản lý)

| Thành phần | Chi tiết |
|------------|----------|
| **Provider** | Oracle Cloud Infrastructure - **Always Free Tier** |
| **Instance** | VM.Standard.E2.1.Micro (1 OCPU, 1GB RAM) |
| **OS** | Ubuntu 22.04 LTS |
| **Network** | Public IP (x.x.x.x), Security List allow UDP 4433 |
| **Software** | quiche (server+client) |
| **Vai trò** | Remote QUIC Server/Client cho real-world latency testing |
| **Người phụ trách** | **Cả 2 thành viên cùng quản lý** |

### Network Setup Options

#### Option 1: LAN + Cloud (Recommended)

```
PC1 (192.168.1.100) ─┬── LAN ──┬─ PC2 (192.168.1.101)
                     │         │
                     └── Router ─── Internet ─── Cloud VM (x.x.x.x)
```

- **Local demos**: PC1 ↔ PC2 qua LAN (fast, controlled)
- **Cloud demos**: PC1/PC2 ↔ Cloud qua Internet (real latency)

#### Option 2: Direct Cable + Cloud

```
PC1 (10.0.0.1) ──── Crossover Cable ──── PC2 (10.0.0.2)
       │                                        │
       └─────────── WiFi/LTE ───────────────────┴─── Cloud VM
```

- **Direct demos**: PC1 ↔ PC2 qua Ethernet (lowest latency)
- **Cloud demos**: Cả 2 PC connect Cloud qua WiFi/LTE

#### Option 3: WiFi Hotspot + Cloud (for Migration Demo)

```
PC1 (Hotspot: 192.168.43.1) ──── WiFi ──── PC2 (192.168.43.x)
       │                                          │
       └─ Ethernet ─┬─ Router ─── Internet ─── Cloud VM
                    │
                    └─ PC2 Ethernet (192.168.1.101)
```

- **Migration demo**: PC2 switch giữa WiFi và Ethernet
- **Cloud involved**: Cloud VM observe connection migration

---

# PHẦN A: LÝ THUYẾT VÀ NGHIÊN CỨU

---

## A1. Tổng quan về QUIC

### 🎯 Mục tiêu phần này:
> Hiểu **tại sao QUIC ra đời**, **QUIC là gì**, và **ai đang sử dụng QUIC**. Đây là nền tảng để hiểu các phần tiếp theo.

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A1.1 | Lịch sử phát triển QUIC | gQUIC (2012) → IETF QUIC (2016-2021) → RFC 9000 | Timeline document |
| A1.2 | Động lực phát triển | Tại sao cần QUIC? Vấn đề của TCP? | Analysis document |
| A1.3 | QUIC adoption statistics | Google, Cloudflare, Meta, etc. | Statistics summary |
| A1.4 | 📊 **Vẽ biểu đồ timeline** | Timeline phát triển QUIC từ 2012-2021 | **Timeline diagram** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV1</b></summary>

#### A1.1: Lịch sử phát triển QUIC
**Cần làm gì:**
- Nghiên cứu và viết tài liệu về lịch sử QUIC từ 2012 đến nay
- Các mốc quan trọng cần đề cập:
  - **2012**: Google bắt đầu phát triển gQUIC (Google QUIC)
  - **2013**: gQUIC được deploy trên Chrome và Google servers
  - **2016**: IETF Working Group thành lập, bắt đầu chuẩn hóa
  - **2018**: HTTP/3 được đặt tên (trước đó là HTTP-over-QUIC)
  - **2021**: RFC 9000, 9001, 9002 được publish → QUIC v1 chính thức
  - **2023**: RFC 9369 → QUIC v2

**Tại sao cần làm:**
- Để hiểu quá trình phát triển và motivation của QUIC
- Để biết QUIC đã được sử dụng production từ lâu, không phải công nghệ mới thử nghiệm

**Kết quả mong đợi:**
- Document 1-2 trang với timeline rõ ràng
- Có thể đưa vào báo cáo chương 1

#### A1.2: Động lực phát triển QUIC
**Cần làm gì:**
- Phân tích các vấn đề của TCP khiến Google phải phát triển QUIC:
  1. **Handshake latency**: TCP 3-way handshake + TLS handshake = nhiều RTT
  2. **Head-of-Line (HOL) blocking**: Mất 1 packet → block tất cả data
  3. **Không có Connection Migration**: Đổi IP/port = mất connection
  4. **Ossification**: TCP trong kernel, khó upgrade
  5. **Middlebox interference**: Firewall/NAT can thiệp TCP

**Tại sao cần làm:**
- Để trả lời câu hỏi quan trọng: "Tại sao không cải tiến TCP mà lại tạo protocol mới?"
- Đây là phần quan trọng khi thuyết trình

**Kết quả mong đợi:**
- Document 2-3 trang phân tích chi tiết
- Mỗi vấn đề có ví dụ minh họa

#### A1.3: QUIC Adoption Statistics
**Cần làm gì:**
- Thu thập số liệu về việc sử dụng QUIC:
  - Google: >7% of global Internet traffic
  - Cloudflare: Hỗ trợ QUIC cho tất cả websites
  - Meta (Facebook, Instagram): Dùng QUIC cho mobile apps
  - Akamai: CDN hỗ trợ QUIC
- Nguồn: W3Techs, HTTP Archive, blog posts của các công ty

**Kết quả mong đợi:**
- Bảng thống kê với số liệu cụ thể
- Có nguồn reference cho mỗi số liệu

#### A1.4: Vẽ Timeline Diagram
**Cần làm gì:**
- Sử dụng draw.io hoặc Canva vẽ timeline ngang
- Các mốc từ 2012 → 2023
- Có hình ảnh logo (Google, IETF) nếu được

**Kết quả mong đợi:**
- File PNG/SVG chất lượng cao
- Có thể in ra A4 hoặc đưa vào slides

</details>

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A1.5 | Các RFC liên quan | RFC 9000, 9001, 9002, 9114, 9369 | RFC summary |
| A1.6 | QUIC implementations | quiche, ngtcp2, quinn, etc. | Comparison table |
| A1.7 | Browser support | Chrome, Firefox, Edge, Safari | Support matrix |
| A1.8 | 📊 **Vẽ biểu đồ adoption** | Pie/Bar chart: QUIC adoption % theo platform | **Adoption chart** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV2</b></summary>

#### A1.5: Các RFC liên quan
**Cần làm gì:**
- Đọc tổng quan (Introduction, Abstract) của các RFC:
  - **RFC 9000**: QUIC: A UDP-Based Multiplexed and Secure Transport (core protocol)
  - **RFC 9001**: Using TLS to Secure QUIC (security)
  - **RFC 9002**: QUIC Loss Detection and Congestion Control
  - **RFC 9114**: HTTP/3 (HTTP over QUIC)
  - **RFC 9369**: QUIC Version 2 (improvements)

**Tại sao cần làm:**
- RFC là nguồn chính thức và authoritative nhất
- Khi cần tra cứu chi tiết, biết tìm ở RFC nào

**Kết quả mong đợi:**
- Bảng tóm tắt 5 RFC với mô tả ngắn gọn
- Ghi chú số trang quan trọng để dễ tra cứu

#### A1.6: QUIC Implementations
**Cần làm gì:**
- Nghiên cứu các implementation phổ biến:
  - **quiche** (Cloudflare, Rust): Chúng ta sẽ dùng cái này
  - **ngtcp2** (C): Được dùng trong curl
  - **quinn** (Rust): Async QUIC
  - **quic-go** (Go): Được dùng trong Caddy
  - **msquic** (Microsoft, C): Windows native
  - **lsquic** (LiteSpeed, C): Web server

**Kết quả mong đợi:**
- Bảng so sánh: Language, License, Features, Who uses

#### A1.7: Browser Support
**Cần làm gì:**
- Kiểm tra và document QUIC/HTTP/3 support:
  - **Chrome**: Enabled by default từ version nào?
  - **Firefox**: Enabled by default từ version nào?
  - **Edge**: Chromium-based, same as Chrome
  - **Safari**: iOS 15+, macOS Big Sur+
- Cách kiểm tra: `chrome://flags/#enable-quic`

**Kết quả mong đợi:**
- Support matrix với version numbers
- Screenshot của browser settings

#### A1.8: Vẽ Adoption Chart
**Cần làm gì:**
- Dùng Excel/Google Sheets hoặc Canva
- Vẽ Pie chart: % traffic QUIC vs HTTP/2 vs HTTP/1.1
- Hoặc Bar chart: Adoption % theo company

**Kết quả mong đợi:**
- Chart đẹp, có legend rõ ràng
- File PNG chất lượng cao

</details>

### 📋 Deliverables A1:
- [ ] Timeline lịch sử QUIC (TV1)
- [ ] Analysis tại sao cần QUIC (TV1)
- [ ] RFC summary table (TV2)
- [ ] Implementation comparison (TV2)
- [ ] 📊 **Timeline diagram (TV1)**
- [ ] 📊 **Adoption pie/bar chart (TV2)**

---

## A2. Kiến trúc QUIC Protocol

### 🎯 Mục tiêu phần này:
> Hiểu **cấu trúc** của QUIC protocol, **các khái niệm cơ bản** như Connection và Stream. Đây là nền tảng kỹ thuật quan trọng nhất.

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A2.1 | Protocol Stack | Application → HTTP/3 → QUIC → UDP → IP | Sơ đồ kiến trúc |
| A2.2 | So sánh với TCP/IP stack | QUIC stack vs TCP/TLS/HTTP stack | Comparison diagram |
| A2.3 | Connection concept | Connection ID, multiplexing, states | Technical document |
| A2.4 | Stream concept | Stream ID, types (bidi/unidi), states | Technical document |
| A2.5 | Đọc RFC 9000 Sections 1-5 | Overview, Versions, Streams | Ghi chú tóm tắt |
| A2.6 | 📊 **Vẽ sơ đồ Protocol Stack** | QUIC vs TCP/TLS/HTTP stack side-by-side | **Stack comparison diagram** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV1</b></summary>

#### A2.1: Protocol Stack
**Cần làm gì:**
- Vẽ sơ đồ các tầng của QUIC:
  ```
  ┌─────────────────┐
  │  Application    │  ← Ứng dụng (Browser, curl...)
  ├─────────────────┤
  │  HTTP/3         │  ← HTTP semantics
  ├─────────────────┤
  │  QUIC           │  ← Connection, Stream, Flow Control, Loss Recovery
  ├─────────────────┤
  │  TLS 1.3        │  ← Encryption (tích hợp trong QUIC)
  ├─────────────────┤
  │  UDP            │  ← Transport layer
  ├─────────────────┤
  │  IP             │  ← Network layer
  └─────────────────┘
  ```

**Điểm quan trọng cần giải thích:**
- QUIC chạy trên **UDP** thay vì TCP
- TLS 1.3 được **tích hợp** vào QUIC, không phải layer riêng
- HTTP/3 là tên mới của "HTTP over QUIC"

#### A2.2: So sánh với TCP/TLS/HTTP Stack
**Cần làm gì:**
- Vẽ 2 stack cạnh nhau để so sánh:
  ```
  QUIC Stack          vs      TCP/TLS Stack
  ─────────────              ─────────────
  HTTP/3                     HTTP/1.1 hoặc HTTP/2
  QUIC                       TLS 1.2/1.3
  UDP                        TCP
  IP                         IP
  ```

**Điểm khác biệt quan trọng:**
- TCP stack: 3 layers riêng biệt (TCP, TLS, HTTP)
- QUIC stack: Hợp nhất nhiều chức năng vào QUIC layer

#### A2.3: Connection Concept
**Cần làm gì:**
- Giải thích **Connection ID** (CID):
  - CID là identifier cho QUIC connection
  - Không dùng 4-tuple (src IP, src port, dst IP, dst port) như TCP
  - Cho phép **Connection Migration** (đổi IP vẫn giữ connection)
  - Client và Server có CID riêng

- Connection States:
  - **Handshaking**: Đang thiết lập connection
  - **Connected**: Đã kết nối, có thể transfer data
  - **Draining**: Đang đóng connection
  - **Closed**: Đã đóng

#### A2.4: Stream Concept
**Cần làm gì:**
- Giải thích **Stream** trong QUIC:
  - Stream là **lightweight channel** trong 1 connection
  - Mỗi connection có thể có **nhiều streams** đồng thời
  - Streams **độc lập** nhau (không HOL blocking)

- Stream ID Encoding:
  ```
  Bit 0: Client (0) / Server (1) initiated
  Bit 1: Bidirectional (0) / Unidirectional (1)
  
  Ví dụ:
  - Stream ID 0: Client-initiated, Bidirectional
  - Stream ID 1: Server-initiated, Bidirectional
  - Stream ID 2: Client-initiated, Unidirectional
  - Stream ID 3: Server-initiated, Unidirectional
  ```

#### A2.5: Đọc RFC 9000
**Cần làm gì:**
- Đọc các sections sau của RFC 9000:
  - **Section 1**: Introduction (tổng quan)
  - **Section 2**: Streams (quan trọng!)
  - **Section 3**: Stream States
  - **Section 4**: Flow Control
  - **Section 5**: Connections

**Tips khi đọc RFC:**
- Không cần đọc hết, tập trung vào concepts
- Ghi chú những điểm quan trọng
- Mark những phần không hiểu để thảo luận với teammate

#### A2.6: Vẽ Stack Comparison Diagram
**Cần làm gì:**
- Dùng draw.io vẽ sơ đồ so sánh
- 2 columns: QUIC Stack và TCP Stack
- Dùng màu khác nhau cho từng layer
- Có arrows chỉ data flow

**Kết quả mong đợi:**
- File PNG/SVG chất lượng cao
- Có thể dùng trong báo cáo và slides

</details>

### 📋 Deliverables A2:
- [ ] QUIC Protocol Stack diagram (TV1)
- [ ] Stack comparison diagram (TV1)
- [ ] Connection/Stream concepts document (TV1)
- [ ] 📊 **Stack comparison visual diagram (TV1)**

---

## A3. Packet và Frame Structure

### 🎯 Mục tiêu phần này:
> Hiểu **cấu trúc chi tiết** của QUIC packets và frames. Đây là phần kỹ thuật quan trọng để hiểu cách QUIC hoạt động ở mức byte-level.

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A3.1 | Long Header Packets | Initial, 0-RTT, Handshake, Retry | Diagrams + Table |
| A3.2 | Short Header Packets | 1-RTT packets, format | Diagrams |
| A3.3 | Packet Number Spaces | Initial, Handshake, Application | Document |
| A3.4 | Frame Types | STREAM, ACK, CRYPTO, MAX_DATA, etc. | Complete table |
| A3.5 | STREAM Frame chi tiết | Format, flags, offset, length | Technical document |
| A3.6 | ACK Frame chi tiết | ACK ranges, ECN counts | Technical document |
| A3.7 | CRYPTO Frame | TLS handshake messages | Document |
| A3.8 | Flow Control Frames | MAX_DATA, MAX_STREAM_DATA, etc. | Document |
| A3.9 | Đọc RFC 9000 Sections 12-19 | Packet/Frame formats | Ghi chú |
| A3.10 | 📊 **Vẽ sơ đồ Packet/Frame** | Diagram các loại packet và frame structure | **Packet/Frame diagrams** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV2</b></summary>

#### A3.1: Long Header Packets
**Cần làm gì:**
- Nghiên cứu và document 4 loại Long Header packets:

1. **Initial Packet**: Packet đầu tiên trong handshake
   - Chứa CRYPTO frame (TLS ClientHello)
   - Encrypted với Initial keys (derived từ Destination CID)
   
2. **0-RTT Packet**: Early data packet
   - Gửi data trước khi handshake hoàn thành
   - Dùng PSK (Pre-Shared Key) từ session trước
   
3. **Handshake Packet**: Tiếp tục handshake
   - Chứa CRYPTO frame (TLS messages)
   - Encrypted với Handshake keys
   
4. **Retry Packet**: Server yêu cầu retry
   - Dùng cho address validation
   - Chứa Retry Token

**Cấu trúc Long Header:**
```
Long Header Format:
+-+-+-+-+-+-+-+-+
|1|1|T T|X X X X|    1 bit: Header Form (1=Long), 1 bit: Fixed, 2 bits: Type, 4 bits: Type-specific
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                         Version (32)                          |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| DCID Len (8)  |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|               Destination Connection ID (0..160)              |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| SCID Len (8)  |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Source Connection ID (0..160)                 |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

#### A3.2: Short Header Packets (1-RTT)
**Cần làm gì:**
- Document cấu trúc Short Header:
  - Dùng sau khi handshake hoàn thành
  - Header nhỏ gọn hơn Long Header
  - Chỉ có Destination CID (không có Source CID)

**Cấu trúc Short Header:**
```
Short Header Format:
+-+-+-+-+-+-+-+-+
|0|1|S|R|R|K|P P|    1 bit: Header Form (0=Short), 1 bit: Fixed, các bit khác
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Destination Connection ID (*)                 |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                      Packet Number (8/16/24/32)               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                          Payload (*)                          |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

#### A3.3: Packet Number Spaces
**Cần làm gì:**
- Giải thích 3 Packet Number Spaces:
  1. **Initial**: Cho Initial packets
  2. **Handshake**: Cho Handshake packets
  3. **Application Data**: Cho 0-RTT và 1-RTT packets

**Tại sao có 3 spaces:**
- Mỗi space có ACK riêng
- Tránh confusion giữa các loại packets
- Loss recovery riêng biệt

#### A3.4: Frame Types
**Cần làm gì:**
- Tạo bảng tất cả Frame Types trong QUIC:

| Frame Type | Value | Mô tả |
|------------|-------|-------|
| PADDING | 0x00 | Padding bytes |
| PING | 0x01 | Keep-alive |
| ACK | 0x02-0x03 | Acknowledgment |
| RESET_STREAM | 0x04 | Reset a stream |
| STOP_SENDING | 0x05 | Stop sending on stream |
| CRYPTO | 0x06 | TLS data |
| NEW_TOKEN | 0x07 | New token for 0-RTT |
| STREAM | 0x08-0x0f | Stream data |
| MAX_DATA | 0x10 | Connection flow control |
| MAX_STREAM_DATA | 0x11 | Stream flow control |
| MAX_STREAMS | 0x12-0x13 | Stream count limit |
| DATA_BLOCKED | 0x14 | Connection blocked |
| STREAM_DATA_BLOCKED | 0x15 | Stream blocked |
| STREAMS_BLOCKED | 0x16-0x17 | Stream limit blocked |
| NEW_CONNECTION_ID | 0x18 | New CID |
| RETIRE_CONNECTION_ID | 0x19 | Retire CID |
| PATH_CHALLENGE | 0x1a | Path validation |
| PATH_RESPONSE | 0x1b | Path validation response |
| CONNECTION_CLOSE | 0x1c-0x1d | Close connection |
| HANDSHAKE_DONE | 0x1e | Handshake complete |

#### A3.5-A3.8: Chi tiết các Frame quan trọng
**STREAM Frame:**
- Chứa application data
- Có flags: FIN, LEN, OFF
- Stream ID, Offset, Length, Data

**ACK Frame:**
- Acknowledge received packets
- ACK Ranges: Cho phép ACK nhiều packets với gaps
- ECN counts (optional)

**CRYPTO Frame:**
- Chứa TLS handshake messages
- Offset + Length + Crypto Data

#### A3.10: Vẽ Diagrams
**Cần làm gì:**
- Dùng draw.io vẽ:
  1. Long Header structure
  2. Short Header structure
  3. STREAM Frame structure
  4. ACK Frame structure

</details>

### 📋 Deliverables A3:
- [ ] Packet Types diagram (TV2)
- [ ] Complete Frame Types table (TV2)
- [ ] STREAM/ACK Frame analysis (TV2)
- [ ] 📊 **Packet structure diagrams (TV2)**

---

## A4. Connection Establishment (0-RTT/1-RTT)

### 🎯 Mục tiêu phần này:
> Hiểu **handshake process** của QUIC - đây là **điểm mạnh nổi bật nhất** của QUIC so với TCP+TLS. Đặc biệt quan trọng là 0-RTT handshake.

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A4.1 | Initial Handshake | Initial packets, CRYPTO frames | Sequence diagram |
| A4.2 | 1-RTT Handshake chi tiết | Full handshake flow | Detailed sequence |
| A4.3 | 0-RTT Early Data | PSK, session resumption | Sequence diagram |
| A4.4 | TLS 1.3 Integration | Không dùng TLS record layer | Technical document |
| A4.5 | Encryption Levels | Initial, Handshake, 1-RTT, 0-RTT | Document + Diagram |
| A4.6 | Key Derivation | HKDF, traffic secrets | Crypto document |
| A4.7 | Address Validation | Token, Retry mechanism | Security document |
| A4.8 | Version Negotiation | Version selection process | Document |
| A4.9 | 0-RTT Security | Replay attack mitigation | Security analysis |
| A4.10 | Đọc RFC 9001 | Using TLS to Secure QUIC | Ghi chú |
| A4.11 | 📊 **Vẽ timing diagram** | So sánh thời gian: TCP+TLS vs QUIC 1-RTT vs 0-RTT | **Timing comparison chart** |
| A4.12 | 📊 **Vẽ sequence diagram** | Sequence diagram chi tiết cho handshake flows | **Handshake sequence diagrams** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV1 (QUAN TRỌNG!)</b></summary>

#### A4.1 & A4.2: 1-RTT Handshake
**Cần làm gì:**
- Hiểu và vẽ sequence diagram cho QUIC 1-RTT handshake:

```
Client                                    Server
   |                                         |
   |  Initial[CRYPTO: ClientHello]           |
   |---------------------------------------->|  (1)
   |                                         |
   |       Initial[CRYPTO: ServerHello...]   |
   |       Handshake[CRYPTO: EncryptedExts]  |
   |       Handshake[CRYPTO: Certificate]    |
   |       Handshake[CRYPTO: CertVerify]     |
   |       Handshake[CRYPTO: Finished]       |
   |<----------------------------------------|  (2)
   |                                         |
   |  Handshake[CRYPTO: Finished]            |
   |  1-RTT[STREAM: Application Data]  ←──── Data có thể gửi ngay!
   |---------------------------------------->|  (3)
   |                                         |
   |       1-RTT[STREAM: Response Data]      |
   |       HANDSHAKE_DONE                    |
   |<----------------------------------------|  (4)
```

**Điểm quan trọng:**
- **1 RTT** = Client gửi Initial → Server reply → **Client có thể gửi data**
- So sánh với TCP+TLS 1.3: 
  - TCP SYN → SYN-ACK → ACK (1 RTT cho TCP)
  - TLS ClientHello → ServerHello...Finished → Finished (1 RTT cho TLS)
  - **Tổng: 2 RTT** mới gửi được data
- QUIC kết hợp cả 2: **1 RTT** tổng cộng!

#### A4.3: 0-RTT Early Data
**Cần làm gì:**
- Hiểu và vẽ 0-RTT handshake:

```
Client                                    Server
   |                                         |
   |  Initial[CRYPTO: ClientHello]           |
   |  0-RTT[STREAM: Early Data]  ←────────── Data gửi CÙNG LÚC với handshake!
   |---------------------------------------->|  (1)
   |                                         |
   |       Initial[CRYPTO: ServerHello...]   |
   |       Handshake[CRYPTO: ...]            |
   |       1-RTT[STREAM: Response]           |
   |<----------------------------------------|  (2)
```

**Yêu cầu cho 0-RTT:**
- Client đã từng connect tới Server trước đó
- Server gửi **NEW_TOKEN** frame hoặc TLS session ticket
- Client lưu lại và dùng cho lần sau

**Ưu điểm:**
- Data gửi **ngay lập tức** không cần đợi handshake
- Với high-latency networks (100ms RTT), tiết kiệm 100-200ms!

**Nhược điểm (Security):**
- 0-RTT data có thể bị **replay attack**
- Chỉ nên dùng cho **idempotent requests** (GET, không phải POST payment)

#### A4.4: TLS 1.3 Integration
**Cần làm gì:**
- Giải thích cách QUIC tích hợp TLS 1.3:
  - **Không dùng TLS record layer**: TLS messages đặt trực tiếp trong CRYPTO frames
  - **Header protection**: QUIC header được encrypt thêm
  - **Separate packet protection**: Mỗi packet được encrypt riêng với AEAD

**Tại sao không dùng TLS record layer:**
- TLS record layer được thiết kế cho TCP (byte stream)
- QUIC là packet-based, không cần record layer
- Giảm overhead

#### A4.5: Encryption Levels
**Cần làm gì:**
- Document 4 encryption levels:

| Level | Keys derived from | Used for |
|-------|-------------------|----------|
| **Initial** | Destination Connection ID | Initial packets |
| **0-RTT** | TLS early_traffic_secret | 0-RTT packets |
| **Handshake** | TLS handshake_traffic_secret | Handshake packets |
| **1-RTT** | TLS traffic_secret | 1-RTT packets |

#### A4.9: 0-RTT Security Analysis
**Cần làm gì (QUAN TRỌNG cho báo cáo):**
- Phân tích **replay attack risk**:
  - Attacker có thể capture và replay 0-RTT packets
  - Server không thể detect replay (stateless)
  
- Mitigation strategies:
  - Chỉ accept 0-RTT cho idempotent requests
  - Server-side replay detection (với trade-off stateful)
  - Limited time window cho 0-RTT acceptance

- Viết 1-2 trang phân tích security

#### A4.11 & A4.12: Vẽ Diagrams
**Timing Comparison Diagram:**
```
TCP + TLS 1.3:
Client ──SYN────────────────> Server
       <───────────SYN-ACK──
       ──ACK, ClientHello──>
       <─ServerHello...Fin──
       ──Finished, DATA────>          Total: 2 RTT before DATA

QUIC 1-RTT:
Client ──Initial[ClientHello]────> Server
       <─Initial,Handshake,1-RTT──
       ──Handshake,1-RTT[DATA]───>    Total: 1 RTT before DATA

QUIC 0-RTT:
Client ──Initial,0-RTT[DATA]─────> Server
       <─All responses──────────      Total: 0 RTT before DATA!
```

</details>

### 📋 Deliverables A4:
- [ ] 1-RTT Handshake sequence diagram (TV1)
- [ ] 0-RTT sequence diagram (TV1)
- [ ] TLS 1.3 integration document (TV1)
- [ ] 0-RTT security analysis (TV1)
- [ ] 📊 **Timing comparison chart: TCP vs QUIC (TV1)**
- [ ] 📊 **Detailed handshake sequence diagrams (TV1)**

---

## A5. Stream Multiplexing

### 🎯 Mục tiêu phần này:
> Hiểu **Stream Multiplexing** và **Head-of-Line (HOL) Blocking Problem** - đây là **điểm mạnh thứ 2** của QUIC sau 0-RTT.

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A5.1 | Stream Types | Client/Server initiated, Bidi/Unidi | Document |
| A5.2 | Stream ID Encoding | Bits 0-1 meaning, numbering | Technical document |
| A5.3 | Stream States | Ready, Send, Data Sent, Reset Sent, etc. | State diagram |
| A5.4 | Stream Prioritization | Priority, dependency (optional) | Document |
| A5.5 | HOL Blocking Problem | Tại sao TCP có HOL? | Explanation + Diagram |
| A5.6 | QUIC giải quyết HOL | Stream independence | Explanation + Diagram |
| A5.7 | Stream Concurrency | MAX_STREAMS frame | Document |
| A5.8 | Đọc RFC 9000 Section 2 | Streams | Ghi chú |
| A5.9 | 📊 **Vẽ HOL blocking diagram** | So sánh trực quan TCP HOL vs QUIC no-HOL | **HOL comparison diagram** |
| A5.10 | 📊 **Vẽ Stream state diagram** | State machine cho QUIC streams | **State machine diagram** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV2 (QUAN TRỌNG!)</b></summary>

#### A5.5: HOL Blocking Problem (QUAN TRỌNG - phải hiểu rõ!)
**Head-of-Line Blocking là gì?**

Trong **TCP**, tất cả data được coi là 1 byte stream duy nhất. Khi một packet bị mất:
```
TCP Scenario (HTTP/2 over TCP):
┌─────────────────────────────────────────────────────────────┐
│ TCP Byte Stream (single ordered sequence)                   │
│                                                             │
│  Packet 1     Packet 2     Packet 3     Packet 4            │
│  [Stream A]   [Stream B]   [Stream A]   [Stream C]          │
│     ✓           ✗ LOST        ✓            ✓                │
│                                                             │
│  Application Layer nhận được:                               │
│  Stream A: chờ... (blocked vì Packet 2 chưa tới)           │
│  Stream B: chờ... (data bị mất)                            │
│  Stream C: chờ... (blocked vì phải đợi Stream A, B)        │
│                                                             │
│  Tất cả streams đều BLOCKED vì 1 packet mất!               │
└─────────────────────────────────────────────────────────────┘
```

**Tại sao HTTP/2 vẫn bị HOL blocking?**
- HTTP/2 có multiplexing ở application layer
- Nhưng vẫn chạy trên TCP
- TCP đảm bảo ordered delivery → 1 packet mất = tất cả blocked

#### A5.6: QUIC giải quyết HOL
**Trong QUIC**, mỗi stream là **độc lập**:
```
QUIC Scenario:
┌─────────────────────────────────────────────────────────────┐
│ QUIC Streams (independent streams)                          │
│                                                             │
│  Packet 1     Packet 2     Packet 3     Packet 4            │
│  [Stream A]   [Stream B]   [Stream A]   [Stream C]          │
│     ✓           ✗ LOST        ✓            ✓                │
│                                                             │
│  Application Layer nhận được:                               │
│  Stream A: ✓ Packet 1 + ✓ Packet 3 → có thể xử lý ngay!    │
│  Stream B: chờ retransmit (CHỈ Stream B bị blocked)         │
│  Stream C: ✓ Packet 4 → có thể xử lý ngay!                 │
│                                                             │
│  Chỉ Stream B bị blocked, A và C không bị ảnh hưởng!       │
└─────────────────────────────────────────────────────────────┘
```

**Key insight:**
- QUIC streams là **độc lập** (independent)
- Packet loss trên 1 stream **không ảnh hưởng** streams khác
- Đây là lý do QUIC tốt hơn HTTP/2 over TCP trong điều kiện lossy networks

#### A5.1: Stream Types
**4 loại streams:**

| Stream Type | Bit 0 | Bit 1 | Initiated by | Direction |
|-------------|-------|-------|--------------|-----------|
| 0x0 | 0 | 0 | Client | Bidirectional |
| 0x1 | 1 | 0 | Server | Bidirectional |
| 0x2 | 0 | 1 | Client | Unidirectional |
| 0x3 | 1 | 1 | Server | Unidirectional |

**Ví dụ Stream IDs:**
- 0, 4, 8, 12, ... : Client-initiated bidirectional
- 1, 5, 9, 13, ... : Server-initiated bidirectional
- 2, 6, 10, 14, ... : Client-initiated unidirectional
- 3, 7, 11, 15, ... : Server-initiated unidirectional

#### A5.3: Stream States
**Vẽ State Diagram cho QUIC Stream:**

```
          ┌───────────┐
          │   Idle    │
          └─────┬─────┘
                │ open (send/receive)
                ▼
          ┌───────────┐
          │   Open    │
          └─────┬─────┘
                │
    ┌───────────┼───────────┐
    │           │           │
    ▼           ▼           ▼
┌───────┐  ┌────────┐  ┌───────────┐
│ Send  │  │  Both  │  │  Receive  │
│  ↓    │  │   ↓    │  │     ↓     │
│ Data  │  │  Data  │  │   Data    │
│ Sent  │  │  Both  │  │  Received │
└───┬───┘  └────┬───┘  └─────┬─────┘
    │           │            │
    └───────────┼────────────┘
                │ FIN
                ▼
          ┌───────────┐
          │  Closed   │
          └───────────┘
```

#### A5.9: Vẽ HOL Blocking Diagram
**Cần vẽ 2 diagrams so sánh:**
1. **TCP + HTTP/2**: Tất cả streams blocked khi 1 packet mất
2. **QUIC**: Chỉ affected stream bị blocked

**Tips:**
- Dùng màu khác nhau cho mỗi stream
- Dùng X đỏ để mark packet loss
- Dùng mũi tên để show data flow
- Highlight sự khác biệt quan trọng

</details>

### 📋 Deliverables A5:
- [ ] Stream types document (TV2)
- [ ] Stream state diagram (TV2)
- [ ] HOL blocking explanation (TV2)
- [ ] 📊 **HOL blocking comparison diagram (TV2)**
- [ ] 📊 **Stream state machine diagram (TV2)**

---

## A6. Connection Migration

### 🎯 Mục tiêu phần này:
> Hiểu **Connection Migration** - **đặc điểm độc đáo (unique feature)** mà TCP không có. Cho phép connection tồn tại khi đổi network.

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A6.1 | Connection ID | Format, purpose, multiple CIDs | Document |
| A6.2 | CID Rotation | NEW_CONNECTION_ID, RETIRE_CONNECTION_ID | Technical document |
| A6.3 | Path Validation | PATH_CHALLENGE, PATH_RESPONSE | Sequence diagram |
| A6.4 | NAT Rebinding | Handling NAT timeout | Document |
| A6.5 | Active Migration | Client-initiated migration | Document |
| A6.6 | Passive Migration | Server detects address change | Document |
| A6.7 | Migration Security | Off-path attack prevention | Security analysis |
| A6.8 | Đọc RFC 9000 Section 9 | Connection Migration | Ghi chú |
| A6.9 | 📊 **Vẽ migration sequence** | Sequence diagram cho connection migration process | **Migration sequence diagram** |

<details>
<summary><b>📖 Hướng dẫn chi tiết cho TV1</b></summary>

#### Tại sao Connection Migration quan trọng?
**Vấn đề với TCP:**
- TCP connection được identify bằng **4-tuple**: (src IP, src port, dst IP, dst port)
- Khi thay đổi network (WiFi → 4G, hoặc đổi WiFi network) → IP thay đổi
- 4-tuple thay đổi → **Connection bị drop** → phải reconnect

**QUIC giải quyết:**
- Connection được identify bằng **Connection ID (CID)**, không phải IP/port
- Khi IP thay đổi, CID giữ nguyên → **Connection vẫn tồn tại**
- Data transfer tiếp tục không bị gián đoạn

#### A6.1: Connection ID
**Cần làm gì:**
- Giải thích Connection ID:
  - CID là opaque byte string (max 20 bytes)
  - Client và Server có CID riêng (Source CID, Destination CID)
  - Mỗi endpoint có thể có **nhiều CIDs** active cùng lúc

```
TCP Identification:
┌────────────────────────────────────────────────────┐
│  (192.168.1.100, 54321, 10.0.0.1, 443)            │
│  Change IP → Different 4-tuple → Connection lost! │
└────────────────────────────────────────────────────┘

QUIC Identification:
┌────────────────────────────────────────────────────┐
│  Connection ID: 0x1234567890abcdef                │
│  Change IP → CID unchanged → Connection survives!  │
└────────────────────────────────────────────────────┘
```

#### A6.3: Path Validation
**Cần làm gì:**
- Vẽ sequence diagram cho path validation:

```
Client (new IP)                           Server
       |                                     |
       |  Packet from new address            |
       |  [Application data]                 |
       |------------------------------------>|
       |                                     | (Server detects address change)
       |                                     |
       |  PATH_CHALLENGE(random_data)        |
       |<------------------------------------|
       |                                     |
       |  PATH_RESPONSE(same_random_data)    |
       |------------------------------------>|
       |                                     | (Server validates new path)
       |                                     |
       |  Continue communication             |
       |<----------------------------------->|
```

**Tại sao cần Path Validation:**
- Tránh **off-path attacks**: Attacker không thể redirect traffic
- Xác nhận client thực sự ở địa chỉ mới

#### A6.5 & A6.6: Active vs Passive Migration
**Active Migration (Client-initiated):**
- Client chủ động migrate (ví dụ: app biết sẽ đổi network)
- Client gửi data từ new address
- Server responds với PATH_CHALLENGE

**Passive Migration (Server detects):**
- Server nhận được packet từ new address
- Server trigger path validation
- Ví dụ: NAT rebinding (NAT gán port mới)

</details>

### 📋 Deliverables A6:
- [ ] Connection ID document (TV1)
- [ ] Path Validation sequence (TV1)
- [ ] Migration types comparison (TV1)
- [ ] 📊 **Migration sequence diagram (TV1)**

---

## A7. Flow Control

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A7.1 | Connection-level Flow Control | MAX_DATA frame | Document |
| A7.2 | Stream-level Flow Control | MAX_STREAM_DATA frame | Document |
| A7.3 | Credit-based System | How flow control works | Explanation |
| A7.4 | DATA_BLOCKED, STREAM_DATA_BLOCKED | When sender is blocked | Document |
| A7.5 | Initial Limits | Transport parameters | Document |
| A7.6 | Flow Control Tuning | Performance implications | Analysis |
| A7.7 | Đọc RFC 9000 Section 4 | Flow Control | Ghi chú |
| A7.8 | 📊 **Vẽ flow control diagram** | Diagram credit-based flow control mechanism | **Flow control visual diagram** |

### 📋 Deliverables A7:
- [ ] Flow Control mechanism document (TV2)
- [ ] Connection vs Stream flow control diagram (TV2)
- [ ] 📊 **Flow control visual diagram (TV2)**

---

## A8. Loss Detection & Congestion Control

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A8.1 | ACK Mechanism | ACK frame, ACK ranges | Technical document |
| A8.2 | Packet Number | Strictly increasing, never reused | Document |
| A8.3 | Loss Detection | Time-based, packet-based | Algorithm document |
| A8.4 | RTT Estimation | min_rtt, smoothed_rtt, rttvar | Technical document |
| A8.5 | PTO (Probe Timeout) | Replacing RTO | Document |
| A8.6 | Congestion Control | CUBIC, NewReno default | Algorithm overview |
| A8.7 | BBR Support | Optional, better for some cases | Document |
| A8.8 | ECN Support | Explicit Congestion Notification | Document |
| A8.9 | Đọc RFC 9002 | Loss Detection and Congestion Control | Ghi chú |
| A8.10 | 📊 **Vẽ congestion window graph** | Graph cwnd theo thời gian (CUBIC vs NewReno) | **Congestion control chart** |
| A8.11 | 📊 **Vẽ RTT estimation diagram** | Diagram RTT calculation | **RTT estimation diagram** |

### 📋 Deliverables A8:
- [ ] ACK mechanism document (TV1)
- [ ] Loss detection algorithm (TV1)
- [ ] Congestion control overview (TV1)
- [ ] 📊 **Congestion window graph (TV1)**
- [ ] 📊 **RTT estimation diagram (TV1)**

---

## A9. Security (TLS 1.3 Integration)

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A9.1 | TLS 1.3 trong QUIC | Không dùng TLS record layer | Document |
| A9.2 | CRYPTO Frame | Carries TLS messages | Technical document |
| A9.3 | Header Protection | Packet number encryption | Document |
| A9.4 | Payload Encryption | AEAD (AES-GCM, ChaCha20) | Document |
| A9.5 | Key Update | Updating encryption keys | Technical document |
| A9.6 | Certificate Handling | Server authentication | Document |
| A9.7 | Anti-Amplification | Address validation, Retry | Security document |
| A9.8 | Đọc RFC 9001 | Using TLS to Secure QUIC | Ghi chú |

### 📋 Deliverables A9:
- [ ] TLS 1.3 integration document (TV2)
- [ ] Header/Payload protection document (TV2)
- [ ] Security mechanisms overview (TV2)

---

## A10. HTTP/3 over QUIC

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| A10.1 | HTTP/3 Overview | HTTP semantics over QUIC | Document |
| A10.2 | Stream Mapping | Request/Response streams | Diagram |
| A10.3 | QPACK | Header compression | Technical document |
| A10.4 | Server Push | Push promises in HTTP/3 | Document |
| A10.5 | So sánh HTTP/2 vs HTTP/3 | Performance, features | Comparison table |
| A10.6 | Đọc RFC 9114 | HTTP/3 | Ghi chú |

### 📋 Deliverables A10:
- [ ] HTTP/3 overview document (TV1)
- [ ] HTTP/2 vs HTTP/3 comparison (TV1)

---

## A11. So sánh QUIC vs TCP+TLS

### Công việc của cả 2 thành viên:

| STT | Công việc | Thành viên | Output |
|-----|-----------|------------|--------|
| A11.1 | Handshake latency comparison | TV1 | Comparison table |
| A11.2 | HOL blocking comparison | TV2 | Diagram + Explanation |
| A11.3 | Migration capability | TV1 | Feature comparison |
| A11.4 | Security comparison | TV2 | Security analysis |
| A11.5 | Performance comparison | TV1 | Data from papers |
| A11.6 | Deployment comparison | TV2 | Pros/Cons analysis |
| A11.7 | Tạo bảng so sánh tổng hợp | Cả 2 | Final comparison table |
| A11.8 | Vẽ infographic | TV2 | Visual comparison |
| A11.9 | 📊 **Vẽ bar chart so sánh** | Bar chart so sánh latency, throughput các protocol | **Performance comparison bar chart** |
| A11.10 | 📊 **Vẽ radar chart** | Radar chart so sánh features | **Feature radar chart** |

### 📊 Bảng So sánh Tổng hợp:

| Feature | TCP + TLS 1.2 | TCP + TLS 1.3 | QUIC |
|---------|---------------|---------------|------|
| **New Connection** | 3 RTT | 2 RTT | **1 RTT** |
| **Resumed Connection** | 2 RTT | 1 RTT | **0 RTT** |
| **HOL Blocking** | Yes (TCP level) | Yes (TCP level) | **No** |
| **Connection Migration** | No | No | **Yes** |
| **Built-in Encryption** | Separate | Separate | **Integrated** |
| **User-space Implementation** | No (kernel) | No (kernel) | **Yes** |
| **Multiplexing** | At app layer | At app layer | **Native** |
| **Loss Recovery** | RTO-based | RTO-based | **PTO-based** |

### 📋 Deliverables A11:
- [ ] Complete comparison table (Cả 2)
- [ ] Infographic (TV2)
- [ ] 📊 **Performance comparison bar chart (TV1)**
- [ ] 📊 **Feature radar chart (TV2)**

---

# PHẦN B: THỰC HÀNH VÀ DEMO

---

## B1. Setup Topology

### Công việc của Thành viên 1 (Setup Server):

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B1.1 | Install Ubuntu 22.04 | Clean install hoặc existing | Working OS |
| B1.2 | Install dependencies | build-essential, cmake, openssl, etc. | Script |
| B1.3 | Install Rust | rustup | Working Rust |
| B1.4 | Clone và build quiche | Cloudflare QUIC implementation | Working quiche |
| B1.5 | Generate certificates | Self-signed SSL certs | cert.pem, key.pem |
| B1.6 | Create test files | index.html, small/medium/large files | Test content |
| B1.7 | Configure firewall | UFW allow 4433/udp | Open port |
| B1.8 | Test server locally | quiche-server running | Working server |
| B1.9 | Document setup | Step-by-step guide | Setup guide |

### Công việc của Thành viên 2 (Setup Client):

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B1.10 | Install Ubuntu 22.04 | Clean install hoặc existing | Working OS |
| B1.11 | Install dependencies | build-essential, cmake, openssl, etc. | Script |
| B1.12 | Install Rust | rustup | Working Rust |
| B1.13 | Clone và build quiche | quiche-client | Working client |
| B1.14 | Install Wireshark | Packet capture tool | Working Wireshark |
| B1.15 | Install tc (iproute2) | Traffic control for demos | Working tc |
| B1.16 | Configure network | Connect to PC1 | Network ready |
| B1.17 | Test connectivity | Ping, basic QUIC connection | Connection verified |
| B1.18 | Document setup | Step-by-step guide | Setup guide |

### 📋 Setup Scripts:

#### setup_server.sh (PC1)
```bash
#!/bin/bash
echo "=== Setting up QUIC Server on Ubuntu PC1 ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    wireshark tshark tcpdump curl git iproute2 net-tools

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

# Create directories
mkdir -p ~/quic-demo/{certs,www,captures,logs}

# Generate certificates
openssl req -x509 -newkey rsa:2048 \
  -keyout ~/quic-demo/certs/key.pem \
  -out ~/quic-demo/certs/cert.pem \
  -days 365 -nodes \
  -subj "/CN=quic-demo-server"

# Create test files
echo "<h1>QUIC Demo Server</h1><p>Hello from PC1!</p>" > ~/quic-demo/www/index.html
dd if=/dev/urandom of=~/quic-demo/www/small.bin bs=100K count=1     # 100KB
dd if=/dev/urandom of=~/quic-demo/www/medium.bin bs=1M count=10     # 10MB
dd if=/dev/urandom of=~/quic-demo/www/large.bin bs=1M count=100     # 100MB

# Multiple files for multiplexing test
for i in {1..5}; do
  dd if=/dev/urandom of=~/quic-demo/www/file$i.bin bs=1M count=5
done

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

#### setup_client.sh (PC2)
```bash
#!/bin/bash
echo "=== Setting up QUIC Client on Ubuntu PC2 ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    wireshark tshark tcpdump curl git iproute2 net-tools

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

# Create directories
mkdir -p ~/quic-demo/{captures,logs,downloads}

echo "=== Client Setup Complete ==="
echo ""
echo "Test connection with:"
echo "cd ~/quiche && ./target/release/examples/quiche-client \\"
echo "  --no-verify https://SERVER_IP:4433/index.html"
echo ""
echo "Replace SERVER_IP with PC1's IP address (e.g., 192.168.1.100)"
```

#### setup_cloud.sh (Oracle Cloud VM - Cả 2 cùng setup)
```bash
#!/bin/bash
echo "=== Setting up QUIC Server/Client on Oracle Cloud VM ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    curl git iproute2 net-tools

# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env

# Clone and build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

# Create directories
mkdir -p ~/quic-demo/{certs,www,captures,logs}

# Generate certificates
openssl req -x509 -newkey rsa:2048 \
  -keyout ~/quic-demo/certs/key.pem \
  -out ~/quic-demo/certs/cert.pem \
  -days 365 -nodes \
  -subj "/CN=quic-cloud-server"

# Create test files
echo "<h1>QUIC Cloud Server</h1><p>Hello from Oracle Cloud!</p>" > ~/quic-demo/www/index.html
dd if=/dev/urandom of=~/quic-demo/www/small.bin bs=100K count=1
dd if=/dev/urandom of=~/quic-demo/www/medium.bin bs=1M count=10

# Note: Configure Oracle Cloud Security List to allow UDP 4433 inbound

echo "=== Cloud Setup Complete ==="
echo ""
echo "IMPORTANT: Configure Oracle Cloud Security List:"
echo "  - Allow Ingress UDP port 4433 from 0.0.0.0/0 (hoặc giới hạn IP nếu cần bảo mật)"
echo ""
echo "Start server with:"
echo "cd ~/quiche && ./target/release/examples/quiche-server \\"
echo "  --cert ~/quic-demo/certs/cert.pem \\"
echo "  --key ~/quic-demo/certs/key.pem \\"
echo "  --root ~/quic-demo/www \\"
echo "  --listen 0.0.0.0:4433"
echo ""
echo "Test from local PCs with:"
echo "./quiche-client --no-verify https://CLOUD_PUBLIC_IP:4433/index.html"
```

### Oracle Cloud Setup Guide (Cả 2 cùng làm)

#### Bước 1: Tạo Oracle Cloud Account (Free Tier)
1. Truy cập https://www.oracle.com/cloud/free/
2. Đăng ký tài khoản (cần credit card để xác minh, sẽ có authorization hold nhỏ ~$1 và được hoàn lại)
3. Chọn region gần nhất (e.g., Singapore, Tokyo)

#### Bước 2: Tạo VM Instance
1. Go to Compute → Instances → Create Instance
2. Chọn **VM.Standard.E2.1.Micro** (Always Free)
3. Chọn **Ubuntu 22.04** image
4. Chọn **Assign public IP address**
5. Download SSH key pair
6. Create instance

#### Bước 3: Configure Security List
1. Go to Networking → Virtual Cloud Networks
2. Click VCN → Security Lists → Default Security List
3. Add Ingress Rule:
   - Source: `0.0.0.0/0` (hoặc giới hạn theo IP của bạn để bảo mật hơn)
   - Protocol: `UDP`
   - Destination Port: `4433`
4. Save

> ⚠️ **Lưu ý bảo mật**: Để an toàn hơn, có thể giới hạn Source IP thay vì 0.0.0.0/0

#### Bước 4: SSH và Setup
```bash
# Đảm bảo SSH key có quyền đúng
chmod 600 ~/oracle_key.pem

# SSH từ PC1 hoặc PC2
ssh -i ~/oracle_key.pem ubuntu@CLOUD_PUBLIC_IP

# Chạy setup script
./setup_cloud.sh
```

### 📋 Deliverables B1:
- [ ] Working QUIC Server on PC1 (TV1)
- [ ] Working QUIC Client on PC2 (TV2)
- [ ] Working QUIC Server/Client on Cloud VM (Cả 2)
- [ ] Network connectivity verified: PC1↔PC2, PC1↔Cloud, PC2↔Cloud (Cả 2)
- [ ] Setup scripts documented (Cả 2)

---

## B2. Demo 1: Handshake Comparison

### Mục tiêu: Chứng minh QUIC handshake nhanh hơn TCP+TLS

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B2.1 | Setup TCP+TLS server | nginx với HTTPS | Comparison baseline |
| B2.2 | Đo TCP+TLS 1.2 handshake | curl với timing | Time measurements |
| B2.3 | Đo TCP+TLS 1.3 handshake | curl với timing | Time measurements |
| B2.4 | Đo QUIC 1-RTT handshake | First connection | Time measurements |
| B2.5 | Đo QUIC 0-RTT handshake | Resumed connection | Time measurements |
| B2.6 | Tổng hợp kết quả | Table comparison | Results document |

### Kịch bản Demo:

#### Kịch bản A: Local Network (PC1 ↔ PC2)
```bash
# === TRÊN PC1 (Server) ===
# Start QUIC server
cd ~/quiche
./target/release/examples/quiche-server \
  --cert ~/quic-demo/certs/cert.pem \
  --key ~/quic-demo/certs/key.pem \
  --root ~/quic-demo/www \
  --listen 0.0.0.0:4433

# === TRÊN PC2 (Client) ===

# Test 1: QUIC 1-RTT (First connection - clear any cached session)
echo "=== LOCAL: QUIC 1-RTT (First Connection) ==="
time ./quiche-client --no-verify https://192.168.1.100:4433/index.html

# Test 2: QUIC 0-RTT (Resumed connection)
echo "=== LOCAL: QUIC 0-RTT (Resumed Connection) ==="
time ./quiche-client --no-verify https://192.168.1.100:4433/index.html

# Capture handshake with Wireshark
tshark -i eth0 -f "udp port 4433" -c 20 -Y "quic" -T fields \
  -e frame.number -e frame.time_relative -e quic.packet_type
```

#### Kịch bản B: Cloud Testing (PC1/PC2 ↔ Cloud) - Thấy rõ latency benefit
```bash
# === TRÊN CLOUD VM (Server) ===
cd ~/quiche
./target/release/examples/quiche-server \
  --cert ~/quic-demo/certs/cert.pem \
  --key ~/quic-demo/certs/key.pem \
  --root ~/quic-demo/www \
  --listen 0.0.0.0:4433

# === TRÊN PC1 hoặc PC2 (Client) ===

# Đo ping để biết RTT thực tế
ping -c 5 CLOUD_PUBLIC_IP

# Test 1: QUIC 1-RTT to Cloud (thấy rõ latency)
echo "=== CLOUD: QUIC 1-RTT (First Connection) ==="
time ./quiche-client --no-verify https://CLOUD_PUBLIC_IP:4433/index.html

# Test 2: QUIC 0-RTT to Cloud (latency giảm đáng kể!)
echo "=== CLOUD: QUIC 0-RTT (Resumed Connection) ==="
time ./quiche-client --no-verify https://CLOUD_PUBLIC_IP:4433/index.html

# So sánh: Với Cloud latency ~50-100ms, 0-RTT tiết kiệm đáng kể!
```

### Kết quả mong đợi:

> **Giải thích**: TCP+TLS 1.3 cần 2 RTT (TCP handshake + TLS), QUIC 1-RTT cần 1 RTT, QUIC 0-RTT cần ~0 RTT (data gửi cùng Initial packet)

| Scenario | TCP+TLS 1.3 (2 RTT) | QUIC 1-RTT (1 RTT) | QUIC 0-RTT (~0 RTT) | Savings |
|----------|---------------------|--------------------|--------------------|---------|
| **Local (LAN ~1ms RTT)** | ~2-3ms | ~1-2ms | ~1ms | Nhỏ |
| **Cloud (~50ms RTT)** | ~100ms | ~50ms | ~0ms + data | **50-100ms!** |
| **Cloud (~100ms RTT)** | ~200ms | ~100ms | ~0ms + data | **100-200ms!** |

> 💡 **Key insight**: Với network có latency cao (Cloud/Internet), 0-RTT tiết kiệm đáng kể thời gian!

### 📋 Deliverables B2:
- [ ] Handshake timing measurements - Local (TV1)
- [ ] Handshake timing measurements - Cloud (TV1)
- [ ] Comparison table (TV1)
- [ ] Wireshark captures (TV2)
- [ ] Screenshots (TV1 + TV2)
- [ ] 📊 **Bar chart so sánh handshake timing (TV1)**

---

## B3. Demo 2: Stream Multiplexing

### Mục tiêu: Chứng minh QUIC không bị HOL blocking

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B3.1 | Create test scenario | Multiple files download | Test plan |
| B3.2 | Simulate packet loss | tc netem loss | Commands documented |
| B3.3 | Run concurrent downloads | 5 streams QUIC | Timing results |
| B3.4 | Run TCP comparison | Sequential downloads | Timing results |
| B3.5 | Capture stream interleaving | Wireshark | Captures |
| B3.6 | Analyze results | HOL blocking evidence | Analysis document |
| B3.7 | 📊 **Vẽ stream timeline** | Timeline diagram các streams xen kẽ | **Stream interleaving diagram** |
| B3.8 | 📊 **Vẽ so sánh completion time** | Bar chart so sánh TCP vs QUIC với packet loss | **Completion time comparison chart** |

### Kịch bản Demo:

```bash
# === TRÊN PC1 (Server) ===
# Server đã chạy từ Demo 1

# === TRÊN PC2 (Client) ===

# Terminal 1: Simulate 5% packet loss
sudo tc qdisc add dev eth0 root netem loss 5% delay 20ms

# Terminal 2: Download 5 files concurrently with QUIC
echo "=== QUIC Concurrent Downloads (5% loss) ==="
time (
  for i in {1..5}; do
    ./quiche-client --no-verify https://192.168.1.100:4433/file$i.bin \
      > ~/quic-demo/downloads/file$i.bin &
  done
  wait
)
echo "All files downloaded!"

# Terminal 3: Capture stream interleaving
tshark -i eth0 -f "udp port 4433" -Y "quic.stream" -T fields \
  -e frame.time_relative -e quic.stream.stream_id -e quic.stream.length \
  > ~/quic-demo/captures/stream_interleaving.txt

# Clear packet loss
sudo tc qdisc del dev eth0 root

# Verify all files downloaded completely
ls -la ~/quic-demo/downloads/
```

### 📋 Deliverables B3:
- [ ] Stream multiplexing demo completed (TV2)
- [ ] Wireshark captures showing interleaving (TV2)
- [ ] Timing comparison data (TV2)
- [ ] Screenshots (TV2)
- [ ] 📊 **Stream interleaving diagram (TV2)**
- [ ] 📊 **Completion time comparison chart: QUIC vs TCP (TV2)**

---

## B4. Demo 3: Connection Migration

### Mục tiêu: Chứng minh QUIC duy trì connection khi đổi network

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B4.1 | Setup dual network | WiFi + Ethernet on PC2 | Network config |
| B4.2 | Create migration script | Switch interface during download | Script |
| B4.3 | Run migration demo | Download large file, switch network | Demo results |
| B4.4 | Capture PATH frames | PATH_CHALLENGE/RESPONSE | Wireshark capture |
| B4.5 | Measure downtime | Time to resume after switch | Measurements |
| B4.6 | Compare with TCP | TCP connection drops | Comparison |
| B4.7 | 📊 **Vẽ migration timeline** | Timeline diagram showing migration process | **Migration timeline diagram** |

### Yêu cầu Network:
- PC2 cần có cả WiFi và Ethernet kết nối được tới PC1
- Hoặc: PC1 tạo WiFi hotspot, PC2 connect qua WiFi + Ethernet

### Kịch bản Demo:

```bash
# === CHUẨN BỊ PC2 ===
# Đảm bảo cả wlan0 và eth0 đều có thể reach tới PC1
ip route show
# Nếu cần thêm route:
# sudo ip route add 192.168.1.100/32 dev wlan0 metric 100
# sudo ip route add 192.168.1.100/32 dev eth0 metric 200

# === THỰC HIỆN ===

# Terminal 1 (PC2): Start Wireshark capture
sudo tshark -i any -f "udp port 4433" -w ~/quic-demo/captures/migration.pcap

# Terminal 2 (PC2): Start download large file qua Ethernet (lower metric)
cd ~/quiche
./target/release/examples/quiche-client --no-verify \
  https://192.168.1.100:4433/large.bin > ~/quic-demo/downloads/migration_test.bin &
PID=$!

# Terminal 3 (PC2): Trong khi download - switch to WiFi
sleep 5  # Wait for download to start
echo "=== Switching from Ethernet to WiFi ==="

# Bring down Ethernet, QUIC should migrate to WiFi
sudo ip link set eth0 down

# Wait a moment, then check download still running
sleep 2
ps -p $PID && echo "Download still running after migration!"

# Wait for download to complete
wait $PID
echo "Download completed!"

# Verify file integrity
ls -la ~/quic-demo/downloads/migration_test.bin

# Analyze capture for PATH frames
echo "=== PATH_CHALLENGE frames ==="
tshark -r ~/quic-demo/captures/migration.pcap -Y "quic.frame_type == 0x1a"
echo "=== PATH_RESPONSE frames ==="
tshark -r ~/quic-demo/captures/migration.pcap -Y "quic.frame_type == 0x1b"

# Restore Ethernet
sudo ip link set eth0 up
```

### 📋 Deliverables B4:
- [ ] Connection migration demo completed (TV1)
- [ ] PATH_CHALLENGE/RESPONSE captures (TV1)
- [ ] Downtime measurement (TV1)
- [ ] TCP comparison showing dropped connection (TV1)
- [ ] 📊 **Migration timeline diagram (TV1)**

---

## B5. Demo 4: Packet Loss Recovery

### Mục tiêu: Chứng minh QUIC recovery tốt hơn TCP khi có packet loss

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B5.1 | Setup packet loss scenarios | 1%, 5%, 10% loss | Test scenarios |
| B5.2 | Run QUIC tests | Download với các mức loss | Timing data |
| B5.3 | Run TCP tests | curl với các mức loss | Timing data |
| B5.4 | Capture ACK frames | ACK ranges analysis | Wireshark captures |
| B5.5 | Compare recovery | QUIC vs TCP | Comparison table |
| B5.6 | Document findings | Analysis | Report |
| B5.7 | 📊 **Vẽ line chart packet loss** | Line chart: Packet loss % vs Download time | **Packet loss impact chart** |
| B5.8 | 📊 **Vẽ recovery comparison** | Bar chart so sánh QUIC vs TCP recovery | **Recovery comparison chart** |

### Kịch bản Demo:

```bash
# === TRÊN PC2 (Client) ===

# Function để test với packet loss
test_with_loss() {
  LOSS=$1
  echo "=== Testing with $LOSS% packet loss ==="
  
  # Apply packet loss
  sudo tc qdisc add dev eth0 root netem loss $LOSS%
  
  # Test QUIC
  echo "QUIC download:"
  time ./quiche-client --no-verify https://192.168.1.100:4433/medium.bin > /dev/null
  
  # Test TCP (if nginx setup on PC1)
  # echo "TCP download:"
  # time curl -k https://192.168.1.100/medium.bin > /dev/null
  
  # Clear
  sudo tc qdisc del dev eth0 root
  echo ""
}

# Run tests
test_with_loss 0   # Baseline
test_with_loss 1
test_with_loss 5
test_with_loss 10

# Capture ACK frames
sudo tc qdisc add dev eth0 root netem loss 5%
tshark -i eth0 -f "udp port 4433" -Y "quic.ack" -c 50 -T fields \
  -e frame.number -e quic.ack.largest_acknowledged -e quic.ack.ack_range
sudo tc qdisc del dev eth0 root
```

### 📋 Deliverables B5:
- [ ] Packet loss test results (TV2)
- [ ] ACK frame captures (TV2)
- [ ] Recovery comparison table (TV2)
- [ ] 📊 **Packet loss impact line chart (TV2)**
- [ ] 📊 **Recovery comparison bar chart (TV2)**

---

## B6. Demo 5: Multi-client Stress Test

### Mục tiêu: Chứng minh Server handle được nhiều clients

### Công việc của cả 2:

| STT | Công việc | Thành viên | Output |
|-----|-----------|------------|--------|
| B6.1 | Setup multiple client instances | TV2 | Multiple clients ready |
| B6.2 | Monitor server | TV1 | Server metrics |
| B6.3 | Run stress test | Cả 2 | Test results |
| B6.4 | Analyze throughput | TV1 | Performance data |
| B6.5 | Document results | TV2 | Test report |
| B6.6 | 📊 **Vẽ throughput chart** | Chart số clients vs throughput | **Scalability chart** |

### Kịch bản Demo:

```bash
# === TRÊN PC1 (Server - TV1) ===
# Monitor connections
watch -n 1 "netstat -anu | grep 4433 | wc -l"
# Or monitor với tcpdump
tcpdump -i eth0 udp port 4433 -c 100 | grep -E "length [0-9]+"

# === TRÊN PC2 (Client - TV2) ===
# Run multiple client instances
echo "Starting 10 concurrent QUIC connections..."
for i in {1..10}; do
  ./quiche-client --no-verify https://192.168.1.100:4433/small.bin > /dev/null &
done
wait
echo "All connections completed!"

# === BONUS: PC1 cũng chạy client để tăng load ===
# Trên PC1:
for i in {1..5}; do
  ./quiche-client --no-verify https://127.0.0.1:4433/small.bin > /dev/null &
done
wait
```

### 📋 Deliverables B6:
- [ ] Multi-client test completed (Cả 2)
- [ ] Server metrics captured (TV1)
- [ ] Test report (TV2)
- [ ] 📊 **Scalability chart: Clients vs Throughput (TV1)**

---

## B7. Wireshark Analysis

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B7.1 | Capture QUIC handshake | Full handshake flow | Capture file |
| B7.2 | Analyze Initial packets | Client/Server Initial | Screenshots |
| B7.3 | Analyze Handshake packets | Crypto data | Screenshots |
| B7.4 | Analyze 1-RTT packets | Application data | Screenshots |
| B7.5 | Analyze STREAM frames | Data transfer | Screenshots |
| B7.6 | Analyze ACK frames | Acknowledgments | Screenshots |
| B7.7 | Analyze PATH frames | Migration | Screenshots |
| B7.8 | Create analysis document | All captures explained | Document |

### 📋 Deliverables B7:
- [ ] All captures collected (TV2)
- [ ] Screenshots with annotations (TV2)
- [ ] Wireshark analysis document (TV2)

---

# PHẦN C: PHÂN TÍCH VÀ BÁO CÁO

---

## C1. Performance Analysis

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| C1.1 | Tổng hợp demo metrics | Từ Demo 1-5 | Data compilation |
| C1.2 | Handshake latency analysis | 0-RTT/1-RTT vs TCP | Analysis |
| C1.3 | Throughput analysis | With/without loss | Analysis |
| C1.4 | Migration performance | Downtime measurement | Analysis |
| C1.5 | Create performance charts | Graphs, tables | Visualizations |
| C1.6 | Write performance report | Complete analysis | Document |
| C1.7 | 📊 **Vẽ tổng hợp performance** | Bar/Line charts tổng hợp từ tất cả demos | **Comprehensive performance charts** |
| C1.8 | 📊 **Vẽ summary dashboard** | Dashboard tổng kết metrics | **Performance dashboard** |

### 📋 Deliverables C1:
- [ ] Performance data compiled (TV1)
- [ ] Charts và visualizations (TV1)
- [ ] Performance analysis report (TV1)
- [ ] 📊 **Comprehensive performance charts (TV1)**
- [ ] 📊 **Performance summary dashboard (TV1)**

---

## C2. Case Studies

### Công việc của Thành viên 2:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| C2.1 | Google QUIC | YouTube, Search deployment | Case study |
| C2.2 | Cloudflare QUIC | Edge network rollout | Case study |
| C2.3 | Meta QUIC | Facebook, Instagram usage | Case study |
| C2.4 | Akamai QUIC | CDN implementation | Case study |
| C2.5 | Adoption statistics | Global QUIC adoption | Data summary |
| C2.6 | Write case studies report | All cases combined | Document |
| C2.7 | 📊 **Vẽ adoption statistics** | Pie/Bar chart QUIC adoption theo company/platform | **Adoption statistics charts** |
| C2.8 | 📊 **Vẽ performance comparison** | Charts so sánh hiệu năng từ case studies | **Case study performance charts** |

### 📋 Deliverables C2:
- [ ] Google case study (TV2)
- [ ] Cloudflare case study (TV2)
- [ ] Meta case study (TV2)
- [ ] Case studies report (TV2)
- [ ] 📊 **QUIC adoption statistics charts (TV2)**
- [ ] 📊 **Case study performance comparison charts (TV2)**

---

## C3. QUIC v2 và Future

### Công việc của Thành viên 1:

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| C3.1 | QUIC v2 (RFC 9369) | What's new, improvements | Document |
| C3.2 | Multipath QUIC | Multiple paths simultaneously | Overview |
| C3.3 | QUIC-LB | Load balancing | Overview |
| C3.4 | WebTransport | Bidirectional streams | Overview |
| C3.5 | DNS over QUIC | DoQ | Overview |
| C3.6 | MASQUE | UDP proxying | Overview |
| C3.7 | Future challenges | UDP blocking, middleboxes | Analysis |
| C3.8 | Write future directions | Combined document | Document |

### 📋 Deliverables C3:
- [ ] QUIC v2 summary (TV1)
- [ ] Future extensions overview (TV1)
- [ ] Challenges analysis (TV1)

---

## C4. Viết Báo cáo

### Công việc của Thành viên 1:

| Chương | Nội dung | Trang |
|--------|----------|-------|
| 1 | Giới thiệu (Đặt vấn đề, Mục tiêu, Phạm vi) | 2-3 |
| 2 | Kiến trúc QUIC (Stack, Connection, Stream, Packet, Frame) | 8-10 |
| 3 | Đặc điểm nổi bật (Handshake, Multiplexing, Migration, Security, Flow/Congestion Control) | 12-15 |
| 4 | Demo thực hành (Topology, 5 Demos, Kết quả) | 8-10 |
| 5 | Case Studies (Google, Cloudflare, Meta) | 4-5 |
| 6 | QUIC v2 và Future | 3-4 |
| 7 | Kết luận (Tổng kết, Hạn chế, Hướng phát triển) | 2-3 |
| | **TỔNG** | **40-50** |

### 📋 Deliverables C4:
- [ ] Chương 1-3 (TV1)
- [ ] Chương 4 (TV1 + TV2)
- [ ] Chương 5-7 (TV1)
- [ ] Complete report 40-50 pages (TV1)

---

## C5. Làm Slides Thuyết trình

### Công việc của Thành viên 2:

| Section | Số slides | Nội dung |
|---------|-----------|----------|
| Introduction | 3 | Đặt vấn đề, Mục tiêu |
| QUIC Overview | 5 | History, Why QUIC |
| Architecture | 8 | Stack, Connection, Stream, Packets |
| Key Features | 12 | Handshake, Multiplexing, Migration, Security |
| Demo | 8 | Topology, 5 Demos với screenshots |
| Case Studies | 4 | Google, Cloudflare, Meta |
| Future | 3 | QUIC v2, Extensions |
| Conclusion | 2 | Summary, Q&A |
| **TỔNG** | **45** | |

### 📋 Deliverables C5:
- [ ] Complete slides 45 slides (TV2)
- [ ] Demo video embedded (TV2)
- [ ] Speaker notes (TV2)

---

## C6. Quay Video Demo

### Công việc của cả 2:

| STT | Công việc | Thành viên | Output |
|-----|-----------|------------|--------|
| C6.1 | Quay Demo 1: Handshake | TV1 | Video clip |
| C6.2 | Quay Demo 2: Multiplexing | TV2 | Video clip |
| C6.3 | Quay Demo 3: Migration | TV1 | Video clip |
| C6.4 | Quay Demo 4: Packet Loss | TV2 | Video clip |
| C6.5 | Quay Demo 5: Multi-client | Cả 2 | Video clip |
| C6.6 | Edit video tổng hợp | TV2 | Final video |
| C6.7 | Add narration/subtitles | TV1 | Enhanced video |

### 📋 Deliverables C6:
- [ ] Individual demo clips (Cả 2)
- [ ] Final demo video 10-15 minutes (TV2)
- [ ] Backup copies (Cả 2)

---

## ✅ CHECKLIST TỔNG HỢP

### PHẦN A: Lý thuyết
- [ ] A1: Tổng quan QUIC (TV1 + TV2)
- [ ] A2: Kiến trúc Protocol (TV1)
- [ ] A3: Packet/Frame Structure (TV2)
- [ ] A4: Connection Establishment (TV1)
- [ ] A5: Stream Multiplexing (TV2)
- [ ] A6: Connection Migration (TV1)
- [ ] A7: Flow Control (TV2)
- [ ] A8: Loss/Congestion Control (TV1)
- [ ] A9: Security (TV2)
- [ ] A10: HTTP/3 (TV1)
- [ ] A11: Comparison (TV1 + TV2)

### PHẦN B: Thực hành
- [ ] B1: Setup Topology (TV1 + TV2)
- [ ] B2: Demo Handshake (TV1)
- [ ] B3: Demo Multiplexing (TV2)
- [ ] B4: Demo Migration (TV1)
- [ ] B5: Demo Packet Loss (TV2)
- [ ] B6: Demo Multi-client (TV1 + TV2)
- [ ] B7: Wireshark Analysis (TV2)

### PHẦN C: Báo cáo
- [ ] C1: Performance Analysis (TV1)
- [ ] C2: Case Studies (TV2)
- [ ] C3: QUIC v2 & Future (TV1)
- [ ] C4: Báo cáo 40-50 trang (TV1)
- [ ] C5: Slides 45 slides (TV2)
- [ ] C6: Video Demo 10-15 phút (TV1 + TV2)

---

## 🔧 Công cụ sử dụng

| Công cụ | Mục đích | Link |
|---------|----------|------|
| quiche | QUIC implementation (Cloudflare) | https://github.com/cloudflare/quiche |
| Wireshark | Packet analysis | https://wireshark.org |
| tc (iproute2) | Traffic control, packet loss | Included in Ubuntu |
| OBS Studio | Screen recording | https://obsproject.com |
| draw.io | Diagrams | https://app.diagrams.net |
| LaTeX/Word | Report writing | - |
| PowerPoint/Canva | Slides | - |

## 📚 Tài liệu tham khảo

| RFC | Tên | Mô tả |
|-----|-----|-------|
| RFC 9000 | QUIC: A UDP-Based Multiplexed and Secure Transport | Core protocol |
| RFC 9001 | Using TLS to Secure QUIC | TLS 1.3 integration |
| RFC 9002 | QUIC Loss Detection and Congestion Control | Loss recovery |
| RFC 9114 | HTTP/3 | HTTP over QUIC |
| RFC 9369 | QUIC Version 2 | Protocol improvements |

---

## 🎯 Tiêu chí đạt điểm 10

| Tiêu chí | Yêu cầu | ✓ |
|----------|---------|---|
| **Nội dung toàn diện** | Bao quát TẤT CẢ đặc điểm QUIC (11 chủ đề lý thuyết) | |
| **Demo thực tế** | 5 kịch bản demo với video và captures | |
| **Topology rõ ràng** | 2 Ubuntu PCs + Cloud, các scenario cụ thể | |
| **So sánh data thực** | QUIC vs TCP+TLS với số liệu từ demo | |
| **Hiểu sâu** | Giải thích được WHY, không chỉ WHAT | |
| **Báo cáo chất lượng** | 40-50 trang, diagrams chuyên nghiệp | |
| **Slides đẹp** | 45 slides với embedded video | |
| **Demo live** | Có thể demo trực tiếp + video backup | |
| **Phân tích case studies** | Google, Cloudflare, Meta | |
| **Hướng phát triển** | QUIC v2, Future extensions | |
| **📊 Biểu đồ chuyên nghiệp** | Charts, diagrams minh họa rõ ràng | |

---

## 📊 DANH SÁCH BIỂU ĐỒ CẦN VẼ

> **Lưu ý**: Biểu đồ là phần QUAN TRỌNG để báo cáo và slides đạt điểm cao. Sử dụng các công cụ như **draw.io**, **Excel/Google Sheets**, **Matplotlib/Python**, hoặc **Canva**.

### Biểu đồ Lý thuyết (PHẦN A):

| STT | Loại | Nội dung | Người vẽ | Phần |
|-----|------|----------|----------|------|
| 1 | Timeline | Lịch sử phát triển QUIC (2012-2021) | TV1 | A1 |
| 2 | Pie/Bar Chart | QUIC adoption statistics theo platform | TV2 | A1 |
| 3 | Diagram | QUIC vs TCP/TLS Protocol Stack | TV1 | A2 |
| 4 | Diagram | Packet và Frame Structure | TV2 | A3 |
| 5 | Timing Diagram | Handshake comparison: TCP vs QUIC | TV1 | A4 |
| 6 | Sequence Diagram | 1-RTT và 0-RTT handshake flows | TV1 | A4 |
| 7 | Diagram | HOL blocking: TCP vs QUIC | TV2 | A5 |
| 8 | State Diagram | Stream state machine | TV2 | A5 |
| 9 | Sequence Diagram | Connection Migration process | TV1 | A6 |
| 10 | Diagram | Flow Control mechanism | TV2 | A7 |
| 11 | Line Graph | Congestion window over time | TV1 | A8 |
| 12 | Diagram | RTT estimation | TV1 | A8 |
| 13 | Bar Chart | Performance comparison (latency, throughput) | TV1 | A11 |
| 14 | Radar Chart | Feature comparison QUIC vs TCP | TV2 | A11 |

### Biểu đồ Demo (PHẦN B):

| STT | Loại | Nội dung | Người vẽ | Phần |
|-----|------|----------|----------|------|
| 15 | Bar Chart | Handshake timing: Local vs Cloud | TV1 | B2 |
| 16 | Timeline | Stream interleaving during download | TV2 | B3 |
| 17 | Bar Chart | Completion time: QUIC vs TCP with loss | TV2 | B3 |
| 18 | Timeline | Migration process with timestamps | TV1 | B4 |
| 19 | Line Chart | Packet loss % vs Download time | TV2 | B5 |
| 20 | Bar Chart | Recovery comparison: QUIC vs TCP | TV2 | B5 |
| 21 | Line Chart | Scalability: Clients vs Throughput | TV1 | B6 |

### Biểu đồ Phân tích (PHẦN C):

| STT | Loại | Nội dung | Người vẽ | Phần |
|-----|------|----------|----------|------|
| 22 | Dashboard | Performance summary từ tất cả demos | TV1 | C1 |
| 23 | Mixed Charts | Comprehensive performance comparison | TV1 | C1 |
| 24 | Pie Chart | QUIC adoption by company | TV2 | C2 |
| 25 | Bar Chart | Case study performance improvements | TV2 | C2 |

### Tổng hợp phân bổ biểu đồ:

| Thành viên | Số biểu đồ | Loại chính |
|------------|------------|------------|
| **TV1** | 13 biểu đồ | Timing, Sequence, Performance, Dashboard |
| **TV2** | 12 biểu đồ | Diagrams, Charts, State machines, Adoption |

### Công cụ vẽ biểu đồ khuyến nghị:

| Loại biểu đồ | Công cụ |
|--------------|---------|
| Diagrams, Flowcharts | draw.io, Lucidchart |
| Sequence Diagrams | draw.io, PlantUML, Mermaid |
| Bar/Line/Pie Charts | Excel, Google Sheets, Matplotlib |
| Infographics | Canva, Figma |
| Network Topology | draw.io, Packet Tracer |
| State Diagrams | draw.io, PlantUML |

---

## 📊 Phân bổ công việc

### Thành viên 1 (TV1):
- A2, A4, A6, A8, A10: Kiến trúc, Handshake, Migration, Loss/Congestion, HTTP/3
- B2, B4: Demo Handshake, Demo Migration
- C1, C3, C4: Performance Analysis, QUIC v2, Báo cáo chính

### Thành viên 2 (TV2):
- A3, A5, A7, A9: Packet/Frame, Multiplexing, Flow Control, Security
- B3, B5, B7: Demo Multiplexing, Demo Packet Loss, Wireshark Analysis
- C2, C5: Case Studies, Slides thuyết trình

### Cả 2:
- A1, A11: Tổng quan, So sánh QUIC vs TCP
- B1, B6: Setup Topology, Multi-client Test
- C6: Quay Video Demo

---

*Cập nhật lần cuối: 08/02/2026*
