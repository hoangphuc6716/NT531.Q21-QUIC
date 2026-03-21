# 📘 ĐỒ ÁN CHUYÊN NGÀNH: NGHIÊN CỨU GIAO THỨC QUIC

## BÁO CÁO CÔNG VIỆC THÀNH VIÊN 2 (TV2)

---

### 📋 Thông tin

| Thông tin | Chi tiết |
|-----------|----------|
| **Họ và tên** | Bùi Lê Huy Phước |
| **Vai trò** | Thành viên 2 (TV2) |
| **Môn học** | NT531.Q21 - Đánh giá hiệu năng mạng máy tính |
| **Đề tài** | Nghiên cứu và Demo các Đặc điểm Nổi bật của Giao thức QUIC |
| **Thiết bị phụ trách** | ☁️ Cloud VM 2 - Client (AP Singapore) |

---

## 📑 MỤC LỤC

### PHẦN A: LÝ THUYẾT VÀ NGHIÊN CỨU
- [A1. Tổng quan về QUIC (phần TV2)](#a1-tổng-quan-về-quic-phần-tv2)
- [A3. Packet và Frame Structure](#a3-packet-và-frame-structure)
- [A5. Stream Multiplexing](#a5-stream-multiplexing)
- [A7. Flow Control](#a7-flow-control)
- [A9. Security - TLS 1.3 Integration](#a9-security---tls-13-integration)
- [A11. So sánh QUIC vs TCP+TLS (phần TV2)](#a11-so-sánh-quic-vs-tcptls-phần-tv2)

### PHẦN B: THỰC HÀNH VÀ DEMO
- [B1. Setup Topology (phần TV2 - Client)](#b1-setup-topology-phần-tv2---client)
- [B3. Demo 2: Stream Multiplexing](#b3-demo-2-stream-multiplexing)
- [B5. Demo 4: Packet Loss Recovery](#b5-demo-4-packet-loss-recovery)
- [B6. Demo 5: Multi-client Stress Test (phần TV2)](#b6-demo-5-multi-client-stress-test-phần-tv2)
- [B7. Wireshark Analysis](#b7-wireshark-analysis)

### PHẦN C: PHÂN TÍCH VÀ BÁO CÁO
- [C2. Case Studies](#c2-case-studies)
- [C4. Viết báo cáo (phần TV2)](#c4-viết-báo-cáo-phần-tv2)
- [C5. Slides thuyết trình (phần TV2)](#c5-slides-thuyết-trình-phần-tv2)
- [C6. Quay video demo (phần TV2)](#c6-quay-video-demo-phần-tv2)

---

# PHẦN A: LÝ THUYẾT VÀ NGHIÊN CỨU

---

## A1. Tổng quan về QUIC (phần TV2)

### 🎯 Mục tiêu
> Nghiên cứu các RFC liên quan, các QUIC implementations phổ biến, hỗ trợ trình duyệt, và tạo biểu đồ thống kê adoption.

---

### A1.5: Các RFC liên quan đến QUIC

QUIC được chuẩn hóa bởi IETF thông qua nhiều RFC. Dưới đây là tổng hợp các RFC quan trọng nhất:

| RFC | Tên đầy đủ | Mô tả | Năm |
|-----|-----------|-------|-----|
| **RFC 9000** | QUIC: A UDP-Based Multiplexed and Secure Transport | Đặc tả core protocol: connection, stream, flow control, loss recovery | 2021 |
| **RFC 9001** | Using TLS to Secure QUIC | Cách tích hợp TLS 1.3 vào QUIC, encryption levels, key derivation | 2021 |
| **RFC 9002** | QUIC Loss Detection and Congestion Control | Cơ chế phát hiện mất gói, PTO, congestion control (NewReno/CUBIC) | 2021 |
| **RFC 9114** | HTTP/3 | Định nghĩa HTTP/3 - lớp ứng dụng chạy trên QUIC, QPACK header compression | 2022 |
| **RFC 9369** | QUIC Version 2 | Phiên bản cải tiến, thay đổi salt và labels cho key derivation | 2023 |

> **📌 Chú thích:** RFC 9000 là tài liệu quan trọng nhất, mô tả toàn bộ kiến trúc QUIC. Khi cần tra cứu chi tiết một tính năng cụ thể, nên tham chiếu RFC tương ứng. Ví dụ: cần tìm hiểu về encryption → RFC 9001, cần tìm hiểu congestion control → RFC 9002.

#### Mối quan hệ giữa các RFC

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│  RFC 9114   │     │  RFC 9369   │     │             │
│  HTTP/3     │     │  QUIC v2    │     │  Ứng dụng   │
│ (App Layer) │     │ (Updates)   │     │  khác       │
└──────┬──────┘     └──────┬──────┘     └──────┬──────┘
       │                   │                   │
       └───────────────────┼───────────────────┘
                           │
                    ┌──────┴──────┐
                    │  RFC 9000   │
                    │  QUIC Core  │
                    │ (Transport) │
                    └──────┬──────┘
                           │
              ┌────────────┼────────────┐
              │                         │
       ┌──────┴──────┐          ┌──────┴──────┐
       │  RFC 9001   │          │  RFC 9002   │
       │  TLS 1.3    │          │  Loss Det.  │
       │ (Security)  │          │ (Recovery)  │
       └─────────────┘          └─────────────┘
```

> **📌 Chú thích:** Sơ đồ trên cho thấy RFC 9000 (QUIC Core) là nền tảng. RFC 9001 xử lý bảo mật, RFC 9002 xử lý phục hồi mất gói. RFC 9114 (HTTP/3) và RFC 9369 (QUIC v2) xây dựng phía trên QUIC core.

---

### A1.6: Các QUIC Implementations phổ biến

| Implementation | Ngôn ngữ | License | Tổ chức | Đặc điểm nổi bật | Maturity |
|---------------|----------|---------|---------|-------------------|----------|
| **quiche** | Rust | BSD-2 | Cloudflare | Dùng cho Cloudflare edge, hiệu năng cao | ⭐⭐⭐⭐⭐ |
| **ngtcp2** | C | MIT | Tatsuhiro Tsujikawa | Được tích hợp trong curl, nhẹ | ⭐⭐⭐⭐½ |
| **quinn** | Rust | MIT/Apache | Community | Async QUIC, tích hợp tốt với Tokio | ⭐⭐⭐⭐ |
| **quic-go** | Go | MIT | Marten Seemann | Dùng trong Caddy web server | ⭐⭐⭐⭐½ |
| **msquic** | C | MIT | Microsoft | Native Windows, dùng trong Windows OS | ⭐⭐⭐⭐½ |
| **lsquic** | C | MIT | LiteSpeed | Dùng trong LiteSpeed web server | ⭐⭐⭐⭐ |

> **📌 Chú thích:** Trong đề tài này, nhóm sử dụng **quiche** (Cloudflare) vì: (1) hiệu năng cao nhờ viết bằng Rust, (2) documentation tốt, (3) có sẵn examples cho server/client, (4) được Cloudflare sử dụng production cho hàng triệu requests/giây.

#### Code minh họa - Biểu đồ so sánh Implementations & Browser Support

```python
# === [A1.6-A1.7] QUIC Implementations & Browser Support ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
import numpy as np

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(18, 8))

# === QUIC Implementations Comparison ===
impls = ['quiche\n(Cloudflare)', 'ngtcp2\n(curl)', 'quinn\n(Rust)', 'quic-go\n(Caddy)',
         'msquic\n(Microsoft)', 'lsquic\n(LiteSpeed)']
languages = ['Rust', 'C', 'Rust', 'Go', 'C', 'C']
maturity = [95, 90, 85, 88, 92, 80]
colors_impl = ['#e67e22', '#3498db', '#9b59b6', '#00d2d3', '#00a4ef', '#27ae60']

bars = ax1.barh(impls, maturity, color=colors_impl, edgecolor='white', linewidth=2, height=0.6)
ax1.set_xlabel('Maturity Score (%)', fontsize=12)
ax1.set_title('QUIC Implementations Comparison', fontsize=14, fontweight='bold')
ax1.set_xlim(0, 110)
ax1.grid(axis='x', alpha=0.3)

for bar, val, lang in zip(bars, maturity, languages):
    ax1.text(val + 1, bar.get_y() + bar.get_height()/2, f'{val}% ({lang})',
             va='center', fontsize=10, fontweight='bold')

# === Browser HTTP/3 Support Timeline ===
browsers = ['Chrome', 'Firefox', 'Edge', 'Safari', 'Opera']
support_year = [2020, 2021, 2020, 2021, 2020]
versions = ['v87+', 'v88+', 'v87+', 'v15+', 'v73+']
colors_br = ['#4285F4', '#FF7139', '#0078D7', '#007AFF', '#FF1B2D']

y_pos = np.arange(len(browsers))
bars2 = ax2.barh(y_pos, [2024 - y for y in support_year], left=support_year,
                  color=colors_br, edgecolor='white', linewidth=2, height=0.5)
ax2.set_yticks(y_pos)
ax2.set_yticklabels(browsers, fontsize=11)
ax2.set_xlabel('Year', fontsize=12)
ax2.set_title('Browser HTTP/3 (QUIC) Support', fontsize=14, fontweight='bold')
ax2.set_xlim(2019, 2025)
ax2.grid(axis='x', alpha=0.3)

for i, (bar, ver) in enumerate(zip(bars2, versions)):
    ax2.text(2024.1, i, ver, va='center', fontsize=10, fontweight='bold', color=colors_br[i])

plt.tight_layout()
plt.savefig('a1_implementations_browsers.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

---

### A1.7: Hỗ trợ trình duyệt (Browser Support)

| Trình duyệt | Phiên bản hỗ trợ HTTP/3 | Năm bắt đầu | Ghi chú |
|-------------|-------------------------|-------------|---------|
| **Google Chrome** | v87+ | 2020 | Enabled by default, kiểm tra tại `chrome://flags/#enable-quic` |
| **Mozilla Firefox** | v88+ | 2021 | Enabled by default từ Firefox 88 |
| **Microsoft Edge** | v87+ | 2020 | Chromium-based, đồng bộ với Chrome |
| **Apple Safari** | v15+ (iOS 15, macOS Monterey) | 2021 | Hỗ trợ trên cả iOS và macOS |
| **Opera** | v73+ | 2020 | Chromium-based |

> **📌 Chú thích:** Tính đến năm 2024, tất cả các trình duyệt lớn đều hỗ trợ HTTP/3 (QUIC) theo mặc định. Điều này cho thấy QUIC đã đạt mức độ adoption rộng rãi trong thực tế.

---

### A1.8: Biểu đồ QUIC Adoption Statistics

#### Code minh họa - QUIC Adoption Pie Chart & Bar Chart

```python
# === [A1.8] QUIC Adoption Statistics ===
import matplotlib.pyplot as plt
import numpy as np

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(16, 7))

# --- Pie Chart: Protocol share on Internet ---
labels_pie = ['QUIC (HTTP/3)', 'HTTP/2', 'HTTP/1.1']
sizes = [26.5, 45.3, 28.2]
colors_pie = ['#3498db', '#2ecc71', '#e74c3c']
explode = (0.06, 0, 0)

wedges, texts, autotexts = ax1.pie(
    sizes, explode=explode, labels=labels_pie, colors=colors_pie,
    autopct='%1.1f%%', shadow=True, startangle=90,
    textprops={'fontsize': 12}, pctdistance=0.75)

for autotext in autotexts:
    autotext.set_fontweight('bold')
    autotext.set_color('white')

ax1.set_title('Internet Traffic by Protocol (2024)\nSource: W3Techs',
              fontsize=13, fontweight='bold')

# --- Bar Chart: Adoption by company ---
companies = ['Google\n(YouTube)', 'Cloudflare', 'Meta\n(FB, IG)', 'Akamai', 'Microsoft', 'Apple']
adoption = [95, 85, 75, 60, 50, 45]
colors_bar = ['#4285F4', '#F38020', '#1877F2', '#009ACD', '#00A4EF', '#A2AAAD']

bars = ax2.barh(companies, adoption, color=colors_bar, edgecolor='white', linewidth=2, height=0.6)
ax2.set_xlabel('QUIC Adoption (%)', fontsize=12)
ax2.set_title('QUIC Adoption by Company (2024 est.)', fontsize=13, fontweight='bold')
ax2.set_xlim(0, 110)
ax2.grid(axis='x', alpha=0.3)

for bar, val in zip(bars, adoption):
    ax2.text(val + 1.5, bar.get_y() + bar.get_height()/2, f'{val}%',
             va='center', fontsize=11, fontweight='bold')

plt.tight_layout()
plt.savefig('a1_quic_adoption.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

> **📌 Chú thích:** Biểu đồ Pie cho thấy QUIC (HTTP/3) chiếm khoảng 26.5% lưu lượng Internet toàn cầu tính đến 2024. Google dẫn đầu adoption với 95% traffic sử dụng QUIC (YouTube, Search, Gmail).

---

## A3. Packet và Frame Structure

### 🎯 Mục tiêu
> Hiểu **cấu trúc chi tiết** của QUIC packets và frames ở mức byte-level. Đây là kiến thức nền tảng để phân tích Wireshark captures trong phần demo.

---

### A3.1: Long Header Packets

QUIC sử dụng 2 loại header: **Long Header** (dùng trong handshake) và **Short Header** (dùng sau handshake). Long Header có 4 loại packet:

#### 4 loại Long Header Packets

| Loại Packet | Type Value | Mục đích | Encryption Level |
|------------|------------|----------|-----------------|
| **Initial** | 0x00 | Packet đầu tiên trong handshake, chứa ClientHello | Initial keys (từ Destination CID) |
| **0-RTT** | 0x01 | Early data trước khi handshake hoàn thành | 0-RTT keys (từ PSK) |
| **Handshake** | 0x02 | Tiếp tục handshake, chứa Certificate, Finished | Handshake keys |
| **Retry** | 0x03 | Server yêu cầu client retry (address validation) | Không encrypt |

#### Cấu trúc Long Header

```
Long Header Format (RFC 9000, Section 17.2):
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+
|1|1|T T|X X X X|    Byte 0: Header Form (1=Long), Fixed Bit (1),
+-+-+-+-+-+-+-+-+             Type (2 bits), Type-Specific (4 bits)
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                         Version (32 bits)                      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| DCID Len (8)  |    Destination Connection ID Length
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|               Destination Connection ID (0..160 bits)          |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
| SCID Len (8)  |    Source Connection ID Length
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Source Connection ID (0..160 bits)              |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Type-Specific Payload (*)                   |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

> **📌 Giải thích các trường:**
> - **Header Form (1 bit):** Giá trị `1` → Long Header, `0` → Short Header
> - **Fixed Bit (1 bit):** Luôn bằng `1` (dùng để phân biệt với non-QUIC packets)
> - **Type (2 bits):** Xác định loại packet (Initial=00, 0-RTT=01, Handshake=10, Retry=11)
> - **Version (32 bits):** QUIC version (v1 = 0x00000001, v2 = 0x6b3343cf)
> - **DCID/SCID:** Connection ID của destination/source, tối đa 20 bytes mỗi cái

---

### A3.2: Short Header Packets (1-RTT)

Short Header được sử dụng **sau khi handshake hoàn thành**, tối ưu cho data transfer:

```
Short Header Format (RFC 9000, Section 17.3):
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+
|0|1|S|R|R|K|P P|    Byte 0: Header Form (0=Short), Fixed (1),
+-+-+-+-+-+-+-+-+             Spin Bit, Reserved, Key Phase, PN Length
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                 Destination Connection ID (*)                  |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                      Packet Number (8/16/24/32 bits)           |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                     Encrypted Payload (*)                      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

> **📌 So sánh Long Header vs Short Header:**
> | Đặc điểm | Long Header | Short Header |
> |----------|-------------|-------------|
> | Khi nào dùng | Handshake (Initial, 0-RTT, Handshake) | Sau handshake (1-RTT data) |
> | Version field | Có (32 bits) | Không |
> | Source CID | Có | Không |
> | Kích thước | Lớn hơn (nhiều overhead) | Nhỏ gọn (ít overhead) |
> | Spin Bit | Không | Có (đo RTT passive) |

---

### A3.3: Packet Number Spaces

QUIC sử dụng **3 Packet Number Spaces** riêng biệt:

| Space | Dùng cho | Packet Types | ACK riêng |
|-------|---------|-------------|-----------|
| **Initial** | Giai đoạn khởi tạo | Initial packets | Có |
| **Handshake** | Giai đoạn bắt tay | Handshake packets | Có |
| **Application Data** | Truyền dữ liệu | 0-RTT và 1-RTT packets | Có |

> **📌 Tại sao cần 3 spaces riêng biệt?**
> - Mỗi space có **ACK riêng** → tránh nhầm lẫn giữa các loại packets
> - **Loss recovery riêng biệt** cho mỗi space → hiệu quả hơn
> - Packet numbers trong mỗi space **bắt đầu từ 0** và **tăng đều, không bao giờ lặp lại**

---

### A3.4: Bảng tổng hợp Frame Types

Dưới đây là bảng đầy đủ tất cả Frame Types trong QUIC (RFC 9000, Sections 12-19):

| Frame Type | Value | Mô tả | Phân loại |
|------------|-------|-------|-----------|
| **PADDING** | 0x00 | Padding bytes, không có ý nghĩa data | Connection Mgmt |
| **PING** | 0x01 | Keep-alive, kiểm tra connection còn sống | Connection Mgmt |
| **ACK** | 0x02-0x03 | Báo nhận packets, hỗ trợ ACK ranges | Connection Mgmt |
| **RESET_STREAM** | 0x04 | Hủy một stream (abrupt termination) | Error Handling |
| **STOP_SENDING** | 0x05 | Yêu cầu peer ngừng gửi trên stream | Error Handling |
| **CRYPTO** | 0x06 | Chứa TLS handshake messages | Data Transfer |
| **NEW_TOKEN** | 0x07 | Token mới cho 0-RTT (address validation) | Connection Mgmt |
| **STREAM** | 0x08-0x0f | Chứa application data | Data Transfer |
| **MAX_DATA** | 0x10 | Connection-level flow control limit | Flow Control |
| **MAX_STREAM_DATA** | 0x11 | Stream-level flow control limit | Flow Control |
| **MAX_STREAMS** | 0x12-0x13 | Giới hạn số streams tối đa | Flow Control |
| **DATA_BLOCKED** | 0x14 | Sender bị blocked ở connection level | Flow Control |
| **STREAM_DATA_BLOCKED** | 0x15 | Sender bị blocked ở stream level | Flow Control |
| **STREAMS_BLOCKED** | 0x16-0x17 | Sender đạt giới hạn streams | Flow Control |
| **NEW_CONNECTION_ID** | 0x18 | Cung cấp CID mới cho migration | Path/Migration |
| **RETIRE_CONNECTION_ID** | 0x19 | Hủy CID cũ | Path/Migration |
| **PATH_CHALLENGE** | 0x1a | Xác thực đường đi (path validation) | Path/Migration |
| **PATH_RESPONSE** | 0x1b | Phản hồi PATH_CHALLENGE | Path/Migration |
| **CONNECTION_CLOSE** | 0x1c-0x1d | Đóng connection | Error Handling |
| **HANDSHAKE_DONE** | 0x1e | Server báo handshake hoàn thành | Connection Mgmt |

#### Code minh họa - Frame Types Overview

```python
# === [A3.4] QUIC Frame Types Overview ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, ax = plt.subplots(figsize=(14, 8))

categories = ['Data Transfer', 'Flow Control', 'Connection Mgmt', 'Path/Migration', 'Error Handling']
frames = {
    'Data Transfer': ['STREAM (0x08-0x0f)', 'CRYPTO (0x06)', 'DATAGRAM'],
    'Flow Control': ['MAX_DATA (0x10)', 'MAX_STREAM_DATA (0x11)', 'MAX_STREAMS (0x12-0x13)',
                     'DATA_BLOCKED (0x14)', 'STREAM_DATA_BLOCKED (0x15)'],
    'Connection Mgmt': ['ACK (0x02-0x03)', 'PING (0x01)', 'PADDING (0x00)',
                        'NEW_TOKEN (0x07)', 'HANDSHAKE_DONE (0x1e)'],
    'Path/Migration': ['NEW_CONNECTION_ID (0x18)', 'RETIRE_CONNECTION_ID (0x19)',
                       'PATH_CHALLENGE (0x1a)', 'PATH_RESPONSE (0x1b)'],
    'Error Handling': ['RESET_STREAM (0x04)', 'STOP_SENDING (0x05)',
                       'CONNECTION_CLOSE (0x1c-0x1d)'],
}

colors_cat = ['#3498db', '#27ae60', '#e67e22', '#9b59b6', '#e74c3c']
y_pos = 0
for i, (cat, frame_list) in enumerate(frames.items()):
    for j, frame in enumerate(frame_list):
        rect = mpatches.FancyBboxPatch((0.5, y_pos), 12, 0.6,
                                        boxstyle="round,pad=0.02",
                                        facecolor=colors_cat[i], alpha=0.2,
                                        edgecolor=colors_cat[i], linewidth=1.5)
        ax.add_patch(rect)
        ax.text(6.5, y_pos + 0.3, frame, ha='center', va='center',
                fontsize=10, fontweight='bold' if j == 0 else 'normal')
        if j == 0:
            ax.text(14, y_pos + 0.3, f'[{cat}]', ha='left', va='center',
                    fontsize=11, fontweight='bold', color=colors_cat[i])
        y_pos += 0.75
    y_pos += 0.3

ax.set_xlim(0, 20)
ax.set_ylim(-0.5, y_pos + 0.5)
ax.invert_yaxis()
ax.set_title('QUIC Frame Types -- Classified by Function', fontsize=15, fontweight='bold')
ax.axis('off')
plt.tight_layout()
plt.savefig('a3_frame_types.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

---

### A3.5: STREAM Frame - Chi tiết

STREAM frame là frame quan trọng nhất, chứa application data:

```
STREAM Frame Format:
+-+-+-+-+-+-+-+-+
|0 0 0 1|O|L|F|  Type: 0x08-0x0f (bits 0-2: OFF, LEN, FIN flags)
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                         Stream ID (i)                          |  Variable-length integer
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                      [Offset (i)]                              |  Có nếu OFF=1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                      [Length (i)]                              |  Có nếu LEN=1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       Stream Data (*)                          |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

| Flag | Ký hiệu | Ý nghĩa |
|------|---------|---------|
| **FIN** (bit 0) | F | Đánh dấu đây là data cuối cùng trên stream |
| **LEN** (bit 1) | L | Có trường Length hay không |
| **OFF** (bit 2) | O | Có trường Offset hay không |

> **📌 Chú thích:** Offset cho phép receiver sắp xếp lại data đúng thứ tự ngay cả khi packets đến không theo thứ tự. Đây là cơ chế quan trọng cho stream independence - giúp loại bỏ HOL blocking.

---

### A3.6: ACK Frame - Chi tiết

ACK frame có cơ chế **ACK Ranges** mạnh mẽ hơn TCP:

```
ACK Frame Format:
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Largest Acknowledged (i)                    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                          ACK Delay (i)                         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       ACK Range Count (i)                      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                       First ACK Range (i)                      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                         [ACK Ranges]                           |
|   ┌───────────────────────────────────────────────────────┐   |
|   │  Gap (i)                                               │   |
|   │  ACK Range Length (i)                                  │   |
|   └───────────────────────────────────────────────────────┘   |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                      [ECN Counts]                              |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

> **📌 So sánh ACK trong QUIC vs TCP:**
> | Đặc điểm | TCP | QUIC |
> |----------|-----|------|
> | ACK format | Cumulative (1 số) | Ranges (nhiều khoảng) |
> | Ví dụ: nhận 1,2,4,5 | ACK=2 (chỉ ACK đến 2) | ACK [1-2, 4-5] (ACK cả 2 khoảng) |
> | Retransmit | Có thể retransmit đã nhận | Chính xác biết packet nào mất |
> | Packet Number | Có thể reuse | **Không bao giờ reuse** |

---

### A3.7: CRYPTO Frame

CRYPTO frame chứa TLS handshake messages:

```
CRYPTO Frame Format:
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                          Offset (i)                            |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                          Length (i)                             |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                        Crypto Data (*)                         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

> **📌 Chú thích:** CRYPTO frame tương tự STREAM frame nhưng **không có Stream ID** vì TLS data được xử lý riêng. Offset đảm bảo TLS messages được reassembled đúng thứ tự. CRYPTO frames xuất hiện trong Initial và Handshake packets.

---

### A3.8: Flow Control Frames

| Frame | Chức năng | Hướng |
|-------|----------|-------|
| **MAX_DATA** | Tăng connection-level limit | Receiver → Sender |
| **MAX_STREAM_DATA** | Tăng stream-level limit | Receiver → Sender |
| **MAX_STREAMS** | Tăng giới hạn số streams | Receiver → Sender |
| **DATA_BLOCKED** | Báo bị blocked ở connection level | Sender → Receiver |
| **STREAM_DATA_BLOCKED** | Báo bị blocked ở stream level | Sender → Receiver |
| **STREAMS_BLOCKED** | Báo đạt giới hạn streams | Sender → Receiver |

---

### A3.10: Biểu đồ Packet Structure

#### Code minh họa - Packet Structure Visualization

```python
# === [A3.10] QUIC Packet Structure Visualization ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(16, 10))

def draw_field(ax, x, y, w, h, label, sublabel, color, fontsize=10):
    rect = mpatches.FancyBboxPatch((x, y), w, h, boxstyle="round,pad=0.02",
                                    facecolor=color, edgecolor='white', linewidth=2, alpha=0.85)
    ax.add_patch(rect)
    ax.text(x + w/2, y + h*0.65, label, ha='center', va='center',
            fontsize=fontsize, fontweight='bold', color='white')
    if sublabel:
        ax.text(x + w/2, y + h*0.25, sublabel, ha='center', va='center',
                fontsize=7, color='white', alpha=0.8)

# === Long Header ===
ax1.set_xlim(0, 16); ax1.set_ylim(0, 5)
ax1.set_title('QUIC Long Header Packet (Initial, Handshake, 0-RTT, Retry)',
              fontsize=14, fontweight='bold')
ax1.axis('off')
y = 3.5
draw_field(ax1, 0.5, y, 1.5, 1, 'Form\n(1=Long)', '1 bit', '#e74c3c')
draw_field(ax1, 2, y, 1.5, 1, 'Fixed\nBit=1', '1 bit', '#e67e22')
draw_field(ax1, 3.5, y, 2, 1, 'Packet\nType', '2 bits', '#f1c40f')
draw_field(ax1, 5.5, y, 2, 1, 'Type-\nSpecific', '4 bits', '#f39c12')
draw_field(ax1, 7.5, y, 4, 1, 'Version', '32 bits', '#3498db')
draw_field(ax1, 11.5, y, 4, 1, 'DCID Len + DCID', '8 + 0-160 bits', '#2980b9')
y = 2
draw_field(ax1, 0.5, y, 4, 1, 'SCID Len + SCID', '8 + 0-160 bits', '#27ae60')
draw_field(ax1, 4.5, y, 3, 1, 'Packet\nNumber', '8-32 bits', '#8e44ad')
draw_field(ax1, 7.5, y, 8, 1, 'Payload (Frames)', 'Variable length', '#2c3e50')

# === Short Header ===
ax2.set_xlim(0, 16); ax2.set_ylim(0, 4)
ax2.set_title('QUIC Short Header Packet (1-RTT -- after handshake)',
              fontsize=14, fontweight='bold')
ax2.axis('off')
y = 2
draw_field(ax2, 0.5, y, 1.5, 1, 'Form\n(0=Short)', '1 bit', '#95a5a6')
draw_field(ax2, 2, y, 1.5, 1, 'Fixed\nBit=1', '1 bit', '#95a5a6')
draw_field(ax2, 3.5, y, 1.2, 1, 'Spin', '1 bit', '#16a085')
draw_field(ax2, 4.7, y, 1.5, 1, 'Reserved', '2 bits', '#7f8c8d')
draw_field(ax2, 6.2, y, 1.5, 1, 'Key\nPhase', '1 bit', '#e74c3c')
draw_field(ax2, 7.7, y, 1.5, 1, 'PN Len', '2 bits', '#9b59b6')
y = 0.5
draw_field(ax2, 0.5, y, 4, 1, 'Destination CID', 'Variable (no SCID!)', '#3498db')
draw_field(ax2, 4.5, y, 3, 1, 'Packet Number', '8-32 bits', '#8e44ad')
draw_field(ax2, 7.5, y, 8, 1, 'Payload (Encrypted Frames)', 'Variable length', '#2c3e50')

plt.tight_layout()
plt.savefig('a3_packet_structure.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```


## A5. Stream Multiplexing

### 🎯 Mục tiêu
> Hiểu **Stream Multiplexing** và **Head-of-Line (HOL) Blocking Problem** - điểm mạnh thứ 2 của QUIC.

### A5.1: Stream Types — 4 loại streams trong QUIC

| Stream Type | Bit 0 | Bit 1 | Initiated by | Direction | Ví dụ IDs |
|-------------|-------|-------|-------------|-----------|-----------|
| 0x0 | 0 | 0 | Client | Bidirectional | 0, 4, 8, 12... |
| 0x1 | 1 | 0 | Server | Bidirectional | 1, 5, 9, 13... |
| 0x2 | 0 | 1 | Client | Unidirectional | 2, 6, 10, 14... |
| 0x3 | 1 | 1 | Server | Unidirectional | 3, 7, 11, 15... |

> **📌 Chú thích:** Trong HTTP/3, mỗi HTTP request/response sử dụng 1 client-initiated bidirectional stream riêng (ID 0, 4, 8...). Unidirectional streams dùng cho QPACK control.

### A5.3: Stream States (RFC 9000 Section 3)

```
          ┌───────────┐
          │   Idle    │
          └─────┬─────┘
                │ open
                ▼
          ┌───────────┐
          │   Open    │
          └─────┬─────┘
    ┌───────────┼───────────┐
    ▼                       ▼
┌────────┐            ┌──────────┐
│  Half  │            │   Half   │
│ Closed │            │  Closed  │
│(Local) │            │ (Remote) │
└────┬───┘            └────┬─────┘
     │                     │
     └──────────┬──────────┘
                ▼
          ┌───────────┐
          │  Closed   │
          └───────────┘
```

#### Code minh họa - Stream State Machine

```python
# === [A5.3] QUIC Stream State Machine ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, ax = plt.subplots(figsize=(14, 10))
ax.set_xlim(0, 14); ax.set_ylim(0, 12); ax.axis('off')
ax.set_title('QUIC Stream States (RFC 9000 Section 3)', fontsize=15, fontweight='bold', pad=15)

states = [
    ('Idle', 7, 11, '#95a5a6', 1.0), ('Open', 7, 8.5, '#3498db', 1.0),
    ('Half-Closed\n(Local)', 3, 6, '#e67e22', 1.0),
    ('Half-Closed\n(Remote)', 11, 6, '#9b59b6', 1.0),
    ('Data Sent', 3, 3.5, '#f1c40f', 0.9), ('Data Recvd', 11, 3.5, '#2ecc71', 0.9),
    ('Closed', 7, 0.5, '#2c3e50', 1.0),
]
for name, x, y, color, radius in states:
    circle = plt.Circle((x, y), radius, facecolor=color, edgecolor='white', linewidth=2, alpha=0.85)
    ax.add_patch(circle)
    ax.text(x, y, name, ha='center', va='center', fontsize=9 if '\n' in name else 10,
            fontweight='bold', color='white')

plt.tight_layout()
plt.savefig('a5_stream_state_machine.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

### A5.5 & A5.6: HOL Blocking — Vấn đề và giải pháp QUIC

**TCP + HTTP/2 (HOL Blocking):**
```
TCP Byte Stream: Packet1[A]✓ → Packet2[B]✗LOST → Packet3[A]⏳ → Packet4[C]⏳
Kết quả: TẤT CẢ streams BLOCKED vì TCP yêu cầu in-order delivery!
```

**QUIC (No HOL Blocking):**
```
QUIC Streams: Packet1[A]✓ → Packet2[B]✗LOST → Packet3[A]✓ → Packet4[C]✓
Kết quả: Chỉ Stream B chờ retransmit. Stream A và C xử lý NGAY!
```

> **📌 Key insight:** QUIC streams hoàn toàn **độc lập** — packet loss trên 1 stream KHÔNG ảnh hưởng streams khác. Đây là lý do QUIC vượt trội HTTP/2 over TCP trên mạng có packet loss.

#### Code minh họa - HOL Blocking Comparison

```python
# === [A5.9] HOL Blocking Comparison: TCP vs QUIC ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(18, 8))
ax1.set_title('TCP + HTTP/2: Head-of-Line Blocking', fontsize=14, fontweight='bold', color='#c0392b')
streams_tcp = [
    ('Stream A', [(0, 2, '#3498db', '+OK'), (2, 4, '#bdc3c7', 'BLOCKED')]),
    ('Stream B', [(0, 1, '#e74c3c', 'X LOST'), (5, 2, '#3498db', '+OK Retransmit')]),
    ('Stream C', [(0, 0.5, '#3498db', '+OK'), (2, 4, '#bdc3c7', 'BLOCKED')]),
]
for i, (name, segments) in enumerate(streams_tcp):
    y = len(streams_tcp) - i - 1
    for start, duration, color, label in segments:
        rect = mpatches.FancyBboxPatch((start, y+0.1), duration, 0.8, boxstyle="round,pad=0.02",
                                        facecolor=color, edgecolor='white', linewidth=2, alpha=0.85)
        ax1.add_patch(rect)
        ax1.text(start+duration/2, y+0.5, label, ha='center', va='center',
                fontsize=9, fontweight='bold', color='white')
    ax1.text(-0.3, y+0.5, name, ha='right', va='center', fontsize=11, fontweight='bold')
ax1.set_xlim(-2, 8); ax1.set_ylim(-0.5, 3.5); ax1.set_xlabel('Time →'); ax1.set_yticks([])

ax2.set_title('QUIC: No Head-of-Line Blocking', fontsize=14, fontweight='bold', color='#27ae60')
streams_quic = [
    ('Stream A', [(0, 2, '#3498db', '+OK'), (2, 2, '#3498db', '+OK Continue!')]),
    ('Stream B', [(0, 1, '#e74c3c', 'X LOST'), (3, 2, '#27ae60', '+OK Retransmit')]),
    ('Stream C', [(0, 1.5, '#3498db', '+OK'), (1.5, 2.5, '#3498db', '+OK Continue!')]),
]
for i, (name, segments) in enumerate(streams_quic):
    y = len(streams_quic) - i - 1
    for start, duration, color, label in segments:
        rect = mpatches.FancyBboxPatch((start, y+0.1), duration, 0.8, boxstyle="round,pad=0.02",
                                        facecolor=color, edgecolor='white', linewidth=2, alpha=0.85)
        ax2.add_patch(rect)
        ax2.text(start+duration/2, y+0.5, label, ha='center', va='center',
                fontsize=9, fontweight='bold', color='white')
    ax2.text(-0.3, y+0.5, name, ha='right', va='center', fontsize=11, fontweight='bold')
ax2.set_xlim(-2, 8); ax2.set_ylim(-0.5, 3.5); ax2.set_xlabel('Time →'); ax2.set_yticks([])
plt.tight_layout()
plt.savefig('a5_hol_blocking_comparison.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

---

## A7. Flow Control

### A7.1-A7.2: 2 cấp độ Flow Control

| Cấp độ | Frame | Mô tả |
|--------|-------|-------|
| **Connection** | MAX_DATA | Giới hạn tổng data trên toàn connection |
| **Stream** | MAX_STREAM_DATA | Giới hạn data trên từng stream riêng |

### A7.3: Credit-based System

```
Sender ──── STREAM data ────→ Receiver
Sender ←── MAX_DATA (tăng limit) ── Receiver
Sender ←── MAX_STREAM_DATA ── Receiver
[Nếu hết quota]: Sender ──── DATA_BLOCKED ────→ Receiver
```

> **📌 So sánh:** TCP chỉ có 1 cấp flow control (rwnd). QUIC có 2 cấp → stream bị blocked không ảnh hưởng stream khác.

#### Code minh họa - Flow Control

```python
# === [A7.8] QUIC Flow Control Mechanism ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(18, 8))
# Connection-level
ax1.set_xlim(0, 12); ax1.set_ylim(0, 10); ax1.axis('off')
ax1.set_title('Connection-level Flow Control\n(MAX_DATA frame)', fontsize=13, fontweight='bold')
rect_bg = mpatches.FancyBboxPatch((1, 6), 10, 2, boxstyle="round,pad=0.05",
                                   facecolor='#ecf0f1', edgecolor='#bdc3c7', linewidth=2)
ax1.add_patch(rect_bg)
rect_used = mpatches.FancyBboxPatch((1, 6), 6.8, 2, boxstyle="round,pad=0.05",
                                     facecolor='#3498db', edgecolor='white', linewidth=2, alpha=0.8)
ax1.add_patch(rect_used)
ax1.text(4.4, 7, 'Used: 700KB', ha='center', va='center', fontsize=12, fontweight='bold', color='white')
ax1.text(6, 8.5, 'Connection Limit (MAX_DATA): 1024KB', ha='center', fontsize=11, fontweight='bold')

# Stream-level
ax2.set_xlim(0, 12); ax2.set_ylim(0, 10); ax2.axis('off')
ax2.set_title('Stream-level Flow Control\n(MAX_STREAM_DATA frame)', fontsize=13, fontweight='bold')
for name, used, limit, color, y in [('Stream 0', 180, 256, '#3498db', 7),
                                      ('Stream 4', 120, 256, '#e67e22', 4.5),
                                      ('Stream 8', 50, 256, '#9b59b6', 2)]:
    ratio = used / limit
    rect_bg = mpatches.FancyBboxPatch((2, y), 8, 1.5, boxstyle="round,pad=0.05",
                                       facecolor='#ecf0f1', edgecolor='#bdc3c7', linewidth=1.5)
    ax2.add_patch(rect_bg)
    rect_u = mpatches.FancyBboxPatch((2, y), 8*ratio, 1.5, boxstyle="round,pad=0.05",
                                      facecolor=color, edgecolor='white', linewidth=1.5, alpha=0.7)
    ax2.add_patch(rect_u)
    ax2.text(0.5, y+0.75, name, ha='left', fontsize=11, fontweight='bold', color=color)
    ax2.text(6, y+0.75, f'{used}/{limit}KB', ha='center', fontsize=10, fontweight='bold', color='white')
plt.tight_layout()
plt.savefig('a7_flow_control.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

---

## A9. Security (TLS 1.3 Integration)

### A9.1: So sánh TLS trong TCP vs QUIC

| Đặc điểm | TCP + TLS | QUIC + TLS 1.3 |
|----------|----------|----------------|
| TLS Record Layer | Sử dụng | **Không sử dụng** |
| TLS messages | Trong TLS Records | Trong **CRYPTO frames** |
| Header protection | Không | **Có** - PN encrypted |
| Plaintext data | Có thể | **Không bao giờ** |

### A9.3-A9.4: Header Protection & Payload Encryption

- **Header Protection:** Packet Number được encrypt bằng AES-ECB → chống traffic analysis
- **Payload Encryption:** AEAD — AES-128-GCM hoặc ChaCha20-Poly1305 (bắt buộc trong QUIC v1)
- **Key Update:** Cập nhật key mà không cần re-handshake (Key Phase bit toggle)
- **Anti-Amplification:** Server không gửi quá 3x data trước khi validate address

#### Code minh họa - Security Layers

```python
# === [A9] QUIC Security Layers ===
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches

fig, ax = plt.subplots(figsize=(16, 9))
ax.set_xlim(0, 16); ax.set_ylim(0, 10); ax.axis('off')
ax.set_title('QUIC Security Architecture', fontsize=16, fontweight='bold', pad=15)

features = [
    ('Always Encrypted', 'All QUIC packets encrypted (except Initial)', '#27ae60', 7),
    ('Header Protection', 'Packet Number encrypted → prevents traffic analysis', '#f39c12', 5),
    ('Forward Secrecy', 'TLS 1.3 ECDHE key exchange', '#3498db', 3),
    ('0-RTT Replay Protection', 'Server can reject replayed 0-RTT data', '#9b59b6', 1),
]
for label, desc, color, y in features:
    rect = mpatches.FancyBboxPatch((1, y), 14, 1.5, boxstyle="round,pad=0.1",
                                    facecolor=color, alpha=0.15, edgecolor=color, linewidth=2)
    ax.add_patch(rect)
    ax.text(2, y+0.75, f'🔒 {label}', ha='left', fontsize=12, fontweight='bold', color=color)
    ax.text(8, y+0.75, desc, ha='left', fontsize=10)
plt.tight_layout()
plt.savefig('a9_security_layers.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

---

## A11. So sánh QUIC vs TCP+TLS (phần TV2)

### Bảng So sánh Tổng hợp

| Feature | TCP + TLS 1.2 | TCP + TLS 1.3 | QUIC |
|---------|---------------|---------------|------|
| **New Connection** | 3 RTT | 2 RTT | **1 RTT** |
| **Resumed Connection** | 2 RTT | 1 RTT | **0 RTT** |
| **HOL Blocking** | Yes | Yes | **No** |
| **Connection Migration** | No | No | **Yes** |
| **Built-in Encryption** | Separate | Separate | **Integrated** |
| **User-space Impl.** | No (kernel) | No (kernel) | **Yes** |

#### Code minh họa - Feature Radar Chart

```python
# === [A11.10] Feature Radar Chart ===
import matplotlib.pyplot as plt
import numpy as np

fig, ax = plt.subplots(figsize=(10, 10), subplot_kw=dict(projection='polar'))
categories = ['Latency', 'HOL\nBlocking', 'Migration', 'Security', 'Multiplexing', 'Recovery']
N = len(categories)
tcp = [2, 2, 1, 3, 3, 3]; quic = [5, 5, 5, 5, 5, 4]
angles = [n/float(N)*2*np.pi for n in range(N)] + [0]
tcp += tcp[:1]; quic += quic[:1]
ax.plot(angles, tcp, 'o-', lw=2, label='TCP+TLS', color='#e74c3c', ms=8)
ax.fill(angles, tcp, alpha=0.25, color='#e74c3c')
ax.plot(angles, quic, 'o-', lw=2, label='QUIC', color='#3498db', ms=8)
ax.fill(angles, quic, alpha=0.25, color='#3498db')
ax.set_xticks(angles[:-1]); ax.set_xticklabels(categories, fontsize=11)
ax.set_ylim(0, 5); ax.legend(fontsize=12)
ax.set_title('Feature Comparison: QUIC vs TCP+TLS', fontsize=14, fontweight='bold', pad=20)
plt.tight_layout()
plt.savefig('a11_feature_radar.png', dpi=300, bbox_inches='tight', facecolor='white')
plt.show()
```

---

# PHẦN B: THỰC HÀNH VÀ DEMO

---

## B1. Setup Topology (phần TV2 - Client)

### Cloud VM 2 — Client (AP Singapore)

| Thành phần | Chi tiết |
|------------|----------|
| **Provider** | Oracle Cloud — Always Free Tier |
| **Region** | AP Southeast (Singapore) |
| **OS** | Ubuntu 22.04 LTS |
| **Software** | quiche-client, tshark, tcpdump, tc, curl |

### setup_client.sh

```bash
#!/bin/bash
echo "=== Setting up QUIC Client on Cloud VM 2 (AP Singapore) ==="
sudo apt update && sudo apt upgrade -y
sudo apt install -y build-essential cmake pkg-config libssl-dev \
                    tshark tcpdump curl git iproute2 net-tools
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
source $HOME/.cargo/env
git clone --recursive https://github.com/cloudflare/quiche.git
cd quiche && cargo build --release --examples
mkdir -p ~/quic-demo/{captures,logs,downloads}
echo "=== Setup Complete. Test: ping -c 10 <SERVER_IP> ==="
```

---

## B3. Demo 2: Stream Multiplexing

### 🎯 Chứng minh QUIC không bị HOL blocking

```bash
# Thêm 5% packet loss
sudo tc qdisc add dev ens3 root netem loss 5%

# QUIC concurrent downloads (5 streams)
time (
  for i in {1..5}; do
    ./target/release/examples/quiche-client --no-verify \
      https://<SERVER_IP>:4433/file$i.bin > ~/quic-demo/downloads/file$i.bin &
  done; wait
)

# TCP comparison
time (
  for i in {1..5}; do
    curl -k https://<SERVER_IP>/file$i.bin > ~/quic-demo/downloads/tcp_file$i.bin &
  done; wait
)
sudo tc qdisc del dev ens3 root
```

---

## B5. Demo 4: Packet Loss Recovery

### 🎯 Chứng minh QUIC recovery tốt hơn TCP

```bash
test_with_loss() {
  LOSS=$1
  echo "=== Testing with $LOSS% loss ==="
  sudo tc qdisc add dev ens3 root netem loss $LOSS%
  echo "QUIC:"; time ./target/release/examples/quiche-client --no-verify \
    https://<SERVER_IP>:4433/medium.bin > /dev/null
  echo "TCP:"; time curl -k -o /dev/null https://<SERVER_IP>/medium.bin
  sudo tc qdisc del dev ens3 root
}
test_with_loss 0; test_with_loss 1; test_with_loss 5; test_with_loss 10
```

### Kết quả mong đợi

| Packet Loss | TCP | QUIC | QUIC advantage |
|------------|-----|------|----------------|
| 0% | ~5.0s | ~4.8s | ~4% |
| 5% | ~7.8s | ~5.5s | ~30% |
| 10% | ~12.0s | ~7.0s | ~42% |

#### Code minh họa - Packet Loss Impact

```python
# === [B5.7] Packet Loss Impact ===
import matplotlib.pyplot as plt
loss = [0, 1, 2, 5, 10, 15, 20]
quic = [1.0, 1.08, 1.18, 1.45, 2.1, 3.2, 4.8]
tcp = [1.0, 1.25, 1.55, 2.3, 4.0, 6.5, 10.5]
fig, ax = plt.subplots(figsize=(12, 7))
ax.plot(loss, quic, 'o-', label='QUIC', color='#3498db', lw=2.5, ms=10)
ax.plot(loss, tcp, 's-', label='TCP', color='#e74c3c', lw=2.5, ms=10)
ax.fill_between(loss, quic, tcp, alpha=0.1, color='gray')
ax.set_xlabel('Packet Loss (%)'); ax.set_ylabel('Download Time (s)')
ax.set_title('Packet Loss Impact on Download Time', fontsize=14, fontweight='bold')
ax.legend(fontsize=12); ax.grid(True, alpha=0.3)
plt.tight_layout(); plt.savefig('b5_packet_loss.png', dpi=300); plt.show()
```

---

## B6. Demo 5: Multi-client Stress Test (phần TV2)

```bash
# 10 concurrent QUIC connections
time (for i in {1..10}; do
  ./target/release/examples/quiche-client --no-verify \
    https://<SERVER_IP>:4433/small.bin > /dev/null &
done; wait)

# TCP comparison
time (for i in {1..10}; do
  curl -k -o /dev/null https://<SERVER_IP>/small.bin &
done; wait)
```

---

## B7. Wireshark Analysis

### Các capture cần thực hiện

| Capture | Filter | Phân tích |
|---------|--------|-----------|
| Handshake | `tshark -Y "quic" -c 20` | Initial, Handshake, 1-RTT |
| STREAM | `tshark -Y "quic.stream"` | Stream ID, Offset, Length |
| ACK | `tshark -Y "quic.ack"` | Largest ACKed, Ranges |
| PATH | `tshark -Y "quic.frame_type == 0x1a"` | Migration validation |

```bash
# Capture handshake
tshark -i ens3 -f "udp port 4433" -c 20 -T fields \
  -e frame.number -e frame.time_relative -e quic.packet_type \
  -e quic.dcid -e quic.frame_type
```

---

# PHẦN C: PHÂN TÍCH VÀ BÁO CÁO

---

## C2. Case Studies

### C2.1: Google

| Tiêu chí | Chi tiết |
|----------|----------|
| **Traffic** | ~95% Google traffic dùng QUIC (2024) |
| **Kết quả** | -8% rebuffering YouTube, -3% search latency |
| **Đặc biệt** | Google tạo ra QUIC, push IETF standardization |

### C2.2: Cloudflare

| Tiêu chí | Chi tiết |
|----------|----------|
| **Implementation** | quiche (Rust) — open source |
| **Kết quả** | Cải thiện TTFB 12-15% cho mobile users |

### C2.3: Meta

| Tiêu chí | Chi tiết |
|----------|----------|
| **Phạm vi** | Facebook, Instagram, WhatsApp |
| **Kết quả** | -6% request errors, -3% tail latency |
| **Đặc biệt** | Connection migration rất hữu ích cho mobile |

---

## C4-C6. Báo cáo, Slides, Video (phần TV2)

### C4: Báo cáo (~20-21 trang)
- Chương 2: Packet/Frame Structure (~4 trang)
- Chương 3: Multiplexing + Flow Control + Security (~7 trang)
- Chương 4: Demo 2, 4, Wireshark (~4 trang)
- Chương 5: Case Studies (~4-5 trang)
- Chương 7: Hạn chế + Hướng phát triển (~1 trang)

### C5: Slides (~21 slides)
- Architecture (Packets): 4 slides
- Key Features (Multiplexing/Security/FlowControl): 7 slides
- Demo 2, 4, Wireshark: 4 slides
- Case Studies: 4 slides
- Conclusion: 2 slides

### C6: Video Demo
- Demo 2: Stream Multiplexing (~3 phút)
- Demo 4: Packet Loss (~3 phút)
- Edit video tổng hợp (~10-15 phút)

---

## ✅ CHECKLIST TỔNG HỢP - TV2

### Phần A: Lý thuyết
- [ ] A1.5-A1.8: RFC, Implementations, Browser, Adoption chart
- [ ] A3.1-A3.10: Packet/Frame Structure (10 items)
- [ ] A5.1-A5.10: Stream Multiplexing + HOL blocking
- [ ] A7.1-A7.8: Flow Control
- [ ] A9.1-A9.8: Security TLS 1.3
- [ ] A11 (phần TV2): HOL, Security, Deployment, Radar chart

### Phần B: Thực hành
- [ ] B1.11-B1.20: Setup Client VM 2
- [ ] B3: Demo Stream Multiplexing
- [ ] B5: Demo Packet Loss Recovery
- [ ] B6 (phần TV2): Multi-client
- [ ] B7: Wireshark Analysis

### Phần C: Báo cáo
- [ ] C2: Case Studies
- [ ] C4: Báo cáo (~20-21 trang)
- [ ] C5: Slides (~21 slides)
- [ ] C6: Video Demo + Edit

### 📊 12 Biểu đồ TV2
- [ ] A1.8: Adoption chart
- [ ] A3.10: Packet/Frame diagrams
- [ ] A5.9: HOL blocking comparison
- [ ] A5.10: Stream state machine
- [ ] A7.8: Flow control diagram
- [ ] A11.10: Feature radar chart
- [ ] B3.7: Stream interleaving timeline
- [ ] B3.8: Completion time comparison
- [ ] B5.7: Packet loss line chart
- [ ] B5.8: Recovery comparison chart
- [ ] C2.7: Adoption statistics charts
- [ ] C2.8: Case study performance charts

---

*Tài liệu TV2 — Bùi Lê Huy Phước — NT531.Q21*
*Đề tài: QUIC Protocol — Nghiên cứu và Demo*
