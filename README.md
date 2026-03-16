# 🚀 ĐỒ ÁN: NGHIÊN CỨU TOÀN DIỆN GIAO THỨC QUIC (QUIC PROTOCOL)

## Đề tài: Nghiên cứu và Demo các Đặc điểm Nổi bật của Giao thức QUIC

### Môn học: NT531.Q21 - Đánh giá hiệu năng mạng máy tính

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò | Thiết bị |
|-----|-----------|------|---------|----------|
| 1 | Đỗ Hoàng Phúc | [MSSV] | Trưởng nhóm | ☁️ Cloud VM 1 - Server (US East) |
| 2 | Bùi Lê Huy Phước | [MSSV] | Thành viên | ☁️ Cloud VM 2 - Client (AP Singapore) |
| - | Cả 2 | - | Cùng quản lý | SSH từ máy cá nhân vào 2 Cloud VMs |

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
| **C4** | [Viết báo cáo](#c4-viết-báo-cáo) | TV1 + TV2 | [↓](#c4-viết-báo-cáo) |
| **C5** | [Làm slides thuyết trình](#c5-làm-slides-thuyết-trình) | TV1 + TV2 | [↓](#c5-làm-slides-thuyết-trình) |
| **C6** | [Quay video demo](#c6-quay-video-demo) | TV1 + TV2 | [↓](#c6-quay-video-demo) |

---

## 🎯 Mục tiêu đề tài - Điểm 10/10

### Các đặc điểm nổi bật của QUIC cần nghiên cứu:

| # | Đặc điểm | Tại sao quan trọng? | Output |
|---|----------|---------------------|--------|
| 1 | **0-RTT/1-RTT Handshake** | Giảm latency từ 2-3 RTT xuống 0-1 RTT | So sánh với TCP+TLS |
| 2 | **Stream Multiplexing** | Không có Head-of-Line blocking | Demo nhiều streams |
| 3 | **Connection Migration** | Duy trì kết nối khi đổi network | Demo đổi network path trên Cloud |
| 4 | **Built-in Encryption** | TLS 1.3 tích hợp, always encrypted | Phân tích bảo mật |
| 5 | **Flow Control** | Connection + Stream level | Demo flow control |
| 6 | **Loss Detection & Recovery** | ACK ranges, improved recovery | Demo packet loss |
| 7 | **Congestion Control** | CUBIC, BBR support | Phân tích throughput |
| 8 | **HTTP/3** | Application layer trên QUIC | Demo HTTP/3 requests |
| 9 | **QUIC v2** | RFC 9369, improvements | Tài liệu tóm tắt |

---

## 🌐 TOPOLOGY DEMO - 2 CLOUD VMs (Cross-Region End-to-End)

### Sơ đồ Topology

```
┌─────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                    QUIC DEMO TOPOLOGY                                                │
│          (2 Cloud VMs ở 2 vùng khác nhau — US East ↔ AP Singapore — End-to-End Cloud)               │
├─────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                                                                      │
│   ☁️ AWS EC2 VM 1 — REGION: US EAST (N. Virginia)        ☁️ AWS EC2 VM 2 — REGION: AP (Singapore)     │
│   ┌──────────────────────────────────────┐               ┌──────────────────────────────────────┐    │
│   │     QUIC SERVER                      │               │     QUIC CLIENT + ANALYSIS           │    │
│   │     (quiche-server)                  │               │     (quiche-client)                  │    │
│   │     Public IP: <SERVER_IP>           │               │     Public IP: <CLIENT_IP>           │    │
│   │     Port: 4433/UDP                   │◄─── INTERNET ─┤     Wireshark / tshark               │    │
│   │     OS: Ubuntu 22.04 LTS             │  RTT ~200-300ms│     tcpdump, tc (traffic control)    │    │
│   │     t2.micro (Free Tier)              │               │     OS: Ubuntu 22.04 LTS             │    │
│   │     1 vCPU, 1GB RAM                  │               │     t2.micro (Free Tier)             │    │
│   │     nginx (TCP+TLS baseline)         │               │     1 vCPU, 1GB RAM                  │    │
│   │     tcpdump, test files              │               │     curl (TCP+TLS baseline)          │    │
│   └──────────────────────────────────────┘               └──────────────────────────────────────┘    │
│              ▲                                                         ▲                              │
│              │ SSH                                                     │ SSH                          │
│              │                                                         │                              │
│   ┌──────────┴────────────────────┐                       ┌───────────┴───────────────────┐          │
│   │  💻 Laptop TV1 (Việt Nam)     │                       │  💻 Laptop TV2 (Việt Nam)     │          │
│   │  (Đỗ Hoàng Phúc)             │                       │  (Bùi Lê Huy Phước)          │          │
│   │  SSH → Cloud VM 1 (Server)    │                       │  SSH → Cloud VM 2 (Client)    │          │
│   └───────────────────────────────┘                       └───────────────────────────────┘          │
│                                                                                                      │
│   ┌──────────────────────────────────────────────────────────────────────────────────────────────┐   │
│   │                                    DEMO SCENARIOS                                             │   │
│   │                                                                                               │   │
│   │   🔹 CLOUD END-TO-END (High latency US↔Asia, thấy rõ lợi ích QUIC):                         │   │
│   │      ├── VM1 (Server US) ↔ VM2 (Client Asia): 0-RTT vs 1-RTT handshake                      │   │
│   │      ├── VM1 ↔ VM2: Stream multiplexing, HOL blocking comparison                             │   │
│   │      ├── VM1 ↔ VM2: Packet loss simulation với tc netem                                      │   │
│   │      ├── VM1 ↔ VM2: Connection migration (đổi network interface trên VM2)                    │   │
│   │      └── VM1 ↔ VM2: Multi-client stress test                                                 │   │
│   │                                                                                               │   │
│   │   🔹 WIRESHARK ANALYSIS (trên VM2):                                                          │   │
│   │      ├── Capture QUIC handshake packets                                                       │   │
│   │      ├── Analyze STREAM, ACK, PATH frames                                                     │   │
│   │      └── So sánh QUIC vs TCP+TLS packets                                                      │   │
│   │                                                                                               │   │
│   │   💡 Lợi thế End-to-End Cloud:                                                                │   │
│   │      ├── RTT thực tế ~200-300ms (US ↔ Asia) — thấy rõ lợi ích 0-RTT                          │   │
│   │      ├── Không phụ thuộc mạng LAN local — ổn định, reproducible                               │   │
│   │      └── Dễ demo từ bất kỳ đâu — chỉ cần SSH                                                 │   │
│   └──────────────────────────────────────────────────────────────────────────────────────────────┘   │
│                                                                                                      │
└─────────────────────────────────────────────────────────────────────────────────────────────────────┘
```

### Chi tiết các thành phần

#### ☁️ Cloud VM 1 — Server (TV1: Đỗ Hoàng Phúc quản lý)

| Thành phần | Chi tiết |
|------------|----------|
| **Provider** | Amazon Web Services (AWS) — **Free Tier (12 tháng)** |
| **Instance** | t2.micro (1 vCPU, 1GB RAM) |
| **Region** | **US East (N. Virginia)** — xa Việt Nam, RTT cao (~200-300ms tới Asia) |
| **OS** | Ubuntu 22.04 LTS |
| **Network** | Public IP (<SERVER_IP>), Security Group allow UDP 4433, TCP 443 |
| **Software** | quiche (server+client), nginx (TCP+TLS baseline), tcpdump |
| **Vai trò** | QUIC Server + TCP+TLS baseline server |
| **Người phụ trách** | **Thành viên 1 (TV1)** — SSH từ laptop cá nhân |

#### ☁️ Cloud VM 2 — Client + Analysis (TV2: Bùi Lê Huy Phước quản lý)

| Thành phần | Chi tiết |
|------------|----------|
| **Provider** | Amazon Web Services (AWS) — **Free Tier (12 tháng)** |
| **Instance** | t2.micro (1 vCPU, 1GB RAM) |
| **Region** | **AP Southeast (Singapore)** hoặc **AP Northeast (Tokyo)** — gần Việt Nam hơn so với US East, tạo khoảng cách cross-continent |
| **OS** | Ubuntu 22.04 LTS |
| **Network** | Public IP (<CLIENT_IP>), Security Group allow UDP outbound |
| **Software** | quiche-client, tshark, tcpdump, tc (iproute2), curl |
| **Vai trò** | QUIC Client + Packet analysis + TCP comparison |
| **Người phụ trách** | **Thành viên 2 (TV2)** — SSH từ laptop cá nhân |

### Network Architecture: Cloud End-to-End

```
☁️ Cloud VM 1 (US East - N. Virginia)      ☁️ Cloud VM 2 (AP - Singapore)
   QUIC Server: 0.0.0.0:4433/UDP              QUIC Client
   nginx: 0.0.0.0:443/TCP                     tshark, tcpdump, tc
   Public IP: <SERVER_IP>                      Public IP: <CLIENT_IP>
          │                                            │
          └────────── INTERNET (RTT ~200-300ms) ───────┘
                    (Cross-continent: US ↔ Asia)

💻 Laptop TV1 (Việt Nam) ── SSH ──→ Cloud VM 1 (Server)
💻 Laptop TV2 (Việt Nam) ── SSH ──→ Cloud VM 2 (Client)
```

> 💡 **Tại sao chọn 2 region xa nhau?**
> - RTT ~200-300ms giữa US và Asia → thấy rõ lợi ích 0-RTT (tiết kiệm 200-600ms)
> - Mô phỏng thực tế: user ở châu Á truy cập server ở Mỹ (rất phổ biến)
> - QUIC được thiết kế để giải quyết vấn đề high-latency networks → demo đúng use case
> - Không phụ thuộc mạng LAN local → kết quả ổn định, reproducible

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

### Công việc của Thành viên 1 (Setup Cloud VM 1 — Server, US East):

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B1.1 | Tạo AWS EC2 VM 1 | Region: US East (N. Virginia), Ubuntu 22.04 | Working VM |
| B1.2 | Configure Security Group | Allow UDP 4433, TCP 443, TCP 22 inbound | Open ports |
| B1.3 | SSH vào VM và install dependencies | build-essential, cmake, openssl, nginx, etc. | Script |
| B1.4 | Install Rust | rustup | Working Rust |
| B1.5 | Clone và build quiche | Cloudflare QUIC implementation | Working quiche |
| B1.6 | Generate certificates | Self-signed SSL certs | cert.pem, key.pem |
| B1.7 | Create test files | index.html, small/medium/large files | Test content |
| B1.8 | Setup nginx (TCP+TLS baseline) | HTTPS server để so sánh với QUIC | Working nginx |
| B1.9 | Test server | quiche-server running, nginx running | Working servers |
| B1.10 | Document setup | Step-by-step guide | Setup guide |

### Công việc của Thành viên 2 (Setup Cloud VM 2 — Client, AP Singapore):

| STT | Công việc | Chi tiết | Output |
|-----|-----------|----------|--------|
| B1.11 | Tạo AWS EC2 VM 2 | Region: AP Southeast (Singapore), Ubuntu 22.04 | Working VM |
| B1.12 | Configure Security Group | Allow outbound UDP/TCP, SSH inbound | Open ports |
| B1.13 | SSH vào VM và install dependencies | build-essential, cmake, openssl, etc. | Script |
| B1.14 | Install Rust | rustup | Working Rust |
| B1.15 | Clone và build quiche | quiche-client | Working client |
| B1.16 | Install tshark + tcpdump | Packet capture tools (headless, no GUI) | Working tshark |
| B1.17 | Install tc (iproute2) | Traffic control for demos | Working tc |
| B1.18 | Test connectivity tới VM1 | Ping, basic QUIC connection tới Server VM | Connection verified |
| B1.19 | Đo RTT baseline | ping <SERVER_IP> — expected ~200-300ms | RTT measurement |
| B1.20 | Document setup | Step-by-step guide | Setup guide |

### 📋 Setup Scripts:

#### setup_server.sh (Cloud VM 1 — US East)
```bash
#!/bin/bash
echo "=== Setting up QUIC Server on Cloud VM 1 (US East) ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    tshark tcpdump curl git iproute2 net-tools \
                    nginx netfilter-persistent  # netfilter-persistent: lưu iptables rules qua reboot

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
echo "<h1>QUIC Cloud Server</h1><p>Hello from Cloud VM 1 (US East)!</p>" > ~/quic-demo/www/index.html
dd if=/dev/urandom of=~/quic-demo/www/small.bin bs=100K count=1     # 100KB
dd if=/dev/urandom of=~/quic-demo/www/medium.bin bs=1M count=10     # 10MB
dd if=/dev/urandom of=~/quic-demo/www/large.bin bs=1M count=100     # 100MB

# Multiple files for multiplexing test
for i in {1..5}; do
  dd if=/dev/urandom of=~/quic-demo/www/file$i.bin bs=1M count=5
done

# Setup nginx for TCP+TLS baseline comparison
sudo mkdir -p /etc/nginx/ssl
sudo cp ~/quic-demo/certs/cert.pem /etc/nginx/ssl/cert.pem
sudo cp ~/quic-demo/certs/key.pem /etc/nginx/ssl/key.pem
sudo tee /etc/nginx/sites-available/quic-baseline > /dev/null <<'EOF'
server {
    listen 443 ssl;
    ssl_certificate /etc/nginx/ssl/cert.pem;
    ssl_certificate_key /etc/nginx/ssl/key.pem;
    root /home/ubuntu/quic-demo/www;
    location / {
        try_files $uri $uri/ =404;
    }
}
EOF
sudo ln -sf /etc/nginx/sites-available/quic-baseline /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl restart nginx

# Configure iptables (AWS EC2 Ubuntu uses iptables)
sudo iptables -I INPUT -p udp --dport 4433 -j ACCEPT
sudo iptables -I INPUT -p tcp --dport 443 -j ACCEPT
sudo netfilter-persistent save

echo "=== Server Setup Complete ==="
echo ""
echo "Start QUIC server with:"
echo "cd ~/quiche && ./target/release/examples/quiche-server \\"
echo "  --cert ~/quic-demo/certs/cert.pem \\"
echo "  --key ~/quic-demo/certs/key.pem \\"
echo "  --root ~/quic-demo/www \\"
echo "  --listen 0.0.0.0:4433"
echo ""
echo "nginx (TCP+TLS baseline) is already running on port 443"
```

#### setup_client.sh (Cloud VM 2 — AP Singapore)
```bash
#!/bin/bash
echo "=== Setting up QUIC Client on Cloud VM 2 (AP Singapore) ==="

# Update system
sudo apt update && sudo apt upgrade -y

# Install dependencies
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    tshark tcpdump curl git iproute2 net-tools

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
echo "Đo RTT tới Server VM (US East):"
echo "ping -c 10 <SERVER_IP>"
echo ""
echo "Test QUIC connection:"
echo "cd ~/quiche && ./target/release/examples/quiche-client \\"
echo "  --no-verify https://<SERVER_IP>:4433/index.html"
echo ""
echo "Test TCP+TLS connection (baseline):"
echo "curl -k -o /dev/null -w 'Total: %{time_total}s\n' https://<SERVER_IP>/index.html"
```

### AWS Setup Guide

#### Bước 1: Tạo AWS Account (Free Tier)
1. Truy cập https://aws.amazon.com/free/
2. Đăng ký tài khoản (cần credit card để xác minh, sẽ có authorization hold nhỏ ~$1 và được hoàn lại)
3. Chọn **Default Region** — lưu ý: có thể tạo EC2 instances ở bất kỳ region nào

> ⚠️ **Quan trọng**: Cần tạo 2 VMs ở 2 regions khác nhau:
> - **VM 1 (Server)**: US East (N. Virginia) — xa Việt Nam
> - **VM 2 (Client)**: AP Southeast (Singapore) hoặc AP Northeast (Tokyo) — gần Việt Nam hơn
> - RTT giữa US East ↔ AP Singapore: ~200-300ms → thấy rõ lợi ích QUIC

#### Bước 2: Tạo VM 1 — Server (US East)
1. Go to EC2 → Instances → Launch Instance
2. Chọn Region: **US East (N. Virginia)**
3. Chọn **t2.micro** (Free Tier)
4. Chọn **Ubuntu 22.04** image
5. Chọn **Auto-assign public IP: Enable**
6. Download SSH key pair
7. Launch instance

#### Bước 3: Configure Security Group cho VM 1
1. Go to EC2 → Security Groups
2. Click Security Group của VM 1 → Edit Inbound Rules
3. Add Inbound Rules:
   - UDP port `4433` from `0.0.0.0/0` (QUIC)
   - TCP port `443` from `0.0.0.0/0` (HTTPS baseline)
   - TCP port `22` from `0.0.0.0/0` (SSH) — đã có sẵn
4. Save

#### Bước 4: Tạo VM 2 — Client (AP Singapore)
1. Chuyển Region sang **AP Southeast (Singapore)** hoặc **AP Northeast (Tokyo)**
2. Tạo VM tương tự như VM 1
3. Security Group: chỉ cần SSH inbound (port 22) — VM 2 là client, không cần open thêm port

#### Bước 5: SSH và Setup
```bash
# === Setup VM 1 (Server) ===
chmod 600 ~/aws_vm1_key.pem
ssh -i ~/aws_vm1_key.pem ubuntu@<SERVER_IP>
# Chạy setup_server.sh

# === Setup VM 2 (Client) ===
chmod 600 ~/aws_vm2_key.pem
ssh -i ~/aws_vm2_key.pem ubuntu@<CLIENT_IP>
# Chạy setup_client.sh

# === Verify connectivity (trên VM 2) ===
ping -c 10 <SERVER_IP>
# Expected RTT: ~200-300ms (US East ↔ AP Singapore)
```

> ⚠️ **Lưu ý bảo mật**: Để an toàn hơn, có thể giới hạn Source IP trong Security Group thay vì 0.0.0.0/0

### 📋 Deliverables B1:
- [ ] Working Cloud VM 1 — QUIC Server + nginx (US East) (TV1)
- [ ] Working Cloud VM 2 — QUIC Client + tshark (AP Singapore) (TV2)
- [ ] Network connectivity verified: VM1 ↔ VM2, RTT ~200-300ms (Cả 2)
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

### Kịch bản Demo: Cloud End-to-End (VM1 US East ↔ VM2 AP Singapore)

```bash
# === TRÊN CLOUD VM 1 (Server — US East) ===
# Start QUIC server
cd ~/quiche
./target/release/examples/quiche-server \
  --cert ~/quic-demo/certs/cert.pem \
  --key ~/quic-demo/certs/key.pem \
  --root ~/quic-demo/www \
  --listen 0.0.0.0:4433

# nginx (TCP+TLS baseline) đã chạy sẵn trên port 443

# === TRÊN CLOUD VM 2 (Client — AP Singapore) ===

# Bước 1: Đo RTT thực tế
ping -c 10 <SERVER_IP>
# Expected: ~200-300ms

# Bước 2: TCP+TLS Handshake (Baseline - qua nginx)
echo "=== TCP+TLS 1.3 Handshake (2 RTT) ==="
curl -k -o /dev/null -w "TCP Connect: %{time_connect}s\nTLS Handshake: %{time_appconnect}s\nTotal: %{time_total}s\n" \
  https://<SERVER_IP>/index.html

# Bước 3: QUIC 1-RTT (First connection)
echo "=== QUIC 1-RTT (First Connection — 1 RTT) ==="
time ./target/release/examples/quiche-client --no-verify \
  https://<SERVER_IP>:4433/index.html

# Bước 4: QUIC 0-RTT (Resumed connection — ngay sau lần đầu)
echo "=== QUIC 0-RTT (Resumed Connection — ~0 RTT) ==="
time ./target/release/examples/quiche-client --no-verify \
  https://<SERVER_IP>:4433/index.html

# Bước 5: Capture handshake packets
tshark -i ens3 -f "udp port 4433" -c 20 -Y "quic" -T fields \
  -e frame.number -e frame.time_relative -e quic.packet_type \
  > ~/quic-demo/captures/handshake_capture.txt
```

### Kết quả mong đợi:

> **Giải thích**: TCP+TLS 1.3 cần 2 RTT (TCP handshake + TLS handshake), QUIC 1-RTT cần 1 RTT, QUIC 0-RTT cần ~0 RTT (data gửi cùng Initial packet). Với RTT ~200-300ms giữa US và Asia, sự khác biệt rất lớn!

| Scenario (VM1 US ↔ VM2 Asia) | TCP+TLS 1.3 (2 RTT) | QUIC 1-RTT (1 RTT) | QUIC 0-RTT (~0 RTT) | Savings vs TCP |
|-------------------------------|---------------------|--------------------|--------------------|----------------|
| **RTT ~200ms** | ~400ms | ~200ms | ~0ms + data | **200-400ms!** |
| **RTT ~250ms** | ~500ms | ~250ms | ~0ms + data | **250-500ms!** |
| **RTT ~300ms** | ~600ms | ~300ms | ~0ms + data | **300-600ms!** |

> 💡 **Key insight**: Với 2 Cloud VMs ở 2 vùng xa nhau (US East ↔ AP Singapore, RTT ~200-300ms), sự khác biệt giữa 0-RTT và TCP+TLS **rất rõ ràng** và dễ đo lường — đây là lợi thế lớn nhất của QUIC!

### 📋 Deliverables B2:
- [ ] Handshake timing measurements — Cloud end-to-end (TV1)
- [ ] TCP+TLS vs QUIC comparison table (TV1)
- [ ] tshark captures from VM2 (TV2)
- [ ] Screenshots (TV1 + TV2)
- [ ] 📊 **Bar chart so sánh handshake timing: TCP+TLS vs QUIC 1-RTT vs QUIC 0-RTT (TV1)**

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

### Kịch bản Demo: Cloud End-to-End (VM1 US ↔ VM2 Asia)

```bash
# === TRÊN CLOUD VM 1 (Server — US East) ===
# Server đã chạy từ Demo 1 (quiche-server trên port 4433)

# === TRÊN CLOUD VM 2 (Client — AP Singapore) ===

# Terminal 1: Simulate thêm 5% packet loss (bên cạnh latency thực tế ~200-300ms)
sudo tc qdisc add dev ens3 root netem loss 5%

# Terminal 2: Download 5 files concurrently with QUIC
echo "=== QUIC Concurrent Downloads (5% loss + real latency ~200-300ms) ==="
time (
  for i in {1..5}; do
    ./target/release/examples/quiche-client --no-verify \
      https://<SERVER_IP>:4433/file$i.bin \
      > ~/quic-demo/downloads/file$i.bin &
  done
  wait
)
echo "All files downloaded!"

# Terminal 3: Capture stream interleaving
tshark -i ens3 -f "udp port 4433" -Y "quic.stream" -T fields \
  -e frame.time_relative -e quic.stream.stream_id -e quic.stream.length \
  > ~/quic-demo/captures/stream_interleaving.txt

# Clear packet loss
sudo tc qdisc del dev ens3 root

# So sánh: TCP concurrent downloads (qua nginx)
echo "=== TCP Concurrent Downloads (5% loss) ==="
sudo tc qdisc add dev ens3 root netem loss 5%
time (
  for i in {1..5}; do
    curl -k https://<SERVER_IP>/file$i.bin > ~/quic-demo/downloads/tcp_file$i.bin &
  done
  wait
)
sudo tc qdisc del dev ens3 root

# Verify all files downloaded
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
| B4.1 | Chuẩn bị secondary ENI trên VM2 | Thêm ENI thứ 2 trên AWS | Network config |
| B4.2 | Create migration script | Đổi IP source trong khi download | Script |
| B4.3 | Run migration demo | Download large file, đổi network path | Demo results |
| B4.4 | Capture PATH frames | PATH_CHALLENGE/RESPONSE | tshark capture |
| B4.5 | Measure downtime | Time to resume after migration | Measurements |
| B4.6 | Compare with TCP | TCP connection drops khi đổi IP | Comparison |
| B4.7 | 📊 **Vẽ migration timeline** | Timeline diagram showing migration process | **Migration timeline diagram** |

### Cách thực hiện Connection Migration trên Cloud:

> **Lưu ý**: Trên Cloud VM không có WiFi/Ethernet vật lý. Thay vào đó, sử dụng **Secondary ENI (Elastic Network Interface)** trên AWS để mô phỏng migration — VM2 sẽ có 2 IP addresses, và ta sẽ đổi source IP trong khi download.

**Cách setup Secondary ENI trên AWS:**
1. Go to EC2 → Network Interfaces → Create Network Interface
2. Attach ENI mới vào VM2 instance (cùng VPC, chọn subnet khác hoặc cùng subnet)
3. SSH vào VM2 và configure interface mới:
```bash
# Kiểm tra interface mới (thường là ens4 hoặc ens5)
ip link show

# Nếu interface chưa được tự động cấu hình, dùng dhclient:
sudo dhclient ens4

# Ghi lại gateway của từng interface (cần cho migration script)
# Primary gateway:
ip route show default
# → default via <PRIMARY_GATEWAY> dev ens3 (ghi lại giá trị này)

# Secondary gateway (xem trong AWS Console → ENI details → Subnet → Route Table)
# Hoặc dùng: ip route show dev ens4
```
4. VM2 sẽ có 2 interfaces: `ens3` (primary) và `ens4` (secondary), mỗi interface có IP và gateway riêng

### Kịch bản Demo: Cloud End-to-End (VM1 US ↔ VM2 Asia)

```bash
# === TRÊN CLOUD VM 2 (Client — AP Singapore) ===

# Kiểm tra 2 interfaces
ip addr show
# ens3: <PRIMARY_IP> (primary ENI)
# ens4: <SECONDARY_IP> (secondary ENI)

# Ghi lại gateways trước khi bắt đầu (xem ở bước setup ENI ở trên)
PRIMARY_GW="<PRIMARY_GATEWAY>"    # e.g., 10.0.0.1 (từ ip route show default)
SECONDARY_GW="<SECONDARY_GATEWAY>"  # e.g., 10.0.1.1 (từ ENI details)

# Cả 2 IP đều có thể reach tới VM1 Server
ping -c 3 -I ens3 <SERVER_IP>
ping -c 3 -I ens4 <SERVER_IP>

# === THỰC HIỆN ===

# Terminal 1 (VM2): Start capture
sudo tshark -i any -f "udp port 4433" -w ~/quic-demo/captures/migration.pcap &
TSHARK_PID=$!

# Terminal 2 (VM2): Start download large file qua ens3 (primary)
cd ~/quiche
./target/release/examples/quiche-client --no-verify \
  https://<SERVER_IP>:4433/large.bin > ~/quic-demo/downloads/migration_test.bin &
DOWNLOAD_PID=$!

# Terminal 3 (VM2): Trong khi download — mô phỏng migration bằng cách đổi default route
sleep 5  # Wait for download to start
echo "=== Migrating from ens3 to ens4 ==="

# Thay đổi route — QUIC sẽ tự động migration sang path mới
sudo ip route del default
sudo ip route add default via $SECONDARY_GW dev ens4

# Wait a moment, then check download still running
sleep 2
ps -p $DOWNLOAD_PID && echo "Download still running after migration!"

# Wait for download to complete
wait $DOWNLOAD_PID
echo "Download completed!"

# Stop capture
kill $TSHARK_PID

# Verify file
ls -la ~/quic-demo/downloads/migration_test.bin

# Analyze capture for PATH frames
echo "=== PATH_CHALLENGE frames ==="
tshark -r ~/quic-demo/captures/migration.pcap -Y "quic.frame_type == 0x1a"
echo "=== PATH_RESPONSE frames ==="
tshark -r ~/quic-demo/captures/migration.pcap -Y "quic.frame_type == 0x1b"

# So sánh: TCP bị disconnect khi đổi route
echo "=== TCP Migration Test (sẽ fail) ==="
curl -k https://<SERVER_IP>/large.bin > /dev/null &
TCP_PID=$!
sleep 3
sudo ip route del default
sudo ip route add default via $PRIMARY_GW dev ens3
sleep 2
ps -p $TCP_PID && echo "TCP still running" || echo "TCP connection DROPPED!"

# Restore default route
sudo ip route del default
sudo ip route add default via $PRIMARY_GW dev ens3
```

### 📋 Deliverables B4:
- [ ] Connection migration demo trên Cloud completed (TV1)
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

### Kịch bản Demo: Cloud End-to-End (VM1 US ↔ VM2 Asia)

```bash
# === TRÊN CLOUD VM 2 (Client — AP Singapore) ===
# Server đã chạy trên VM1 (quiche-server + nginx)

# Function để test với packet loss
test_with_loss() {
  LOSS=$1
  echo "=== Testing with $LOSS% packet loss (+ real latency ~200-300ms) ==="
  
  # Apply packet loss
  sudo tc qdisc add dev ens3 root netem loss $LOSS%
  
  # Test QUIC
  echo "QUIC download:"
  time ./target/release/examples/quiche-client --no-verify \
    https://<SERVER_IP>:4433/medium.bin > /dev/null
  
  # Test TCP (qua nginx trên VM1)
  echo "TCP download:"
  time curl -k -o /dev/null https://<SERVER_IP>/medium.bin
  
  # Clear
  sudo tc qdisc del dev ens3 root
  echo ""
}

# Run tests — latency thực tế ~200-300ms + thêm packet loss
test_with_loss 0   # Baseline (chỉ có real latency)
test_with_loss 1
test_with_loss 5
test_with_loss 10

# Capture ACK frames
sudo tc qdisc add dev ens3 root netem loss 5%
tshark -i ens3 -f "udp port 4433" -Y "quic.ack" -c 50 -T fields \
  -e frame.number -e quic.ack.largest_acknowledged -e quic.ack.ack_range
sudo tc qdisc del dev ens3 root
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

### Kịch bản Demo: Cloud End-to-End (VM1 US ↔ VM2 Asia)

```bash
# === TRÊN CLOUD VM 1 (Server — US East, TV1 monitor) ===
# Monitor connections
watch -n 1 "ss -anu | grep 4433 | wc -l"
# Or monitor với tcpdump
tcpdump -i ens3 udp port 4433 -c 100 | grep -E "length [0-9]+"

# === TRÊN CLOUD VM 2 (Client — AP Singapore, TV2 chạy test) ===
# Run multiple client instances qua cross-continent link
echo "Starting 10 concurrent QUIC connections (US ↔ Asia)..."
for i in {1..10}; do
  ./target/release/examples/quiche-client --no-verify \
    https://<SERVER_IP>:4433/small.bin > /dev/null &
done
wait
echo "All QUIC connections completed!"

# So sánh: TCP concurrent connections
echo "Starting 10 concurrent TCP connections..."
for i in {1..10}; do
  curl -k -o /dev/null https://<SERVER_IP>/small.bin &
done
wait
echo "All TCP connections completed!"
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

### Công việc chia đều cả 2 thành viên:

| Chương | Nội dung | Trang | Người viết |
|--------|----------|-------|------------|
| 1 | Giới thiệu (Đặt vấn đề, Mục tiêu, Phạm vi) | 2-3 | TV1 |
| 2 | Kiến trúc QUIC (Stack, Connection, Stream, Packet, Frame) | 8-10 | TV1 (phần A2) + TV2 (phần A3) |
| 3 | Đặc điểm nổi bật (Handshake, Multiplexing, Migration, Security, Flow/Congestion Control) | 12-15 | TV1 (Handshake A4, Migration A6, Loss/Congestion A8) + TV2 (Multiplexing A5, Flow Control A7, Security A9) |
| 4 | Demo thực hành (Topology, 5 Demos, Kết quả) | 8-10 | TV1 (Demo 1,3,5) + TV2 (Demo 2,4, Wireshark) |
| 5 | Case Studies (Google, Cloudflare, Meta) | 4-5 | TV2 |
| 6 | QUIC v2 và Future | 3-4 | TV1 |
| 7 | Kết luận (Tổng kết, Hạn chế, Hướng phát triển) | 2-3 | TV1 + TV2 cùng viết |
| | **TỔNG** | **40-50** | |

### Chi tiết phân chia viết báo cáo:

| Thành viên | Chương phụ trách | Số trang ước tính |
|------------|-----------------|-------------------|
| **TV1** | Chương 1 (2-3tr), Chương 2 phần kiến trúc (5tr), Chương 3 phần Handshake+Migration+Loss (7tr), Chương 4 phần Demo 1,3,5 (4tr), Chương 6 (3-4tr), Chương 7 phần tổng kết (1tr) | ~22-24 trang |
| **TV2** | Chương 2 phần Packet/Frame (4tr), Chương 3 phần Multiplexing+FlowControl+Security (7tr), Chương 4 phần Demo 2,4,Wireshark (4tr), Chương 5 (4-5tr), Chương 7 phần hạn chế+hướng phát triển (1tr) | ~20-21 trang |
| **Cả 2** | Review chéo toàn bộ, chỉnh sửa, format thống nhất | - |

### 📋 Deliverables C4:
- [ ] Chương 1: Giới thiệu (TV1)
- [ ] Chương 2: Kiến trúc - phần Stack, Connection, Stream (TV1) + phần Packet, Frame (TV2)
- [ ] Chương 3: Đặc điểm - phần Handshake, Migration, Loss/Congestion (TV1) + phần Multiplexing, Flow Control, Security (TV2)
- [ ] Chương 4: Demo - phần Demo 1, 3, 5 (TV1) + phần Demo 2, 4, Wireshark (TV2)
- [ ] Chương 5: Case Studies (TV2)
- [ ] Chương 6: QUIC v2 và Future (TV1)
- [ ] Chương 7: Kết luận (TV1 + TV2)
- [ ] Review chéo và chỉnh sửa (Cả 2)
- [ ] Complete report 40-50 pages (Cả 2 cùng hoàn thiện)

---

## C5. Làm Slides Thuyết trình

### Công việc chia cả 2 thành viên:

| Section | Số slides | Nội dung | Người làm |
|---------|-----------|----------|-----------|
| Introduction | 3 | Đặt vấn đề, Mục tiêu | TV1 |
| QUIC Overview | 5 | History, Why QUIC | TV1 |
| Architecture | 8 | Stack, Connection, Stream, Packets | TV1 (Stack, Connection) + TV2 (Packets, Frame) |
| Key Features | 12 | Handshake, Multiplexing, Migration, Security | TV1 (Handshake, Migration) + TV2 (Multiplexing, Security, Flow Control) |
| Demo | 8 | Topology, 5 Demos với screenshots | TV1 (Demo 1, 3, 5) + TV2 (Demo 2, 4, Wireshark) |
| Case Studies | 4 | Google, Cloudflare, Meta | TV2 |
| Future | 3 | QUIC v2, Extensions | TV1 |
| Conclusion | 2 | Summary, Q&A | TV2 |
| **TỔNG** | **45** | | |

### Chi tiết phân chia slides:

| Thành viên | Slides phụ trách | Số slides ước tính |
|------------|-----------------|---------------------|
| **TV1** | Introduction (3), QUIC Overview (5), Architecture phần Stack (4), Key Features phần Handshake+Migration (5), Demo phần Demo 1,3,5 (4), Future (3) | ~24 slides |
| **TV2** | Architecture phần Packets (4), Key Features phần Multiplexing+Security+FlowControl (7), Demo phần Demo 2,4,Wireshark (4), Case Studies (4), Conclusion (2) | ~21 slides |
| **Cả 2** | Review, chỉnh format thống nhất, thêm animation/transition | - |

### 📋 Deliverables C5:
- [ ] Slides phần Introduction + Overview + Future (TV1)
- [ ] Slides phần Architecture + Key Features (TV1 + TV2)
- [ ] Slides phần Demo (TV1 + TV2)
- [ ] Slides phần Case Studies + Conclusion (TV2)
- [ ] Demo video embedded (TV2)
- [ ] Speaker notes (Cả 2, mỗi người viết notes cho slides mình làm)
- [ ] Review chéo và format thống nhất (Cả 2)

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
- [ ] C4: Báo cáo 40-50 trang (TV1 + TV2 cùng viết, mỗi người viết phần phụ trách)
- [ ] C5: Slides 45 slides (TV1 + TV2 cùng làm, mỗi người làm slides phần mình)
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
| **Topology rõ ràng** | 2 Cloud VMs ở 2 regions khác nhau (US ↔ Asia), end-to-end | |
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
| 15 | Bar Chart | Handshake timing: TCP+TLS vs QUIC 1-RTT vs 0-RTT (Cloud) | TV1 | B2 |
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

### Thành viên 1 - TV1 (Đỗ Hoàng Phúc - Trưởng nhóm):

#### Phần A - Lý thuyết:
| Mã | Nội dung | Công việc cụ thể |
|----|----------|-------------------|
| A1 | Tổng quan QUIC (cùng TV2) | A1.1 Lịch sử, A1.2 Động lực, A1.3 Adoption stats, A1.4 Vẽ timeline |
| A2 | Kiến trúc QUIC Protocol | Protocol stack, Connection, Stream concepts, Connection ID |
| A4 | Connection Establishment | 1-RTT/0-RTT handshake, TLS 1.3 integration, so sánh TCP |
| A6 | Connection Migration | Cơ chế migration, Path validation, demo scenario |
| A8 | Loss Detection & Congestion Control | ACK ranges, CUBIC/BBR, RTT estimation |
| A10 | HTTP/3 over QUIC | HTTP/3 features, so sánh HTTP/2, QPACK |
| A11 | So sánh QUIC vs TCP+TLS (cùng TV2) | Bảng so sánh tổng hợp, biểu đồ performance |

#### Phần B - Thực hành:
| Mã | Nội dung | Công việc cụ thể |
|----|----------|-------------------|
| B1 | Setup Topology (cùng TV2) | Setup Server trên Cloud VM 1 (B1.1-B1.10) |
| B2 | Demo 1: Handshake Comparison | Đo TCP+TLS vs QUIC handshake, cloud end-to-end |
| B4 | Demo 3: Connection Migration | Demo đổi network path trên Cloud VM, capture migration process |
| B6 | Demo 5: Multi-client (cùng TV2) | Stress test nhiều clients, đo scalability |

#### Phần C - Phân tích & Báo cáo:
| Mã | Nội dung | Công việc cụ thể |
|----|----------|-------------------|
| C1 | Performance Analysis | Tổng hợp metrics từ 5 demos, vẽ charts, viết phân tích |
| C3 | QUIC v2 và Future | RFC 9369, Multipath QUIC, WebTransport, DNS over QUIC |
| C4 | Viết báo cáo (cùng TV2) | Chương 1, 2 (phần kiến trúc), 3 (phần Handshake/Migration/Loss), 4 (Demo 1,3,5), 6, 7 (phần tổng kết) ≈ 22-24 trang |
| C5 | Slides (cùng TV2) | ~24 slides: Intro, Overview, Architecture (Stack), Features (Handshake/Migration), Demo 1,3,5, Future |
| C6 | Video Demo (cùng TV2) | Quay Demo 1 (Handshake), Demo 3 (Migration), Demo 5 (Multi-client), thêm narration |

#### Biểu đồ TV1: 13 biểu đồ
- Timeline, Protocol Stack, Timing diagrams, Sequence diagrams, Congestion graphs, Performance charts, Dashboard

---

### Thành viên 2 - TV2 (Bùi Lê Huy Phước):

#### Phần A - Lý thuyết:
| Mã | Nội dung | Công việc cụ thể |
|----|----------|-------------------|
| A1 | Tổng quan QUIC (cùng TV1) | A1.5 Các RFC, A1.6 Implementations, A1.7 Browser support, A1.8 Vẽ adoption chart |
| A3 | Packet và Frame Structure | Long/Short header, Frame types, encoding |
| A5 | Stream Multiplexing | Stream types, HOL blocking solution, interleaving |
| A7 | Flow Control | Connection + Stream level, WINDOW_UPDATE |
| A9 | Security (TLS 1.3) | TLS 1.3 integration, encryption levels, key updates |
| A11 | So sánh QUIC vs TCP+TLS (cùng TV1) | Bảng so sánh tổng hợp, feature radar chart |

#### Phần B - Thực hành:
| Mã | Nội dung | Công việc cụ thể |
|----|----------|-------------------|
| B1 | Setup Topology (cùng TV1) | Setup Client trên Cloud VM 2 (B1.11-B1.20) |
| B3 | Demo 2: Stream Multiplexing | Demo nhiều streams đồng thời, so sánh với TCP HOL blocking |
| B5 | Demo 4: Packet Loss Recovery | Mô phỏng packet loss với tc netem, đo recovery |
| B6 | Demo 5: Multi-client (cùng TV1) | Stress test nhiều clients, capture & analysis |
| B7 | Wireshark Analysis | Capture và phân tích QUIC packets từ tất cả demos |

#### Phần C - Phân tích & Báo cáo:
| Mã | Nội dung | Công việc cụ thể |
|----|----------|-------------------|
| C2 | Case Studies | Google, Cloudflare, Meta, Akamai - nghiên cứu triển khai thực tế |
| C4 | Viết báo cáo (cùng TV1) | Chương 2 (phần Packet/Frame), 3 (phần Multiplexing/FlowControl/Security), 4 (Demo 2,4,Wireshark), 5, 7 (phần hạn chế+hướng phát triển) ≈ 20-21 trang |
| C5 | Slides (cùng TV1) | ~21 slides: Architecture (Packets), Features (Multiplexing/Security/FlowControl), Demo 2,4,Wireshark, Case Studies, Conclusion |
| C6 | Video Demo (cùng TV1) | Quay Demo 2 (Multiplexing), Demo 4 (Packet Loss), edit video tổng hợp |

#### Biểu đồ TV2: 12 biểu đồ
- Adoption charts, Packet/Frame diagrams, HOL blocking, State machines, Flow control, Line/Bar charts

---

### Cả 2 cùng làm:
| Mã | Nội dung | Chi tiết |
|----|----------|----------|
| A1 | Tổng quan QUIC | TV1: Lịch sử + Động lực + Stats, TV2: RFCs + Implementations + Browser support |
| A11 | So sánh QUIC vs TCP+TLS | TV1: Performance comparison, TV2: Feature comparison |
| B1 | Setup Topology | TV1: Setup Cloud VM 1 (Server, US East), TV2: Setup Cloud VM 2 (Client, AP Singapore) |
| B6 | Multi-client Stress Test | TV1: Setup server + scripts, TV2: Client scripts + analysis |
| C4 | Viết báo cáo | Mỗi người viết chương phụ trách (~20-24 trang/người), review chéo |
| C5 | Slides thuyết trình | Mỗi người làm slides phần mình (~21-24 slides/người), format thống nhất |
| C6 | Quay Video Demo | TV1: Demo 1,3 + narration, TV2: Demo 2,4 + edit, Cả 2: Demo 5 |

### Tổng hợp khối lượng:

| Tiêu chí | TV1 | TV2 |
|----------|-----|-----|
| Chủ đề lý thuyết (riêng) | 5 (A2, A4, A6, A8, A10) | 4 (A3, A5, A7, A9) |
| Chủ đề lý thuyết (chung) | 2 (A1, A11) | 2 (A1, A11) |
| Demo riêng | 2 (B2, B4) | 3 (B3, B5, B7) |
| Demo chung | 2 (B1, B6) | 2 (B1, B6) |
| Phân tích riêng | 2 (C1, C3) | 1 (C2) |
| Báo cáo viết | ~22-24 trang | ~20-21 trang |
| Slides làm | ~24 slides | ~21 slides |
| Biểu đồ | 13 | 12 |

---

# 📊 HƯỚNG DẪN VẼ BIỂU ĐỒ BẰNG CODE

> Phần này chứa hướng dẫn và code mẫu hoàn chỉnh để vẽ tất cả biểu đồ cần thiết cho đề tài QUIC.

---

## 📋 MỤC LỤC BIỂU ĐỒ

1. [Vẽ bằng Mermaid (Markdown)](#1-vẽ-bằng-mermaid-markdown)
2. [Vẽ bằng Python (Matplotlib)](#2-vẽ-bằng-python-matplotlib)
3. [Vẽ bằng PlantUML](#3-vẽ-bằng-plantuml)
4. [Vẽ bằng Draw.io](#4-vẽ-bằng-drawio-diagramsnet)
5. [Tổng hợp công cụ theo loại biểu đồ](#5-tổng-hợp-công-cụ-theo-loại-biểu-đồ)
6. [Checklist Biểu đồ](#6-checklist-biểu-đồ)

---

## 1. Vẽ bằng Mermaid (Markdown)

Mermaid có thể nhúng trực tiếp trong Markdown, GitHub hỗ trợ render.

### Timeline Diagram (A1.4)
```mermaid
timeline
    title Lịch sử phát triển QUIC
    2012 : Google bắt đầu phát triển gQUIC
    2013 : Deploy trên Chrome và Google servers
    2016 : IETF Working Group thành lập
    2018 : HTTP/3 được đặt tên
    2021 : RFC 9000, 9001, 9002 - QUIC v1 chính thức
    2023 : RFC 9369 - QUIC v2
```

### Sequence Diagram - Handshake (A4.12)
```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    
    Note over C,S: QUIC 1-RTT Handshake
    
    C->>S: Initial[CRYPTO: ClientHello]
    S->>C: Initial[CRYPTO: ServerHello]
    S->>C: Handshake[CRYPTO: Certificate, Finished]
    C->>S: Handshake[CRYPTO: Finished]
    C->>S: 1-RTT[STREAM: Application Data]
    S->>C: 1-RTT[STREAM: Response]
    
    Note over C,S: Total: 1 RTT before data!
```

### Sequence Diagram - 0-RTT (A4.12)
```mermaid
sequenceDiagram
    participant C as Client
    participant S as Server
    
    Note over C,S: QUIC 0-RTT Handshake (Resumed)
    
    C->>S: Initial[CRYPTO: ClientHello]
    C->>S: 0-RTT[STREAM: Early Data]
    S->>C: Initial + Handshake + 1-RTT[Response]
    
    Note over C,S: Total: 0 RTT before data!
```

### State Diagram - Stream States (A5.10)
```mermaid
stateDiagram-v2
    [*] --> Idle
    Idle --> Open: open
    Open --> Send: send
    Open --> Recv: receive
    Open --> Both: send + receive
    Send --> DataSent: data sent
    Recv --> DataRecvd: data received
    Both --> DataSent: FIN sent
    Both --> DataRecvd: FIN received
    DataSent --> Closed: FIN acked
    DataRecvd --> Closed: all data read
    Closed --> [*]
```

### Flowchart - Protocol Stack (A2.6)
```mermaid
graph TB
    subgraph QUIC["QUIC Stack"]
        A1[Application]
        H31[HTTP/3]
        Q1[QUIC]
        T1[TLS 1.3 - Integrated]
        U1[UDP]
        I1[IP]
        A1 --> H31 --> Q1 --> T1 --> U1 --> I1
    end
    
    subgraph TCP["TCP Stack"]
        A2[Application]
        H2[HTTP/1.1 or HTTP/2]
        T2[TLS 1.2/1.3]
        TC[TCP]
        I2[IP]
        A2 --> H2 --> T2 --> TC --> I2
    end
```

### Comparison Diagram - HOL Blocking (A5.9)
```mermaid
graph LR
    subgraph TCP["TCP + HTTP/2 (HOL Blocking)"]
        direction TB
        T1[Stream A: ✓]
        T2[Stream B: ✗ LOST]
        T3[Stream A: Waiting...]
        T4[Stream C: Waiting...]
        T1 --> T2 --> T3 --> T4
        style T2 fill:#ff6666
        style T3 fill:#ffcc00
        style T4 fill:#ffcc00
    end
    
    subgraph QUIC["QUIC (No HOL Blocking)"]
        direction TB
        Q1[Stream A: ✓]
        Q2[Stream B: ✗ Retransmit]
        Q3[Stream A: ✓ Continue!]
        Q4[Stream C: ✓ Continue!]
        Q1 --> Q3
        Q2
        Q4
        style Q2 fill:#ff6666
        style Q3 fill:#66ff66
        style Q4 fill:#66ff66
    end
```

### Sequence Diagram - 1-RTT Handshake Chi tiết
```mermaid
sequenceDiagram
    autonumber
    participant C as 🖥️ Client
    participant S as 🌐 Server
    
    Note over C,S: QUIC 1-RTT Handshake
    
    C->>S: Initial [CRYPTO: ClientHello]
    
    S->>C: Initial [CRYPTO: ServerHello]
    S->>C: Handshake [CRYPTO: EncryptedExtensions]
    S->>C: Handshake [CRYPTO: Certificate]
    S->>C: Handshake [CRYPTO: CertificateVerify]
    S->>C: Handshake [CRYPTO: Finished]
    
    Note right of S: 1 RTT elapsed
    
    C->>S: Handshake [CRYPTO: Finished]
    C->>S: 1-RTT [STREAM: Application Data]
    
    S->>C: 1-RTT [STREAM: Response Data]
    S->>C: HANDSHAKE_DONE
    
    Note over C,S: ✅ Total: 1 RTT before sending data!
```

### Sequence Diagram - 0-RTT Handshake Chi tiết
```mermaid
sequenceDiagram
    autonumber
    participant C as 🖥️ Client
    participant S as 🌐 Server
    
    Note over C,S: QUIC 0-RTT Handshake (Session Resumption)
    Note left of C: Client có PSK từ session trước
    
    C->>S: Initial [CRYPTO: ClientHello + PSK]
    C->>S: 0-RTT [STREAM: Early Application Data]
    
    Note right of S: Data nhận được NGAY!
    
    S->>C: Initial [CRYPTO: ServerHello]
    S->>C: Handshake [CRYPTO: ...]
    S->>C: 1-RTT [STREAM: Response]
    
    Note over C,S: ✅ Total: 0 RTT before sending data!
```

### Protocol Stack Comparison Chi tiết
```mermaid
graph TB
    subgraph QUIC["🚀 QUIC Stack"]
        direction TB
        A1["Application Layer"]
        H31["HTTP/3"]
        Q1["QUIC<br/>(Connection, Stream, Flow Control)"]
        T1["TLS 1.3<br/>(Integrated)"]
        U1["UDP"]
        I1["IP"]
        A1 --> H31
        H31 --> Q1
        Q1 --> T1
        T1 --> U1
        U1 --> I1
        
        style Q1 fill:#3498db,color:#fff
        style T1 fill:#2ecc71,color:#fff
    end
    
    subgraph TCP["📦 TCP/TLS Stack"]
        direction TB
        A2["Application Layer"]
        H2["HTTP/1.1 or HTTP/2"]
        T2["TLS 1.2/1.3<br/>(Separate Layer)"]
        TC["TCP"]
        I2["IP"]
        A2 --> H2
        H2 --> T2
        T2 --> TC
        TC --> I2
        
        style TC fill:#e74c3c,color:#fff
        style T2 fill:#f39c12,color:#fff
    end
```

### Stream State Machine Chi tiết
```mermaid
stateDiagram-v2
    [*] --> Idle: Stream created
    
    Idle --> Open: open()
    
    state Open {
        [*] --> Ready
        Ready --> Sending: send()
        Ready --> Receiving: receive()
        Ready --> Bidirectional: send() + receive()
        
        Sending --> DataSent: all data sent
        Receiving --> DataReceived: all data received
        Bidirectional --> DataSent: FIN sent
        Bidirectional --> DataReceived: FIN received
    }
    
    DataSent --> ResetSent: RESET_STREAM
    DataReceived --> DataRead: application read
    
    ResetSent --> Closed: acked
    DataRead --> Closed: all data consumed
    DataSent --> Closed: acked
    
    Closed --> [*]
    
    note right of Open: Có thể gửi/nhận data
    note right of Closed: Stream resources freed
```

### Connection Migration Sequence
```mermaid
sequenceDiagram
    autonumber
    participant C as 🖥️ Client
    participant S as 🌐 Server
    
    Note over C,S: Connection đang hoạt động<br/>Client IP: ens3 (Primary ENI)
    
    C->>S: 1-RTT [STREAM: Data] (IP: Primary ENI)
    S->>C: 1-RTT [ACK]
    
    Note left of C: Client đổi sang Secondary ENI<br/>New IP: ens4 (Secondary ENI)
    
    C->>S: 1-RTT [STREAM: Data] (IP: Secondary ENI)
    
    Note right of S: Server detect IP change!<br/>Trigger Path Validation
    
    S->>C: PATH_CHALLENGE (random data)
    C->>S: PATH_RESPONSE (same random data)
    
    Note right of S: ✅ Path validated!
    
    S->>C: 1-RTT [STREAM: Continue...] (to new IP)
    
    Note over C,S: ✅ Connection survived migration!<br/>No data loss, no reconnection needed
```

### HOL Blocking Comparison Chi tiết
```mermaid
graph TB
    subgraph TCP["TCP + HTTP/2: HOL Blocking"]
        direction TB
        T1["Packet 1 (Stream A) ✅"]
        T2["Packet 2 (Stream B) ❌ LOST"]
        T3["Packet 3 (Stream A) ⏳ Blocked"]
        T4["Packet 4 (Stream C) ⏳ Blocked"]
        
        T1 --> T2
        T2 --> T3
        T3 --> T4
        
        style T2 fill:#e74c3c,color:#fff
        style T3 fill:#f39c12,color:#fff
        style T4 fill:#f39c12,color:#fff
    end
    
    subgraph QUIC["QUIC: No HOL Blocking"]
        direction TB
        Q1["Packet 1 (Stream A) ✅"]
        Q2["Packet 2 (Stream B) ❌ Retransmit"]
        Q3["Packet 3 (Stream A) ✅ Delivered!"]
        Q4["Packet 4 (Stream C) ✅ Delivered!"]
        
        Q1 --> Q3
        Q2
        Q4
        
        style Q2 fill:#e74c3c,color:#fff
        style Q3 fill:#27ae60,color:#fff
        style Q4 fill:#27ae60,color:#fff
    end
```

### Flow Control Diagram
```mermaid
flowchart LR
    subgraph Connection["Connection Flow Control"]
        direction TB
        CF["MAX_DATA Frame<br/>Connection Limit: 1MB"]
        CD["DATA_BLOCKED<br/>When limit reached"]
    end
    
    subgraph Stream["Stream Flow Control"]
        direction TB
        SF["MAX_STREAM_DATA Frame<br/>Per-Stream Limit: 256KB"]
        SD["STREAM_DATA_BLOCKED<br/>When stream limit reached"]
    end
    
    Sender --> Connection
    Sender --> Stream
    
    Connection --> CF
    Connection --> CD
    
    Stream --> SF
    Stream --> SD
    
    CF --> Receiver
    SF --> Receiver
```

---

## 2. Vẽ bằng Python (Matplotlib)

### Cài đặt

```bash
pip install matplotlib numpy pandas seaborn
```

### 1. Timeline - Lịch sử QUIC (A1.4)

```python
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, ax = plt.subplots(figsize=(14, 6))

# Data
events = [
    (2012, "Google bắt đầu\nphát triển gQUIC"),
    (2013, "Deploy trên Chrome\nvà Google servers"),
    (2016, "IETF Working Group\nthành lập"),
    (2018, "HTTP/3\nđược đặt tên"),
    (2021, "RFC 9000, 9001, 9002\nQUIC v1 chính thức"),
    (2023, "RFC 9369\nQUIC v2"),
]

years = [e[0] for e in events]
labels = [e[1] for e in events]

# Draw timeline
ax.axhline(y=0, color='#3498db', linewidth=3, zorder=1)

# Draw events
for i, (year, label) in enumerate(events):
    y = 0.5 if i % 2 == 0 else -0.5
    ax.scatter(year, 0, s=200, color='#3498db', zorder=2)
    ax.annotate(f"{year}\n{label}", 
                xy=(year, 0), 
                xytext=(year, y),
                fontsize=10,
                ha='center',
                va='center' if y > 0 else 'center',
                bbox=dict(boxstyle='round,pad=0.5', facecolor='white', edgecolor='#3498db'),
                arrowprops=dict(arrowstyle='->', color='#3498db'))

ax.set_xlim(2010, 2025)
ax.set_ylim(-1.5, 1.5)
ax.set_xlabel('Năm', fontsize=12)
ax.set_title('Lịch sử phát triển QUIC Protocol', fontsize=14, fontweight='bold')
ax.axis('off')

plt.tight_layout()
plt.savefig('quic_timeline.png', dpi=300, bbox_inches='tight')
plt.show()
```

### 2. Bar Chart - Handshake Latency Comparison (A11.9, B2)

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
protocols = ['TCP + TLS 1.2', 'TCP + TLS 1.3', 'QUIC 1-RTT', 'QUIC 0-RTT']
new_connection = [3, 2, 1, 0]  # RTT
resumed_connection = [2, 1, 1, 0]  # RTT

x = np.arange(len(protocols))
width = 0.35

fig, ax = plt.subplots(figsize=(12, 7))

# Colors
color1 = '#3498db'  # Blue
color2 = '#2ecc71'  # Green

bars1 = ax.bar(x - width/2, new_connection, width, label='New Connection', color=color1, edgecolor='white', linewidth=1.5)
bars2 = ax.bar(x + width/2, resumed_connection, width, label='Resumed Connection', color=color2, edgecolor='white', linewidth=1.5)

# Labels and styling
ax.set_ylabel('RTT (Round Trip Time)', fontsize=12)
ax.set_xlabel('Protocol', fontsize=12)
ax.set_title('Handshake Latency Comparison\nQUIC vs TCP + TLS', fontsize=14, fontweight='bold')
ax.set_xticks(x)
ax.set_xticklabels(protocols, fontsize=11)
ax.legend(fontsize=11)
ax.set_ylim(0, 4)
ax.yaxis.grid(True, alpha=0.3)

# Value labels
def add_labels(bars):
    for bar in bars:
        height = bar.get_height()
        ax.annotate(f'{int(height)} RTT',
                    xy=(bar.get_x() + bar.get_width()/2, height),
                    xytext=(0, 3),
                    textcoords="offset points",
                    ha='center', va='bottom',
                    fontsize=10, fontweight='bold')

add_labels(bars1)
add_labels(bars2)

plt.tight_layout()
plt.savefig('handshake_comparison.png', dpi=300)
plt.show()
```

### 3. Pie Chart - QUIC Adoption (A1.8, C2.7)

```python
import matplotlib.pyplot as plt

# Data
labels = ['QUIC (HTTP/3)', 'HTTP/2', 'HTTP/1.1']
sizes = [26.5, 45.3, 28.2]  # Approximate percentages from W3Techs (Q4 2024)
colors = ['#3498db', '#2ecc71', '#e74c3c']
explode = (0.05, 0, 0)

fig, ax = plt.subplots(figsize=(10, 8))
wedges, texts, autotexts = ax.pie(sizes, explode=explode, labels=labels, colors=colors, 
                                   autopct='%1.1f%%', shadow=True, startangle=90,
                                   textprops={'fontsize': 12})

# Bold percentages
for autotext in autotexts:
    autotext.set_fontweight('bold')
    autotext.set_color('white')

ax.set_title('Internet Traffic by Protocol (2024)', fontsize=14, fontweight='bold')

# Legend
ax.legend(wedges, labels, title="Protocols", loc="center left", bbox_to_anchor=(1, 0, 0.5, 1))

plt.tight_layout()
plt.savefig('quic_adoption_pie.png', dpi=300, bbox_inches='tight')
plt.show()
```

### 4. Line Chart - Packet Loss Impact (B5.7)

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
packet_loss = [0, 1, 2, 5, 10, 15, 20]
quic_time = [1.0, 1.08, 1.18, 1.45, 2.1, 3.2, 4.8]  # seconds (simulated)
tcp_time = [1.0, 1.25, 1.55, 2.3, 4.0, 6.5, 10.5]   # seconds (simulated)

fig, ax = plt.subplots(figsize=(12, 7))

# Plot lines
ax.plot(packet_loss, quic_time, 'o-', label='QUIC', color='#3498db', linewidth=2.5, markersize=10, markerfacecolor='white', markeredgewidth=2)
ax.plot(packet_loss, tcp_time, 's-', label='TCP', color='#e74c3c', linewidth=2.5, markersize=10, markerfacecolor='white', markeredgewidth=2)

# Fill area between lines
ax.fill_between(packet_loss, quic_time, tcp_time, alpha=0.1, color='gray')

# Labels
ax.set_xlabel('Packet Loss (%)', fontsize=12)
ax.set_ylabel('Download Time (seconds)', fontsize=12)
ax.set_title('Impact of Packet Loss on Download Time\n10MB File Transfer', fontsize=14, fontweight='bold')
ax.legend(fontsize=12, loc='upper left')
ax.grid(True, alpha=0.3)
ax.set_xticks(packet_loss)

# Annotation
ax.annotate('QUIC more resilient\nto packet loss!', 
            xy=(10, 3), xytext=(12, 6),
            arrowprops=dict(arrowstyle='->', color='gray'),
            fontsize=11, style='italic',
            bbox=dict(boxstyle='round', facecolor='wheat', alpha=0.5))

plt.tight_layout()
plt.savefig('packet_loss_impact.png', dpi=300)
plt.show()
```

### 5. Radar Chart - Feature Comparison (A11.10)

```python
import matplotlib.pyplot as plt
import numpy as np

# Categories
categories = ['Handshake\nLatency', 'HOL Blocking\nResistance', 'Connection\nMigration', 
              'Built-in\nSecurity', 'Multiplexing', 'Loss\nRecovery']
N = len(categories)

# Scores (1-5 scale, 5 is best)
tcp_tls_scores = [2, 2, 1, 3, 3, 3]
quic_scores = [5, 5, 5, 5, 5, 4]

# Compute angle
angles = [n / float(N) * 2 * np.pi for n in range(N)]
angles += angles[:1]

tcp_tls_scores += tcp_tls_scores[:1]
quic_scores += quic_scores[:1]

# Plot
fig, ax = plt.subplots(figsize=(10, 10), subplot_kw=dict(projection='polar'))

# TCP + TLS
ax.plot(angles, tcp_tls_scores, 'o-', linewidth=2, label='TCP + TLS', color='#e74c3c', markersize=8)
ax.fill(angles, tcp_tls_scores, alpha=0.25, color='#e74c3c')

# QUIC
ax.plot(angles, quic_scores, 'o-', linewidth=2, label='QUIC', color='#3498db', markersize=8)
ax.fill(angles, quic_scores, alpha=0.25, color='#3498db')

# Styling
ax.set_xticks(angles[:-1])
ax.set_xticklabels(categories, fontsize=11)
ax.set_ylim(0, 5)
ax.set_yticks([1, 2, 3, 4, 5])
ax.set_yticklabels(['1', '2', '3', '4', '5'], fontsize=9)
ax.legend(loc='upper right', bbox_to_anchor=(1.3, 1.1), fontsize=12)
ax.set_title('Feature Comparison: QUIC vs TCP+TLS\n(Score 1-5, higher is better)', fontsize=14, fontweight='bold', pad=20)

plt.tight_layout()
plt.savefig('feature_radar.png', dpi=300, bbox_inches='tight')
plt.show()
```

### 6. Scalability Chart (B6.6)

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
clients = [1, 5, 10, 20, 50, 100, 200]
quic_throughput = [100, 98, 95, 90, 82, 72, 60]  # Mbps per client (simulated)
tcp_throughput = [100, 95, 88, 78, 65, 50, 35]   # Mbps per client (simulated)

fig, ax = plt.subplots(figsize=(12, 7))

ax.plot(clients, quic_throughput, 'o-', label='QUIC Server', color='#3498db', linewidth=2.5, markersize=10)
ax.plot(clients, tcp_throughput, 's-', label='TCP Server', color='#e74c3c', linewidth=2.5, markersize=10)

ax.set_xlabel('Number of Concurrent Clients', fontsize=12)
ax.set_ylabel('Throughput per Client (Mbps)', fontsize=12)
ax.set_title('Server Scalability: QUIC vs TCP', fontsize=14, fontweight='bold')
ax.legend(fontsize=12)
ax.grid(True, alpha=0.3)
ax.set_xscale('log')
ax.set_xticks(clients)
ax.set_xticklabels(clients)

plt.tight_layout()
plt.savefig('scalability.png', dpi=300)
plt.show()
```

### 7. Congestion Window Graph (A8.10)

```python
import matplotlib.pyplot as plt
import numpy as np

# Time axis
time = np.linspace(0, 100, 1000)

# CUBIC cwnd simulation
def cubic_cwnd(t):
    cwnd = np.zeros_like(t)
    for i, ti in enumerate(t):
        if ti < 10:
            cwnd[i] = ti * 10  # Slow start
        elif ti < 25:
            cwnd[i] = 100 * (1 - np.exp(-0.3 * (ti - 10)))  # Recovery
        elif ti < 35:
            cwnd[i] = 70 + (ti - 25) ** 1.3  # CUBIC growth
        elif ti < 45:
            cwnd[i] = max(90 - (ti - 35) * 8, 30)  # Loss event
        elif ti < 60:
            cwnd[i] = 30 + (ti - 45) ** 1.5  # CUBIC recovery
        else:
            cwnd[i] = min(60 + (ti - 60) ** 1.2, 120)
    return cwnd

# NewReno cwnd simulation
def newreno_cwnd(t):
    cwnd = np.zeros_like(t)
    for i, ti in enumerate(t):
        if ti < 10:
            cwnd[i] = ti * 10
        elif ti < 25:
            cwnd[i] = 100 * (1 - np.exp(-0.2 * (ti - 10)))
        elif ti < 35:
            cwnd[i] = 60 + (ti - 25) * 2  # Linear growth
        elif ti < 45:
            cwnd[i] = max(80 - (ti - 35) * 6, 30)
        elif ti < 60:
            cwnd[i] = 30 + (ti - 45) * 2
        else:
            cwnd[i] = min(60 + (ti - 60) * 1.5, 100)
    return cwnd

fig, ax = plt.subplots(figsize=(14, 7))

ax.plot(time, cubic_cwnd(time), label='CUBIC', color='#3498db', linewidth=2)
ax.plot(time, newreno_cwnd(time), label='NewReno', color='#e74c3c', linewidth=2)

# Add loss event markers
loss_times = [35, 45]
for lt in loss_times:
    ax.axvline(x=lt, color='gray', linestyle='--', alpha=0.5)
    ax.annotate('Packet\nLoss', xy=(lt, 90), fontsize=9, ha='center', color='gray')

ax.set_xlabel('Time (s)', fontsize=12)
ax.set_ylabel('Congestion Window (packets)', fontsize=12)
ax.set_title('Congestion Window Evolution: CUBIC vs NewReno', fontsize=14, fontweight='bold')
ax.legend(fontsize=12)
ax.grid(True, alpha=0.3)
ax.set_ylim(0, 130)

plt.tight_layout()
plt.savefig('cwnd_comparison.png', dpi=300)
plt.show()
```

### 8. HOL Blocking Comparison (A5.9)

```python
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
import numpy as np

fig, axes = plt.subplots(1, 2, figsize=(16, 7))

# === TCP + HTTP/2 (Left) ===
ax1 = axes[0]
ax1.set_title('TCP + HTTP/2: Head-of-Line Blocking', fontsize=13, fontweight='bold')

# Packets
packets = [
    {'id': 1, 'stream': 'A', 'status': 'delivered', 'y': 4},
    {'id': 2, 'stream': 'B', 'status': 'lost', 'y': 3},
    {'id': 3, 'stream': 'A', 'status': 'blocked', 'y': 2},
    {'id': 4, 'stream': 'C', 'status': 'blocked', 'y': 1},
]

colors = {'delivered': '#27ae60', 'lost': '#e74c3c', 'blocked': '#f39c12'}
labels = {'delivered': '✓ Delivered', 'lost': '✗ Lost', 'blocked': '⏳ Blocked'}

for p in packets:
    color = colors[p['status']]
    rect = mpatches.FancyBboxPatch((0.5, p['y'] - 0.3), 3, 0.6,
                                    boxstyle="round,pad=0.02",
                                    facecolor=color, edgecolor='white', linewidth=2)
    ax1.add_patch(rect)
    ax1.text(2, p['y'], f"Packet {p['id']} (Stream {p['stream']})\n{labels[p['status']]}", 
             ha='center', va='center', fontsize=11, fontweight='bold', color='white')

ax1.set_xlim(0, 4)
ax1.set_ylim(0, 5)
ax1.axis('off')

# Explanation box
ax1.text(2, 0.3, "ALL streams blocked when Packet 2 is lost!\n(TCP requires in-order delivery)", 
         ha='center', fontsize=11, style='italic',
         bbox=dict(boxstyle='round', facecolor='#fff3cd', edgecolor='#ffc107'))

# === QUIC (Right) ===
ax2 = axes[1]
ax2.set_title('QUIC: No Head-of-Line Blocking', fontsize=13, fontweight='bold')

packets_quic = [
    {'id': 1, 'stream': 'A', 'status': 'delivered', 'y': 4},
    {'id': 2, 'stream': 'B', 'status': 'lost', 'y': 3},
    {'id': 3, 'stream': 'A', 'status': 'delivered', 'y': 2},
    {'id': 4, 'stream': 'C', 'status': 'delivered', 'y': 1},
]

colors_quic = {'delivered': '#27ae60', 'lost': '#e74c3c'}
labels_quic = {'delivered': '✓ Delivered', 'lost': '✗ Waiting retransmit'}

for p in packets_quic:
    color = colors_quic[p['status']]
    rect = mpatches.FancyBboxPatch((0.5, p['y'] - 0.3), 3, 0.6,
                                    boxstyle="round,pad=0.02",
                                    facecolor=color, edgecolor='white', linewidth=2)
    ax2.add_patch(rect)
    text = f"Packet {p['id']} (Stream {p['stream']})\n{labels_quic[p['status']]}"
    ax2.text(2, p['y'], text, ha='center', va='center', fontsize=11, fontweight='bold', color='white')

ax2.set_xlim(0, 4)
ax2.set_ylim(0, 5)
ax2.axis('off')

# Explanation box
ax2.text(2, 0.3, "Only Stream B is blocked!\nStreams A and C continue normally.", 
         ha='center', fontsize=11, style='italic',
         bbox=dict(boxstyle='round', facecolor='#d4edda', edgecolor='#28a745'))

plt.tight_layout()
plt.savefig('hol_blocking_comparison.png', dpi=300, bbox_inches='tight')
plt.show()
```

### 9. Performance Dashboard (C1.8)

```python
import matplotlib.pyplot as plt
import numpy as np

fig = plt.figure(figsize=(16, 10))

# Create grid
gs = fig.add_gridspec(2, 3, hspace=0.3, wspace=0.3)

# 1. Handshake Comparison (top left)
ax1 = fig.add_subplot(gs[0, 0])
protocols = ['TCP+TLS\n1.2', 'TCP+TLS\n1.3', 'QUIC\n1-RTT', 'QUIC\n0-RTT']
rtt = [3, 2, 1, 0]
colors = ['#e74c3c', '#f39c12', '#3498db', '#27ae60']
bars = ax1.bar(protocols, rtt, color=colors, edgecolor='white', linewidth=2)
ax1.set_ylabel('RTT')
ax1.set_title('Handshake Latency', fontweight='bold')
ax1.set_ylim(0, 4)
for bar, val in zip(bars, rtt):
    ax1.text(bar.get_x() + bar.get_width()/2, val + 0.1, f'{val}', ha='center', fontweight='bold')

# 2. Packet Loss Impact (top middle)
ax2 = fig.add_subplot(gs[0, 1])
loss = [0, 5, 10, 15, 20]
quic_t = [1.0, 1.4, 2.0, 3.0, 4.5]
tcp_t = [1.0, 2.0, 3.5, 6.0, 10.0]
ax2.plot(loss, quic_t, 'o-', label='QUIC', color='#3498db', linewidth=2)
ax2.plot(loss, tcp_t, 's-', label='TCP', color='#e74c3c', linewidth=2)
ax2.set_xlabel('Packet Loss (%)')
ax2.set_ylabel('Download Time (s)')
ax2.set_title('Packet Loss Resilience', fontweight='bold')
ax2.legend(fontsize=9)
ax2.grid(True, alpha=0.3)

# 3. Scalability (top right)
ax3 = fig.add_subplot(gs[0, 2])
clients = [1, 10, 50, 100]
throughput = [100, 95, 80, 65]
ax3.plot(clients, throughput, 'o-', color='#3498db', linewidth=2, markersize=8)
ax3.fill_between(clients, throughput, alpha=0.3, color='#3498db')
ax3.set_xlabel('Concurrent Clients')
ax3.set_ylabel('Throughput/Client (Mbps)')
ax3.set_title('Server Scalability', fontweight='bold')
ax3.grid(True, alpha=0.3)

# 4. Feature Radar (bottom left, spanning 2 columns)
ax4 = fig.add_subplot(gs[1, 0:2], projection='polar')
categories = ['Latency', 'HOL\nBlocking', 'Migration', 'Security', 'Recovery']
tcp_scores = [2, 2, 1, 3, 3]
quic_scores = [5, 5, 5, 5, 4]

angles = [n / float(len(categories)) * 2 * np.pi for n in range(len(categories))]
angles += angles[:1]
tcp_scores += tcp_scores[:1]
quic_scores += quic_scores[:1]

ax4.plot(angles, tcp_scores, 'o-', label='TCP+TLS', color='#e74c3c', linewidth=2)
ax4.fill(angles, tcp_scores, alpha=0.25, color='#e74c3c')
ax4.plot(angles, quic_scores, 'o-', label='QUIC', color='#3498db', linewidth=2)
ax4.fill(angles, quic_scores, alpha=0.25, color='#3498db')
ax4.set_xticks(angles[:-1])
ax4.set_xticklabels(categories, fontsize=10)
ax4.set_ylim(0, 5)
ax4.legend(loc='upper right', bbox_to_anchor=(1.2, 1.0))
ax4.set_title('Feature Comparison', fontweight='bold', pad=20)

# 5. Protocol Adoption (bottom right)
ax5 = fig.add_subplot(gs[1, 2])
labels = ['QUIC\n(HTTP/3)', 'HTTP/2', 'HTTP/1.1']
sizes = [26, 46, 28]
colors = ['#3498db', '#27ae60', '#e74c3c']
explode = (0.05, 0, 0)
ax5.pie(sizes, explode=explode, labels=labels, colors=colors, autopct='%1.0f%%',
        shadow=True, startangle=90, textprops={'fontsize': 10})
ax5.set_title('Protocol Adoption', fontweight='bold')

plt.suptitle('QUIC Performance Dashboard', fontsize=16, fontweight='bold', y=1.02)
plt.tight_layout()
plt.savefig('performance_dashboard.png', dpi=300, bbox_inches='tight')
plt.show()
```

### 10. Stream Interleaving Timeline (B3.7)

```python
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
import numpy as np

fig, ax = plt.subplots(figsize=(16, 6))

# Stream colors
colors = {'A': '#3498db', 'B': '#e74c3c', 'C': '#27ae60', 'D': '#9b59b6', 'E': '#f39c12'}

# Simulated packet data (time, stream, size_proportion)
packets = [
    (0.0, 'A', 0.2), (0.1, 'B', 0.15), (0.2, 'C', 0.18), (0.3, 'A', 0.22),
    (0.4, 'D', 0.16), (0.5, 'E', 0.2), (0.6, 'B', 0.19), (0.7, 'A', 0.17),
    (0.8, 'C', 0.21), (0.9, 'D', 0.15), (1.0, 'E', 0.18), (1.1, 'A', 0.23),
    (1.2, 'B', 0.2), (1.3, 'C', 0.16), (1.4, 'D', 0.19), (1.5, 'E', 0.17),
]

# Draw packets as colored bars
for time, stream, size in packets:
    y = {'A': 5, 'B': 4, 'C': 3, 'D': 2, 'E': 1}[stream]
    rect = mpatches.FancyBboxPatch((time, y - 0.3), 0.08, 0.6,
                                    boxstyle="round,pad=0.01",
                                    facecolor=colors[stream], 
                                    edgecolor='white', linewidth=1)
    ax.add_patch(rect)

# Draw timeline
ax.axhline(y=0, color='gray', linewidth=1)
for i, t in enumerate(np.arange(0, 1.7, 0.1)):
    ax.axvline(x=t, color='lightgray', linewidth=0.5, alpha=0.5)

# Labels
ax.set_yticks([1, 2, 3, 4, 5])
ax.set_yticklabels(['Stream E', 'Stream D', 'Stream C', 'Stream B', 'Stream A'], fontsize=11)
ax.set_xlabel('Time (seconds)', fontsize=12)
ax.set_title('QUIC Stream Multiplexing: Packet Interleaving\nDuring 5-File Concurrent Download', fontsize=14, fontweight='bold')

ax.set_xlim(-0.05, 1.7)
ax.set_ylim(0.3, 5.7)
ax.grid(True, axis='x', alpha=0.3)

# Legend
patches = [mpatches.Patch(color=colors[s], label=f'Stream {s}') for s in ['A', 'B', 'C', 'D', 'E']]
ax.legend(handles=patches, loc='upper right', fontsize=10)

plt.tight_layout()
plt.savefig('stream_interleaving.png', dpi=300, bbox_inches='tight')
plt.show()
```

---

## 3. Vẽ bằng PlantUML

### Sequence Diagram
```plantuml
@startuml
title QUIC 1-RTT Handshake

participant "Client" as C
participant "Server" as S

C -> S: Initial[CRYPTO: ClientHello]
S -> C: Initial[CRYPTO: ServerHello]
S -> C: Handshake[CRYPTO: Certificate, Finished]
C -> S: Handshake[CRYPTO: Finished]
C -> S: 1-RTT[STREAM: Application Data]
S -> C: 1-RTT[STREAM: Response]

note over C,S: Total: 1 RTT before data transfer

@enduml
```

### State Diagram
```plantuml
@startuml
title QUIC Stream States

[*] --> Idle

Idle --> Open : open stream

state Open {
    [*] --> Ready
    Ready --> Send : send data
    Ready --> Recv : receive data
    Ready --> Both : bidirectional
}

Open --> DataSent : FIN sent
Open --> DataRecvd : FIN received

DataSent --> Closed : acked
DataRecvd --> Closed : read

Closed --> [*]

@enduml
```

---

## 4. Vẽ bằng Draw.io (Diagrams.net)

Draw.io là công cụ trực quan, phù hợp cho:
- Network topology
- Protocol stack diagrams
- Packet/Frame structure
- Complex flowcharts

**Cách sử dụng:**
1. Truy cập https://app.diagrams.net
2. Chọn template phù hợp
3. Drag & drop shapes
4. Export PNG/SVG

**Tips:**
- Sử dụng shapes từ "Network" category
- Dùng colors nhất quán
- Export với DPI cao (300+)

---

## 5. Tổng hợp công cụ theo loại biểu đồ

| Loại biểu đồ | Công cụ khuyến nghị | Lý do |
|--------------|---------------------|-------|
| Timeline | Mermaid, draw.io | Đơn giản, nhúng được Markdown |
| Sequence Diagram | Mermaid, PlantUML | Text-based, dễ version control |
| State Diagram | Mermaid, PlantUML | Text-based, chính xác |
| Bar/Line/Pie Chart | Python Matplotlib | Dữ liệu động, chuyên nghiệp |
| Radar Chart | Python Matplotlib | Nhiều parameters so sánh |
| Protocol Stack | draw.io | Trực quan, flexible |
| Packet Structure | draw.io | Chi tiết byte-level |
| Network Topology | draw.io | Network shapes có sẵn |
| Infographics | Canva | Đẹp, chuyên nghiệp |

---

## 6. Checklist Biểu đồ

### PHẦN A (Lý thuyết): 14 biểu đồ
- [ ] A1.4: Timeline lịch sử QUIC (TV1)
- [ ] A1.8: Adoption chart (TV2)
- [ ] A2.6: Protocol Stack comparison (TV1)
- [ ] A3.10: Packet/Frame structure (TV2)
- [ ] A4.11: Timing comparison (TV1)
- [ ] A4.12: Handshake sequences (TV1)
- [ ] A5.9: HOL blocking comparison (TV2)
- [ ] A5.10: Stream state machine (TV2)
- [ ] A6.9: Migration sequence (TV1)
- [ ] A7.8: Flow control diagram (TV2)
- [ ] A8.10: Congestion window graph (TV1)
- [ ] A8.11: RTT estimation diagram (TV1)
- [ ] A11.9: Performance bar chart (TV1)
- [ ] A11.10: Feature radar chart (TV2)

### PHẦN B (Demo): 7 biểu đồ
- [ ] B2: Handshake timing bar chart (TV1)
- [ ] B3.7: Stream interleaving timeline (TV2)
- [ ] B3.8: Completion time comparison (TV2)
- [ ] B4.7: Migration timeline (TV1)
- [ ] B5.7: Packet loss line chart (TV2)
- [ ] B5.8: Recovery comparison chart (TV2)
- [ ] B6.6: Scalability chart (TV1)

### PHẦN C (Phân tích): 4 biểu đồ
- [ ] C1.7: Comprehensive performance charts (TV1)
- [ ] C1.8: Performance dashboard (TV1)
- [ ] C2.7: Adoption statistics charts (TV2)
- [ ] C2.8: Case study performance charts (TV2)

**TỔNG CỘNG: 25 biểu đồ**
- TV1: 13 biểu đồ
- TV2: 12 biểu đồ

---

## Tips để có biểu đồ đẹp

1. **Consistent Colors**: Sử dụng color palette nhất quán
   - QUIC: `#3498db` (blue)
   - TCP: `#e74c3c` (red)
   - Success: `#27ae60` (green)
   - Warning: `#f39c12` (orange)

2. **High DPI**: Export với dpi=300 cho print quality

3. **Clear Labels**: Font size ≥ 10pt

4. **White Background**: Dễ đọc khi in

5. **Legend**: Luôn có legend cho multi-series charts

---

## Hướng dẫn chạy Python Code

```bash
# 1. Cài đặt thư viện
pip install matplotlib numpy pandas seaborn

# 2. Tạo file .py và paste code
nano draw_charts.py

# 3. Chạy
python draw_charts.py

# 4. File PNG sẽ được lưu trong cùng thư mục
```

## Sử dụng Mermaid

### Option A: Nhúng trong README.md

GitHub tự động render Mermaid diagrams:

````markdown
```mermaid
graph TD
    A --> B
```
````

### Option B: Mermaid Live Editor

1. Truy cập https://mermaid.live
2. Paste code Mermaid
3. Download PNG/SVG

### Option C: CLI Tool

```bash
# Cài đặt
npm install -g @mermaid-js/mermaid-cli

# Convert to PNG
mmdc -i diagram.mmd -o diagram.png -b transparent
```

---

*Tài liệu được tạo để hỗ trợ nghiên cứu đề tài QUIC - NT531.Q21*

---

*Cập nhật lần cuối: 08/02/2026*
