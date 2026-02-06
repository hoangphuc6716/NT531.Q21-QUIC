# PHÂN CÔNG CÔNG VIỆC VÀ THỜI GIAN THỰC HIỆN

## Đề tài: Nghiên cứu toàn diện giao thức QUIC - Thiết kế, Cơ chế hoạt động và Ứng dụng thực tế

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò | Trách nhiệm chính |
|-----|-----------|------|---------|-------------------|
| 1 | Thành viên 1 | [MSSV] | Trưởng nhóm | Kiến trúc QUIC, Bảo mật, Connection Management |
| 2 | Thành viên 2 | [MSSV] | Thành viên | Stream Multiplexing, Congestion Control, Demo thực hành |

---

## 🎯 Mục tiêu đề tài

1. **Nghiên cứu kiến trúc QUIC** - Hiểu rõ thiết kế và các thành phần cốt lõi của giao thức
2. **Phân tích cơ chế bảo mật** - Tìm hiểu tích hợp TLS 1.3 và các tính năng bảo mật
3. **Nghiên cứu Stream Multiplexing** - Hiểu cách QUIC xử lý nhiều streams đồng thời
4. **Nghiên cứu Connection Migration** - Khả năng duy trì kết nối khi đổi mạng
5. **Phân tích Loss Detection & Congestion Control** - Cơ chế phát hiện mất gói và điều khiển tắc nghẽn
6. **Xây dựng Demo thực hành** - Triển khai và demo các tính năng của QUIC
7. **Phân tích ứng dụng thực tế** - Tìm hiểu việc triển khai QUIC trong các hệ thống lớn

---

## 📅 Kế hoạch thời gian tổng quan

| Giai đoạn | Nội dung | Thời gian | Số tuần | Giờ/tuần/người |
|-----------|----------|-----------|---------|----------------|
| 1 | Nghiên cứu nền tảng và kiến trúc QUIC | Tuần 1-2 | 2 tuần | 15 giờ/tuần |
| 2 | Nghiên cứu các cơ chế hoạt động | Tuần 3-4 | 2 tuần | 17.5 giờ/tuần |
| 3 | Triển khai và Demo thực hành | Tuần 5-6 | 2 tuần | 20 giờ/tuần |
| 4 | Phân tích ứng dụng và Case Studies | Tuần 7 | 1 tuần | 15 giờ |
| 5 | Viết báo cáo và hoàn thiện | Tuần 8 | 1 tuần | 20 giờ |
| **TỔNG** | | **8 tuần** | | **~145 giờ/người** |

---

## 📝 CHI TIẾT PHÂN CÔNG CÔNG VIỆC THEO TUẦN

---

## 🗓️ TUẦN 1: NỀN TẢNG VÀ KIẾN TRÚC QUIC (15 giờ/người)

### Thành viên 1 (15 giờ) - Lịch sử và Kiến trúc cốt lõi

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 1.1 | Nghiên cứu lịch sử phát triển QUIC | - Đọc tài liệu về gQUIC (Google QUIC 2012-2015)<br>- Quá trình chuẩn hóa IETF (2016-2021)<br>- Sự khác biệt gQUIC vs IETF QUIC<br>- Động lực phát triển QUIC | 4 | Tài liệu 2-3 trang |
| 1.2 | Nghiên cứu kiến trúc QUIC Protocol Stack | - Vẽ sơ đồ protocol stack (QUIC, TLS 1.3, UDP, IP)<br>- Mô tả Connection, Stream, Frame, Packet<br>- Phân tích mối quan hệ giữa các components | 5 | Sơ đồ kiến trúc + mô tả chi tiết |
| 1.3 | Đọc RFC 9000 (Sections 1-8) | - Giới thiệu và tổng quan<br>- Packet Types và Formats<br>- Stream States và Lifecycle<br>- Frame Types và Encoding | 4 | Ghi chú tóm tắt với diagrams |
| 1.4 | Thu thập tài liệu tham khảo | - RFC 9000, 9001, 9002, 9114<br>- Academic papers từ Google Scholar<br>- Blog posts từ Cloudflare, Google, Meta | 2 | Danh sách 15-20 tài liệu có chú thích |

### Thành viên 2 (15 giờ) - Packet Structure và Frame Types

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 1.1 | Nghiên cứu QUIC Packet Structure | - Long Header vs Short Header packets<br>- Packet Number Spaces (Initial, Handshake, 1-RTT)<br>- Version Negotiation packet<br>- Retry packet | 4 | Tài liệu kỹ thuật với diagrams |
| 1.2 | Phân tích chi tiết Frame Types | - STREAM, ACK, CRYPTO frames<br>- CONNECTION_CLOSE, RESET_STREAM<br>- PADDING, PING, PATH_CHALLENGE<br>- MAX_DATA, MAX_STREAM_DATA | 5 | Bảng tổng hợp Frame Types |
| 1.3 | Đọc RFC 9000 (Sections 9-19) | - Connection Termination<br>- Error Handling<br>- Security Considerations<br>- IANA Considerations | 4 | Ghi chú tóm tắt |
| 1.4 | Tìm hiểu HTTP/3 và mối quan hệ với QUIC | - HTTP/3 sử dụng QUIC như thế nào<br>- QPACK header compression<br>- Mapping HTTP semantics to QUIC streams | 2 | Tài liệu tóm tắt HTTP/3 |

### 📋 Deliverables cuối Tuần 1:
> **Ghi chú:** TV1 = Thành viên 1, TV2 = Thành viên 2

