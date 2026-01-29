# PHÂN CÔNG CÔNG VIỆC VÀ THỜI GIAN THỰC HIỆN

## Đề tài: Tìm hiểu về thiết kế và đánh giá hiệu năng của QUIC

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò |
|-----|-----------|------|---------|
| 1 | Thành viên 1 | [MSSV] | Trưởng nhóm - Phụ trách kiến trúc QUIC |
| 2 | Thành viên 2 | [MSSV] | Thành viên - Phụ trách thử nghiệm hiệu năng |

---

## 🎯 Mục tiêu đề tài

1. **Nghiên cứu kiến trúc QUIC** - Hiểu rõ thiết kế và các thành phần của giao thức
2. **Đánh giá hiệu năng QUIC** - Thử nghiệm trong các điều kiện mạng khác nhau
3. **So sánh với HTTP/2** - Phân tích ưu nhược điểm của QUIC so với HTTP/2
4. **Đưa ra khuyến nghị** - Kết luận về việc áp dụng QUIC trong thực tế

---

## 📅 Kế hoạch thời gian tổng quan

| Giai đoạn | Nội dung | Thời gian | Số tuần |
|-----------|----------|-----------|---------|
| 1 | Nghiên cứu lý thuyết về QUIC | Tuần 1-2 | 2 tuần |
| 2 | Triển khai và thử nghiệm | Tuần 3-5 | 3 tuần |
| 3 | Phân tích kết quả và so sánh | Tuần 6-7 | 2 tuần |
| 4 | Viết báo cáo và hoàn thiện | Tuần 8 | 1 tuần |

---

## 📝 Bảng phân công công việc chi tiết

### GIAI ĐOẠN 1: NGHIÊN CỨU LÝ THUYẾT VỀ QUIC (Tuần 1-2)

#### Tuần 1: Tổng quan về QUIC

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Tìm hiểu lịch sử phát triển QUIC | Từ gQUIC (Google) đến IETF QUIC (RFC 9000) | Thành viên 1 | Cuối tuần 1 | Tài liệu tổng hợp |
| Nghiên cứu kiến trúc tổng quan QUIC | Các thành phần chính: Connection, Stream, Packet | Thành viên 1 | Cuối tuần 1 | Sơ đồ kiến trúc |
| Nghiên cứu QUIC so với TCP/UDP | Tại sao QUIC chạy trên UDP, ưu điểm so với TCP | Thành viên 2 | Cuối tuần 1 | Bảng so sánh |
| Tổng hợp tài liệu tham khảo | Thu thập RFC 9000-9002, papers, documentation | Cả 2 | Cuối tuần 1 | Danh sách tài liệu |

#### Tuần 2: Chi tiết thiết kế QUIC

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Nghiên cứu Connection Establishment | 1-RTT handshake, 0-RTT resumption | Thành viên 1 | Cuối tuần 2 | Sơ đồ handshake |
| Nghiên cứu Stream Multiplexing | Cách QUIC xử lý nhiều streams độc lập | Thành viên 1 | Cuối tuần 2 | Tài liệu kỹ thuật |
| Nghiên cứu cơ chế bảo mật | TLS 1.3 integration, encryption | Thành viên 2 | Cuối tuần 2 | Tài liệu bảo mật |
| Nghiên cứu Loss Detection & Congestion Control | Cách QUIC xử lý mất gói và điều khiển tắc nghẽn | Thành viên 2 | Cuối tuần 2 | Tài liệu kỹ thuật |
| Nghiên cứu Connection Migration | Khả năng duy trì kết nối khi đổi IP | Thành viên 1 | Cuối tuần 2 | Tài liệu |

---

### GIAI ĐOẠN 2: TRIỂN KHAI VÀ THỬ NGHIỆM (Tuần 3-5)

#### Tuần 3: Thiết lập môi trường

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Cài đặt QUIC server | Sử dụng quiche (Cloudflare) hoặc aioquic | Thành viên 1 | Cuối tuần 3 | Server QUIC hoạt động |
| Cài đặt HTTP/2 server | Sử dụng nginx với HTTP/2 để so sánh | Thành viên 2 | Cuối tuần 3 | Server HTTP/2 hoạt động |
| Thiết lập network emulation | Sử dụng tc/netem để giả lập điều kiện mạng | Thành viên 2 | Cuối tuần 3 | Script cấu hình mạng |
| Chuẩn bị công cụ benchmark | Cài đặt curl, h2load, Wireshark | Cả 2 | Cuối tuần 3 | Công cụ sẵn sàng |

