# 📋 PHÂN CÔNG CÔNG VIỆC VÀ THỜI GIAN THỰC HIỆN CHI TIẾT

## Đề tài: Tìm hiểu về thiết kế và đánh giá hiệu năng của QUIC rồi so sánh với HTTP/2

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 👥 THÔNG TIN NHÓM

| STT | Họ và tên | MSSV | Email | Vai trò | Số điện thoại |
|-----|-----------|------|-------|---------|---------------|
| 1 | Thành viên 1 | [MSSV] | [email@student.edu.vn] | Trưởng nhóm | [SĐT] |
| 2 | Thành viên 2 | [MSSV] | [email@student.edu.vn] | Thành viên | [SĐT] |

### Phân chia vai trò chi tiết:

**Thành viên 1 (Trưởng nhóm):**
- Chịu trách nhiệm chính về QUIC protocol
- Quản lý tiến độ dự án
- Thiết lập và quản lý server QUIC
- Phân tích hiệu năng connection establishment
- Viết báo cáo phần giới thiệu và phương pháp

**Thành viên 2:**
- Chịu trách nhiệm chính về HTTP/2 protocol
- Thiết lập và quản lý server HTTP/2
- Phân tích hiệu năng throughput/latency
- Viết báo cáo phần cơ sở lý thuyết và kết quả

---

## 🎯 MỤC TIÊU ĐỀ TÀI CHI TIẾT

### Mục tiêu tổng quát:
Nghiên cứu, phân tích và đánh giá hiệu năng của giao thức QUIC so với HTTP/2 trong các điều kiện mạng khác nhau.

### Mục tiêu cụ thể:

| STT | Mục tiêu | Tiêu chí đánh giá | Mức độ ưu tiên |
|-----|----------|-------------------|----------------|
| 1 | Hiểu rõ kiến trúc QUIC | Có thể giải thích được 100% các thành phần của QUIC | Cao |
| 2 | Hiểu rõ kiến trúc HTTP/2 | Có thể giải thích được 100% các thành phần của HTTP/2 | Cao |
| 3 | Triển khai thành công môi trường thử nghiệm | Server QUIC và HTTP/2 hoạt động ổn định | Cao |
| 4 | Thu thập dữ liệu hiệu năng | Có ít nhất 1000 data points cho mỗi metric | Trung bình |
| 5 | Phân tích và so sánh | Có biểu đồ và bảng so sánh chi tiết | Cao |
| 6 | Đưa ra kết luận | Kết luận dựa trên dữ liệu thực tế | Cao |

---

## 📅 KẾ HOẠCH THỜI GIAN TỔNG QUAN (10 TUẦN)

| Giai đoạn | Nội dung | Thời gian | Số tuần | Số giờ dự kiến/người |
|-----------|----------|-----------|---------|---------------------|
| 1 | Nghiên cứu lý thuyết | Tuần 1-3 | 3 tuần | 45 giờ |
| 2 | Triển khai và thử nghiệm | Tuần 4-6 | 3 tuần | 60 giờ |
| 3 | Phân tích và so sánh | Tuần 7-8 | 2 tuần | 30 giờ |
| 4 | Viết báo cáo và hoàn thiện | Tuần 9-10 | 2 tuần | 40 giờ |
| **TỔNG** | | | **10 tuần** | **175 giờ** |

---

# ═══════════════════════════════════════════════════════════════════
# GIAI ĐOẠN 1: NGHIÊN CỨU LÝ THUYẾT (TUẦN 1-3)
# ═══════════════════════════════════════════════════════════════════

## 📚 TUẦN 1: TỔNG QUAN VỀ GIAO THỨC TRUYỀN TẢI (15 giờ/người)

### 1.1 Nghiên cứu lịch sử phát triển giao thức Internet (Thành viên 1)

**Thời gian:** 8 giờ | **Deadline:** Thứ 6, Tuần 1

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 1.1.1 | Đọc tài liệu về HTTP/1.0 (RFC 1945) | 1 giờ | Ghi chú tóm tắt |
| 1.1.2 | Đọc tài liệu về HTTP/1.1 (RFC 2616, RFC 7230-7235) | 1.5 giờ | Ghi chú tóm tắt |
| 1.1.3 | Đọc tài liệu về HTTP/2 (RFC 7540) | 2 giờ | Ghi chú tóm tắt |
| 1.1.4 | Đọc tài liệu về QUIC (RFC 9000) | 2 giờ | Ghi chú tóm tắt |
| 1.1.5 | Tổng hợp timeline phát triển | 1 giờ | Sơ đồ timeline |
| 1.1.6 | Viết tài liệu tổng hợp | 0.5 giờ | File .md hoàn chỉnh |

#### Nội dung cần nghiên cứu:

**HTTP/1.0 (1996):**
- [ ] Request-response model
- [ ] Stateless protocol
- [ ] Hạn chế: Mỗi request cần một TCP connection mới
- [ ] Header dạng text
- [ ] Không hỗ trợ persistent connections

**HTTP/1.1 (1997):**
- [ ] Persistent connections (keep-alive)
- [ ] Pipelining (nhưng có Head-of-Line blocking)
- [ ] Chunked transfer encoding
- [ ] Host header (virtual hosting)
- [ ] Caching improvements
- [ ] Hạn chế: Vẫn còn HOL blocking

**HTTP/2 (2015):**
- [ ] Binary framing layer
- [ ] Multiplexing
- [ ] Header compression (HPACK)
- [ ] Server push
- [ ] Stream prioritization
- [ ] Vẫn chạy trên TCP → vẫn có TCP HOL blocking

**QUIC (2021):**
- [ ] Chạy trên UDP
- [ ] Built-in encryption (TLS 1.3)
- [ ] 0-RTT connection establishment
- [ ] Independent stream multiplexing
- [ ] Connection migration
- [ ] Improved congestion control

#### Output yêu cầu:
```
📁 docs/
├── 01-history/
│   ├── HTTP_1_0_overview.md (500+ từ)
│   ├── HTTP_1_1_overview.md (800+ từ)
│   ├── HTTP_2_overview.md (1000+ từ)
│   ├── QUIC_overview.md (1000+ từ)
│   ├── timeline_diagram.png
│   └── evolution_summary.md (2000+ từ)
```

---

### 1.2 Nghiên cứu tổng quan về TCP và UDP (Thành viên 2)

**Thời gian:** 8 giờ | **Deadline:** Thứ 6, Tuần 1

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 1.2.1 | Nghiên cứu TCP protocol (RFC 793) | 2 giờ | Ghi chú chi tiết |
| 1.2.2 | Nghiên cứu UDP protocol (RFC 768) | 1 giờ | Ghi chú chi tiết |
| 1.2.3 | Phân tích ưu điểm của TCP | 1 giờ | Danh sách ưu điểm |
| 1.2.4 | Phân tích nhược điểm của TCP | 1 giờ | Danh sách nhược điểm |
| 1.2.5 | Phân tích ưu/nhược điểm của UDP | 1 giờ | Danh sách ưu/nhược điểm |
| 1.2.6 | Lập bảng so sánh TCP vs UDP | 1 giờ | Bảng so sánh chi tiết |
| 1.2.7 | Viết tài liệu tổng hợp | 1 giờ | File .md hoàn chỉnh |

#### Nội dung cần nghiên cứu về TCP:

**Cơ chế hoạt động:**
- [ ] Three-way handshake (SYN, SYN-ACK, ACK)
- [ ] Four-way termination (FIN, ACK)
- [ ] Sequence numbers và Acknowledgment
- [ ] Window size và Flow control
- [ ] Congestion control algorithms (Slow start, Congestion avoidance, Fast retransmit, Fast recovery)

**Ưu điểm TCP:**
- [ ] Reliable delivery (đảm bảo dữ liệu đến đích)
- [ ] In-order delivery (đảm bảo thứ tự)
- [ ] Error detection và correction
- [ ] Flow control
- [ ] Congestion control

**Nhược điểm TCP:**
- [ ] Head-of-Line (HOL) blocking
- [ ] Connection setup latency (1-RTT minimum)
- [ ] Không thể multiplexing hiệu quả
- [ ] Không hỗ trợ connection migration

#### Nội dung cần nghiên cứu về UDP:

**Cơ chế hoạt động:**
- [ ] Connectionless protocol
- [ ] Simple header structure (8 bytes)
- [ ] No reliability guarantees
- [ ] No congestion control

**Ưu điểm UDP:**
- [ ] Low latency (không cần handshake)
- [ ] No HOL blocking
- [ ] Lightweight
- [ ] Flexibility (có thể xây dựng reliability layer phía trên)

**Nhược điểm UDP:**
- [ ] Không reliable
- [ ] Không có congestion control (có thể gây network congestion)
- [ ] Packets có thể bị mất, duplicate, hoặc out-of-order

#### Bảng so sánh chi tiết TCP vs UDP:

| Tiêu chí | TCP | UDP |
|----------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Guaranteed delivery | Best-effort delivery |
| Ordering | In-order delivery | No ordering |
| Speed | Slower (do overhead) | Faster |
| Header size | 20-60 bytes | 8 bytes |
| Handshake | 3-way handshake | Không cần |
| Flow control | Có | Không |
| Congestion control | Có | Không |
| Error checking | Checksum + ACK | Chỉ checksum |
| Use cases | Web, Email, File transfer | Streaming, Gaming, DNS |

#### Output yêu cầu:
```
📁 docs/
├── 02-transport-layer/
│   ├── TCP_deep_dive.md (1500+ từ)
│   ├── UDP_deep_dive.md (800+ từ)
│   ├── TCP_vs_UDP_comparison.md (1000+ từ)
│   ├── tcp_state_diagram.png
│   └── transport_layer_summary.md
```

---

### 1.3 Tìm kiếm và tổng hợp tài liệu tham khảo (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Chủ nhật, Tuần 1

#### Các bước thực hiện:

| Bước | Công việc cụ thể | Người thực hiện | Thời gian |
|------|------------------|-----------------|-----------|
| 1.3.1 | Tìm kiếm RFC documents | Thành viên 1 | 1 giờ |
| 1.3.2 | Tìm kiếm academic papers | Thành viên 2 | 1 giờ |
| 1.3.3 | Tìm kiếm technical blogs và documentation | Thành viên 1 | 1 giờ |
| 1.3.4 | Tìm kiếm implementation guides | Thành viên 2 | 1 giờ |
| 1.3.5 | Tổng hợp và phân loại tài liệu | Cả 2 | 1 giờ |
| 1.3.6 | Đánh giá chất lượng tài liệu | Cả 2 | 1 giờ |

#### Danh sách tài liệu bắt buộc phải đọc:

**RFCs chính:**
| RFC | Tên | Người đọc | Trạng thái |
|-----|-----|-----------|------------|
| RFC 9000 | QUIC: A UDP-Based Multiplexed and Secure Transport | Thành viên 1 | [ ] |
| RFC 9001 | Using TLS to Secure QUIC | Thành viên 2 | [ ] |
| RFC 9002 | QUIC Loss Detection and Congestion Control | Thành viên 1 | [ ] |
| RFC 7540 | HTTP/2 | Thành viên 2 | [ ] |
| RFC 7541 | HPACK: Header Compression for HTTP/2 | Thành viên 2 | [ ] |
| RFC 793 | TCP | Thành viên 2 | [ ] |
| RFC 768 | UDP | Thành viên 2 | [ ] |

**Academic Papers:**
| Paper | Tác giả/Nguồn | Năm | Người đọc |
|-------|---------------|-----|-----------|
| "The QUIC Transport Protocol: Design and Internet-Scale Deployment" | Google | 2017 | Thành viên 1 |
| "QUIC: A UDP-Based Secure and Reliable Transport for HTTP/2" | Google | 2016 | Thành viên 1 |
| "An Empirical Study of QUIC Performance" | Various | 2020 | Cả 2 |
| "HTTP/2: A New Excerpt of Performance" | Various | 2016 | Thành viên 2 |

**Technical Documentation:**
| Nguồn | URL | Nội dung |
|-------|-----|----------|
| Cloudflare QUIC | cloudflare.com/quic | Implementation details |
| Google QUIC | chromium.org/quic | Original QUIC docs |
| HTTP/2 explained | http2-explained.haxx.se | HTTP/2 tutorial |
| Mozilla MDN | developer.mozilla.org | HTTP/2, QUIC docs |

#### Output yêu cầu:
```
📁 docs/
├── references/
│   ├── RFC_list.md
│   ├── papers_list.md
│   ├── online_resources.md
│   └── bibliography.bib (nếu dùng LaTeX)
```

---

## 📚 TUẦN 2: KIẾN TRÚC VÀ THIẾT KẾ QUIC (15 giờ/người)

### 2.1 Nghiên cứu kiến trúc QUIC (Thành viên 1)

**Thời gian:** 10 giờ | **Deadline:** Thứ 6, Tuần 2

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 2.1.1 | Đọc RFC 9000 Sections 1-4 (Introduction, Streams) | 2 giờ | Ghi chú |
| 2.1.2 | Đọc RFC 9000 Sections 5-7 (Connections) | 2 giờ | Ghi chú |
| 2.1.3 | Vẽ sơ đồ kiến trúc QUIC | 1.5 giờ | Diagram |
| 2.1.4 | Phân tích Connection establishment | 1.5 giờ | Flow chart |
| 2.1.5 | Phân tích Stream multiplexing | 1.5 giờ | Diagram + mô tả |
| 2.1.6 | Phân tích Flow control | 1 giờ | Tài liệu |
| 2.1.7 | Viết tài liệu tổng hợp | 0.5 giờ | File .md |

#### Nội dung chi tiết cần nghiên cứu:

**2.1.1 QUIC Connection Establishment:**

```
┌─────────────┐                              ┌─────────────┐
│   Client    │                              │   Server    │
└──────┬──────┘                              └──────┬──────┘
       │                                            │
       │  ──────── Initial (CRYPTO) ──────────────► │
       │  ClientHello + QUIC transport params       │  1-RTT
       │                                            │
       │  ◄─────── Initial (CRYPTO) ─────────────── │
       │  ServerHello + EncryptedExtensions +       │
       │  Certificate + CertificateVerify +         │
       │  Finished + QUIC transport params          │
       │                                            │
       │  ──────── Handshake (CRYPTO) ───────────► │
       │  Finished                                  │
       │                                            │
       │  ◄═══════ 1-RTT Data ═══════════════════► │
       │  Application data có thể gửi ngay         │
```

**Các bước chi tiết:**
- [ ] Bước 1: Client gửi Initial packet chứa ClientHello
- [ ] Bước 2: Server phản hồi với ServerHello, Certificate
- [ ] Bước 3: Client xác nhận với Finished message
- [ ] Bước 4: Bắt đầu truyền dữ liệu ứng dụng

**0-RTT Connection Resumption:**
```
┌─────────────┐                              ┌─────────────┐
│   Client    │                              │   Server    │
└──────┬──────┘                              └──────┬──────┘
       │                                            │
       │  ──────── Initial + 0-RTT data ─────────► │  0-RTT!
       │  ClientHello + Early application data     │
       │                                            │
       │  ◄─────── Initial + 1-RTT data ────────── │
       │  ServerHello + Application response       │
```

**2.1.2 Stream Multiplexing:**

```
QUIC Connection
┌────────────────────────────────────────────────────┐
│  ┌──────────┐  ┌──────────┐  ┌──────────┐        │
│  │ Stream 0 │  │ Stream 4 │  │ Stream 8 │  ...   │
│  │ (bidi)   │  │ (bidi)   │  │ (bidi)   │        │
│  └──────────┘  └──────────┘  └──────────┘        │
│                                                    │
│  ┌──────────┐  ┌──────────┐                       │
│  │ Stream 2 │  │ Stream 6 │  (unidirectional)    │
│  │ (uni)    │  │ (uni)    │                       │
│  └──────────┘  └──────────┘                       │
└────────────────────────────────────────────────────┘
```

**Đặc điểm Stream:**
- [ ] Stream ID: 62-bit identifier
- [ ] Bidirectional streams: client-initiated (ID % 4 == 0), server-initiated (ID % 4 == 1)
- [ ] Unidirectional streams: client-initiated (ID % 4 == 2), server-initiated (ID % 4 == 3)
- [ ] Independent flow control per stream
- [ ] No HOL blocking between streams

**2.1.3 Flow Control:**

| Level | Mô tả | Parameters |
|-------|-------|------------|
| Connection-level | Giới hạn tổng data trên connection | MAX_DATA frame |
| Stream-level | Giới hạn data trên mỗi stream | MAX_STREAM_DATA frame |
| Stream count | Giới hạn số streams | MAX_STREAMS frame |

**Flow Control Mechanism:**
```
┌─────────────┐
│   Sender    │
└──────┬──────┘
       │ Gửi data
       ▼
┌─────────────────────────────────────┐
│  Credit-based flow control         │
│  ┌─────────────────────────────┐   │
│  │ Available credit = MAX_DATA │   │
│  │ - bytes_sent                │   │
│  └─────────────────────────────┘   │
└─────────────────────────────────────┘
       │
       ▼
┌─────────────┐
│  Receiver   │──► Gửi MAX_DATA/MAX_STREAM_DATA để tăng credit
└─────────────┘
```

#### Output yêu cầu:
```
📁 docs/
├── 03-quic-architecture/
│   ├── quic_overview.md (2000+ từ)
│   ├── connection_establishment.md (1500+ từ)
│   ├── stream_multiplexing.md (1500+ từ)
│   ├── flow_control.md (1000+ từ)
│   ├── diagrams/
│   │   ├── quic_architecture.png
│   │   ├── handshake_flow.png
│   │   ├── stream_multiplexing.png
│   │   └── flow_control.png
│   └── quic_architecture_summary.md
```

---

### 2.2 Nghiên cứu cơ chế bảo mật của QUIC (Thành viên 2)