- [ ] Tài liệu lịch sử và động lực phát triển QUIC (TV1)
- [ ] Sơ đồ kiến trúc QUIC Protocol Stack (TV1)
- [ ] Tài liệu về QUIC Packet Structure (TV2)
- [ ] Bảng tổng hợp Frame Types (TV2)
- [ ] Danh sách tài liệu tham khảo (Cả 2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 1

#### Task 1.1 (TV1): Nghiên cứu lịch sử phát triển QUIC

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

**Bước 4: Phân tích động lực phát triển (1 giờ)**
- Vấn đề của TCP: HOL blocking, handshake chậm
- Nhu cầu từ các ứng dụng web hiện đại
- Sự phổ biến của mobile internet

**Bước 5: Viết tài liệu tổng hợp (30 phút)**
- Viết 2-3 trang tổng hợp
- Thêm timeline diagram
- Cite nguồn tài liệu

#### Task 1.2 (TV1): Nghiên cứu kiến trúc QUIC Protocol Stack

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

**Bước 3: Mô tả các thành phần cốt lõi (2 giờ)**
- **Connection**: Connection ID, state machine, multiple paths
- **Stream**: Stream ID, bidirectional/unidirectional, states, flow control
- **Frame**: STREAM, ACK, CRYPTO, PADDING, CONNECTION_CLOSE, etc.
- **Packet**: Long header vs Short header, packet number spaces

**Bước 4: Viết mô tả chi tiết (1 giờ)**
- Giải thích từng component
- Thêm ví dụ cụ thể
- Export sơ đồ dạng PNG/SVG

#### Task 1.1 (TV2): Nghiên cứu QUIC Packet Structure

**Bước 1: Đọc RFC 9000 Section 17 - Packet Formats (1 giờ)**
- Long Header Packets: Initial, 0-RTT, Handshake, Retry
- Short Header Packets: 1-RTT

**Bước 2: Vẽ diagram Packet Headers (1.5 giờ)**
```
Long Header Packet:
+-+-+-+-+-+-+-+-+
|1|1| Type |Res |  Header Form = 1 (Long)
+-+-+-+-+-+-+-+-+
|    Version    |
+-+-+-+-+-+-+-+-+
| DCID Len | Destination Connection ID ...
+-+-+-+-+-+-+-+-+
| SCID Len | Source Connection ID ...
+-+-+-+-+-+-+-+-+
| Payload ...
+-+-+-+-+-+-+-+-+

Short Header Packet:
+-+-+-+-+-+-+-+-+
|0|1|S|R|R|K|P P|  Header Form = 0 (Short)
+-+-+-+-+-+-+-+-+
| Destination Connection ID ...
+-+-+-+-+-+-+-+-+
| Packet Number ...
+-+-+-+-+-+-+-+-+
| Protected Payload ...
+-+-+-+-+-+-+-+-+
```

**Bước 3: Phân tích Packet Number Spaces (1 giờ)**
- Initial Packet Number Space
- Handshake Packet Number Space
- Application Data Packet Number Space

**Bước 4: Viết tài liệu (0.5 giờ)**
- Tổng hợp về packet structure
- Thêm diagrams

#### Task 1.2 (TV2): Phân tích chi tiết Frame Types

**Bước 1: Đọc RFC 9000 Section 19 - Frame Types (2 giờ)**
- Liệt kê tất cả Frame Types
- Hiểu format của mỗi frame

**Bước 2: Tạo bảng tổng hợp Frame Types (2 giờ)**
```
| Frame Type | Value | Description | Use Case |
|------------|-------|-------------|----------|
| PADDING | 0x00 | Padding frame | Increase packet size |
| PING | 0x01 | Keep-alive | Connection liveness |
| ACK | 0x02-0x03 | Acknowledgment | Reliable delivery |
| RESET_STREAM | 0x04 | Reset stream | Error handling |
| STOP_SENDING | 0x05 | Stop sending | Flow control |
| CRYPTO | 0x06 | Crypto data | TLS handshake |
| NEW_TOKEN | 0x07 | New token | Address validation |
| STREAM | 0x08-0x0f | Stream data | Application data |
| MAX_DATA | 0x10 | Connection-level flow control | |
| MAX_STREAM_DATA | 0x11 | Stream-level flow control | |
| ... | ... | ... | ... |
```

**Bước 3: Viết mô tả chi tiết (1 giờ)**
- Giải thích use case của từng frame
- Thêm ví dụ cụ thể

---

## 🗓️ TUẦN 2: BẢO MẬT VÀ CONNECTION MANAGEMENT (15 giờ/người)

### Thành viên 1 (15 giờ) - Bảo mật và Handshake

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 2.1 | Nghiên cứu TLS 1.3 Integration | - Cách QUIC tích hợp TLS 1.3<br>- CRYPTO frames và TLS messages<br>- Không dùng TLS record layer<br>- Encryption levels | 5 | Tài liệu bảo mật chi tiết |
| 2.2 | Nghiên cứu 1-RTT và 0-RTT Handshake | - Phân tích 1-RTT handshake chi tiết<br>- Cơ chế 0-RTT Resumption<br>- Pre-Shared Key (PSK)<br>- Replay attack considerations | 5 | Sequence diagrams + tài liệu |
| 2.3 | Nghiên cứu Packet Protection | - Header protection mechanism<br>- Payload encryption (AEAD)<br>- Key derivation process | 3 | Tài liệu kỹ thuật |
| 2.4 | Phân tích Security Considerations | - Address validation<br>- Connection ID và privacy<br>- Amplification attack mitigation | 2 | Security analysis document |

### Thành viên 2 (15 giờ) - Connection Migration và Flow Control

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 2.1 | Nghiên cứu Connection Migration | - Khả năng đổi IP/port<br>- Connection ID rotation<br>- Path validation<br>- NAT rebinding handling | 5 | Tài liệu + diagrams |
| 2.2 | Nghiên cứu Flow Control | - Connection-level flow control<br>- Stream-level flow control<br>- MAX_DATA, MAX_STREAM_DATA frames<br>- Credit-based flow control | 4 | Tài liệu kỹ thuật |
| 2.3 | Nghiên cứu Stream Multiplexing | - Stream ID encoding<br>- Bidirectional vs Unidirectional streams<br>- Stream prioritization<br>- Stream concurrency limits | 4 | Tài liệu + diagrams |
| 2.4 | Phân tích NAT/Firewall Traversal | - UDP và middleboxes<br>- Connection ID và NAT<br>- Fallback mechanisms | 2 | Analysis document |

### 📋 Deliverables cuối Tuần 2:
- [ ] Tài liệu TLS 1.3 Integration (TV1)
- [ ] Sequence diagrams cho 1-RTT và 0-RTT handshake (TV1)
- [ ] Tài liệu Connection Migration (TV2)
- [ ] Tài liệu Flow Control và Stream Multiplexing (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 2

#### Task 2.1 (TV1): Nghiên cứu TLS 1.3 Integration

**Bước 1: Đọc RFC 9001 - Using TLS to Secure QUIC (1.5 giờ)**
- Hiểu cách QUIC integrate TLS 1.3
- Không dùng TLS record layer
- CRYPTO frames carry TLS messages

**Bước 2: Hiểu Encryption Levels (1.5 giờ)**
```
Level 0: Initial (derived from connection ID)
         - Dùng cho Initial packets
         - Keys derived from Destination Connection ID
         
Level 1: Handshake (derived from handshake secrets)
         - Dùng sau khi nhận ServerHello
         
Level 2: 1-RTT (derived from handshake completion)
         - Application data encryption
         
Level 3: 0-RTT (derived from PSK)
         - Early data encryption
```

**Bước 3: Hiểu Key Derivation (1.5 giờ)**
- HKDF-Extract và HKDF-Expand-Label
- Separate keys cho client và server
- Separate keys cho header protection
- Key update mechanism

**Bước 4: Viết tài liệu (0.5 giờ)**

#### Task 2.2 (TV1): Nghiên cứu 1-RTT và 0-RTT Handshake

**Bước 1: Vẽ 1-RTT Handshake Sequence Diagram (1.5 giờ)**
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

**Bước 2: Vẽ 0-RTT Resumption Diagram (1.5 giờ)**
```
Client                                    Server
  |                                         |
  |--- Initial[CRYPTO: ClientHello] ------->|
  |--- 0-RTT[STREAM: Early Data] ---------->|  <- Data sent immediately!
  |<-- Initial[CRYPTO: ServerHello] --------|
  |<-- Handshake[...] ----------------------|
  |<========== 1-RTT Data =================>|
```

**Bước 3: Phân tích 0-RTT Security (1.5 giờ)**
- Replay attack risk
- Anti-replay mechanisms
- Idempotent requests only

**Bước 4: Viết tài liệu (0.5 giờ)**

#### Task 2.1 (TV2): Nghiên cứu Connection Migration

**Bước 1: Đọc RFC 9000 Section 9 (1.5 giờ)**
- Connection Migration cơ bản
- Path validation process
- Connection ID rotation

**Bước 2: Vẽ diagrams (2 giờ)**
```
Connection Migration Scenario:
Client (WiFi: IP1) ────────────> Server
        |                           |
        | [Switch to Mobile]        |
        |                           |
Client (4G: IP2) ──────────────────>|  <- Same Connection ID!
        |                           |
        |<── PATH_CHALLENGE ────────|
        |─── PATH_RESPONSE ────────>|
        |                           |
        |<═══ Continue Data ════════|
```

**Bước 3: Phân tích use cases (1 giờ)**
- Mobile handoff (WiFi → Cellular)
- NAT rebinding
- Multi-path QUIC (future)

**Bước 4: Viết tài liệu (0.5 giờ)**

#### Task 2.2 (TV2): Nghiên cứu Flow Control

**Bước 1: Hiểu Connection-level Flow Control (1 giờ)**
- MAX_DATA frame
- Initial connection flow control limit
- Flow control window updates

**Bước 2: Hiểu Stream-level Flow Control (1 giờ)**
- MAX_STREAM_DATA frame
- Per-stream limits
- Independent of connection-level

**Bước 3: Vẽ diagrams (1.5 giờ)**
```
Flow Control Example:
Client                                    Server
  |                                         |
  |─── STREAM (1000 bytes) ───────────────>|
  |                                         |
  |<── MAX_STREAM_DATA (limit: 5000) ──────|  <- More credit
  |                                         |
  |─── STREAM (2000 bytes) ───────────────>|
```

**Bước 4: Viết tài liệu (0.5 giờ)**

---

## 🗓️ TUẦN 3: LOSS DETECTION VÀ CONGESTION CONTROL (20 giờ/người)

### Thành viên 1 (20 giờ) - Loss Detection

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 3.1 | Nghiên cứu ACK Mechanism | - ACK frame structure<br>- ACK ranges và gaps<br>- ACK Delay field<br>- RTT estimation | 6 | Tài liệu kỹ thuật |
| 3.2 | Nghiên cứu Packet Number Encoding | - Packet number spaces<br>- Truncated packet numbers<br>- Packet number decoding | 4 | Tài liệu |
| 3.3 | Nghiên cứu Loss Detection Algorithm | - Time-based detection<br>- Packet-based detection (3 packets)<br>- Probe Timeout (PTO)<br>- Persistent Congestion | 6 | Tài liệu chi tiết + flowcharts |
| 3.4 | So sánh với TCP Loss Detection | - TCP FACK<br>- TCP RACK<br>- Ưu điểm của QUIC approach | 4 | Comparison document |

### Thành viên 2 (20 giờ) - Congestion Control

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 3.1 | Nghiên cứu QUIC Congestion Control | - Congestion window<br>- Slow start<br>- Congestion avoidance<br>- Recovery phase | 6 | Tài liệu kỹ thuật |
| 3.2 | Phân tích RFC 9002 Algorithms | - NewReno-like congestion control<br>- Pacing<br>- Application-limited behavior | 5 | Tài liệu |
| 3.3 | Tìm hiểu các Congestion Control khác | - CUBIC for QUIC<br>- BBR for QUIC<br>- Pluggable congestion control | 5 | Comparison document |
| 3.4 | Nghiên cứu ECN support | - Explicit Congestion Notification<br>- ECN in QUIC<br>- Benefits và limitations | 4 | Tài liệu |

### 📋 Deliverables cuối Tuần 3:
- [ ] Tài liệu ACK Mechanism và Loss Detection (TV1)
- [ ] Flowcharts cho Loss Detection Algorithm (TV1)
- [ ] Tài liệu Congestion Control (TV2)
- [ ] Comparison document: QUIC CC vs TCP CC (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 3

#### Task 3.1 (TV1): Nghiên cứu ACK Mechanism

**Bước 1: Đọc RFC 9002 Section 2 (1.5 giờ)**
- Hiểu ACK frame structure
- Largest Acknowledged, ACK Delay, ACK Range Count
- First ACK Range, ACK Ranges

**Bước 2: Vẽ diagram ACK mechanism (2 giờ)**
```
ACK Frame Example:
Largest Acknowledged: 10
ACK Delay: 25ms
ACK Range Count: 2
First ACK Range: 3        -> Received: 10, 9, 8, 7
ACK Range [Gap: 1, Length: 2] -> Received: 5, 4, 3
                          -> Missing: 6

Received packets: 3, 4, 5, 7, 8, 9, 10
Missing packet: 6
```

**Bước 3: Hiểu RTT Estimation (1.5 giờ)**
- min_rtt, smoothed_rtt, rttvar
- RTT calculation from ACK Delay
- Impact on loss detection

**Bước 4: Viết tài liệu (1 giờ)**

#### Task 3.3 (TV1): Nghiên cứu Loss Detection Algorithm

**Bước 1: Hiểu Packet-based Detection (2 giờ)**
- Packet Threshold: kPacketThreshold = 3
- Khi nhận ACK cho packet N, packets < N-3 được coi là lost

**Bước 2: Hiểu Time-based Detection (2 giờ)**
- Time Threshold: 9/8 * max(smoothed_rtt, latest_rtt)
- Packets sent before time threshold are lost

**Bước 3: Vẽ flowchart (1.5 giờ)**
```
                    ┌─────────────────┐
                    │ Receive ACK     │
                    └────────┬────────┘
                             │
              ┌──────────────┴──────────────┐
              │                              │
    ┌─────────▼─────────┐        ┌──────────▼──────────┐
    │ Packet Threshold  │        │  Time Threshold     │
    │ Check (N-3 rule)  │        │  Check              │
    └─────────┬─────────┘        └──────────┬──────────┘
              │                              │
              └──────────────┬───────────────┘
                             │
                    ┌────────▼────────┐
                    │ Mark packets    │
                    │ as LOST         │
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │ Retransmit      │
                    │ lost data       │
                    └─────────────────┘
```

**Bước 4: Viết tài liệu (0.5 giờ)**

#### Task 3.1 (TV2): Nghiên cứu QUIC Congestion Control

**Bước 1: Đọc RFC 9002 Sections 6-7 (2 giờ)**
- Congestion window (cwnd)
- Slow start threshold (ssthresh)
- Bytes in flight

**Bước 2: Hiểu các phases (2 giờ)**
```
Slow Start:
- cwnd tăng theo số bytes được ACK
- Dừng khi cwnd >= ssthresh hoặc có loss

Congestion Avoidance:
- cwnd tăng chậm hơn (additive increase)
- Dựa trên RTT

Recovery:
- Khi phát hiện loss
- cwnd = cwnd / 2
- ssthresh = cwnd
```

**Bước 3: Hiểu Pacing (1.5 giờ)**
- Spread packets over time
- Avoid bursts
- Pacing rate calculation

**Bước 4: Viết tài liệu (0.5 giờ)**

---

## 🗓️ TUẦN 4: TRIỂN KHAI VÀ DEMO THỰC HÀNH (20 giờ/người)

### Thành viên 1 (20 giờ) - Setup QUIC Environment

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 4.1 | Cài đặt QUIC Implementation | - Chọn implementation: quiche (Cloudflare) hoặc msquic (Microsoft)<br>- Cài đặt dependencies<br>- Build từ source | 6 | Working QUIC stack |
| 4.2 | Tạo QUIC Server Demo | - Setup QUIC server với HTTP/3<br>- Tạo SSL certificates<br>- Configure server parameters | 5 | QUIC Server running |
| 4.3 | Demo Connection Establishment | - Capture 1-RTT handshake với Wireshark<br>- Demo 0-RTT resumption<br>- Phân tích packets | 5 | Wireshark captures + screenshots |
| 4.4 | Demo Packet Protection | - Capture encrypted packets<br>- Show header protection in action<br>- Compare với unencrypted | 4 | Demo documentation |

### Thành viên 2 (20 giờ) - Demo các tính năng QUIC

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 4.1 | Demo Stream Multiplexing | - Setup multiple concurrent streams<br>- Show stream independence<br>- Capture stream frames | 6 | Demo + screenshots |
| 4.2 | Demo Flow Control | - Configure flow control limits<br>- Show MAX_DATA, MAX_STREAM_DATA<br>- Monitor flow control behavior | 5 | Demo documentation |
| 4.3 | Demo Connection Migration | - Simulate IP change<br>- Show connection maintained<br>- PATH_CHALLENGE/RESPONSE | 5 | Demo + screenshots |
| 4.4 | Setup Monitoring Tools | - Wireshark với QUIC dissector<br>- qlog format logging<br>- Visualization tools | 4 | Tools configured |

### 📋 Deliverables cuối Tuần 4:
- [ ] QUIC Server hoạt động (TV1)
- [ ] Demo Connection Establishment với captures (TV1)
- [ ] Demo Stream Multiplexing (TV2)
- [ ] Demo Connection Migration (TV2)
- [ ] Monitoring tools configured (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 4

#### Task 4.1 (TV1): Cài đặt QUIC Implementation

**Bước 1: Cài đặt quiche (Cloudflare) (2 giờ)**
```bash
# Install Rust
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source $HOME/.cargo/env

# Install dependencies
sudo apt install -y cmake build-essential pkg-config libssl-dev

# Clone và build quiche
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche
cargo build --release --examples

# Test với quiche-client (terminal khác)
./target/release/examples/quiche-client \
  --no-verify \
  https://localhost:4433/index.html
```
```

**Bước 2: Verify installation (1 giờ)**
```bash
# Check built binaries
ls -la target/release/examples/
# Should see: quiche-server, quiche-client

# Test basic functionality
./target/release/examples/quiche-client --help
./target/release/examples/quiche-server --help
```

**Bước 3: Tạo SSL certificates (1 giờ)**
```bash
mkdir -p ~/quic-demo/certs
cd ~/quic-demo/certs

# Generate self-signed certificate
openssl req -x509 -newkey rsa:4096 \
  -keyout key.pem -out cert.pem \
  -days 365 -nodes \
  -subj "/C=VN/ST=HCMC/L=HCMC/O=UIT/CN=localhost"
```

**Bước 4: Document setup (2 giờ)**
- Ghi chú các bước cài đặt
- Note các issues gặp phải
- Tạo troubleshooting guide

#### Task 4.2 (TV1): Tạo QUIC Server Demo

**Bước 1: Start QUIC server (1 giờ)**
```bash
cd ~/quiche
./target/release/examples/quiche-server \
  --cert ~/quic-demo/certs/cert.pem \
  --key ~/quic-demo/certs/key.pem \
  --root ~/quic-demo/www \
  --listen 0.0.0.0:4433
```

**Bước 2: Create test content (1 giờ)**
```bash
mkdir -p ~/quic-demo/www
echo "<h1>QUIC Demo Server</h1>" > ~/quic-demo/www/index.html
```

**Bước 3: Test với client (2 giờ)**
```bash
# Test with quiche-client
./target/release/examples/quiche-client \
  --no-verify \
  https://localhost:4433/index.html

# Test with curl (if HTTP/3 enabled)
curl --http3 -k https://localhost:4433/index.html
```

**Bước 4: Document server setup (1 giờ)**

#### Task 4.1 (TV2): Demo Stream Multiplexing

**Bước 1: Setup test scenario (2 giờ)**
```bash
# Create multiple files for concurrent requests
for i in {1..5}; do
  dd if=/dev/urandom of=~/quic-demo/www/file$i.bin bs=100K count=1
done
```

**Bước 2: Capture multiplexed streams (2 giờ)**
```bash
# Start Wireshark with QUIC filter
# Filter: quic

# Run concurrent requests
# Observe multiple STREAM frames on same connection
```

**Bước 3: Analyze stream independence (1.5 giờ)**
- Show multiple Stream IDs
- Demonstrate data on different streams
- Note: streams don't block each other

**Bước 4: Document findings (0.5 giờ)**

#### Task 4.3 (TV2): Demo Connection Migration

**Bước 1: Setup network interfaces (1.5 giờ)**
```bash
# Tạo virtual network interface để test connection migration
sudo ip link add dummy0 type dummy
sudo ip addr add 192.168.100.1/24 dev dummy0
sudo ip link set dummy0 up

# Hoặc sử dụng Docker để tạo các network namespaces
docker network create quic-net-1
docker network create quic-net-2

# Kiểm tra network interfaces
ip addr show
```

**Bước 2: Demo migration scenario (2 giờ)**
```bash
# Terminal 1: Start QUIC server
cd ~/quiche
./target/release/examples/quiche-server \
  --cert ~/quic-demo/certs/cert.pem \
  --key ~/quic-demo/certs/key.pem \
  --root ~/quic-demo/www \
  --listen 0.0.0.0:4433

# Terminal 2: Start Wireshark capture
tshark -i any -f "udp port 4433" -w ~/quic-demo/migration.pcap

# Terminal 3: Start client và trigger migration
# Bước 1: Kết nối qua interface A
./target/release/examples/quiche-client \
  --no-verify \
  https://localhost:4433/largefile.bin

# Note: Connection Migration scenario:
# 1. Establish QUIC connection on Interface A
# 2. During data transfer, change source IP
# 3. QUIC will automatically send PATH_CHALLENGE
# 4. Server responds with PATH_RESPONSE
# 5. Connection continues with same Connection ID
```

**Bước 3: Capture và analyze (1 giờ)**
- Wireshark capture before/after migration
- Show Connection ID unchanged
- Show PATH validation frames

**Bước 4: Document demo (0.5 giờ)**

---

## 🗓️ TUẦN 5: PHÂN TÍCH SÂU CÁC CƠ CHẾ (20 giờ/người)

### Thành viên 1 (20 giờ) - Phân tích Handshake và Bảo mật

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 5.1 | Phân tích chi tiết Handshake Packets | - Decode Initial packets<br>- Decode Handshake packets<br>- Analyze CRYPTO frames content | 6 | Detailed packet analysis |
| 5.2 | Phân tích Key Derivation | - Track key derivation process<br>- Show encryption key changes<br>- Document key hierarchy | 5 | Technical document |
| 5.3 | Phân tích Header Protection | - Show protected vs unprotected headers<br>- Analyze protection algorithm<br>- Impact on security | 5 | Analysis document |
| 5.4 | Security Analysis Summary | - Summarize security mechanisms<br>- Compare với TLS over TCP<br>- Identify potential vulnerabilities | 4 | Security summary |

### Thành viên 2 (20 giờ) - Phân tích Performance Mechanisms

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 5.1 | Phân tích ACK Behavior | - Capture ACK frames<br>- Analyze ACK ranges<br>- Measure ACK Delay | 6 | ACK analysis document |
| 5.2 | Phân tích Congestion Control | - Monitor cwnd changes<br>- Observe slow start<br>- Capture loss recovery | 5 | CC analysis document |
| 5.3 | Phân tích Flow Control | - Track flow control limits<br>- Analyze credit updates<br>- Stream vs Connection level | 5 | Flow control analysis |
| 5.4 | Performance Summary | - Summarize performance mechanisms<br>- Identify optimization opportunities<br>- Best practices | 4 | Performance summary |

### 📋 Deliverables cuối Tuần 5:
- [ ] Detailed Handshake Analysis (TV1)
- [ ] Key Derivation Documentation (TV1)
- [ ] ACK và Congestion Control Analysis (TV2)
- [ ] Performance Mechanisms Summary (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 5

#### Task 5.1 (TV1): Phân tích chi tiết Handshake Packets

**Bước 1: Capture handshake với Wireshark (2 giờ)**
```
Wireshark settings:
- Capture filter: udp port 4433
- Display filter: quic
- Enable QUIC decryption (if possible)
```

**Bước 2: Decode Initial Packets (2 giờ)**
- Identify packet type (Long Header, Type = Initial)
- Decode Connection IDs
- Analyze CRYPTO frame với ClientHello

**Bước 3: Document each packet (2 giờ)**
```
Initial Packet Analysis:
- Header Form: Long (1)
- Fixed Bit: 1
- Type: Initial (0x00)
- Version: 0x00000001
- DCID Length: 8
- DCID: [bytes]
- SCID Length: 0
- Token Length: 0
- Payload: CRYPTO frame containing TLS ClientHello
```

#### Task 5.1 (TV2): Phân tích ACK Behavior

**Bước 1: Capture ACK frames (2 giờ)**
- Start data transfer
- Capture ACK frames
- Note ACK timing

**Bước 2: Analyze ACK content (2 giờ)**
```
ACK Frame Analysis:
- Largest Acknowledged: 15
- ACK Delay: 2500 (25ms)
- ACK Range Count: 1
- First ACK Range: 5 (acknowledges 11-15)
- Gap: 2 (missing 8, 9)
- ACK Range: 3 (acknowledges 4-7)

→ Received: 4,5,6,7,11,12,13,14,15
→ Missing: 8,9,10
```

**Bước 3: Calculate RTT (1.5 giờ)**
- Track packet send time
- Receive ACK time
- Calculate RTT samples

**Bước 4: Document findings (0.5 giờ)**

---

## 🗓️ TUẦN 6: ỨNG DỤNG THỰC TẾ VÀ CASE STUDIES (20 giờ/người)

### Thành viên 1 (20 giờ) - Triển khai QUIC trong thực tế

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 6.1 | Nghiên cứu Google's QUIC Deployment | - Chrome browser support<br>- YouTube, Google services<br>- Deployment statistics | 5 | Case study document |
| 6.2 | Nghiên cứu Cloudflare's QUIC | - Cloudflare edge network<br>- HTTP/3 support<br>- Performance improvements | 5 | Case study document |
| 6.3 | Nghiên cứu Facebook/Meta's QUIC | - Proxygen framework<br>- Mobile app usage<br>- Performance results | 5 | Case study document |
| 6.4 | Tổng hợp Deployment Best Practices | - Server configuration<br>- Client compatibility<br>- Fallback strategies | 5 | Best practices guide |

### Thành viên 2 (20 giờ) - Challenges và Future của QUIC

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 6.1 | Phân tích Deployment Challenges | - UDP blocking<br>- Middlebox issues<br>- CPU overhead | 5 | Challenges document |
| 6.2 | Nghiên cứu QUIC Extensions | - QUIC Version 2 (RFC 9369)<br>- Multipath QUIC<br>- QUIC-LB (Load Balancing) | 5 | Extensions document |
| 6.3 | Nghiên cứu QUIC Applications | - WebTransport<br>- MASQUE (proxy)<br>- Media over QUIC | 5 | Applications document |
| 6.4 | Tổng hợp Future Directions | - Ongoing IETF work<br>- Research areas<br>- Industry adoption | 5 | Future directions |

### 📋 Deliverables cuối Tuần 6:
- [ ] Case Studies: Google, Cloudflare, Meta (TV1)
- [ ] Deployment Best Practices Guide (TV1)
- [ ] Challenges và Solutions Document (TV2)
- [ ] QUIC Extensions và Future Document (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 6

#### Task 6.1 (TV1): Nghiên cứu Google's QUIC Deployment

**Bước 1: Thu thập thông tin (2 giờ)**
- Google QUIC blog posts
- Chrome platform status
- YouTube engineering blog

**Bước 2: Phân tích deployment scale (2 giờ)**
```
Google QUIC Statistics:
- % traffic using QUIC
- Services using QUIC: YouTube, Gmail, Google Search, etc.
- Latency improvements observed
- Mobile vs desktop usage
```

**Bước 3: Viết case study (1 giờ)**
```markdown
## Case Study: Google QUIC Deployment

### Background
- Google developed gQUIC in 2012
- Initial deployment in Chrome 2013

### Scale
- X% of Google's traffic uses QUIC
- Billions of connections per day

### Key Results
- Y% reduction in latency
- Z% improvement in video rebuffering

### Lessons Learned
- ...
```

#### Task 6.1 (TV2): Phân tích Deployment Challenges

**Bước 1: Research UDP blocking (1.5 giờ)**
- Corporate firewalls
- Mobile carriers
- Statistics on UDP reachability

**Bước 2: Analyze middlebox issues (1.5 giờ)**
- NAT behavior
- Load balancer challenges
- DDoS protection

**Bước 3: Document CPU overhead (1.5 giờ)**
- User-space vs kernel
- Encryption cost
- Comparison với TCP

**Bước 4: Write summary (0.5 giờ)**
```markdown
## QUIC Deployment Challenges

### 1. UDP Blocking
- ~5-10% of networks block UDP/443
- Solution: Fallback to TCP/TLS

### 2. Middlebox Issues
- NATs may timeout UDP flows faster
- Load balancers need Connection ID awareness
- Solution: QUIC-LB protocol

### 3. CPU Overhead
- User-space processing costs
- Encryption in software
- Solution: Hardware acceleration, kernel implementation
```

---

## 🗓️ TUẦN 7: PHÂN TÍCH VÀ ĐÁNH GIÁ (15 giờ/người)

### Thành viên 1 (15 giờ) - Tổng hợp và Đánh giá

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 7.1 | Tổng hợp kiến thức về QUIC | - Kiến trúc và thiết kế<br>- Các cơ chế hoạt động<br>- Ưu điểm chính | 4 | Summary document |
| 7.2 | Đánh giá ưu điểm QUIC | - Faster handshake<br>- No HOL blocking<br>- Connection migration<br>- Built-in encryption | 4 | Advantages analysis |
| 7.3 | Đánh giá hạn chế QUIC | - UDP challenges<br>- CPU overhead<br>- Deployment complexity | 3 | Limitations analysis |
| 7.4 | Đưa ra khuyến nghị | - Khi nào nên dùng QUIC<br>- Best practices<br>- Migration strategies | 4 | Recommendations |

### Thành viên 2 (15 giờ) - Chuẩn bị Demo và Presentation

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 7.1 | Chuẩn bị Demo Script | - Demo scenarios<br>- Step-by-step guide<br>- Troubleshooting | 4 | Demo script |
| 7.2 | Tạo Video Demo | - Record demo sessions<br>- Edit và annotate<br>- Voiceover | 5 | Demo videos |
| 7.3 | Tạo Diagrams tổng hợp | - Architecture diagrams<br>- Flow diagrams<br>- Comparison charts | 4 | Visual assets |
| 7.4 | Review Demo với TV1 | - Run through demos<br>- Fix issues<br>- Finalize | 2 | Ready demos |

### 📋 Deliverables cuối Tuần 7:
- [ ] Tổng hợp kiến thức QUIC (TV1)
- [ ] Đánh giá ưu/nhược điểm (TV1)
- [ ] Demo Script và Videos (TV2)
- [ ] Visual Assets (TV2)

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 7

#### Task 7.1 (TV1): Tổng hợp kiến thức về QUIC

**Bước 1: Compile all research (2 giờ)**
- Review Tuần 1-6 materials
- Organize by topic
- Identify key points

**Bước 2: Write summary (2 giờ)**
```markdown
## Tổng hợp: QUIC Protocol

### 1. Kiến trúc
- Transport layer over UDP
- Integrated TLS 1.3
- Stream-based multiplexing

### 2. Các cơ chế chính
- 1-RTT/0-RTT handshake
- Connection migration
- Per-stream flow control
- Pluggable congestion control

### 3. Bảo mật
- Always encrypted
- Header protection
- Forward secrecy

### 4. Ứng dụng
- HTTP/3
- WebTransport
- Real-time media
```

#### Task 7.2 (TV2): Tạo Video Demo

**Bước 1: Plan demo scenarios (1 giờ)**
```
Demo 1: QUIC Handshake (3 minutes)
- Show 1-RTT handshake
- Packet analysis

Demo 2: Stream Multiplexing (3 minutes)
- Multiple concurrent streams
- Show independence

Demo 3: Connection Migration (2 minutes)
- IP change
- Connection persists
```

**Bước 2: Record demos (3 giờ)**
- Screen recording
- Clear explanations
- Highlight key points

**Bước 3: Edit videos (1 giờ)**
- Add annotations
- Cut unnecessary parts
- Add voiceover

---

## 🗓️ TUẦN 8: VIẾT BÁO CÁO VÀ HOÀN THIỆN (20 giờ/người)

### Thành viên 1 (20 giờ) - Viết báo cáo

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 8.1 | Viết Chương 1: Giới thiệu | - Đặt vấn đề<br>- Mục tiêu nghiên cứu<br>- Phạm vi | 3 | Chương 1 (2-3 trang) |
| 8.2 | Viết Chương 2: Kiến trúc QUIC | - Lịch sử phát triển<br>- Kiến trúc tổng quan<br>- Packet và Frame structure | 6 | Chương 2 (10-12 trang) |
| 8.3 | Viết Chương 3: Các cơ chế hoạt động | - Handshake<br>- Stream Multiplexing<br>- Loss Detection<br>- Congestion Control | 6 | Chương 3 (10-12 trang) |
| 8.4 | Viết Chương 6: Kết luận | - Tóm tắt<br>- Đóng góp<br>- Hướng phát triển | 3 | Chương 6 (2-3 trang) |
| 8.5 | Review báo cáo | - Kiểm tra lỗi<br>- Đồng bộ format<br>- References | 2 | Final review |

### Thành viên 2 (20 giờ) - Viết báo cáo và Slides

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 8.1 | Viết Chương 4: Demo và Thực hành | - Môi trường setup<br>- Demo scenarios<br>- Screenshots | 5 | Chương 4 (8-10 trang) |
| 8.2 | Viết Chương 5: Ứng dụng thực tế | - Case studies<br>- Best practices<br>- Challenges | 5 | Chương 5 (8-10 trang) |
| 8.3 | Thiết kế Slides thuyết trình | - 20-25 slides<br>- Key findings<br>- Demo screenshots | 5 | Slide deck |
| 8.4 | Format báo cáo | - Mục lục<br>- Danh mục hình<br>- Tài liệu tham khảo | 3 | Formatted document |
| 8.5 | Review và finalize | - Final proofreading<br>- Cross-check data<br>- Package deliverables | 2 | Final review |

### 📋 Deliverables cuối Tuần 8:
- [ ] Báo cáo hoàn chỉnh (40-50 trang)
- [ ] Slide thuyết trình (20-25 slides)
- [ ] Demo videos
- [ ] Source code và scripts

### 📖 HƯỚNG DẪN THỰC HIỆN CHI TIẾT - TUẦN 8

#### Task 8.1 (TV1): Viết Chương 1 - Giới thiệu

**Outline:**
```markdown
## Chương 1: Giới thiệu

### 1.1 Đặt vấn đề
- Sự phát triển của Internet và nhu cầu về hiệu năng
- Hạn chế của TCP trong môi trường hiện đại
- Nhu cầu về giao thức transport mới

### 1.2 Mục tiêu nghiên cứu
- Tìm hiểu toàn diện về QUIC protocol
- Phân tích các cơ chế hoạt động
- Đánh giá ứng dụng thực tế
- Xây dựng demo thực hành

### 1.3 Phạm vi và giới hạn
- Tập trung vào IETF QUIC (RFC 9000)
- Không đi sâu vào implementation details
- Focus on concepts và mechanisms
```

#### Task 8.2 (TV2): Thiết kế Slides

**Slide Structure:**
```
1. Title slide
2. Agenda
3-4. Introduction & Problem Statement
5-8. QUIC Architecture
9-12. Key Mechanisms (Handshake, Streams, etc.)
13-15. Security Features
16-18. Demo Screenshots
19-21. Real-world Applications
22-23. Challenges & Future
24. Conclusions
25. Q&A
```

---

## 📊 BẢNG TỔNG HỢP PHÂN CÔNG THEO THÀNH VIÊN

### Thành viên 1 - Trưởng nhóm (Kiến trúc, Bảo mật, Connection)

| Tuần | Công việc chính | Giờ |
|------|----------------|-----|
| 1 | Lịch sử QUIC + Kiến trúc Protocol Stack + RFC 9000 | 15 |
| 2 | TLS 1.3 Integration + Handshake + Packet Protection | 15 |
| 3 | Loss Detection + ACK Mechanism | 20 |
| 4 | QUIC Implementation Setup + Connection Demo | 20 |
| 5 | Handshake Analysis + Security Analysis | 20 |
| 6 | Case Studies: Google, Cloudflare, Meta | 20 |
| 7 | Tổng hợp + Đánh giá + Khuyến nghị | 15 |
| 8 | Chương 1, 2, 3, 6 + Review | 20 |
| **TỔNG** | | **145 giờ** |

### Thành viên 2 (Stream Multiplexing, Congestion Control, Demo)

| Tuần | Công việc chính | Giờ |
|------|----------------|-----|
| 1 | Packet Structure + Frame Types + HTTP/3 | 15 |
| 2 | Connection Migration + Flow Control + Stream Multiplexing | 15 |
| 3 | Congestion Control + ECN | 20 |
| 4 | Stream Demo + Flow Control Demo + Migration Demo | 20 |
| 5 | ACK Analysis + Performance Analysis | 20 |
| 6 | Challenges + Extensions + Future Directions | 20 |
| 7 | Demo Script + Videos + Diagrams | 15 |
| 8 | Chương 4, 5 + Slides + Format | 20 |
| **TỔNG** | | **145 giờ** |

---

## 📈 Biểu đồ Gantt

```
Tuần        1         2         3         4         5         6         7         8
           |---------|---------|---------|---------|---------|---------|---------|---------|
TV1        [Kiến trúc][Bảo mật ][Loss Det][Demo    ][Analysis][Cases   ][Tổng hợp][Báo cáo ]
           [History ][Handshake][ACK     ][Setup   ][Security][Studies ][Đánh giá][Ch1,2,3,6]
           |---------|---------|---------|---------|---------|---------|---------|---------|
TV2        [Packets ][Migration][Congest ][Demo    ][Perform ][Future  ][Demo    ][Báo cáo ]
           [Frames  ][Flow Ctrl][Control ][Features][Analysis][Ext     ][Videos  ][Ch4,5   ]
           |---------|---------|---------|---------|---------|---------|---------|---------|
Output     [Docs    ][Docs    ][Tech    ][Demos   ][Analysis][Cases   ][Summary ][Report  ]
           [Diagrams][Diagrams][Docs    ][Captures][Docs    ][Guides  ][Slides  ][Slides  ]
           |---------|---------|---------|---------|---------|---------|---------|---------|
```

---

## ✅ CHECKLIST TIẾN ĐỘ CHI TIẾT

### Tuần 1: Nền tảng và Kiến trúc
- [ ] Tài liệu lịch sử và động lực phát triển QUIC (TV1)
- [ ] Sơ đồ kiến trúc QUIC Protocol Stack (TV1)
- [ ] Tài liệu QUIC Packet Structure (TV2)
- [ ] Bảng tổng hợp Frame Types (TV2)
- [ ] Danh sách tài liệu tham khảo (Cả 2)

### Tuần 2: Bảo mật và Connection Management
- [ ] Tài liệu TLS 1.3 Integration (TV1)
- [ ] Sequence diagrams cho 1-RTT và 0-RTT handshake (TV1)
- [ ] Tài liệu Connection Migration (TV2)
- [ ] Tài liệu Flow Control và Stream Multiplexing (TV2)

### Tuần 3: Loss Detection và Congestion Control
- [ ] Tài liệu ACK Mechanism (TV1)
- [ ] Flowcharts cho Loss Detection Algorithm (TV1)
- [ ] Tài liệu Congestion Control (TV2)
- [ ] Comparison document: QUIC CC vs TCP CC (TV2)

### Tuần 4: Triển khai và Demo
- [ ] QUIC Server hoạt động (TV1)
- [ ] Demo Connection Establishment (TV1)
- [ ] Demo Stream Multiplexing (TV2)
- [ ] Demo Connection Migration (TV2)

### Tuần 5: Phân tích sâu
- [ ] Detailed Handshake Analysis (TV1)
- [ ] Security Mechanisms Summary (TV1)
- [ ] ACK và Performance Analysis (TV2)
- [ ] Performance Mechanisms Summary (TV2)

### Tuần 6: Ứng dụng thực tế
- [ ] Case Studies: Google, Cloudflare, Meta (TV1)
- [ ] Deployment Best Practices Guide (TV1)
- [ ] Challenges và Solutions (TV2)
- [ ] QUIC Extensions và Future (TV2)

### Tuần 7: Phân tích và Đánh giá
- [ ] Tổng hợp kiến thức QUIC (TV1)
- [ ] Đánh giá ưu/nhược điểm (TV1)
- [ ] Demo Script và Videos (TV2)
- [ ] Visual Assets (TV2)

### Tuần 8: Báo cáo
- [ ] Chương 1: Giới thiệu (TV1)
- [ ] Chương 2: Kiến trúc QUIC (TV1)
- [ ] Chương 3: Các cơ chế hoạt động (TV1)
- [ ] Chương 4: Demo và Thực hành (TV2)
- [ ] Chương 5: Ứng dụng thực tế (TV2)
- [ ] Chương 6: Kết luận (TV1)
- [ ] Slide thuyết trình (TV2)
- [ ] Nộp báo cáo (Cả 2)

---

## 🔧 Công cụ sử dụng

| Công cụ | Mục đích | Link |
|---------|----------|------|
| quiche | QUIC implementation từ Cloudflare | https://github.com/cloudflare/quiche |
| msquic | QUIC implementation từ Microsoft | https://github.com/microsoft/msquic |
| Wireshark | Packet capture và analysis | https://wireshark.org |
| qvis | QUIC visualization tool | https://qvis.quictools.info |
| curl | HTTP client với HTTP/3 support | https://curl.se |
| draw.io | Vẽ diagrams | https://app.diagrams.net |

## 📚 Tài liệu tham khảo chính

| Tài liệu | Mô tả |
|----------|-------|
| RFC 9000 | QUIC: A UDP-Based Multiplexed and Secure Transport |
| RFC 9001 | Using TLS to Secure QUIC |
| RFC 9002 | QUIC Loss Detection and Congestion Control |
| RFC 9114 | HTTP/3 |
| RFC 9369 | QUIC Version 2 |
| Google Paper | The QUIC Transport Protocol: Design and Internet-Scale Deployment (2017) |

---

*Cập nhật lần cuối: 06/02/2026*