#### Tuần 4: Thử nghiệm hiệu năng cơ bản

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Đo thời gian Handshake | So sánh QUIC (1-RTT) vs HTTP/2 (TCP+TLS) | Thành viên 1 | Cuối tuần 4 | Dữ liệu đo lường |
| Đo Throughput | Tốc độ truyền với file 1KB, 100KB, 1MB, 10MB | Thành viên 2 | Cuối tuần 4 | Dữ liệu đo lường |
| Đo Latency (TTFB) | Time To First Byte trong điều kiện mạng khác nhau | Thành viên 1 | Cuối tuần 4 | Dữ liệu đo lường |
| Thử nghiệm 0-RTT | Đánh giá hiệu quả 0-RTT resumption của QUIC | Thành viên 2 | Cuối tuần 4 | Dữ liệu đo lường |

#### Tuần 5: Thử nghiệm nâng cao

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Thử nghiệm Packet Loss | Hiệu năng khi mất gói 1%, 5%, 10% | Thành viên 1 | Cuối tuần 5 | Dữ liệu đo lường |
| Thử nghiệm Multiplexing | Nhiều streams đồng thời (5, 10, 20 streams) | Thành viên 2 | Cuối tuần 5 | Dữ liệu đo lường |
| Thử nghiệm High Latency | Hiệu năng với RTT cao (50ms, 100ms, 200ms) | Thành viên 1 | Cuối tuần 5 | Dữ liệu đo lường |
| Tổng hợp dữ liệu thử nghiệm | Gom tất cả kết quả vào spreadsheet | Cả 2 | Cuối tuần 5 | File dữ liệu tổng hợp |

---

### GIAI ĐOẠN 3: PHÂN TÍCH KẾT QUẢ VÀ SO SÁNH (Tuần 6-7)

#### Tuần 6: Phân tích dữ liệu

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Xử lý và làm sạch dữ liệu | Loại bỏ outliers, tính toán thống kê | Thành viên 2 | Cuối tuần 6 | Dữ liệu đã xử lý |
| Tạo biểu đồ so sánh | Bar chart, line chart cho các metrics | Thành viên 2 | Cuối tuần 6 | Các biểu đồ |
| Phân tích kết quả Handshake & Latency | Phân tích sâu về connection establishment | Thành viên 1 | Cuối tuần 6 | Báo cáo phân tích |
| Phân tích kết quả Throughput & Loss Recovery | Phân tích hiệu năng truyền tải | Thành viên 2 | Cuối tuần 6 | Báo cáo phân tích |

#### Tuần 7: So sánh và đánh giá

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Lập bảng so sánh QUIC vs HTTP/2 | So sánh chi tiết với dữ liệu thực tế | Cả 2 | Cuối tuần 7 | Bảng so sánh đầy đủ |
| Đánh giá ưu điểm của QUIC | Các tình huống QUIC vượt trội | Thành viên 1 | Cuối tuần 7 | Báo cáo đánh giá |
| Đánh giá hạn chế của QUIC | Các tình huống QUIC chưa tốt | Thành viên 2 | Cuối tuần 7 | Báo cáo đánh giá |
| Đưa ra khuyến nghị sử dụng | Khi nào nên dùng QUIC | Cả 2 | Cuối tuần 7 | Khuyến nghị |

---

### GIAI ĐOẠN 4: VIẾT BÁO CÁO VÀ HOÀN THIỆN (Tuần 8)

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Viết Chương 1-2: Giới thiệu & Lý thuyết QUIC | Đặt vấn đề, kiến trúc QUIC | Thành viên 1 | Giữa tuần 8 | Chương 1-2 |
| Viết Chương 3: Phương pháp thử nghiệm | Mô tả môi trường, quy trình | Thành viên 2 | Giữa tuần 8 | Chương 3 |
| Viết Chương 4: Kết quả và phân tích | Trình bày kết quả, biểu đồ | Thành viên 2 | Cuối tuần 8 | Chương 4 |
| Viết Chương 5: Kết luận | Tổng kết, khuyến nghị | Thành viên 1 | Cuối tuần 8 | Chương 5 |
| Review và chỉnh sửa | Đọc lại, sửa lỗi | Cả 2 | Cuối tuần 8 | Báo cáo hoàn chỉnh |
| Chuẩn bị slide thuyết trình | Thiết kế slide | Thành viên 1 | Cuối tuần 8 | Slide |