**Thời gian:** 8 giờ | **Deadline:** Thứ 6, Tuần 2

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 2.2.1 | Đọc RFC 9001 (Using TLS to Secure QUIC) | 2 giờ | Ghi chú |
| 2.2.2 | Nghiên cứu TLS 1.3 integration | 2 giờ | Tài liệu |
| 2.2.3 | Phân tích 0-RTT handshake security | 1.5 giờ | Phân tích |
| 2.2.4 | Nghiên cứu packet protection | 1.5 giờ | Tài liệu |
| 2.2.5 | Vẽ sơ đồ encryption layers | 0.5 giờ | Diagram |
| 2.2.6 | Viết tài liệu tổng hợp | 0.5 giờ | File .md |

#### Nội dung chi tiết:

**2.2.1 TLS 1.3 Integration:**

```
┌─────────────────────────────────────────────────────┐
│                 QUIC Protocol Stack                 │
├─────────────────────────────────────────────────────┤
│                  HTTP/3 (Application)               │
├─────────────────────────────────────────────────────┤
│                  QUIC (Transport)                   │
│  ┌─────────────────────────────────────────────┐   │
│  │        TLS 1.3 (Integrated Security)        │   │
│  │  ┌─────────┬─────────┬─────────────────┐   │   │
│  │  │Handshake│ Record  │ Key Derivation  │   │   │
│  │  │ Layer   │ Layer   │   (HKDF)        │   │   │
│  │  └─────────┴─────────┴─────────────────┘   │   │
│  └─────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────┤
│                  UDP (Datagram)                     │
├─────────────────────────────────────────────────────┤
│                  IP (Network)                       │
└─────────────────────────────────────────────────────┘
```

**Các điểm khác biệt so với TLS over TCP:**
- [ ] TLS messages được đóng gói trong CRYPTO frames
- [ ] Không có TLS record layer separation
- [ ] Keys derived cho multiple packet number spaces
- [ ] Header protection ngoài payload encryption

**2.2.2 Encryption Levels:**

| Level | Sử dụng cho | Keys |
|-------|-------------|------|
| Initial | Initial packets | Derived from connection ID |
| Handshake | Handshake packets | Derived from handshake secrets |
| 0-RTT | Early data | Derived from PSK |
| 1-RTT | Application data | Derived from handshake |

**2.2.3 Packet Protection:**

```
Encrypted QUIC Packet:
┌─────────────────────────────────────────────────────┐
│ Header (partially protected)                        │
│ ┌───────────────┬──────────────┬──────────────────┐│
│ │ Header Form   │ Fixed Bits   │ Packet Number    ││
│ │ (1 bit)       │ (varies)     │ (protected)      ││
│ └───────────────┴──────────────┴──────────────────┘│
├─────────────────────────────────────────────────────┤
│ Payload (AEAD encrypted)                           │
│ ┌─────────────────────────────────────────────────┐│
│ │            Encrypted Frames                     ││
│ │         + Authentication Tag                    ││
│ └─────────────────────────────────────────────────┘│
└─────────────────────────────────────────────────────┘
```

**Header Protection Algorithm:**
- [ ] AEAD algorithm: AES-128-GCM hoặc ChaCha20-Poly1305
- [ ] Header protection: AES-ECB hoặc ChaCha20
- [ ] Packet number encryption để chống traffic analysis

**2.2.4 0-RTT Security Considerations:**

| Risk | Mô tả | Mitigation |
|------|-------|------------|
| Replay attacks | Attacker có thể replay 0-RTT data | Server-side replay protection |
| Forward secrecy | 0-RTT không có forward secrecy | Limit 0-RTT data types |
| Middlebox interference | Middleboxes có thể block | Use GREASE |

#### Output yêu cầu:
```
📁 docs/
├── 04-quic-security/
│   ├── tls_integration.md (1500+ từ)
│   ├── encryption_levels.md (1000+ từ)
│   ├── packet_protection.md (1000+ từ)
│   ├── zero_rtt_security.md (800+ từ)
│   ├── diagrams/
│   │   ├── encryption_layers.png
│   │   ├── packet_protection.png
│   │   └── key_derivation.png
│   └── security_summary.md
```

---

### 2.3 Nghiên cứu cơ chế xử lý lỗi và khôi phục (Thành viên 1)

**Thời gian:** 8 giờ | **Deadline:** Chủ nhật, Tuần 2

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 2.3.1 | Đọc RFC 9002 (Loss Detection and Congestion Control) | 2 giờ | Ghi chú |
| 2.3.2 | Nghiên cứu Loss Detection mechanisms | 2 giờ | Tài liệu |
| 2.3.3 | Nghiên cứu Congestion Control (NewReno, CUBIC, BBR) | 2 giờ | So sánh |
| 2.3.4 | Nghiên cứu Connection Migration | 1.5 giờ | Tài liệu |
| 2.3.5 | Viết tài liệu tổng hợp | 0.5 giờ | File .md |

#### Nội dung chi tiết:

**2.3.1 Loss Detection:**

```
Loss Detection Timeline:
       │
       ▼
┌──────────────────┐
│ Packet Sent      │
│ (time: T0)       │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐     ┌──────────────────┐
│ ACK Received?    │──No─►│ Timer Expired?   │
└────────┬─────────┘     └────────┬─────────┘
         │Yes                     │Yes
         ▼                        ▼
┌──────────────────┐     ┌──────────────────┐
│ Packet Delivered │     │ Packet Lost      │
└──────────────────┘     │ (Retransmit)     │
                         └──────────────────┘
```

**Loss Detection Methods:**
- [ ] **Packet Threshold:** Packet được coi là lost nếu có 3 packets được ACK sau nó
- [ ] **Time Threshold:** Packet lost nếu không được ACK trong max(kTimeThreshold * RTT, kGranularity)
- [ ] **PTO (Probe Timeout):** Gửi probe packet khi không có ACK trong thời gian dài

**2.3.2 Congestion Control Algorithms:**

| Algorithm | Đặc điểm | Phù hợp với |
|-----------|----------|-------------|
| **NewReno** | AIMD (Additive Increase, Multiplicative Decrease) | Mạng ổn định |
| **CUBIC** | Cubic function cho congestion window | High BDP networks |
| **BBR** | Model-based, measures bandwidth | High-latency networks |

**NewReno trong QUIC:**
```python
# Pseudo-code for congestion control
if ack_received:
    if cwnd < ssthresh:
        # Slow start
        cwnd += acked_bytes
    else:
        # Congestion avoidance
        cwnd += (acked_bytes * MSS) / cwnd

if packet_lost:
    ssthresh = cwnd / 2
    cwnd = ssthresh
```

**2.3.3 Connection Migration:**

```
Before Migration:
┌─────────────┐                    ┌─────────────┐
│   Client    │────Connection──────│   Server    │
│ IP: 1.2.3.4 │    ID: 0xABCD      │ IP: 5.6.7.8 │
└─────────────┘                    └─────────────┘

After Migration (Client changes network):
┌─────────────┐                    ┌─────────────┐
│   Client    │────Connection──────│   Server    │
│ IP: 9.8.7.6 │    ID: 0xABCD      │ IP: 5.6.7.8 │
│ (new WiFi)  │    (same!)         │             │
└─────────────┘                    └─────────────┘
```

**Path Validation:**
- [ ] Client gửi PATH_CHALLENGE frame trên path mới
- [ ] Server phản hồi với PATH_RESPONSE
- [ ] Nếu validation thành công, migration hoàn tất
- [ ] Congestion state được reset cho path mới

#### Output yêu cầu:
```
📁 docs/
├── 05-quic-recovery/
│   ├── loss_detection.md (1500+ từ)
│   ├── congestion_control.md (1500+ từ)
│   ├── connection_migration.md (1000+ từ)
│   ├── diagrams/
│   │   ├── loss_detection_flow.png
│   │   ├── congestion_window.png
│   │   └── connection_migration.png
│   └── recovery_summary.md
```

---

### 2.4 Nghiên cứu QUIC Packet Format (Thành viên 2)

**Thời gian:** 7 giờ | **Deadline:** Chủ nhật, Tuần 2

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 2.4.1 | Nghiên cứu Long Header format | 1.5 giờ | Diagram |
| 2.4.2 | Nghiên cứu Short Header format | 1.5 giờ | Diagram |
| 2.4.3 | Nghiên cứu các loại frames | 2 giờ | Bảng tổng hợp |
| 2.4.4 | Phân tích packet processing flow | 1.5 giờ | Flow chart |
| 2.4.5 | Viết tài liệu tổng hợp | 0.5 giờ | File .md |

#### Nội dung chi tiết:

**2.4.1 Long Header Packet:**

```
Long Header Packet Format:
┌─────────────────────────────────────────────────────────────┐
│ Bit:  0   1   2   3   4   5   6   7                        │
├───────────────────────────────────────────────────────────┤
│      │ 1 │ F │ T │ T │ X │ X │ X │ X │  Header Form = 1   │
├───────────────────────────────────────────────────────────┤
│      │         Version (32 bits)                          │
├───────────────────────────────────────────────────────────┤
│      │ DCID Len (8) │ Destination Connection ID (0-160)   │
├───────────────────────────────────────────────────────────┤
│      │ SCID Len (8) │ Source Connection ID (0-160)        │
├───────────────────────────────────────────────────────────┤
│      │ Type-Specific Payload...                           │
└─────────────────────────────────────────────────────────────┘

Packet Types (TT bits):
- 00: Initial
- 01: 0-RTT
- 10: Handshake
- 11: Retry
```

**2.4.2 Short Header Packet:**

```
Short Header Packet Format (1-RTT):
┌─────────────────────────────────────────────────────────────┐
│ Bit:  0   1   2   3   4   5   6   7                        │
├───────────────────────────────────────────────────────────┤
│      │ 0 │ F │ S │ R │ R │ K │ P │ P │  Header Form = 0   │
├───────────────────────────────────────────────────────────┤
│      │    Destination Connection ID (0-160 bits)          │
├───────────────────────────────────────────────────────────┤
│      │    Packet Number (8-32 bits, protected)            │
├───────────────────────────────────────────────────────────┤
│      │    Encrypted Payload + Auth Tag                    │
└─────────────────────────────────────────────────────────────┘

Flags:
- F: Fixed bit (always 1)
- S: Spin bit
- R: Reserved bits
- K: Key phase bit
- P: Packet number length
```

**2.4.3 QUIC Frame Types:**

| Frame Type | Type Value | Mô tả | Người gửi |
|------------|------------|-------|-----------|
| PADDING | 0x00 | Padding frame | Both |
| PING | 0x01 | Keep connection alive | Both |
| ACK | 0x02-0x03 | Acknowledge packets | Both |
| RESET_STREAM | 0x04 | Abruptly terminate stream | Both |
| STOP_SENDING | 0x05 | Request stop sending | Both |
| CRYPTO | 0x06 | Cryptographic handshake | Both |
| NEW_TOKEN | 0x07 | Address validation token | Server |
| STREAM | 0x08-0x0f | Stream data | Both |
| MAX_DATA | 0x10 | Connection flow control | Both |
| MAX_STREAM_DATA | 0x11 | Stream flow control | Both |
| MAX_STREAMS | 0x12-0x13 | Stream limit | Both |
| DATA_BLOCKED | 0x14 | Connection blocked | Both |
| STREAM_DATA_BLOCKED | 0x15 | Stream blocked | Both |
| STREAMS_BLOCKED | 0x16-0x17 | Streams blocked | Both |
| NEW_CONNECTION_ID | 0x18 | New CID | Both |
| RETIRE_CONNECTION_ID | 0x19 | Retire CID | Both |
| PATH_CHALLENGE | 0x1a | Path validation | Both |
| PATH_RESPONSE | 0x1b | Path validation response | Both |
| CONNECTION_CLOSE | 0x1c-0x1d | Close connection | Both |
| HANDSHAKE_DONE | 0x1e | Handshake complete | Server |

**2.4.4 STREAM Frame Format:**

```
STREAM Frame:
┌─────────────────────────────────────────────────────────────┐
│ Type (8) = 0x08 | OFF | LEN | FIN                          │
├─────────────────────────────────────────────────────────────┤
│ Stream ID (i)                                               │
├─────────────────────────────────────────────────────────────┤
│ [Offset (i)] - present if OFF bit set                       │
├─────────────────────────────────────────────────────────────┤
│ [Length (i)] - present if LEN bit set                       │
├─────────────────────────────────────────────────────────────┤
│ Stream Data (...)                                           │
└─────────────────────────────────────────────────────────────┘

Flags:
- OFF: Offset field present
- LEN: Length field present
- FIN: Final frame in stream
```

#### Output yêu cầu:
```
📁 docs/
├── 06-quic-packet-format/
│   ├── long_header.md (1000+ từ)
│   ├── short_header.md (800+ từ)
│   ├── frame_types.md (1500+ từ)
│   ├── diagrams/
│   │   ├── long_header.png
│   │   ├── short_header.png
│   │   ├── stream_frame.png
│   │   └── packet_processing.png
│   └── packet_format_summary.md
```

---

## 📚 TUẦN 3: KIẾN TRÚC VÀ THIẾT KẾ HTTP/2 + SO SÁNH (15 giờ/người)

### 3.1 Nghiên cứu kiến trúc HTTP/2 (Thành viên 2)

**Thời gian:** 8 giờ | **Deadline:** Thứ 4, Tuần 3

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 3.1.1 | Đọc RFC 7540 Sections 1-4 | 2 giờ | Ghi chú |
| 3.1.2 | Nghiên cứu Binary Framing Layer | 1.5 giờ | Diagram |
| 3.1.3 | Nghiên cứu HPACK Header Compression | 1.5 giờ | Tài liệu |
| 3.1.4 | Nghiên cứu Server Push | 1 giờ | Tài liệu |
| 3.1.5 | Nghiên cứu Stream Prioritization | 1.5 giờ | Diagram |
| 3.1.6 | Viết tài liệu tổng hợp | 0.5 giờ | File .md |

#### Nội dung chi tiết:

**3.1.1 HTTP/2 Protocol Stack:**

```
┌─────────────────────────────────────────────────────┐
│              Application (HTTP Semantics)           │
│         GET, POST, PUT, DELETE, Headers, etc.       │
├─────────────────────────────────────────────────────┤
│              HTTP/2 Framing Layer                   │
│  ┌─────────────────────────────────────────────┐   │
│  │    Binary Framing    │   HPACK Compression  │   │
│  ├─────────────────────────────────────────────┤   │
│  │  Stream Multiplexing │  Flow Control        │   │
│  ├─────────────────────────────────────────────┤   │
│  │  Stream Prioritization │ Server Push        │   │
│  └─────────────────────────────────────────────┘   │
├─────────────────────────────────────────────────────┤
│                    TLS 1.2+                         │
├─────────────────────────────────────────────────────┤
│                      TCP                            │
├─────────────────────────────────────────────────────┤
│                       IP                            │
└─────────────────────────────────────────────────────┘
```

**3.1.2 Binary Framing Layer:**

```
HTTP/2 Frame Format:
┌─────────────────────────────────────────────────────────────┐
│                     Length (24 bits)                        │
├─────────────────────────────────────────────────────────────┤
│     Type (8)    │    Flags (8)    │ R │ Stream ID (31)     │
├─────────────────────────────────────────────────────────────┤
│                     Frame Payload                           │
│                        (variable)                           │
└─────────────────────────────────────────────────────────────┘
```

**HTTP/2 Frame Types:**

| Type | Value | Mô tả |
|------|-------|-------|
| DATA | 0x0 | Application data |
| HEADERS | 0x1 | HTTP headers |
| PRIORITY | 0x2 | Stream priority |
| RST_STREAM | 0x3 | Reset stream |
| SETTINGS | 0x4 | Connection settings |
| PUSH_PROMISE | 0x5 | Server push |
| PING | 0x6 | Connectivity check |
| GOAWAY | 0x7 | Connection shutdown |
| WINDOW_UPDATE | 0x8 | Flow control |
| CONTINUATION | 0x9 | Header continuation |

**3.1.3 HPACK Header Compression:**

```
HPACK Compression Components:
┌─────────────────────────────────────────────────────┐
│                  Static Table                       │
│    (61 pre-defined header name-value pairs)         │
│    :authority, :method GET, :path /, etc.           │
├─────────────────────────────────────────────────────┤
│                  Dynamic Table                      │
│    (Headers added during connection lifetime)       │
│    FIFO order, size limited by SETTINGS            │
├─────────────────────────────────────────────────────┤
│                Huffman Encoding                     │
│    (Optional compression of literal values)         │
└─────────────────────────────────────────────────────┘
```

**HPACK Encoding Methods:**

| Method | Khi sử dụng | Bits |
|--------|-------------|------|
| Indexed Header Field | Header trong table | 1xxxxxxx |
| Literal with Indexing | Add to dynamic table | 01xxxxxx |
| Literal without Indexing | Don't add to table | 0000xxxx |
| Literal Never Indexed | Sensitive data | 0001xxxx |

**3.1.4 Server Push:**

```
Server Push Flow:
┌─────────────┐                              ┌─────────────┐
│   Client    │                              │   Server    │
└──────┬──────┘                              └──────┬──────┘
       │                                            │
       │  ──────── HEADERS (GET /page.html) ──────►│
       │                                            │
       │  ◄──────── PUSH_PROMISE (/style.css) ─────│
       │  (Server promises to push resource)        │
       │                                            │
       │  ◄──────── HEADERS (response /page.html) ─│
       │  ◄──────── DATA (/page.html content) ─────│
       │                                            │
       │  ◄──────── HEADERS (response /style.css) ─│
       │  ◄──────── DATA (/style.css content) ─────│
       │  (Client receives pushed resource)         │
```

**3.1.5 Stream Prioritization:**

```
Priority Tree Example:
                    ┌─────────────┐
                    │   Root      │
                    │   (conn)    │
                    └──────┬──────┘
           ┌───────────────┼───────────────┐
           ▼               ▼               ▼
    ┌─────────────┐ ┌─────────────┐ ┌─────────────┐
    │  Stream 1   │ │  Stream 3   │ │  Stream 5   │
    │  Weight: 16 │ │  Weight: 8  │ │  Weight: 8  │
    │  (HTML)     │ │  (CSS)      │ │  (JS)       │
    └─────────────┘ └──────┬──────┘ └─────────────┘
                           ▼
                    ┌─────────────┐
                    │  Stream 7   │
                    │  Weight: 4  │
                    │  (Image)    │
                    └─────────────┘
```

**Priority Components:**
- [ ] **Stream Dependency:** Parent stream ID
- [ ] **Weight:** 1-256, determines resource allocation
- [ ] **Exclusive Flag:** Moves siblings under this stream

#### Output yêu cầu:
```
📁 docs/
├── 07-http2-architecture/
│   ├── http2_overview.md (2000+ từ)
│   ├── binary_framing.md (1500+ từ)
│   ├── hpack_compression.md (1500+ từ)
│   ├── server_push.md (1000+ từ)
│   ├── stream_prioritization.md (1000+ từ)
│   ├── diagrams/
│   │   ├── http2_stack.png
│   │   ├── frame_format.png
│   │   ├── hpack_tables.png
│   │   ├── server_push_flow.png
│   │   └── priority_tree.png
│   └── http2_summary.md
```

---

### 3.2 Nghiên cứu Stream Multiplexing trong HTTP/2 (Thành viên 1)

**Thời gian:** 5 giờ | **Deadline:** Thứ 5, Tuần 3

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 3.2.1 | Nghiên cứu Stream concept trong HTTP/2 | 1.5 giờ | Tài liệu |
| 3.2.2 | Phân tích Stream lifecycle | 1.5 giờ | State diagram |
| 3.2.3 | So sánh với QUIC stream multiplexing | 1.5 giờ | Bảng so sánh |
| 3.2.4 | Viết tài liệu tổng hợp | 0.5 giờ | File .md |

#### Nội dung chi tiết:

**3.2.1 Stream States in HTTP/2:**

```
HTTP/2 Stream State Machine:
                              ┌─────────────┐
                              │    idle     │
                              └──────┬──────┘
                     send H /        │        \ recv H
                  recv PUSH_PROMISE  │         recv PUSH_PROMISE
                              ┌──────┴──────┐
                     ┌────────│  reserved   │────────┐
                     │        │  (local)    │        │
                     │        └─────────────┘        │
                send H│                              │recv H
                     ▼                               ▼
              ┌─────────────┐                ┌─────────────┐
              │ half-closed │                │ half-closed │
              │  (remote)   │                │  (local)    │
              └──────┬──────┘                └──────┬──────┘
                     │send ES/recv R              │recv ES/send R
                     │                             │
                     └──────────┬──────────────────┘
                               ▼
                        ┌─────────────┐
                        │   closed    │
                        └─────────────┘

Legend:
H = HEADERS
ES = END_STREAM flag
R = RST_STREAM
```

**3.2.2 HTTP/2 vs QUIC Multiplexing:**

| Aspect | HTTP/2 | QUIC |
|--------|--------|------|
| Transport | Single TCP connection | Single UDP connection |
| HOL Blocking | TCP-level HOL blocking | No HOL blocking between streams |
| Stream IDs | 31-bit, odd=client, even=server | 62-bit, more flexible |
| Max Streams | Limited by SETTINGS | Limited by MAX_STREAMS |
| Stream Priority | Dependency tree | Priority hints (in HTTP/3) |
| Flow Control | Connection + Stream level | Connection + Stream level |

**HOL Blocking Problem:**

```
HTTP/2 over TCP (HOL Blocking):
┌─────────────────────────────────────────────────────┐
│                  TCP Connection                      │
│  ┌─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┐ │
│  │ S1  │ S2  │ S1  │ S3  │ S1  │ S2  │ S3  │ S1  │ │
│  │ P1  │ P1  │ P2  │ P1  │ P3  │ P2  │ P2  │ P4  │ │
│  └─────┴─────┴──X──┴─────┴─────┴─────┴─────┴─────┘ │
│                  │                                   │
│                  ▼ Packet lost!                      │
│        ALL streams blocked until retransmit         │
└─────────────────────────────────────────────────────┘

QUIC (No HOL Blocking):
┌─────────────────────────────────────────────────────┐
│                  QUIC Connection                     │
│  Stream 1: ┌─────┬─────┬──X──┬─────┐  ← Blocked    │
│            │ P1  │ P2  │lost │ P4  │                │
│            └─────┴─────┴─────┴─────┘                │
│                                                      │
│  Stream 2: ┌─────┬─────┐  ← NOT blocked!           │
│            │ P1  │ P2  │                            │
│            └─────┴─────┘                            │
│                                                      │
│  Stream 3: ┌─────┬─────┐  ← NOT blocked!           │
│            │ P1  │ P2  │                            │
│            └─────┴─────┘                            │
└─────────────────────────────────────────────────────┘
```

#### Output yêu cầu:
```
📁 docs/
├── 08-http2-multiplexing/
│   ├── stream_concept.md (1000+ từ)
│   ├── stream_lifecycle.md (800+ từ)
│   ├── hol_blocking_analysis.md (1000+ từ)
│   ├── diagrams/
│   │   ├── stream_state_machine.png
│   │   └── hol_blocking_comparison.png
│   └── multiplexing_summary.md
```

---

### 3.3 So sánh sơ bộ QUIC vs HTTP/2 (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Thứ 6, Tuần 3

#### Các bước thực hiện:

| Bước | Công việc cụ thể | Người thực hiện | Thời gian |
|------|------------------|-----------------|-----------|
| 3.3.1 | So sánh Connection Establishment | Thành viên 1 | 1 giờ |
| 3.3.2 | So sánh Security Model | Thành viên 2 | 1 giờ |
| 3.3.3 | So sánh Multiplexing & Flow Control | Thành viên 1 | 1 giờ |
| 3.3.4 | So sánh Error Recovery | Thành viên 2 | 1 giờ |
| 3.3.5 | Tổng hợp bảng so sánh | Cả 2 | 2 giờ |
| 3.3.6 | Thảo luận và finalize | Cả 2 | 2 giờ |

#### Bảng so sánh chi tiết QUIC vs HTTP/2:

| Tiêu chí | QUIC | HTTP/2 | Ưu thế |
|----------|------|--------|--------|
| **Transport Protocol** | UDP | TCP | QUIC (flexible) |
| **Connection Setup** | 1-RTT (0-RTT with resumption) | 2-3 RTT (TCP + TLS) | QUIC |
| **Encryption** | Built-in TLS 1.3 | Requires TLS layer | QUIC |
| **Header Compression** | QPACK | HPACK | Similar |
| **Multiplexing** | Independent streams | Single TCP | QUIC |
| **HOL Blocking** | No | Yes (TCP level) | QUIC |
| **Connection Migration** | Supported | Not supported | QUIC |
| **Congestion Control** | Pluggable | TCP's | QUIC |
| **Loss Recovery** | Per-stream | Entire connection | QUIC |
| **Maturity** | Newer (2021) | Mature (2015) | HTTP/2 |
| **Middlebox Support** | May be blocked | Well supported | HTTP/2 |
| **Implementation Complexity** | Higher | Lower | HTTP/2 |

#### Output yêu cầu:
```
📁 docs/
├── 09-comparison/
│   ├── connection_comparison.md
│   ├── security_comparison.md
│   ├── multiplexing_comparison.md
│   ├── error_recovery_comparison.md
│   ├── full_comparison_table.md (comprehensive)
│   └── preliminary_findings.md
```

---

### 3.4 Viết báo cáo Giai đoạn 1 (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Chủ nhật, Tuần 3

#### Cấu trúc báo cáo Giai đoạn 1:

```
📄 Báo cáo Giai đoạn 1
├── 1. Giới thiệu (500 từ) - Thành viên 1
│   ├── 1.1 Bối cảnh
│   ├── 1.2 Mục tiêu nghiên cứu
│   └── 1.3 Phạm vi nghiên cứu
│
├── 2. Lịch sử phát triển giao thức (1000 từ) - Thành viên 1
│   ├── 2.1 HTTP/1.x
│   ├── 2.2 HTTP/2
│   └── 2.3 QUIC/HTTP/3
│
├── 3. Kiến trúc QUIC (2000 từ) - Thành viên 1
│   ├── 3.1 Connection Establishment
│   ├── 3.2 Stream Multiplexing
│   ├── 3.3 Flow Control
│   ├── 3.4 Loss Detection & Recovery
│   └── 3.5 Connection Migration
│
├── 4. Kiến trúc HTTP/2 (1500 từ) - Thành viên 2
│   ├── 4.1 Binary Framing
│   ├── 4.2 Header Compression
│   ├── 4.3 Stream Multiplexing
│   └── 4.4 Server Push
│
├── 5. Bảo mật (1000 từ) - Thành viên 2
│   ├── 5.1 QUIC Security Model
│   └── 5.2 HTTP/2 + TLS
│
├── 6. So sánh sơ bộ (1000 từ) - Cả 2
│   └── 6.1 Bảng so sánh đầy đủ
│
└── 7. Kế hoạch giai đoạn tiếp theo (500 từ) - Cả 2
```

#### Output yêu cầu:
```
📁 reports/
├── phase1/
│   ├── phase1_report.pdf (8-10 trang)
│   ├── phase1_report.md (source)
│   └── figures/
│       └── (all diagrams used)
```

---

# ═══════════════════════════════════════════════════════════════════
# GIAI ĐOẠN 2: TRIỂN KHAI VÀ THỬ NGHIỆM (TUẦN 4-6)
# ═══════════════════════════════════════════════════════════════════

## 🔧 TUẦN 4: THIẾT LẬP MÔI TRƯỜNG THỬ NGHIỆM (20 giờ/người)

### 4.1 Thiết lập Server QUIC (Thành viên 1)

**Thời gian:** 12 giờ | **Deadline:** Thứ 6, Tuần 4

#### Yêu cầu hệ thống:

| Component | Minimum | Recommended |
|-----------|---------|-------------|
| OS | Ubuntu 20.04 | Ubuntu 22.04 |
| RAM | 4 GB | 8 GB |
| CPU | 2 cores | 4 cores |
| Storage | 20 GB | 50 GB |
| Network | 100 Mbps | 1 Gbps |

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 4.1.1 | Cài đặt dependencies | 1 giờ | System ready |
| 4.1.2 | Cài đặt Rust và cargo | 0.5 giờ | Rust installed |
| 4.1.3 | Clone và build quiche | 2 giờ | Binary compiled |
| 4.1.4 | Tạo SSL certificates | 0.5 giờ | Certs ready |
| 4.1.5 | Cấu hình QUIC server | 2 giờ | Config file |
| 4.1.6 | Test QUIC server locally | 1 giờ | Server running |
| 4.1.7 | Tạo test files (các kích thước) | 1 giờ | Test files |
| 4.1.8 | Viết script automation | 2 giờ | Scripts |
| 4.1.9 | Documentation | 2 giờ | README |

#### Chi tiết từng bước:

**Bước 4.1.1: Cài đặt dependencies**
```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install build dependencies
sudo apt install -y build-essential cmake git pkg-config libssl-dev

# Install additional tools
sudo apt install -y curl wget net-tools iperf3 tcpdump
```

**Bước 4.1.2: Cài đặt Rust**
```bash
# Install rustup
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Source the environment
source $HOME/.cargo/env

# Verify installation
rustc --version
cargo --version
```

**Bước 4.1.3: Build quiche (Cloudflare QUIC)**
```bash
# Clone quiche repository
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche

# Build quiche
cargo build --release --examples

# Verify build
ls -la target/release/examples/
# Should see: quiche-server, quiche-client
```

**Bước 4.1.4: Tạo SSL Certificates**
```bash
# Create certificates directory
mkdir -p ~/certs && cd ~/certs

# Generate private key
openssl genrsa -out server.key 2048

# Generate certificate signing request
openssl req -new -key server.key -out server.csr \
    -subj "/C=VN/ST=HCM/L=HCM/O=UIT/CN=quic-test-server"

# Generate self-signed certificate
openssl x509 -req -days 365 -in server.csr \
    -signkey server.key -out server.crt

# Verify certificate
openssl x509 -in server.crt -text -noout
```

**Bước 4.1.5: Cấu hình và chạy QUIC Server**
```bash
# Create server root directory
mkdir -p ~/quic-server/www

# Create test files of various sizes
cd ~/quic-server/www
dd if=/dev/zero of=1KB.bin bs=1K count=1
dd if=/dev/zero of=10KB.bin bs=1K count=10
dd if=/dev/zero of=100KB.bin bs=1K count=100
dd if=/dev/zero of=1MB.bin bs=1M count=1
dd if=/dev/zero of=10MB.bin bs=1M count=10
dd if=/dev/zero of=100MB.bin bs=1M count=100

# Create index.html
echo "<html><body><h1>QUIC Test Server</h1></body></html>" > index.html

# Start QUIC server
cd ~/quiche
./target/release/examples/quiche-server \
    --cert ~/certs/server.crt \
    --key ~/certs/server.key \
    --root ~/quic-server/www \
    --listen 0.0.0.0:4433
```

**Bước 4.1.6: Test QUIC Server**
```bash
# Test with quiche-client
./target/release/examples/quiche-client \
    --no-verify \
    https://127.0.0.1:4433/index.html

# Test file download
./target/release/examples/quiche-client \
    --no-verify \
    https://127.0.0.1:4433/1MB.bin \
    --output /tmp/test.bin

# Verify download
md5sum /tmp/test.bin ~/quic-server/www/1MB.bin
```

**Bước 4.1.7: Tạo Script tự động**
```bash
#!/bin/bash
# File: ~/scripts/start_quic_server.sh

QUICHE_DIR="$HOME/quiche"
CERT_DIR="$HOME/certs"
WWW_DIR="$HOME/quic-server/www"
PORT=4433
LOG_FILE="$HOME/logs/quic_server.log"

mkdir -p "$HOME/logs"

echo "Starting QUIC server on port $PORT..."
$QUICHE_DIR/target/release/examples/quiche-server \
    --cert $CERT_DIR/server.crt \
    --key $CERT_DIR/server.key \
    --root $WWW_DIR \
    --listen 0.0.0.0:$PORT \
    2>&1 | tee $LOG_FILE
```

#### Output yêu cầu:
```
📁 setup/
├── quic-server/
│   ├── README.md (installation guide)
│   ├── scripts/
│   │   ├── install_dependencies.sh
│   │   ├── build_quiche.sh
│   │   ├── generate_certs.sh
│   │   ├── start_server.sh
│   │   └── test_server.sh
│   ├── config/
│   │   └── server_config.toml
│   └── logs/
│       └── .gitkeep
```

---

### 4.2 Thiết lập Server HTTP/2 (Thành viên 2)

**Thời gian:** 10 giờ | **Deadline:** Thứ 6, Tuần 4

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 4.2.1 | Cài đặt nginx với HTTP/2 support | 1 giờ | nginx installed |
| 4.2.2 | Tạo SSL certificates | 0.5 giờ | Certs ready |
| 4.2.3 | Cấu hình nginx cho HTTP/2 | 2 giờ | Config file |
| 4.2.4 | Tạo test files | 1 giờ | Test files |
| 4.2.5 | Test HTTP/2 server | 1 giờ | Server verified |
| 4.2.6 | Tối ưu hóa cấu hình | 2 giờ | Optimized config |
| 4.2.7 | Viết script automation | 1.5 giờ | Scripts |
| 4.2.8 | Documentation | 1 giờ | README |

#### Chi tiết từng bước:

**Bước 4.2.1: Cài đặt nginx**
```bash
# Add nginx repository (for latest version)
sudo add-apt-repository ppa:nginx/stable -y
sudo apt update

# Install nginx
sudo apt install -y nginx

# Verify HTTP/2 support
nginx -V 2>&1 | grep -o 'http_v2_module'
# Should output: http_v2_module
```

**Bước 4.2.2: Tạo SSL Certificates**
```bash
# Create certificates directory
sudo mkdir -p /etc/nginx/ssl

# Generate certificates
sudo openssl req -x509 -nodes -days 365 \
    -newkey rsa:2048 \
    -keyout /etc/nginx/ssl/nginx.key \
    -out /etc/nginx/ssl/nginx.crt \
    -subj "/C=VN/ST=HCM/L=HCM/O=UIT/CN=http2-test-server"
```

**Bước 4.2.3: Cấu hình nginx cho HTTP/2**
```nginx
# File: /etc/nginx/sites-available/http2-test

server {
    listen 443 ssl http2;
    listen [::]:443 ssl http2;
    server_name localhost;

    # SSL Configuration
    ssl_certificate /etc/nginx/ssl/nginx.crt;
    ssl_certificate_key /etc/nginx/ssl/nginx.key;
    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256;
    ssl_prefer_server_ciphers off;

    # HTTP/2 specific settings
    http2_max_concurrent_streams 128;
    http2_max_field_size 16k;
    http2_max_header_size 32k;

    # Root directory
    root /var/www/http2-test;
    index index.html;

    # Logging
    access_log /var/log/nginx/http2-test-access.log;
    error_log /var/log/nginx/http2-test-error.log;

    location / {
        try_files $uri $uri/ =404;

        # Disable caching for testing
        add_header Cache-Control "no-store, no-cache, must-revalidate";
        expires 0;
    }

    # Enable server push for testing
    location = /index.html {
        http2_push /style.css;
        http2_push /script.js;
    }
}
```