---

## 📊 Bảng tổng hợp phân công theo thành viên

### Thành viên 1 - Trưởng nhóm (Phụ trách kiến trúc QUIC)

| STT | Công việc chính | Tuần |
|-----|----------------|------|
| 1 | Nghiên cứu lịch sử và kiến trúc tổng quan QUIC | 1 |
| 2 | Nghiên cứu Connection Establishment, Stream Multiplexing | 2 |
| 3 | Nghiên cứu Connection Migration | 2 |
| 4 | Cài đặt QUIC server | 3 |
| 5 | Đo Handshake time, Latency | 4 |
| 6 | Thử nghiệm Packet Loss, High Latency | 5 |
| 7 | Phân tích Handshake & Latency | 6 |
| 8 | Đánh giá ưu điểm QUIC | 7 |
| 9 | Viết Chương 1-2, 5 + Slide | 8 |

### Thành viên 2 (Phụ trách thử nghiệm hiệu năng)

| STT | Công việc chính | Tuần |
|-----|----------------|------|
| 1 | Nghiên cứu QUIC so với TCP/UDP | 1 |
| 2 | Nghiên cứu bảo mật, Loss Detection, Congestion Control | 2 |
| 3 | Cài đặt HTTP/2 server, Network emulation | 3 |
| 4 | Đo Throughput, Thử nghiệm 0-RTT | 4 |
| 5 | Thử nghiệm Multiplexing | 5 |
| 6 | Xử lý dữ liệu, Tạo biểu đồ, Phân tích Throughput | 6 |
| 7 | Đánh giá hạn chế QUIC | 7 |
| 8 | Viết Chương 3-4 | 8 |

---

## 📈 Biểu đồ Gantt

```
Tuần        1    2    3    4    5    6    7    8
GĐ1        ████ ████
GĐ2                  ████ ████ ████
GĐ3                                 ████ ████
GĐ4                                           ████
```

---

## ✅ Checklist tiến độ

### Giai đoạn 1: Nghiên cứu lý thuyết
- [ ] Hoàn thành tài liệu về lịch sử QUIC
- [ ] Hoàn thành sơ đồ kiến trúc QUIC
- [ ] Hoàn thành nghiên cứu các cơ chế: Handshake, Multiplexing, Security, Loss Detection
- [ ] Hoàn thành danh sách tài liệu tham khảo

### Giai đoạn 2: Triển khai và thử nghiệm
- [ ] QUIC server hoạt động
- [ ] HTTP/2 server hoạt động
- [ ] Hoàn thành thử nghiệm Handshake time
- [ ] Hoàn thành thử nghiệm Throughput
- [ ] Hoàn thành thử nghiệm Latency
- [ ] Hoàn thành thử nghiệm Packet Loss
- [ ] Hoàn thành thử nghiệm Multiplexing
- [ ] Tổng hợp dữ liệu

### Giai đoạn 3: Phân tích và so sánh
- [ ] Dữ liệu đã được xử lý
- [ ] Biểu đồ so sánh hoàn thành
- [ ] Bảng so sánh QUIC vs HTTP/2 hoàn thành
- [ ] Khuyến nghị sử dụng hoàn thành

### Giai đoạn 4: Báo cáo
- [ ] Chương 1-2 hoàn thành
- [ ] Chương 3 hoàn thành
- [ ] Chương 4 hoàn thành
- [ ] Chương 5 hoàn thành
- [ ] Slide thuyết trình hoàn thành
- [ ] Nộp báo cáo

---

## 🔧 Công cụ sử dụng

- **QUIC Server:** quiche (Cloudflare), aioquic (Python)
- **HTTP/2 Server:** nginx
- **Network Emulation:** tc/netem
- **Monitoring:** Wireshark
- **Benchmarking:** curl, h2load

## 📚 Tài liệu tham khảo chính

- RFC 9000: QUIC - A UDP-Based Multiplexed and Secure Transport
- RFC 9001: Using TLS to Secure QUIC
- RFC 9002: QUIC Loss Detection and Congestion Control

---

*Cập nhật lần cuối: 29/01/2026*