**Bước 4.2.4: Tạo test files**
```bash
# Create www directory
sudo mkdir -p /var/www/http2-test

# Create test files of various sizes
cd /var/www/http2-test
sudo dd if=/dev/zero of=1KB.bin bs=1K count=1
sudo dd if=/dev/zero of=10KB.bin bs=1K count=10
sudo dd if=/dev/zero of=100KB.bin bs=1K count=100
sudo dd if=/dev/zero of=1MB.bin bs=1M count=1
sudo dd if=/dev/zero of=10MB.bin bs=1M count=10
sudo dd if=/dev/zero of=100MB.bin bs=1M count=100

# Create index.html
sudo tee /var/www/http2-test/index.html << EOF
<!DOCTYPE html>
<html>
<head>
    <title>HTTP/2 Test Server</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <h1>HTTP/2 Test Server</h1>
    <p>Server is running with HTTP/2 support.</p>
    <script src="script.js"></script>
</body>
</html>
EOF

# Create CSS and JS files for server push testing
echo "body { font-family: Arial; }" | sudo tee /var/www/http2-test/style.css
echo "console.log('HTTP/2 Test');" | sudo tee /var/www/http2-test/script.js

# Set permissions
sudo chown -R www-data:www-data /var/www/http2-test
```

**Bước 4.2.5: Enable và test server**
```bash
# Enable site
sudo ln -s /etc/nginx/sites-available/http2-test /etc/nginx/sites-enabled/

# Test configuration
sudo nginx -t

# Restart nginx
sudo systemctl restart nginx

# Test HTTP/2
curl -I --http2 -k https://localhost/
# Should see: HTTP/2 200

# Verify HTTP/2 with nghttp
sudo apt install -y nghttp2-client
nghttp -nv https://localhost/index.html
```

#### Output yêu cầu:
```
📁 setup/
├── http2-server/
│   ├── README.md
│   ├── nginx/
│   │   ├── http2-test.conf
│   │   └── nginx.conf (optimized)
│   ├── scripts/
│   │   ├── install_nginx.sh
│   │   ├── generate_certs.sh
│   │   ├── configure_http2.sh
│   │   └── test_http2.sh
│   └── www/
│       └── .gitkeep
```

---

### 4.3 Thiết lập Môi trường Mạng Giả lập (Thành viên 1)

**Thời gian:** 6 giờ | **Deadline:** Chủ nhật, Tuần 4

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 4.3.1 | Nghiên cứu tc/netem | 1 giờ | Notes |
| 4.3.2 | Viết scripts giả lập delay | 1 giờ | Scripts |
| 4.3.3 | Viết scripts giả lập packet loss | 1 giờ | Scripts |
| 4.3.4 | Viết scripts giả lập bandwidth | 1 giờ | Scripts |
| 4.3.5 | Viết scripts giả lập jitter | 1 giờ | Scripts |
| 4.3.6 | Test và verification | 1 giờ | Test results |

#### Scripts giả lập điều kiện mạng:

**Script tổng hợp network emulation:**
```bash
#!/bin/bash
# File: ~/scripts/network_emulation.sh

INTERFACE="eth0"  # Thay đổi theo interface thực tế

# Function to clear all tc rules
clear_tc() {
    sudo tc qdisc del dev $INTERFACE root 2>/dev/null
    echo "Cleared all tc rules on $INTERFACE"
}

# Function to add delay
add_delay() {
    local delay_ms=$1
    local jitter_ms=${2:-0}
    
    clear_tc
    if [ "$jitter_ms" -gt 0 ]; then
        sudo tc qdisc add dev $INTERFACE root netem delay ${delay_ms}ms ${jitter_ms}ms
        echo "Added ${delay_ms}ms delay with ${jitter_ms}ms jitter"
    else
        sudo tc qdisc add dev $INTERFACE root netem delay ${delay_ms}ms
        echo "Added ${delay_ms}ms delay"
    fi
}

# Function to add packet loss
add_loss() {
    local loss_percent=$1
    
    clear_tc
    sudo tc qdisc add dev $INTERFACE root netem loss ${loss_percent}%
    echo "Added ${loss_percent}% packet loss"
}

# Function to add bandwidth limit
add_bandwidth() {
    local rate=$1  # e.g., "10mbit", "100mbit"
    
    clear_tc
    sudo tc qdisc add dev $INTERFACE root tbf rate $rate burst 32kbit latency 400ms
    echo "Limited bandwidth to $rate"
}

# Function to add combined conditions
add_combined() {
    local delay_ms=$1
    local loss_percent=$2
    local rate=$3
    
    clear_tc
    sudo tc qdisc add dev $INTERFACE root handle 1: netem delay ${delay_ms}ms loss ${loss_percent}%
    sudo tc qdisc add dev $INTERFACE parent 1: handle 2: tbf rate $rate burst 32kbit latency 400ms
    echo "Added combined: ${delay_ms}ms delay, ${loss_percent}% loss, $rate bandwidth"
}

# Predefined network conditions
case "$1" in
    "clear")
        clear_tc
        ;;
    "good")
        # Good network: 10ms delay, 0% loss
        add_delay 10 2
        ;;
    "average")
        # Average network: 50ms delay, 0.1% loss
        add_combined 50 0.1 "100mbit"
        ;;
    "poor")
        # Poor network: 100ms delay, 1% loss
        add_combined 100 1 "50mbit"
        ;;
    "bad")
        # Bad network: 200ms delay, 5% loss
        add_combined 200 5 "10mbit"
        ;;
    "terrible")
        # Terrible network: 500ms delay, 10% loss
        add_combined 500 10 "5mbit"
        ;;
    "mobile_3g")
        # 3G mobile: 100ms delay, 2% loss, 2Mbps
        add_combined 100 2 "2mbit"
        ;;
    "mobile_4g")
        # 4G mobile: 50ms delay, 0.5% loss, 20Mbps
        add_combined 50 0.5 "20mbit"
        ;;
    "satellite")
        # Satellite: 600ms delay, 0.5% loss
        add_combined 600 0.5 "10mbit"
        ;;
    "custom")
        # Custom: delay jitter loss bandwidth
        add_delay $2 $3
        ;;
    *)
        echo "Usage: $0 {clear|good|average|poor|bad|terrible|mobile_3g|mobile_4g|satellite|custom}"
        echo ""
        echo "Predefined conditions:"
        echo "  good      - 10ms delay, 2ms jitter"
        echo "  average   - 50ms delay, 0.1% loss, 100Mbps"
        echo "  poor      - 100ms delay, 1% loss, 50Mbps"
        echo "  bad       - 200ms delay, 5% loss, 10Mbps"
        echo "  terrible  - 500ms delay, 10% loss, 5Mbps"
        echo "  mobile_3g - 100ms delay, 2% loss, 2Mbps"
        echo "  mobile_4g - 50ms delay, 0.5% loss, 20Mbps"
        echo "  satellite - 600ms delay, 0.5% loss, 10Mbps"
        ;;
esac
```

#### Bảng điều kiện mạng test:

| Condition | Delay | Jitter | Packet Loss | Bandwidth | Use Case |
|-----------|-------|--------|-------------|-----------|----------|
| Ideal | 1ms | 0ms | 0% | Unlimited | Baseline |
| LAN | 5ms | 1ms | 0% | 1Gbps | Local network |
| Good WAN | 20ms | 5ms | 0.1% | 100Mbps | Good internet |
| Average WAN | 50ms | 10ms | 0.5% | 50Mbps | Average internet |
| Poor WAN | 100ms | 30ms | 2% | 10Mbps | Poor internet |
| Mobile 4G | 50ms | 20ms | 1% | 20Mbps | Mobile network |
| Mobile 3G | 100ms | 50ms | 3% | 2Mbps | Poor mobile |
| Satellite | 600ms | 50ms | 1% | 10Mbps | Satellite link |

#### Output yêu cầu:
```
📁 setup/
├── network-emulation/
│   ├── README.md
│   ├── scripts/
│   │   ├── network_emulation.sh
│   │   ├── apply_delay.sh
│   │   ├── apply_loss.sh
│   │   ├── apply_bandwidth.sh
│   │   └── clear_all.sh
│   └── conditions/
│       └── network_conditions.md
```

---

### 4.4 Chuẩn bị Công cụ Đo lường (Thành viên 2)

**Thời gian:** 8 giờ | **Deadline:** Chủ nhật, Tuần 4

#### Các bước thực hiện chi tiết:

| Bước | Công việc cụ thể | Thời gian | Output |
|------|------------------|-----------|--------|
| 4.4.1 | Cài đặt Wireshark | 0.5 giờ | Wireshark ready |
| 4.4.2 | Cài đặt curl với HTTP/2 & HTTP/3 | 1 giờ | curl ready |
| 4.4.3 | Cài đặt h2load (benchmark HTTP/2) | 1 giờ | h2load ready |
| 4.4.4 | Viết benchmark scripts | 3 giờ | Scripts |
| 4.4.5 | Viết data collection scripts | 2 giờ | Scripts |
| 4.4.6 | Test tools | 0.5 giờ | Verification |

#### Chi tiết công cụ:

**Cài đặt curl với HTTP/2 & HTTP/3 support:**
```bash
# Install dependencies
sudo apt install -y libssl-dev libnghttp2-dev

# For HTTP/3 support, need to build curl with quiche
# Option 1: Use curl with HTTP/2 only (easier)
sudo apt install -y curl

# Verify HTTP/2 support
curl --version | grep -i http2

# Option 2: Build curl with quiche for HTTP/3 (advanced)
git clone https://github.com/curl/curl.git
cd curl
autoreconf -fi
./configure --with-openssl --with-nghttp2 --with-quiche=/path/to/quiche
make
sudo make install
```

**Benchmark Scripts:**

```bash
#!/bin/bash
# File: ~/scripts/benchmark_quic.sh

SERVER="127.0.0.1"
PORT="4433"
ITERATIONS=100
OUTPUT_DIR="$HOME/benchmark_results/quic"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# Test files
FILES=("1KB.bin" "10KB.bin" "100KB.bin" "1MB.bin" "10MB.bin")

echo "Starting QUIC benchmark at $TIMESTAMP"
echo "Server: $SERVER:$PORT"
echo "Iterations per file: $ITERATIONS"
echo ""

for file in "${FILES[@]}"; do
    echo "Testing $file..."
    OUTPUT_FILE="$OUTPUT_DIR/${TIMESTAMP}_${file%.bin}.csv"
    
    echo "iteration,start_time,end_time,duration_ms,bytes_received" > $OUTPUT_FILE
    
    for i in $(seq 1 $ITERATIONS); do
        START_TIME=$(date +%s.%N)
        
        # Run quiche-client and capture output
        $HOME/quiche/target/release/examples/quiche-client \
            --no-verify \
            https://$SERVER:$PORT/$file \
            --output /tmp/test_download 2>/dev/null
        
        END_TIME=$(date +%s.%N)
        DURATION=$(echo "($END_TIME - $START_TIME) * 1000" | bc)
        BYTES=$(stat -f%z /tmp/test_download 2>/dev/null || stat -c%s /tmp/test_download)
        
        echo "$i,$START_TIME,$END_TIME,$DURATION,$BYTES" >> $OUTPUT_FILE
        
        # Progress indicator
        if [ $((i % 10)) -eq 0 ]; then
            echo "  Progress: $i/$ITERATIONS"
        fi
    done
    
    echo "  Results saved to $OUTPUT_FILE"
    echo ""
done

echo "Benchmark completed!"
```

```bash
#!/bin/bash
# File: ~/scripts/benchmark_http2.sh

SERVER="127.0.0.1"
PORT="443"
ITERATIONS=100
OUTPUT_DIR="$HOME/benchmark_results/http2"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

FILES=("1KB.bin" "10KB.bin" "100KB.bin" "1MB.bin" "10MB.bin")

echo "Starting HTTP/2 benchmark at $TIMESTAMP"

for file in "${FILES[@]}"; do
    echo "Testing $file..."
    OUTPUT_FILE="$OUTPUT_DIR/${TIMESTAMP}_${file%.bin}.csv"
    
    echo "iteration,time_namelookup,time_connect,time_appconnect,time_pretransfer,time_starttransfer,time_total,size_download,speed_download" > $OUTPUT_FILE
    
    for i in $(seq 1 $ITERATIONS); do
        curl -k --http2 -s -o /dev/null \
            -w "%{time_namelookup},%{time_connect},%{time_appconnect},%{time_pretransfer},%{time_starttransfer},%{time_total},%{size_download},%{speed_download}" \
            https://$SERVER:$PORT/$file >> $OUTPUT_FILE
        echo "" >> $OUTPUT_FILE
        
        # Add iteration number
        sed -i "${i}s/^/$i,/" $OUTPUT_FILE 2>/dev/null || \
            sed -i '' "${i}s/^/$i,/" $OUTPUT_FILE
        
        if [ $((i % 10)) -eq 0 ]; then
            echo "  Progress: $i/$ITERATIONS"
        fi
    done
    
    echo "  Results saved to $OUTPUT_FILE"
done

echo "Benchmark completed!"
```

**h2load benchmark script:**
```bash
#!/bin/bash
# File: ~/scripts/benchmark_h2load.sh

SERVER="127.0.0.1"
PORT="443"
OUTPUT_DIR="$HOME/benchmark_results/h2load"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# Test configurations
CLIENTS=(1 10 50 100)
REQUESTS=(100 1000 10000)

for clients in "${CLIENTS[@]}"; do
    for requests in "${REQUESTS[@]}"; do
        echo "Testing with $clients clients, $requests requests..."
        
        OUTPUT_FILE="$OUTPUT_DIR/${TIMESTAMP}_c${clients}_n${requests}.txt"
        
        h2load -n $requests -c $clients \
            --h2 \
            https://$SERVER:$PORT/1KB.bin \
            > $OUTPUT_FILE 2>&1
        
        echo "  Results saved to $OUTPUT_FILE"
    done
done
```

#### Output yêu cầu:
```
📁 setup/
├── benchmarking/
│   ├── README.md
│   ├── scripts/
│   │   ├── benchmark_quic.sh
│   │   ├── benchmark_http2.sh
│   │   ├── benchmark_h2load.sh
│   │   ├── collect_data.sh
│   │   └── analyze_results.py
│   └── templates/
│       └── results_template.csv
```

---

## 🧪 TUẦN 5: THỰC HIỆN THỬ NGHIỆM HIỆU NĂNG (20 giờ/người)

### 5.1 Đo lường thời gian Handshake (Thành viên 1)

**Thời gian:** 8 giờ | **Deadline:** Thứ 5, Tuần 5

#### Mục tiêu thử nghiệm:
- So sánh thời gian connection establishment giữa QUIC và HTTP/2
- Đo lường trong các điều kiện mạng khác nhau
- Thu thập ít nhất 1000 samples cho mỗi điều kiện

#### Ma trận thử nghiệm Handshake:

| ID | Protocol | Condition | Delay | Loss | Samples | Status |
|----|----------|-----------|-------|------|---------|--------|
| H1 | QUIC | Ideal | 1ms | 0% | 1000 | [ ] |
| H2 | HTTP/2 | Ideal | 1ms | 0% | 1000 | [ ] |
| H3 | QUIC | Good | 20ms | 0% | 1000 | [ ] |
| H4 | HTTP/2 | Good | 20ms | 0% | 1000 | [ ] |
| H5 | QUIC | Average | 50ms | 0.5% | 1000 | [ ] |
| H6 | HTTP/2 | Average | 50ms | 0.5% | 1000 | [ ] |
| H7 | QUIC | Poor | 100ms | 2% | 1000 | [ ] |
| H8 | HTTP/2 | Poor | 100ms | 2% | 1000 | [ ] |
| H9 | QUIC | Bad | 200ms | 5% | 500 | [ ] |
| H10 | HTTP/2 | Bad | 200ms | 5% | 500 | [ ] |

#### Script đo handshake time:

```bash
#!/bin/bash
# File: ~/scripts/measure_handshake.sh

QUIC_SERVER="127.0.0.1:4433"
HTTP2_SERVER="127.0.0.1:443"
ITERATIONS=1000
OUTPUT_DIR="$HOME/results/handshake"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# Function to measure QUIC handshake
measure_quic_handshake() {
    local condition=$1
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_quic_${condition}.csv"
    
    echo "iteration,handshake_time_ms,total_time_ms" > $output_file
    
    for i in $(seq 1 $ITERATIONS); do
        # Use quiche-client with timing
        START=$(date +%s.%N)
        $HOME/quiche/target/release/examples/quiche-client \
            --no-verify \
            --wire-version 1 \
            https://$QUIC_SERVER/1KB.bin \
            --output /dev/null 2>&1
        END=$(date +%s.%N)
        
        TOTAL=$(echo "($END - $START) * 1000" | bc)
        # Handshake is approximately first RTT
        echo "$i,$TOTAL,$TOTAL" >> $output_file
        
        [ $((i % 100)) -eq 0 ] && echo "QUIC $condition: $i/$ITERATIONS"
    done
}

# Function to measure HTTP/2 handshake
measure_http2_handshake() {
    local condition=$1
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_http2_${condition}.csv"
    
    echo "iteration,dns_time,connect_time,ssl_time,total_handshake_ms" > $output_file
    
    for i in $(seq 1 $ITERATIONS); do
        RESULT=$(curl -k --http2 -s -o /dev/null \
            -w "%{time_namelookup},%{time_connect},%{time_appconnect}" \
            https://$HTTP2_SERVER/1KB.bin)
        
        DNS=$(echo $RESULT | cut -d',' -f1)
        CONNECT=$(echo $RESULT | cut -d',' -f2)
        SSL=$(echo $RESULT | cut -d',' -f3)
        
        # Handshake = TCP handshake + TLS handshake
        HANDSHAKE=$(echo "($SSL) * 1000" | bc)
        
        echo "$i,$DNS,$CONNECT,$SSL,$HANDSHAKE" >> $output_file
        
        [ $((i % 100)) -eq 0 ] && echo "HTTP/2 $condition: $i/$ITERATIONS"
    done
}

# Run tests for each network condition
CONDITIONS=("ideal" "good" "average" "poor" "bad")

for condition in "${CONDITIONS[@]}"; do
    echo "========================================="
    echo "Testing condition: $condition"
    echo "========================================="
    
    # Apply network condition
    ~/scripts/network_emulation.sh $condition
    sleep 2
    
    # Measure QUIC
    echo "Measuring QUIC handshake..."
    measure_quic_handshake $condition
    
    # Measure HTTP/2
    echo "Measuring HTTP/2 handshake..."
    measure_http2_handshake $condition
    
    # Clear network emulation
    ~/scripts/network_emulation.sh clear
    sleep 1
done

echo "All handshake measurements completed!"
echo "Results saved in $OUTPUT_DIR"
```

#### Metrics cần thu thập:

| Metric | QUIC | HTTP/2 | Unit |
|--------|------|--------|------|
| DNS Resolution | N/A | time_namelookup | ms |
| TCP Connect | N/A | time_connect - time_namelookup | ms |
| TLS Handshake | Included | time_appconnect - time_connect | ms |
| QUIC Handshake | Total | N/A | ms |
| Total Establishment | handshake_time | time_appconnect | ms |

#### Expected Results Format:

```csv
# quic_handshake_ideal.csv
iteration,handshake_time_ms,total_time_ms
1,12.34,15.67
2,11.89,14.23
...

# http2_handshake_ideal.csv  
iteration,dns_time,connect_time,ssl_time,total_handshake_ms
1,0.001,0.005,0.025,25.00
2,0.001,0.004,0.024,24.00
...
```

---

### 5.2 Đo lường Throughput (Thành viên 2)

**Thời gian:** 8 giờ | **Deadline:** Thứ 5, Tuần 5

#### Ma trận thử nghiệm Throughput:

| ID | Protocol | File Size | Condition | Samples | Status |
|----|----------|-----------|-----------|---------|--------|
| T1 | QUIC | 1KB | Ideal | 500 | [ ] |
| T2 | HTTP/2 | 1KB | Ideal | 500 | [ ] |
| T3 | QUIC | 10KB | Ideal | 500 | [ ] |
| T4 | HTTP/2 | 10KB | Ideal | 500 | [ ] |
| T5 | QUIC | 100KB | Ideal | 500 | [ ] |
| T6 | HTTP/2 | 100KB | Ideal | 500 | [ ] |
| T7 | QUIC | 1MB | Ideal | 300 | [ ] |
| T8 | HTTP/2 | 1MB | Ideal | 300 | [ ] |
| T9 | QUIC | 10MB | Ideal | 100 | [ ] |
| T10 | HTTP/2 | 10MB | Ideal | 100 | [ ] |
| T11-T20 | Both | All | Good | 300 | [ ] |
| T21-T30 | Both | All | Average | 300 | [ ] |
| T31-T40 | Both | All | Poor | 200 | [ ] |

#### Script đo throughput:

```bash
#!/bin/bash
# File: ~/scripts/measure_throughput.sh

QUIC_SERVER="127.0.0.1:4433"
HTTP2_SERVER="127.0.0.1:443"
OUTPUT_DIR="$HOME/results/throughput"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# File sizes to test
FILES=("1KB.bin" "10KB.bin" "100KB.bin" "1MB.bin" "10MB.bin")
ITERATIONS=(500 500 500 300 100)

# Function to get file size in bytes
get_file_size() {
    case $1 in
        "1KB.bin") echo 1024 ;;
        "10KB.bin") echo 10240 ;;
        "100KB.bin") echo 102400 ;;
        "1MB.bin") echo 1048576 ;;
        "10MB.bin") echo 10485760 ;;
        "100MB.bin") echo 104857600 ;;
    esac
}

# Function to measure QUIC throughput
measure_quic_throughput() {
    local condition=$1
    local file=$2
    local iterations=$3
    local file_size=$(get_file_size $file)
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_quic_${condition}_${file%.bin}.csv"
    
    echo "iteration,download_time_ms,bytes,throughput_mbps" > $output_file
    
    for i in $(seq 1 $iterations); do
        START=$(date +%s.%N)
        $HOME/quiche/target/release/examples/quiche-client \
            --no-verify \
            https://$QUIC_SERVER/$file \
            --output /tmp/download_test 2>/dev/null
        END=$(date +%s.%N)
        
        DURATION=$(echo "($END - $START) * 1000" | bc)
        THROUGHPUT=$(echo "scale=2; $file_size * 8 / ($DURATION / 1000) / 1000000" | bc)
        
        echo "$i,$DURATION,$file_size,$THROUGHPUT" >> $output_file
        
        [ $((i % 50)) -eq 0 ] && echo "QUIC $file $condition: $i/$iterations"
    done
}

# Function to measure HTTP/2 throughput
measure_http2_throughput() {
    local condition=$1
    local file=$2
    local iterations=$3
    local file_size=$(get_file_size $file)
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_http2_${condition}_${file%.bin}.csv"
    
    echo "iteration,download_time_ms,bytes,throughput_mbps,speed_download" > $output_file
    
    for i in $(seq 1 $iterations); do
        RESULT=$(curl -k --http2 -s -o /dev/null \
            -w "%{time_total},%{size_download},%{speed_download}" \
            https://$HTTP2_SERVER/$file)
        
        TIME_TOTAL=$(echo $RESULT | cut -d',' -f1)
        SIZE=$(echo $RESULT | cut -d',' -f2)
        SPEED=$(echo $RESULT | cut -d',' -f3)
        
        DURATION=$(echo "$TIME_TOTAL * 1000" | bc)
        THROUGHPUT=$(echo "scale=2; $SPEED * 8 / 1000000" | bc)
        
        echo "$i,$DURATION,$SIZE,$THROUGHPUT,$SPEED" >> $output_file
        
        [ $((i % 50)) -eq 0 ] && echo "HTTP/2 $file $condition: $i/$iterations"
    done
}

# Main test loop
CONDITIONS=("ideal" "good" "average" "poor")

for condition in "${CONDITIONS[@]}"; do
    echo "========================================="
    echo "Testing throughput - Condition: $condition"
    echo "========================================="
    
    # Apply network condition
    ~/scripts/network_emulation.sh $condition
    sleep 2
    
    for idx in ${!FILES[@]}; do
        file=${FILES[$idx]}
        iters=${ITERATIONS[$idx]}
        
        echo "Testing file: $file (${iters} iterations)"
        
        # Measure QUIC
        measure_quic_throughput $condition $file $iters
        
        # Measure HTTP/2
        measure_http2_throughput $condition $file $iters
    done
    
    # Clear network emulation
    ~/scripts/network_emulation.sh clear
    sleep 1
done

echo "All throughput measurements completed!"
```

---

### 5.3 Đo lường Latency (Thành viên 1)

**Thời gian:** 6 giờ | **Deadline:** Thứ 6, Tuần 5

#### Ma trận thử nghiệm Latency:

| ID | Protocol | Request Type | Condition | Samples | Status |
|----|----------|--------------|-----------|---------|--------|
| L1 | QUIC | Single request | Ideal | 1000 | [ ] |
| L2 | HTTP/2 | Single request | Ideal | 1000 | [ ] |
| L3 | QUIC | 10 sequential | Ideal | 500 | [ ] |
| L4 | HTTP/2 | 10 sequential | Ideal | 500 | [ ] |
| L5-L8 | Both | Single | Good-Poor | 500 | [ ] |
| L9-L12 | Both | Sequential | Good-Poor | 300 | [ ] |

#### Script đo latency:

```bash
#!/bin/bash
# File: ~/scripts/measure_latency.sh

OUTPUT_DIR="$HOME/results/latency"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# Measure Time To First Byte (TTFB)
measure_ttfb() {
    local protocol=$1
    local condition=$2
    local iterations=$3
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_${protocol}_ttfb_${condition}.csv"
    
    echo "iteration,ttfb_ms,total_time_ms" > $output_file
    
    for i in $(seq 1 $iterations); do
        if [ "$protocol" == "quic" ]; then
            START=$(date +%s.%N)
            $HOME/quiche/target/release/examples/quiche-client \
                --no-verify \
                https://127.0.0.1:4433/1KB.bin \
                --output /dev/null 2>/dev/null
            END=$(date +%s.%N)
            TTFB=$(echo "($END - $START) * 1000" | bc)
            TOTAL=$TTFB
        else
            RESULT=$(curl -k --http2 -s -o /dev/null \
                -w "%{time_starttransfer},%{time_total}" \
                https://127.0.0.1:443/1KB.bin)
            TTFB=$(echo "$(echo $RESULT | cut -d',' -f1) * 1000" | bc)
            TOTAL=$(echo "$(echo $RESULT | cut -d',' -f2) * 1000" | bc)
        fi
        
        echo "$i,$TTFB,$TOTAL" >> $output_file
        [ $((i % 100)) -eq 0 ] && echo "$protocol TTFB $condition: $i/$iterations"
    done
}

# Measure sequential request latency
measure_sequential() {
    local protocol=$1
    local condition=$2
    local num_requests=10
    local iterations=$3
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_${protocol}_sequential_${condition}.csv"
    
    echo "iteration,total_time_ms,avg_per_request_ms" > $output_file
    
    for i in $(seq 1 $iterations); do
        START=$(date +%s.%N)
        
        for j in $(seq 1 $num_requests); do
            if [ "$protocol" == "quic" ]; then
                $HOME/quiche/target/release/examples/quiche-client \
                    --no-verify \
                    https://127.0.0.1:4433/1KB.bin \
                    --output /dev/null 2>/dev/null
            else
                curl -k --http2 -s -o /dev/null \
                    https://127.0.0.1:443/1KB.bin
            fi
        done
        
        END=$(date +%s.%N)
        TOTAL=$(echo "($END - $START) * 1000" | bc)
        AVG=$(echo "scale=2; $TOTAL / $num_requests" | bc)
        
        echo "$i,$TOTAL,$AVG" >> $output_file
        [ $((i % 50)) -eq 0 ] && echo "$protocol sequential $condition: $i/$iterations"
    done
}

# Run tests
CONDITIONS=("ideal" "good" "average" "poor")

for condition in "${CONDITIONS[@]}"; do
    echo "Testing latency - Condition: $condition"
    
    ~/scripts/network_emulation.sh $condition
    sleep 2
    
    # TTFB tests
    measure_ttfb "quic" $condition 1000
    measure_ttfb "http2" $condition 1000
    
    # Sequential tests
    measure_sequential "quic" $condition 500
    measure_sequential "http2" $condition 500
    
    ~/scripts/network_emulation.sh clear
done

echo "Latency measurements completed!"
```

---

### 5.4 Thử nghiệm trong điều kiện mất gói (Thành viên 2)

**Thời gian:** 6 giờ | **Deadline:** Thứ 6, Tuần 5

#### Ma trận thử nghiệm Packet Loss:

| ID | Protocol | Loss Rate | File Size | Samples | Status |
|----|----------|-----------|-----------|---------|--------|
| PL1 | QUIC | 0.1% | 1MB | 300 | [ ] |
| PL2 | HTTP/2 | 0.1% | 1MB | 300 | [ ] |
| PL3 | QUIC | 0.5% | 1MB | 300 | [ ] |
| PL4 | HTTP/2 | 0.5% | 1MB | 300 | [ ] |
| PL5 | QUIC | 1% | 1MB | 300 | [ ] |
| PL6 | HTTP/2 | 1% | 1MB | 300 | [ ] |
| PL7 | QUIC | 2% | 1MB | 200 | [ ] |
| PL8 | HTTP/2 | 2% | 1MB | 200 | [ ] |
| PL9 | QUIC | 5% | 1MB | 200 | [ ] |
| PL10 | HTTP/2 | 5% | 1MB | 200 | [ ] |
| PL11 | QUIC | 10% | 1MB | 100 | [ ] |
| PL12 | HTTP/2 | 10% | 1MB | 100 | [ ] |

#### Script đo packet loss impact:

```bash
#!/bin/bash
# File: ~/scripts/measure_packet_loss.sh

OUTPUT_DIR="$HOME/results/packet_loss"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

LOSS_RATES=("0.1" "0.5" "1" "2" "5" "10")
ITERATIONS=(300 300 300 200 200 100)
FILE="1MB.bin"
FILE_SIZE=1048576

measure_with_loss() {
    local protocol=$1
    local loss_rate=$2
    local iterations=$3
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_${protocol}_loss${loss_rate}.csv"
    
    echo "iteration,download_time_ms,success,retransmissions" > $output_file
    
    for i in $(seq 1 $iterations); do
        START=$(date +%s.%N)
        
        if [ "$protocol" == "quic" ]; then
            RESULT=$($HOME/quiche/target/release/examples/quiche-client \
                --no-verify \
                https://127.0.0.1:4433/$FILE \
                --output /tmp/download_test 2>&1)
            SUCCESS=$?
        else
            curl -k --http2 -s -o /tmp/download_test \
                https://127.0.0.1:443/$FILE
            SUCCESS=$?
        fi
        
        END=$(date +%s.%N)
        DURATION=$(echo "($END - $START) * 1000" | bc)
        
        # Check if download was successful
        if [ $SUCCESS -eq 0 ] && [ -f /tmp/download_test ]; then
            DOWNLOADED_SIZE=$(stat -c%s /tmp/download_test 2>/dev/null || stat -f%z /tmp/download_test)
            if [ "$DOWNLOADED_SIZE" -eq "$FILE_SIZE" ]; then
                echo "$i,$DURATION,1,0" >> $output_file
            else
                echo "$i,$DURATION,0,0" >> $output_file
            fi
        else
            echo "$i,$DURATION,0,0" >> $output_file
        fi
        
        [ $((i % 50)) -eq 0 ] && echo "$protocol ${loss_rate}% loss: $i/$iterations"
    done
}

# Run tests for each loss rate
for idx in ${!LOSS_RATES[@]}; do
    loss=${LOSS_RATES[$idx]}
    iters=${ITERATIONS[$idx]}
    
    echo "========================================="
    echo "Testing with ${loss}% packet loss"
    echo "========================================="
    
    # Apply packet loss
    sudo tc qdisc del dev lo root 2>/dev/null
    sudo tc qdisc add dev lo root netem loss ${loss}%
    sleep 2
    
    # Test QUIC
    measure_with_loss "quic" $loss $iters
    
    # Test HTTP/2
    measure_with_loss "http2" $loss $iters
    
    # Clear
    sudo tc qdisc del dev lo root
    sleep 1
done

echo "Packet loss tests completed!"
```

---

## 🧪 TUẦN 6: THỬ NGHIỆM NÂNG CAO (20 giờ/người)

### 6.1 Thử nghiệm Multiplexing (Thành viên 1)

**Thời gian:** 8 giờ | **Deadline:** Thứ 5, Tuần 6

#### Ma trận thử nghiệm Multiplexing:

| ID | Protocol | Concurrent Streams | File Size | Samples | Status |
|----|----------|-------------------|-----------|---------|--------|
| M1 | QUIC | 1 | 100KB | 300 | [ ] |
| M2 | HTTP/2 | 1 | 100KB | 300 | [ ] |
| M3 | QUIC | 5 | 100KB | 300 | [ ] |
| M4 | HTTP/2 | 5 | 100KB | 300 | [ ] |
| M5 | QUIC | 10 | 100KB | 300 | [ ] |
| M6 | HTTP/2 | 10 | 100KB | 300 | [ ] |
| M7 | QUIC | 20 | 100KB | 200 | [ ] |
| M8 | HTTP/2 | 20 | 100KB | 200 | [ ] |
| M9 | QUIC | 50 | 100KB | 100 | [ ] |
| M10 | HTTP/2 | 50 | 100KB | 100 | [ ] |

#### Script thử nghiệm multiplexing:

```bash
#!/bin/bash
# File: ~/scripts/measure_multiplexing.sh

OUTPUT_DIR="$HOME/results/multiplexing"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

CONCURRENT=(1 5 10 20 50)
FILE="100KB.bin"

measure_concurrent_streams() {
    local protocol=$1
    local num_streams=$2
    local iterations=$3
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_${protocol}_streams${num_streams}.csv"
    
    echo "iteration,total_time_ms,avg_stream_time_ms,all_completed" > $output_file
    
    for i in $(seq 1 $iterations); do
        START=$(date +%s.%N)
        
        # Launch concurrent requests
        PIDS=()
        for j in $(seq 1 $num_streams); do
            if [ "$protocol" == "quic" ]; then
                $HOME/quiche/target/release/examples/quiche-client \
                    --no-verify \
                    https://127.0.0.1:4433/$FILE \
                    --output /tmp/stream_$j 2>/dev/null &
            else
                curl -k --http2 -s -o /tmp/stream_$j \
                    https://127.0.0.1:443/$FILE &
            fi
            PIDS+=($!)
        done
        
        # Wait for all to complete
        ALL_SUCCESS=1
        for pid in "${PIDS[@]}"; do
            wait $pid || ALL_SUCCESS=0
        done
        
        END=$(date +%s.%N)
        TOTAL=$(echo "($END - $START) * 1000" | bc)
        AVG=$(echo "scale=2; $TOTAL / $num_streams" | bc)
        
        echo "$i,$TOTAL,$AVG,$ALL_SUCCESS" >> $output_file
        
        # Cleanup
        rm -f /tmp/stream_*
        
        [ $((i % 30)) -eq 0 ] && echo "$protocol ${num_streams} streams: $i/$iterations"
    done
}

# Test different concurrency levels
for num in "${CONCURRENT[@]}"; do
    case $num in
        1|5|10) iters=300 ;;
        20) iters=200 ;;
        50) iters=100 ;;
    esac
    
    echo "Testing $num concurrent streams..."
    
    measure_concurrent_streams "quic" $num $iters
    measure_concurrent_streams "http2" $num $iters
done

echo "Multiplexing tests completed!"
```

#### Metrics cần thu thập:

| Metric | Mô tả | Unit |
|--------|-------|------|
| Total Completion Time | Thời gian hoàn thành tất cả streams | ms |
| Average Stream Time | Thời gian trung bình mỗi stream | ms |
| Success Rate | Tỷ lệ streams hoàn thành thành công | % |
| Throughput per Stream | Throughput trung bình mỗi stream | Mbps |
| Total Throughput | Tổng throughput | Mbps |

---

### 6.2 Thử nghiệm điều kiện mạng không ổn định (Thành viên 2)

**Thời gian:** 8 giờ | **Deadline:** Thứ 5, Tuần 6

#### Ma trận thử nghiệm Jitter:

| ID | Protocol | Delay | Jitter | File Size | Samples | Status |
|----|----------|-------|--------|-----------|---------|--------|
| J1 | QUIC | 50ms | 10ms | 1MB | 300 | [ ] |
| J2 | HTTP/2 | 50ms | 10ms | 1MB | 300 | [ ] |
| J3 | QUIC | 50ms | 25ms | 1MB | 300 | [ ] |
| J4 | HTTP/2 | 50ms | 25ms | 1MB | 300 | [ ] |
| J5 | QUIC | 50ms | 50ms | 1MB | 300 | [ ] |
| J6 | HTTP/2 | 50ms | 50ms | 1MB | 300 | [ ] |
| J7 | QUIC | 100ms | 50ms | 1MB | 200 | [ ] |
| J8 | HTTP/2 | 100ms | 50ms | 1MB | 200 | [ ] |

#### Ma trận thử nghiệm Variable Bandwidth:

| ID | Protocol | Initial BW | Pattern | Duration | Samples | Status |
|----|----------|------------|---------|----------|---------|--------|
| BW1 | QUIC | 50Mbps | Constant | 30s | 50 | [ ] |
| BW2 | HTTP/2 | 50Mbps | Constant | 30s | 50 | [ ] |
| BW3 | QUIC | 50→10Mbps | Step down | 30s | 50 | [ ] |
| BW4 | HTTP/2 | 50→10Mbps | Step down | 30s | 50 | [ ] |
| BW5 | QUIC | 10→50Mbps | Step up | 30s | 50 | [ ] |
| BW6 | HTTP/2 | 10→50Mbps | Step up | 30s | 50 | [ ] |

#### Script thử nghiệm jitter:

```bash
#!/bin/bash
# File: ~/scripts/measure_jitter.sh

OUTPUT_DIR="$HOME/results/jitter"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# Test configurations: delay,jitter
CONFIGS=("50,10" "50,25" "50,50" "100,50")
FILE="1MB.bin"

measure_with_jitter() {
    local protocol=$1
    local delay=$2
    local jitter=$3
    local iterations=$4
    local output_file="$OUTPUT_DIR/${TIMESTAMP}_${protocol}_d${delay}_j${jitter}.csv"
    
    echo "iteration,download_time_ms,throughput_mbps" > $output_file
    
    for i in $(seq 1 $iterations); do
        START=$(date +%s.%N)
        
        if [ "$protocol" == "quic" ]; then
            $HOME/quiche/target/release/examples/quiche-client \
                --no-verify \
                https://127.0.0.1:4433/$FILE \
                --output /tmp/download_test 2>/dev/null
        else
            curl -k --http2 -s -o /tmp/download_test \
                https://127.0.0.1:443/$FILE
        fi
        
        END=$(date +%s.%N)
        DURATION=$(echo "($END - $START) * 1000" | bc)
        THROUGHPUT=$(echo "scale=2; 1048576 * 8 / ($DURATION / 1000) / 1000000" | bc)
        
        echo "$i,$DURATION,$THROUGHPUT" >> $output_file
        
        [ $((i % 50)) -eq 0 ] && echo "$protocol d${delay}ms j${jitter}ms: $i/$iterations"
    done
}

# Run jitter tests
for config in "${CONFIGS[@]}"; do
    delay=$(echo $config | cut -d',' -f1)
    jitter=$(echo $config | cut -d',' -f2)
    
    case "$jitter" in
        10|25) iters=300 ;;
        50) iters=200 ;;
    esac
    
    echo "Testing delay=${delay}ms, jitter=${jitter}ms..."
    
    # Apply jitter
    sudo tc qdisc del dev lo root 2>/dev/null
    sudo tc qdisc add dev lo root netem delay ${delay}ms ${jitter}ms distribution normal
    sleep 2
    
    measure_with_jitter "quic" $delay $jitter $iters
    measure_with_jitter "http2" $delay $jitter $iters
    
    sudo tc qdisc del dev lo root
done

echo "Jitter tests completed!"
```

---

### 6.3 Thử nghiệm 0-RTT Resumption (Thành viên 1)

**Thời gian:** 6 giờ | **Deadline:** Thứ 6, Tuần 6

#### Mục tiêu:
- Đo lường lợi ích của 0-RTT connection resumption trong QUIC
- So sánh với HTTP/2 session resumption

#### Ma trận thử nghiệm 0-RTT:

| ID | Protocol | Connection Type | Delay | Samples | Status |
|----|----------|-----------------|-------|---------|--------|
| 0R1 | QUIC | New connection | 50ms | 500 | [ ] |
| 0R2 | QUIC | 0-RTT resumption | 50ms | 500 | [ ] |
| 0R3 | HTTP/2 | New connection | 50ms | 500 | [ ] |
| 0R4 | HTTP/2 | Session resumption | 50ms | 500 | [ ] |
| 0R5 | QUIC | New connection | 100ms | 500 | [ ] |
| 0R6 | QUIC | 0-RTT resumption | 100ms | 500 | [ ] |

#### Script thử nghiệm 0-RTT:

```bash
#!/bin/bash
# File: ~/scripts/measure_0rtt.sh

OUTPUT_DIR="$HOME/results/0rtt"
TIMESTAMP=$(date +%Y%m%d_%H%M%S)

mkdir -p $OUTPUT_DIR

# For QUIC 0-RTT, need to establish session first
measure_quic_0rtt() {
    local delay=$1
    local iterations=$2
    local output_new="$OUTPUT_DIR/${TIMESTAMP}_quic_new_d${delay}.csv"
    local output_resume="$OUTPUT_DIR/${TIMESTAMP}_quic_0rtt_d${delay}.csv"
    
    echo "iteration,handshake_time_ms,request_time_ms" > $output_new
    echo "iteration,handshake_time_ms,request_time_ms" > $output_resume
    
    # Clear session cache
    rm -f /tmp/quic_session_*
    
    for i in $(seq 1 $iterations); do
        # Test 1: New connection (no 0-RTT)
        START=$(date +%s.%N)
        $HOME/quiche/target/release/examples/quiche-client \
            --no-verify \
            --session-file /tmp/quic_session_new_$i \
            https://127.0.0.1:4433/1KB.bin \
            --output /dev/null 2>/dev/null
        END=$(date +%s.%N)
        NEW_TIME=$(echo "($END - $START) * 1000" | bc)
        echo "$i,$NEW_TIME,$NEW_TIME" >> $output_new
        
        # Small delay between tests
        sleep 0.1
        
        # Test 2: 0-RTT resumption (reuse session)
        START=$(date +%s.%N)
        $HOME/quiche/target/release/examples/quiche-client \
            --no-verify \
            --session-file /tmp/quic_session_new_$i \
            --early-data \
            https://127.0.0.1:4433/1KB.bin \
            --output /dev/null 2>/dev/null
        END=$(date +%s.%N)
        RESUME_TIME=$(echo "($END - $START) * 1000" | bc)
        echo "$i,$RESUME_TIME,$RESUME_TIME" >> $output_resume
        
        # Cleanup
        rm -f /tmp/quic_session_new_$i
        
        [ $((i % 100)) -eq 0 ] && echo "QUIC 0-RTT d${delay}ms: $i/$iterations"
    done
}

# Test with different delays
DELAYS=(50 100 200)

for delay in "${DELAYS[@]}"; do
    echo "Testing 0-RTT with ${delay}ms delay..."
    
    sudo tc qdisc del dev lo root 2>/dev/null
    sudo tc qdisc add dev lo root netem delay ${delay}ms
    sleep 2
    
    measure_quic_0rtt $delay 500
    
    sudo tc qdisc del dev lo root
done

echo "0-RTT tests completed!"
```

---

### 6.4 Ghi chép và Tổng hợp Dữ liệu (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Chủ nhật, Tuần 6

#### Checklist tổng hợp dữ liệu:

| Thử nghiệm | File Output | Thành viên | Status |
|------------|-------------|------------|--------|
| Handshake Time | handshake/*.csv | TV1 | [ ] |
| Throughput | throughput/*.csv | TV2 | [ ] |
| Latency | latency/*.csv | TV1 | [ ] |
| Packet Loss | packet_loss/*.csv | TV2 | [ ] |
| Multiplexing | multiplexing/*.csv | TV1 | [ ] |
| Jitter | jitter/*.csv | TV2 | [ ] |
| 0-RTT | 0rtt/*.csv | TV1 | [ ] |

#### Cấu trúc thư mục kết quả:

```
📁 results/
├── handshake/
│   ├── 20260129_quic_ideal.csv
│   ├── 20260129_http2_ideal.csv
│   ├── 20260129_quic_good.csv
│   └── ...
├── throughput/
│   ├── 20260129_quic_ideal_1KB.csv
│   ├── 20260129_http2_ideal_1KB.csv
│   └── ...
├── latency/
│   ├── 20260129_quic_ttfb_ideal.csv
│   └── ...
├── packet_loss/
│   ├── 20260129_quic_loss0.1.csv
│   └── ...
├── multiplexing/
│   ├── 20260129_quic_streams5.csv
│   └── ...
├── jitter/
│   ├── 20260129_quic_d50_j10.csv
│   └── ...
├── 0rtt/
│   ├── 20260129_quic_new_d50.csv
│   └── ...
└── summary/
    └── all_experiments_summary.xlsx
```

#### Script tổng hợp dữ liệu:

```python
#!/usr/bin/env python3
# File: ~/scripts/aggregate_results.py

import os
import pandas as pd
import glob
from datetime import datetime

RESULTS_DIR = os.path.expanduser("~/results")
OUTPUT_DIR = os.path.join(RESULTS_DIR, "summary")
os.makedirs(OUTPUT_DIR, exist_ok=True)

def aggregate_experiment(experiment_dir, experiment_name):
    """Aggregate all CSV files from an experiment directory."""
    files = glob.glob(os.path.join(experiment_dir, "*.csv"))
    
    summary_data = []
    
    for file in files:
        df = pd.read_csv(file)
        filename = os.path.basename(file)
        
        # Extract metadata from filename
        parts = filename.replace(".csv", "").split("_")
        
        stats = {
            "filename": filename,
            "protocol": "quic" if "quic" in filename else "http2",
            "count": len(df),
            "mean": df.iloc[:, 1].mean(),  # Assuming time/metric is 2nd column
            "std": df.iloc[:, 1].std(),
            "min": df.iloc[:, 1].min(),
            "max": df.iloc[:, 1].max(),
            "median": df.iloc[:, 1].median(),
            "p95": df.iloc[:, 1].quantile(0.95),
            "p99": df.iloc[:, 1].quantile(0.99),
        }
        
        summary_data.append(stats)
    
    return pd.DataFrame(summary_data)

def main():
    experiments = ["handshake", "throughput", "latency", "packet_loss", 
                   "multiplexing", "jitter", "0rtt"]
    
    all_summaries = {}
    
    for exp in experiments:
        exp_dir = os.path.join(RESULTS_DIR, exp)
        if os.path.exists(exp_dir):
            print(f"Aggregating {exp}...")
            summary = aggregate_experiment(exp_dir, exp)
            all_summaries[exp] = summary
            
            # Save individual summary
            summary.to_csv(os.path.join(OUTPUT_DIR, f"{exp}_summary.csv"), index=False)
    
    # Create Excel file with all summaries
    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    excel_file = os.path.join(OUTPUT_DIR, f"all_experiments_summary_{timestamp}.xlsx")
    
    with pd.ExcelWriter(excel_file) as writer:
        for exp, summary in all_summaries.items():
            summary.to_excel(writer, sheet_name=exp, index=False)
    
    print(f"Summary saved to {excel_file}")

if __name__ == "__main__":
    main()
```

---

# ═══════════════════════════════════════════════════════════════════
# GIAI ĐOẠN 3: PHÂN TÍCH VÀ SO SÁNH (TUẦN 7-8)
# ═══════════════════════════════════════════════════════════════════

## 📊 TUẦN 7: PHÂN TÍCH DỮ LIỆU (15 giờ/người)

### 7.1 Xử lý và Làm sạch Dữ liệu (Thành viên 1)

**Thời gian:** 6 giờ | **Deadline:** Thứ 4, Tuần 7

#### Các bước xử lý dữ liệu:

| Bước | Công việc | Thời gian | Output |
|------|-----------|-----------|--------|
| 7.1.1 | Load và inspect tất cả CSV files | 1 giờ | Data overview |
| 7.1.2 | Identify và handle missing values | 1 giờ | Clean data |
| 7.1.3 | Detect và remove outliers | 1.5 giờ | Filtered data |
| 7.1.4 | Calculate statistical summaries | 1.5 giờ | Statistics |
| 7.1.5 | Validate data integrity | 1 giờ | Validation report |

#### Script xử lý dữ liệu:

```python
#!/usr/bin/env python3
# File: ~/scripts/data_processing.py

import pandas as pd
import numpy as np
from scipy import stats
import os
import glob

class DataProcessor:
    def __init__(self, results_dir):
        self.results_dir = results_dir
        self.processed_dir = os.path.join(results_dir, "processed")
        os.makedirs(self.processed_dir, exist_ok=True)
    
    def load_experiment_data(self, experiment):
        """Load all CSV files for an experiment."""
        pattern = os.path.join(self.results_dir, experiment, "*.csv")
        files = glob.glob(pattern)
        
        data = {}
        for file in files:
            name = os.path.basename(file).replace(".csv", "")
            df = pd.read_csv(file)
            data[name] = df
        
        return data
    
    def remove_outliers_iqr(self, df, column, multiplier=1.5):
        """Remove outliers using IQR method."""
        Q1 = df[column].quantile(0.25)
        Q3 = df[column].quantile(0.75)
        IQR = Q3 - Q1
        
        lower_bound = Q1 - multiplier * IQR
        upper_bound = Q3 + multiplier * IQR
        
        original_count = len(df)
        df_clean = df[(df[column] >= lower_bound) & (df[column] <= upper_bound)]
        removed_count = original_count - len(df_clean)
        
        return df_clean, removed_count
    
    def remove_outliers_zscore(self, df, column, threshold=3):
        """Remove outliers using Z-score method."""
        z_scores = np.abs(stats.zscore(df[column]))
        original_count = len(df)
        df_clean = df[z_scores < threshold]
        removed_count = original_count - len(df_clean)
        
        return df_clean, removed_count
    
    def calculate_statistics(self, df, column):
        """Calculate comprehensive statistics."""
        return {
            "count": len(df),
            "mean": df[column].mean(),
            "std": df[column].std(),
            "min": df[column].min(),
            "max": df[column].max(),
            "median": df[column].median(),
            "q1": df[column].quantile(0.25),
            "q3": df[column].quantile(0.75),
            "p90": df[column].quantile(0.90),
            "p95": df[column].quantile(0.95),
            "p99": df[column].quantile(0.99),
            "skewness": df[column].skew(),
            "kurtosis": df[column].kurtosis(),
        }
    
    def process_handshake_data(self):
        """Process handshake experiment data."""
        data = self.load_experiment_data("handshake")
        
        results = []
        for name, df in data.items():
            # Determine time column (varies by protocol)
            if 'handshake_time_ms' in df.columns:
                time_col = 'handshake_time_ms'
            elif 'total_handshake_ms' in df.columns:
                time_col = 'total_handshake_ms'
            else:
                time_col = df.columns[1]  # Assume second column
            
            # Remove outliers
            df_clean, removed = self.remove_outliers_iqr(df, time_col)
            
            # Calculate statistics
            stats = self.calculate_statistics(df_clean, time_col)
            stats['experiment'] = name
            stats['outliers_removed'] = removed
            stats['protocol'] = 'quic' if 'quic' in name else 'http2'
            stats['condition'] = name.split('_')[-1]
            
            results.append(stats)
            
            # Save processed data
            output_file = os.path.join(self.processed_dir, f"processed_{name}.csv")
            df_clean.to_csv(output_file, index=False)
        
        return pd.DataFrame(results)
    
    def process_throughput_data(self):
        """Process throughput experiment data."""
        data = self.load_experiment_data("throughput")
        
        results = []
        for name, df in data.items():
            time_col = 'download_time_ms' if 'download_time_ms' in df.columns else df.columns[1]
            
            # Remove outliers
            df_clean, removed = self.remove_outliers_iqr(df, time_col)
            
            # Calculate statistics
            stats = self.calculate_statistics(df_clean, time_col)
            stats['experiment'] = name
            stats['outliers_removed'] = removed
            
            # Parse protocol and file size from name
            parts = name.split('_')
            stats['protocol'] = 'quic' if 'quic' in name else 'http2'
            stats['file_size'] = parts[-1] if parts[-1].endswith('KB') or parts[-1].endswith('MB') else 'unknown'
            
            # Calculate throughput statistics if available
            if 'throughput_mbps' in df_clean.columns:
                tp_stats = self.calculate_statistics(df_clean, 'throughput_mbps')
                stats['throughput_mean'] = tp_stats['mean']
                stats['throughput_std'] = tp_stats['std']
            
            results.append(stats)
        
        return pd.DataFrame(results)
    
    def validate_data(self, df, expected_count):
        """Validate data integrity."""
        issues = []
        
        # Check sample count
        if len(df) < expected_count * 0.9:  # Allow 10% tolerance
            issues.append(f"Low sample count: {len(df)} < {expected_count * 0.9}")
        
        # Check for negative values (shouldn't exist for time measurements)
        for col in df.select_dtypes(include=[np.number]).columns:
            if (df[col] < 0).any():
                issues.append(f"Negative values found in {col}")
        
        # Check for extreme values
        for col in df.select_dtypes(include=[np.number]).columns:
            z_scores = np.abs(stats.zscore(df[col]))
            extreme_count = (z_scores > 5).sum()
            if extreme_count > len(df) * 0.01:  # More than 1% extreme values
                issues.append(f"High extreme values in {col}: {extreme_count}")
        
        return issues


def main():
    processor = DataProcessor(os.path.expanduser("~/results"))
    
    print("Processing handshake data...")
    handshake_stats = processor.process_handshake_data()
    handshake_stats.to_csv(os.path.join(processor.processed_dir, "handshake_summary.csv"), index=False)
    print(handshake_stats)
    
    print("\nProcessing throughput data...")
    throughput_stats = processor.process_throughput_data()
    throughput_stats.to_csv(os.path.join(processor.processed_dir, "throughput_summary.csv"), index=False)
    print(throughput_stats)


if __name__ == "__main__":
    main()
```

---

### 7.2 Tạo Biểu đồ So sánh (Thành viên 2)

**Thời gian:** 6 giờ | **Deadline:** Thứ 4, Tuần 7

#### Danh sách biểu đồ cần tạo:

| ID | Loại biểu đồ | Nội dung | Định dạng |
|----|--------------|----------|-----------|
| C1 | Bar chart | Handshake time comparison | PNG, PDF |
| C2 | Line chart | Throughput vs file size | PNG, PDF |
| C3 | Box plot | Latency distribution | PNG, PDF |
| C4 | Line chart | Throughput vs packet loss | PNG, PDF |
| C5 | Bar chart | Multiplexing performance | PNG, PDF |
| C6 | Scatter plot | Jitter vs performance | PNG, PDF |
| C7 | Bar chart | 0-RTT improvement | PNG, PDF |
| C8 | Heatmap | Overall comparison matrix | PNG, PDF |

#### Script tạo biểu đồ:

```python
#!/usr/bin/env python3
# File: ~/scripts/create_charts.py

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import os

# Set style
plt.style.use('seaborn-v0_8-whitegrid')
sns.set_palette("husl")

RESULTS_DIR = os.path.expanduser("~/results/processed")
CHARTS_DIR = os.path.expanduser("~/results/charts")
os.makedirs(CHARTS_DIR, exist_ok=True)

def create_handshake_comparison():
    """Create handshake time comparison chart."""
    df = pd.read_csv(os.path.join(RESULTS_DIR, "handshake_summary.csv"))
    
    fig, ax = plt.subplots(figsize=(12, 6))
    
    conditions = df['condition'].unique()
    x = np.arange(len(conditions))
    width = 0.35
    
    quic_data = df[df['protocol'] == 'quic'].set_index('condition')
    http2_data = df[df['protocol'] == 'http2'].set_index('condition')
    
    bars1 = ax.bar(x - width/2, quic_data.loc[conditions, 'mean'], width, 
                   yerr=quic_data.loc[conditions, 'std'], label='QUIC', 
                   color='#2ecc71', capsize=5)
    bars2 = ax.bar(x + width/2, http2_data.loc[conditions, 'mean'], width,
                   yerr=http2_data.loc[conditions, 'std'], label='HTTP/2',
                   color='#3498db', capsize=5)
    
    ax.set_xlabel('Network Condition', fontsize=12)
    ax.set_ylabel('Handshake Time (ms)', fontsize=12)
    ax.set_title('QUIC vs HTTP/2: Connection Establishment Time', fontsize=14)
    ax.set_xticks(x)
    ax.set_xticklabels(conditions)
    ax.legend()
    
    # Add value labels
    for bars in [bars1, bars2]:
        for bar in bars:
            height = bar.get_height()
            ax.annotate(f'{height:.1f}',
                       xy=(bar.get_x() + bar.get_width() / 2, height),
                       xytext=(0, 3), textcoords="offset points",
                       ha='center', va='bottom', fontsize=9)
    
    plt.tight_layout()
    plt.savefig(os.path.join(CHARTS_DIR, 'handshake_comparison.png'), dpi=300)
    plt.savefig(os.path.join(CHARTS_DIR, 'handshake_comparison.pdf'))
    plt.close()
    
    print("Created handshake comparison chart")


def create_throughput_chart():
    """Create throughput vs file size chart."""
    df = pd.read_csv(os.path.join(RESULTS_DIR, "throughput_summary.csv"))
    
    fig, ax = plt.subplots(figsize=(12, 6))
    
    # Filter for ideal condition
    df_ideal = df[df['experiment'].str.contains('ideal')]
    
    file_sizes = ['1KB', '10KB', '100KB', '1MB', '10MB']
    
    quic_throughput = []
    http2_throughput = []
    
    for size in file_sizes:
        quic_row = df_ideal[(df_ideal['protocol'] == 'quic') & 
                            (df_ideal['file_size'] == size)]
        http2_row = df_ideal[(df_ideal['protocol'] == 'http2') & 
                             (df_ideal['file_size'] == size)]
        
        quic_throughput.append(quic_row['throughput_mean'].values[0] if len(quic_row) > 0 else 0)
        http2_throughput.append(http2_row['throughput_mean'].values[0] if len(http2_row) > 0 else 0)
    
    x = np.arange(len(file_sizes))
    
    ax.plot(x, quic_throughput, 'o-', label='QUIC', color='#2ecc71', linewidth=2, markersize=8)
    ax.plot(x, http2_throughput, 's-', label='HTTP/2', color='#3498db', linewidth=2, markersize=8)
    
    ax.set_xlabel('File Size', fontsize=12)
    ax.set_ylabel('Throughput (Mbps)', fontsize=12)
    ax.set_title('QUIC vs HTTP/2: Throughput by File Size', fontsize=14)
    ax.set_xticks(x)
    ax.set_xticklabels(file_sizes)
    ax.legend()
    ax.grid(True, alpha=0.3)
    
    plt.tight_layout()
    plt.savefig(os.path.join(CHARTS_DIR, 'throughput_vs_filesize.png'), dpi=300)
    plt.savefig(os.path.join(CHARTS_DIR, 'throughput_vs_filesize.pdf'))
    plt.close()
    
    print("Created throughput chart")


def create_packet_loss_chart():
    """Create packet loss impact chart."""
    # This would use packet_loss data
    fig, ax = plt.subplots(figsize=(12, 6))
    
    loss_rates = [0, 0.1, 0.5, 1, 2, 5, 10]
    
    # Example data - replace with actual data
    quic_success = [100, 99.9, 99.5, 98, 95, 85, 70]
    http2_success = [100, 99.8, 99, 96, 90, 75, 55]
    
    ax.plot(loss_rates, quic_success, 'o-', label='QUIC', color='#2ecc71', linewidth=2)
    ax.plot(loss_rates, http2_success, 's-', label='HTTP/2', color='#3498db', linewidth=2)
    
    ax.set_xlabel('Packet Loss Rate (%)', fontsize=12)
    ax.set_ylabel('Success Rate (%)', fontsize=12)
    ax.set_title('QUIC vs HTTP/2: Performance Under Packet Loss', fontsize=14)
    ax.legend()
    ax.grid(True, alpha=0.3)
    
    plt.tight_layout()
    plt.savefig(os.path.join(CHARTS_DIR, 'packet_loss_impact.png'), dpi=300)
    plt.savefig(os.path.join(CHARTS_DIR, 'packet_loss_impact.pdf'))
    plt.close()
    
    print("Created packet loss chart")


def create_comparison_heatmap():
    """Create overall comparison heatmap."""
    # Create comparison matrix
    metrics = ['Handshake', 'Throughput', 'Latency', 'Packet Loss\nRecovery', 
               'Multiplexing', 'Connection\nMigration']
    
    # Scores: positive = QUIC better, negative = HTTP/2 better
    # Scale: -2 (much worse) to +2 (much better)
    quic_vs_http2 = [
        2,    # Handshake: QUIC much better (0-RTT)
        0.5,  # Throughput: QUIC slightly better
        0.5,  # Latency: QUIC slightly better
        1.5,  # Packet Loss: QUIC better
        2,    # Multiplexing: QUIC much better (no HOL)
        2,    # Connection Migration: QUIC supports, HTTP/2 doesn't
    ]
    
    fig, ax = plt.subplots(figsize=(10, 6))
    
    colors = ['#e74c3c' if x < 0 else '#2ecc71' for x in quic_vs_http2]
    bars = ax.barh(metrics, quic_vs_http2, color=colors)
    
    ax.axvline(x=0, color='black', linewidth=0.5)
    ax.set_xlabel('QUIC Advantage Score', fontsize=12)
    ax.set_title('QUIC vs HTTP/2: Performance Comparison Summary', fontsize=14)
    ax.set_xlim(-2.5, 2.5)
    
    # Add labels
    for bar, val in zip(bars, quic_vs_http2):
        label = 'QUIC Better' if val > 0 else 'HTTP/2 Better'
        ax.annotate(f'{abs(val):.1f}', 
                   xy=(val, bar.get_y() + bar.get_height()/2),
                   xytext=(5 if val > 0 else -5, 0), 
                   textcoords="offset points",
                   ha='left' if val > 0 else 'right', va='center')
    
    plt.tight_layout()
    plt.savefig(os.path.join(CHARTS_DIR, 'comparison_summary.png'), dpi=300)
    plt.savefig(os.path.join(CHARTS_DIR, 'comparison_summary.pdf'))
    plt.close()
    
    print("Created comparison heatmap")


def main():
    print("Creating charts...")
    
    create_handshake_comparison()
    create_throughput_chart()
    create_packet_loss_chart()
    create_comparison_heatmap()
    
    print(f"\nAll charts saved to {CHARTS_DIR}")


if __name__ == "__main__":
    main()
```

#### Output yêu cầu:
```
📁 results/
├── charts/
│   ├── handshake_comparison.png
│   ├── handshake_comparison.pdf
│   ├── throughput_vs_filesize.png
│   ├── throughput_vs_filesize.pdf
│   ├── latency_distribution.png
│   ├── packet_loss_impact.png
│   ├── multiplexing_performance.png
│   ├── jitter_impact.png
│   ├── 0rtt_improvement.png
│   └── comparison_summary.png
```

---

### 7.3 Phân tích kết quả Handshake Time (Thành viên 1)

**Thời gian:** 4 giờ | **Deadline:** Thứ 6, Tuần 7

#### Nội dung phân tích:

1. **So sánh tổng thể:**
   - QUIC 1-RTT vs HTTP/2 (TCP 3-way + TLS 1.2/1.3)
   - Cải thiện % của QUIC so với HTTP/2

2. **Phân tích theo điều kiện mạng:**
   - Ideal (low latency)
   - Good (moderate latency)
   - Poor (high latency)
   - Impact of RTT on handshake time

3. **Phân tích 0-RTT:**
   - Improvement từ 0-RTT resumption
   - So sánh với HTTP/2 session resumption

#### Template báo cáo phân tích:

```markdown
# Phân tích Handshake Time

## 1. Tổng quan kết quả

### 1.1 Điều kiện Ideal (RTT ~1ms)
| Protocol | Mean (ms) | Std Dev | P95 (ms) | P99 (ms) |
|----------|-----------|---------|----------|----------|
| QUIC | XX.XX | X.XX | XX.XX | XX.XX |
| HTTP/2 | XX.XX | X.XX | XX.XX | XX.XX |
| **Improvement** | **XX%** | | | |

### 1.2 Điều kiện Good (RTT ~20ms)
...

## 2. Phân tích chi tiết

### 2.1 Tại sao QUIC nhanh hơn?
- QUIC kết hợp transport và crypto handshake
- TLS 1.3 integration cho phép 1-RTT handshake
- Không cần TCP 3-way handshake

### 2.2 Tác động của RTT
- Với RTT cao, lợi thế của QUIC càng rõ rệt
- HTTP/2 cần 2-3 RTT, QUIC chỉ cần 1 RTT

### 2.3 0-RTT Analysis
- 0-RTT cho phép gửi data ngay từ packet đầu tiên
- Improvement: XX% so với 1-RTT
- Security considerations

## 3. Kết luận
...
```

---

### 7.4 Phân tích kết quả Throughput/Latency (Thành viên 2)

**Thời gian:** 4 giờ | **Deadline:** Thứ 6, Tuần 7

#### Nội dung phân tích:

1. **Throughput Analysis:**
   - Throughput vs file size
   - Throughput vs network conditions
   - Bandwidth utilization efficiency

2. **Latency Analysis:**
   - Time To First Byte (TTFB)
   - Request-Response latency
   - Tail latency (P95, P99)

3. **Impact Factors:**
   - Network delay
   - Packet loss
   - Jitter

---

## 📊 TUẦN 8: SO SÁNH VÀ ĐÁNH GIÁ (15 giờ/người)

### 8.1 So sánh Tổng thể QUIC vs HTTP/2 (Cả 2 thành viên)

**Thời gian:** 6 giờ/người | **Deadline:** Thứ 4, Tuần 8

#### Bảng so sánh chi tiết với dữ liệu thực tế:

| Tiêu chí | QUIC | HTTP/2 | Kết quả | Điều kiện |
|----------|------|--------|---------|-----------|
| **Connection Establishment** | | | | |
| - New connection (ideal) | X ms | X ms | QUIC -X% | RTT=1ms |
| - New connection (poor) | X ms | X ms | QUIC -X% | RTT=100ms |
| - 0-RTT resumption | X ms | N/A | QUIC wins | |
| **Throughput** | | | | |
| - Small files (1KB) | X Mbps | X Mbps | ~ | |
| - Medium files (100KB) | X Mbps | X Mbps | ~ | |
| - Large files (10MB) | X Mbps | X Mbps | ~ | |
| **Latency (TTFB)** | | | | |
| - Ideal network | X ms | X ms | QUIC -X% | |
| - With packet loss (1%) | X ms | X ms | QUIC -X% | |
| - With jitter (50ms) | X ms | X ms | QUIC -X% | |
| **Packet Loss Recovery** | | | | |
| - 1% loss | X% success | X% success | QUIC +X% | |
| - 5% loss | X% success | X% success | QUIC +X% | |
| - 10% loss | X% success | X% success | QUIC +X% | |
| **Multiplexing** | | | | |
| - 10 concurrent streams | X ms | X ms | QUIC -X% | |
| - 50 concurrent streams | X ms | X ms | QUIC -X% | |
| **HOL Blocking Impact** | | | | |
| - With stream loss | Isolated | All blocked | QUIC wins | |

---

### 8.2 Đánh giá Ưu điểm của QUIC (Thành viên 1)

**Thời gian:** 4 giờ | **Deadline:** Thứ 5, Tuần 8

#### Các ưu điểm chính của QUIC:

| Ưu điểm | Mô tả | Evidence từ thử nghiệm |
|---------|-------|------------------------|
| **Faster Connection** | 1-RTT (0-RTT with resumption) | Handshake time giảm X% |
| **No HOL Blocking** | Independent streams | Stream isolation verified |
| **Better Loss Recovery** | Per-stream recovery | Higher success rate at high loss |
| **Connection Migration** | Change IP without reconnect | Demonstrated in testing |
| **Built-in Encryption** | TLS 1.3 integrated | Simplified security |
| **Improved Congestion Control** | Pluggable algorithms | Better bandwidth utilization |

---

### 8.3 Đánh giá Hạn chế của QUIC (Thành viên 2)

**Thời gian:** 4 giờ | **Deadline:** Thứ 5, Tuần 8

#### Các hạn chế của QUIC:

| Hạn chế | Mô tả | Evidence/Impact |
|---------|-------|-----------------|
| **UDP Blocking** | Some firewalls block UDP | May fail in restrictive networks |
| **CPU Overhead** | More processing due to encryption | Higher server CPU usage |
| **Less Mature** | Newer protocol | Fewer implementations |
| **Middlebox Issues** | May interfere with UDP | Connection issues |
| **Debugging Difficulty** | Encrypted packets | Harder to troubleshoot |

---

### 8.4 Đưa ra Khuyến nghị Sử dụng (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Thứ 6, Tuần 8

#### Recommendations Matrix:

| Use Case | Recommended Protocol | Reason |
|----------|---------------------|--------|
| **Mobile Applications** | QUIC | Connection migration, better loss handling |
| **Video Streaming** | QUIC | No HOL blocking, multiplexing |
| **API Services** | HTTP/2 or QUIC | Depends on network conditions |
| **Enterprise Internal** | HTTP/2 | Better firewall compatibility |
| **High-latency Networks** | QUIC | 0-RTT advantage |
| **Lossy Networks** | QUIC | Better recovery |
| **Low-latency Requirement** | QUIC | Faster handshake |
| **Legacy Support** | HTTP/2 | Wider compatibility |

---

# ═══════════════════════════════════════════════════════════════════
# GIAI ĐOẠN 4: VIẾT BÁO CÁO VÀ HOÀN THIỆN (TUẦN 9-10)
# ═══════════════════════════════════════════════════════════════════

## 📝 TUẦN 9: VIẾT BÁO CÁO (20 giờ/người)

### 9.1 Viết Chương 1: Giới thiệu (Thành viên 1)

**Thời gian:** 4 giờ | **Deadline:** Thứ 4, Tuần 9

#### Cấu trúc Chương 1 (1500-2000 từ):

```markdown
# CHƯƠNG 1: GIỚI THIỆU

## 1.1 Đặt vấn đề (400-500 từ)
- Sự phát triển của Internet và nhu cầu về tốc độ
- Hạn chế của TCP/HTTP/2 trong môi trường hiện đại
- Sự ra đời của QUIC như giải pháp mới
- Tầm quan trọng của việc đánh giá hiệu năng

## 1.2 Mục tiêu nghiên cứu (300-400 từ)
- Mục tiêu tổng quát
- Mục tiêu cụ thể (5-6 mục tiêu)
- Câu hỏi nghiên cứu

## 1.3 Phạm vi nghiên cứu (300-400 từ)
- Giới hạn về giao thức (QUIC, HTTP/2)
- Giới hạn về môi trường thử nghiệm
- Giới hạn về metrics đánh giá

## 1.4 Phương pháp nghiên cứu (300-400 từ)
- Nghiên cứu lý thuyết
- Triển khai thực nghiệm
- Phân tích so sánh

## 1.5 Cấu trúc báo cáo (200-300 từ)
- Mô tả ngắn gọn từng chương
```

---

### 9.2 Viết Chương 2: Cơ sở Lý thuyết (Thành viên 2)

**Thời gian:** 6 giờ | **Deadline:** Thứ 4, Tuần 9

#### Cấu trúc Chương 2 (3000-4000 từ):

```markdown
# CHƯƠNG 2: CƠ SỞ LÝ THUYẾT

## 2.1 Tổng quan về giao thức truyền tải (600-800 từ)
### 2.1.1 TCP (Transmission Control Protocol)
- Cơ chế hoạt động
- Ưu điểm và nhược điểm
- Vấn đề Head-of-Line blocking

### 2.1.2 UDP (User Datagram Protocol)
- Đặc điểm
- So sánh với TCP

## 2.2 Giao thức QUIC (1200-1500 từ)
### 2.2.1 Lịch sử phát triển
- Google QUIC (gQUIC)
- IETF QUIC

### 2.2.2 Kiến trúc QUIC
- Connection establishment
- Stream multiplexing
- Flow control

### 2.2.3 Cơ chế bảo mật
- TLS 1.3 integration
- 0-RTT handshake
- Packet protection

### 2.2.4 Loss detection và Congestion control
- Cơ chế phát hiện mất gói
- Các thuật toán congestion control

### 2.2.5 Connection migration
- Cơ chế hoạt động
- Use cases

## 2.3 Giao thức HTTP/2 (800-1000 từ)
### 2.3.1 Kiến trúc HTTP/2
- Binary framing layer
- HPACK header compression

### 2.3.2 Stream multiplexing trong HTTP/2
- Cơ chế hoạt động
- Vấn đề TCP HOL blocking

### 2.3.3 Server Push
- Cơ chế hoạt động
- Ưu và nhược điểm

## 2.4 So sánh QUIC và HTTP/2 (400-600 từ)
- Bảng so sánh tổng quan
- Điểm khác biệt chính

## 2.5 Các nghiên cứu liên quan (300-400 từ)
- Tổng quan các nghiên cứu trước đó
- Đóng góp của nghiên cứu này
```

---

### 9.3 Viết Chương 3: Phương pháp Thử nghiệm (Thành viên 1)

**Thời gian:** 5 giờ | **Deadline:** Thứ 6, Tuần 9

#### Cấu trúc Chương 3 (2000-2500 từ):

```markdown
# CHƯƠNG 3: PHƯƠNG PHÁP THỬ NGHIỆM

## 3.1 Môi trường thử nghiệm (500-600 từ)
### 3.1.1 Phần cứng
- Cấu hình server
- Cấu hình client
- Network topology

### 3.1.2 Phần mềm
- QUIC server (quiche)
- HTTP/2 server (nginx)
- Các công cụ đo lường

## 3.2 Thiết kế thử nghiệm (600-800 từ)
### 3.2.1 Các thử nghiệm được thực hiện
- Handshake time measurement
- Throughput measurement
- Latency measurement
- Packet loss testing
- Multiplexing testing
- Jitter testing
- 0-RTT testing

### 3.2.2 Các điều kiện mạng
- Ideal network
- Good network
- Poor network
- Các mức packet loss

### 3.2.3 Test cases matrix
- Bảng tổng hợp các test cases

## 3.3 Quy trình thử nghiệm (400-500 từ)
### 3.3.1 Chuẩn bị
### 3.3.2 Thực hiện
### 3.3.3 Thu thập dữ liệu

## 3.4 Xử lý dữ liệu (300-400 từ)
### 3.4.1 Làm sạch dữ liệu
### 3.4.2 Xử lý outliers
### 3.4.3 Tính toán thống kê

## 3.5 Độ tin cậy của thử nghiệm (200-300 từ)
- Số lượng samples
- Validation procedures
```

---

### 9.4 Viết Chương 4: Kết quả và Phân tích (Thành viên 2)

**Thời gian:** 6 giờ | **Deadline:** Thứ 6, Tuần 9

#### Cấu trúc Chương 4 (3000-4000 từ):

```markdown
# CHƯƠNG 4: KẾT QUẢ VÀ PHÂN TÍCH

## 4.1 Kết quả Handshake Time (600-800 từ)
### 4.1.1 Kết quả đo lường
- Bảng kết quả
- Biểu đồ so sánh

### 4.1.2 Phân tích
- So sánh QUIC vs HTTP/2
- Tác động của RTT
- Kết quả 0-RTT

## 4.2 Kết quả Throughput (600-800 từ)
### 4.2.1 Kết quả đo lường
- Bảng kết quả theo file size
- Biểu đồ so sánh

### 4.2.2 Phân tích
- Hiệu quả với các kích thước file khác nhau
- Tác động của điều kiện mạng

## 4.3 Kết quả Latency (500-600 từ)
### 4.3.1 Kết quả TTFB
### 4.3.2 Phân tích tail latency

## 4.4 Kết quả Packet Loss (500-600 từ)
### 4.4.1 Kết quả đo lường
### 4.4.2 Phân tích khả năng phục hồi

## 4.5 Kết quả Multiplexing (400-500 từ)
### 4.5.1 Kết quả với concurrent streams
### 4.5.2 Phân tích HOL blocking impact

## 4.6 Kết quả Jitter (300-400 từ)
### 4.6.1 Kết quả đo lường
### 4.6.2 Phân tích

## 4.7 So sánh tổng thể (400-500 từ)
- Bảng so sánh tổng hợp
- Summary findings
```

---

## 📝 TUẦN 10: HOÀN THIỆN VÀ NỘP BÀI (20 giờ/người)

### 10.1 Viết Chương 5: Kết luận (Cả 2 thành viên)

**Thời gian:** 3 giờ/người | **Deadline:** Thứ 3, Tuần 10

#### Cấu trúc Chương 5 (1000-1500 từ):

```markdown
# CHƯƠNG 5: KẾT LUẬN VÀ HƯỚNG PHÁT TRIỂN

## 5.1 Tổng kết kết quả (400-500 từ)
- Tóm tắt các phát hiện chính
- Trả lời các câu hỏi nghiên cứu
- Đóng góp của nghiên cứu

## 5.2 Khuyến nghị sử dụng (300-400 từ)
- Khi nào nên dùng QUIC
- Khi nào nên dùng HTTP/2
- Use case recommendations

## 5.3 Hạn chế của nghiên cứu (200-300 từ)
- Giới hạn về môi trường
- Giới hạn về thời gian
- Các yếu tố chưa được xem xét

## 5.4 Hướng phát triển (200-300 từ)
- Nghiên cứu HTTP/3
- Mở rộng test cases
- Real-world deployment testing
```

---

### 10.2 Review và Chỉnh sửa (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Thứ 4, Tuần 10

#### Checklist review:

| Mục | Thành viên 1 | Thành viên 2 | Status |
|-----|--------------|--------------|--------|
| Kiểm tra chính tả | Review Ch 2, 4 | Review Ch 1, 3, 5 | [ ] |
| Kiểm tra grammar | Review Ch 2, 4 | Review Ch 1, 3, 5 | [ ] |
| Kiểm tra format | Cả báo cáo | Cả báo cáo | [ ] |
| Kiểm tra references | Cả báo cáo | Cả báo cáo | [ ] |
| Kiểm tra figures/tables | Review TV2's | Review TV1's | [ ] |
| Kiểm tra page numbers | Final check | Final check | [ ] |
| Kiểm tra ToC | Final check | Final check | [ ] |
| Export PDF | Cả 2 | Cả 2 | [ ] |

---

### 10.3 Chuẩn bị Slide Thuyết trình (Thành viên 1)

**Thời gian:** 5 giờ | **Deadline:** Thứ 5, Tuần 10

#### Cấu trúc Slide (15-20 slides):

| Slide | Nội dung | Thời gian trình bày |
|-------|----------|---------------------|
| 1 | Title slide | 30 giây |
| 2 | Agenda | 30 giây |
| 3-4 | Giới thiệu & Đặt vấn đề | 2 phút |
| 5-6 | Mục tiêu nghiên cứu | 1.5 phút |
| 7-9 | Cơ sở lý thuyết (QUIC, HTTP/2) | 3 phút |
| 10-11 | Phương pháp thử nghiệm | 2 phút |
| 12-15 | Kết quả và phân tích | 5 phút |
| 16-17 | So sánh và đánh giá | 2 phút |
| 18 | Kết luận | 1.5 phút |
| 19 | Khuyến nghị | 1 phút |
| 20 | Q&A | - |

---

### 10.4 Demo và Thuyết trình thử (Cả 2 thành viên)

**Thời gian:** 4 giờ/người | **Deadline:** Thứ 6, Tuần 10

#### Chuẩn bị Demo:

| Demo | Nội dung | Người trình bày |
|------|----------|-----------------|
| D1 | Start QUIC server | Thành viên 1 |
| D2 | Start HTTP/2 server | Thành viên 2 |
| D3 | Run handshake comparison | Thành viên 1 |
| D4 | Run throughput test | Thành viên 2 |
| D5 | Show real-time comparison | Cả 2 |

#### Phân công thuyết trình:

| Phần | Nội dung | Người trình bày | Thời gian |
|------|----------|-----------------|-----------|
| 1 | Giới thiệu | Thành viên 1 | 3 phút |
| 2 | Cơ sở lý thuyết | Thành viên 2 | 4 phút |
| 3 | Phương pháp | Thành viên 1 | 3 phút |
| 4 | Kết quả | Thành viên 2 | 5 phút |
| 5 | Demo | Cả 2 | 3 phút |
| 6 | Kết luận | Thành viên 1 | 2 phút |

---

### 10.5 Nộp Báo cáo Cuối cùng (Cả 2 thành viên)

**Thời gian:** 2 giờ | **Deadline:** Chủ nhật, Tuần 10

#### Danh sách files cần nộp:

```
📁 NT531.Q21-QUIC-Final/
├── 📄 BaoCao_QUIC_vs_HTTP2.pdf (Báo cáo chính)
├── 📄 BaoCao_QUIC_vs_HTTP2.docx (Source file)
├── 📁 slides/
│   ├── Presentation.pptx
│   └── Presentation.pdf
├── 📁 source_code/
│   ├── setup/
│   │   ├── quic-server/
│   │   └── http2-server/
│   ├── scripts/
│   │   ├── benchmark_*.sh
│   │   ├── measure_*.sh
│   │   └── analyze_*.py
│   └── README.md
├── 📁 results/
│   ├── raw_data/
│   ├── processed/
│   └── charts/
└── 📄 README.md
```

---

# ═══════════════════════════════════════════════════════════════════
# BẢNG TỔNG HỢP PHÂN CÔNG CÔNG VIỆC
# ═══════════════════════════════════════════════════════════════════

## 📊 THÀNH VIÊN 1 - TRƯỞNG NHÓM

| Tuần | Công việc | Giờ | Deadline |
|------|-----------|-----|----------|
| 1 | Nghiên cứu lịch sử phát triển giao thức | 8 | Cuối T1 |
| 1 | Tổng hợp tài liệu (chung) | 4 | Cuối T1 |
| 2 | Nghiên cứu kiến trúc QUIC | 10 | Cuối T2 |
| 2 | Nghiên cứu loss detection & congestion control | 8 | Cuối T2 |
| 3 | Nghiên cứu stream multiplexing HTTP/2 | 5 | Giữa T3 |
| 3 | So sánh sơ bộ (chung) | 4 | Cuối T3 |
| 3 | Viết báo cáo GĐ1 (chung) | 4 | Cuối T3 |
| 4 | Thiết lập server QUIC | 12 | Cuối T4 |
| 4 | Thiết lập môi trường mạng giả lập | 6 | Cuối T4 |
| 5 | Đo lường handshake time | 8 | Cuối T5 |
| 5 | Đo lường latency | 6 | Cuối T5 |
| 6 | Thử nghiệm multiplexing | 8 | Cuối T6 |
| 6 | Thử nghiệm 0-RTT | 6 | Cuối T6 |
| 6 | Tổng hợp dữ liệu (chung) | 4 | Cuối T6 |
| 7 | Xử lý và làm sạch dữ liệu | 6 | Giữa T7 |
| 7 | Phân tích handshake time | 4 | Cuối T7 |
| 8 | So sánh tổng thể (chung) | 6 | Giữa T8 |
| 8 | Đánh giá ưu điểm QUIC | 4 | Cuối T8 |
| 8 | Khuyến nghị (chung) | 4 | Cuối T8 |
| 9 | Viết Chương 1: Giới thiệu | 4 | Giữa T9 |
| 9 | Viết Chương 3: Phương pháp | 5 | Cuối T9 |
| 10 | Viết Chương 5 (chung) | 3 | Giữa T10 |
| 10 | Review và chỉnh sửa (chung) | 4 | Giữa T10 |
| 10 | Chuẩn bị slide | 5 | Cuối T10 |
| 10 | Demo và thuyết trình thử (chung) | 4 | Cuối T10 |
| 10 | Nộp báo cáo (chung) | 2 | Cuối T10 |
| **TỔNG** | | **~135 giờ** | |

---

## 📊 THÀNH VIÊN 2

| Tuần | Công việc | Giờ | Deadline |
|------|-----------|-----|----------|
| 1 | Nghiên cứu TCP và UDP | 8 | Cuối T1 |
| 1 | Tổng hợp tài liệu (chung) | 4 | Cuối T1 |
| 2 | Nghiên cứu bảo mật QUIC | 8 | Cuối T2 |
| 2 | Nghiên cứu QUIC packet format | 7 | Cuối T2 |
| 3 | Nghiên cứu kiến trúc HTTP/2 | 8 | Giữa T3 |
| 3 | So sánh sơ bộ (chung) | 4 | Cuối T3 |
| 3 | Viết báo cáo GĐ1 (chung) | 4 | Cuối T3 |
| 4 | Thiết lập server HTTP/2 | 10 | Cuối T4 |
| 4 | Chuẩn bị công cụ đo lường | 8 | Cuối T4 |
| 5 | Đo lường throughput | 8 | Cuối T5 |
| 5 | Thử nghiệm packet loss | 6 | Cuối T5 |
| 6 | Thử nghiệm jitter/unstable network | 8 | Cuối T6 |
| 6 | Tổng hợp dữ liệu (chung) | 4 | Cuối T6 |
| 7 | Tạo biểu đồ so sánh | 6 | Giữa T7 |
| 7 | Phân tích throughput/latency | 4 | Cuối T7 |
| 8 | So sánh tổng thể (chung) | 6 | Giữa T8 |
| 8 | Đánh giá hạn chế QUIC | 4 | Cuối T8 |
| 8 | Khuyến nghị (chung) | 4 | Cuối T8 |
| 9 | Viết Chương 2: Cơ sở lý thuyết | 6 | Giữa T9 |
| 9 | Viết Chương 4: Kết quả | 6 | Cuối T9 |
| 10 | Viết Chương 5 (chung) | 3 | Giữa T10 |
| 10 | Review và chỉnh sửa (chung) | 4 | Giữa T10 |
| 10 | Demo và thuyết trình thử (chung) | 4 | Cuối T10 |
| 10 | Nộp báo cáo (chung) | 2 | Cuối T10 |
| **TỔNG** | | **~130 giờ** | |

---

## ✅ CHECKLIST TIẾN ĐỘ TỔNG HỢP

### Giai đoạn 1: Nghiên cứu Lý thuyết (Tuần 1-3)
- [ ] T1: Nghiên cứu lịch sử giao thức (TV1)
- [ ] T1: Nghiên cứu TCP/UDP (TV2)
- [ ] T1: Tổng hợp tài liệu (Cả 2)
- [ ] T2: Nghiên cứu kiến trúc QUIC (TV1)
- [ ] T2: Nghiên cứu bảo mật QUIC (TV2)
- [ ] T2: Nghiên cứu loss detection (TV1)
- [ ] T2: Nghiên cứu packet format (TV2)
- [ ] T3: Nghiên cứu kiến trúc HTTP/2 (TV2)
- [ ] T3: Nghiên cứu multiplexing HTTP/2 (TV1)
- [ ] T3: Bảng so sánh sơ bộ (Cả 2)
- [ ] T3: Báo cáo giai đoạn 1 (Cả 2)

### Giai đoạn 2: Triển khai và Thử nghiệm (Tuần 4-6)
- [ ] T4: Server QUIC hoạt động (TV1)
- [ ] T4: Server HTTP/2 hoạt động (TV2)
- [ ] T4: Network emulation ready (TV1)
- [ ] T4: Benchmark tools ready (TV2)
- [ ] T5: Handshake tests complete (TV1)
- [ ] T5: Throughput tests complete (TV2)
- [ ] T5: Latency tests complete (TV1)
- [ ] T5: Packet loss tests complete (TV2)
- [ ] T6: Multiplexing tests complete (TV1)
- [ ] T6: Jitter tests complete (TV2)
- [ ] T6: 0-RTT tests complete (TV1)
- [ ] T6: Data aggregation complete (Cả 2)

### Giai đoạn 3: Phân tích và So sánh (Tuần 7-8)
- [ ] T7: Data cleaned and processed (TV1)
- [ ] T7: All charts created (TV2)
- [ ] T7: Handshake analysis complete (TV1)
- [ ] T7: Throughput analysis complete (TV2)
- [ ] T8: Comparison table complete (Cả 2)
- [ ] T8: QUIC advantages documented (TV1)
- [ ] T8: QUIC limitations documented (TV2)
- [ ] T8: Recommendations finalized (Cả 2)

### Giai đoạn 4: Viết Báo cáo (Tuần 9-10)
- [ ] T9: Chapter 1 complete (TV1)
- [ ] T9: Chapter 2 complete (TV2)
- [ ] T9: Chapter 3 complete (TV1)
- [ ] T9: Chapter 4 complete (TV2)
- [ ] T10: Chapter 5 complete (Cả 2)
- [ ] T10: Report reviewed (Cả 2)
- [ ] T10: Slides complete (TV1)
- [ ] T10: Demo ready (Cả 2)
- [ ] T10: Final submission (Cả 2)

---

*Cập nhật lần cuối: 29/01/2026*

*Người tạo: Nhóm NT531.Q21-QUIC*
