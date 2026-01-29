# PHÂN CÔNG CÔNG VIỆC VÀ THỜI GIAN THỰC HIỆN

## Đề tài: Tìm hiểu về thiết kế và đánh giá hiệu năng của QUIC rồi so sánh với HTTP/2

### Môn học: NT531.Q21 - Mạng máy tính nâng cao

---

## 📋 Thông tin nhóm

| STT | Họ và tên | MSSV | Vai trò |
|-----|-----------|------|---------|
| 1 | Thành viên 1 | [MSSV] | Trưởng nhóm |
| 2 | Thành viên 2 | [MSSV] | Thành viên |

---

## 🎯 Mục tiêu đề tài

1. **Nghiên cứu và tìm hiểu** kiến trúc, thiết kế của giao thức QUIC
2. **Phân tích và đánh giá** hiệu năng của QUIC trong các điều kiện mạng khác nhau
3. **So sánh chi tiết** giữa QUIC và HTTP/2 về các tiêu chí hiệu năng
4. **Triển khai thử nghiệm** để thu thập dữ liệu thực tế
5. **Đưa ra kết luận** và khuyến nghị sử dụng

---

## 📅 Kế hoạch thời gian tổng quan

| Giai đoạn | Nội dung | Thời gian | Số tuần |
|-----------|----------|-----------|---------|
| 1 | Nghiên cứu lý thuyết | Tuần 1-3 | 3 tuần |
| 2 | Triển khai và thử nghiệm | Tuần 4-6 | 3 tuần |
| 3 | Phân tích và so sánh | Tuần 7-8 | 2 tuần |
| 4 | Viết báo cáo và hoàn thiện | Tuần 9-10 | 2 tuần |

---

## 📝 Chi tiết phân công công việc

### GIAI ĐOẠN 1: NGHIÊN CỨU LÝ THUYẾT (Tuần 1-3)

#### Tuần 1: Tổng quan về giao thức truyền tải

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Nghiên cứu lịch sử phát triển giao thức Internet | Tìm hiểu sự phát triển từ HTTP/1.0 → HTTP/1.1 → HTTP/2 → QUIC | Thành viên 1 | Cuối tuần 1 | Tài liệu tổng hợp |
| Nghiên cứu tổng quan về TCP và UDP | Phân tích ưu nhược điểm của TCP/UDP làm cơ sở cho QUIC | Thành viên 2 | Cuối tuần 1 | Tài liệu so sánh |
| Tìm kiếm và tổng hợp tài liệu tham khảo | Thu thập paper, RFC, tài liệu chính thức | Cả 2 | Cuối tuần 1 | Danh sách tài liệu |

#### Tuần 2: Kiến trúc và thiết kế QUIC

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Nghiên cứu kiến trúc QUIC | Phân tích Connection establishment, Stream multiplexing, Flow control | Thành viên 1 | Cuối tuần 2 | Sơ đồ kiến trúc + mô tả |
| Nghiên cứu cơ chế bảo mật của QUIC | Tìm hiểu về TLS 1.3 integration, 0-RTT handshake, encryption | Thành viên 2 | Cuối tuần 2 | Tài liệu bảo mật |
| Nghiên cứu cơ chế xử lý lỗi và khôi phục | Loss detection, Congestion control, Connection migration | Thành viên 1 | Cuối tuần 2 | Tài liệu kỹ thuật |
| Nghiên cứu QUIC packet format | Phân tích cấu trúc packet, header, payload | Thành viên 2 | Cuối tuần 2 | Biểu đồ cấu trúc |

#### Tuần 3: Kiến trúc và thiết kế HTTP/2

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Nghiên cứu kiến trúc HTTP/2 | Binary framing, Header compression (HPACK), Server push | Thành viên 2 | Cuối tuần 3 | Sơ đồ kiến trúc + mô tả |
| Nghiên cứu Stream multiplexing trong HTTP/2 | Phân tích cách xử lý multiple streams | Thành viên 1 | Cuối tuần 3 | Tài liệu kỹ thuật |
| So sánh sơ bộ QUIC vs HTTP/2 | Lập bảng so sánh các tính năng cơ bản | Cả 2 | Cuối tuần 3 | Bảng so sánh |
| Viết báo cáo giai đoạn 1 | Tổng hợp kết quả nghiên cứu lý thuyết | Cả 2 | Cuối tuần 3 | Báo cáo GĐ1 |

---

### GIAI ĐOẠN 2: TRIỂN KHAI VÀ THỬ NGHIỆM (Tuần 4-6)

#### Tuần 4: Thiết lập môi trường thử nghiệm

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Thiết lập server QUIC | Cài đặt và cấu hình QUIC server (quiche, aioquic, hoặc chromium) | Thành viên 1 | Cuối tuần 4 | Server hoạt động |
| Thiết lập server HTTP/2 | Cài đặt và cấu hình HTTP/2 server (nginx, h2o) | Thành viên 2 | Cuối tuần 4 | Server hoạt động |
| Thiết lập môi trường mạng giả lập | Sử dụng tc/netem để giả lập các điều kiện mạng | Thành viên 1 | Cuối tuần 4 | Script cấu hình |
| Chuẩn bị công cụ đo lường | Cài đặt và cấu hình Wireshark, curl, benchmark tools | Thành viên 2 | Cuối tuần 4 | Công cụ sẵn sàng |

#### Tuần 5: Thực hiện thử nghiệm hiệu năng

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Đo lường thời gian handshake | So sánh connection establishment time QUIC vs HTTP/2 | Thành viên 1 | Cuối tuần 5 | Dữ liệu đo lường |
| Đo lường throughput | Đo tốc độ truyền tải với các kích thước file khác nhau | Thành viên 2 | Cuối tuần 5 | Dữ liệu đo lường |
| Đo lường latency | Đo độ trễ trong các điều kiện mạng khác nhau | Thành viên 1 | Cuối tuần 5 | Dữ liệu đo lường |
| Thử nghiệm trong điều kiện mất gói | Đánh giá hiệu năng khi có packet loss (1%, 5%, 10%) | Thành viên 2 | Cuối tuần 5 | Dữ liệu đo lường |

#### Tuần 6: Thử nghiệm nâng cao

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Thử nghiệm multiplexing | Đánh giá hiệu quả khi có nhiều streams đồng thời | Thành viên 1 | Cuối tuần 6 | Dữ liệu đo lường |
| Thử nghiệm trong điều kiện mạng không ổn định | Đánh giá hiệu năng với jitter, varying bandwidth | Thành viên 2 | Cuối tuần 6 | Dữ liệu đo lường |
| Thử nghiệm 0-RTT resumption | Đánh giá hiệu quả của 0-RTT trong QUIC | Thành viên 1 | Cuối tuần 6 | Dữ liệu đo lường |
| Ghi chép và tổng hợp dữ liệu | Thu thập tất cả kết quả thử nghiệm vào spreadsheet | Cả 2 | Cuối tuần 6 | File dữ liệu |

---

### GIAI ĐOẠN 3: PHÂN TÍCH VÀ SO SÁNH (Tuần 7-8)

#### Tuần 7: Phân tích dữ liệu

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Xử lý và làm sạch dữ liệu | Chuẩn hóa, loại bỏ outliers, tính toán thống kê | Thành viên 1 | Cuối tuần 7 | Dữ liệu đã xử lý |
| Tạo biểu đồ so sánh | Vẽ biểu đồ bar, line chart cho các metrics | Thành viên 2 | Cuối tuần 7 | Biểu đồ |
| Phân tích kết quả handshake time | Phân tích sâu về connection establishment | Thành viên 1 | Cuối tuần 7 | Phân tích chi tiết |
| Phân tích kết quả throughput/latency | Phân tích sâu về hiệu năng truyền tải | Thành viên 2 | Cuối tuần 7 | Phân tích chi tiết |

#### Tuần 8: So sánh và đánh giá

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| So sánh tổng thể QUIC vs HTTP/2 | Lập bảng so sánh chi tiết với dữ liệu thực tế | Cả 2 | Cuối tuần 8 | Bảng so sánh |
| Đánh giá ưu điểm của QUIC | Phân tích các tình huống QUIC vượt trội | Thành viên 1 | Cuối tuần 8 | Báo cáo đánh giá |
| Đánh giá hạn chế của QUIC | Phân tích các tình huống HTTP/2 tốt hơn | Thành viên 2 | Cuối tuần 8 | Báo cáo đánh giá |
| Đưa ra khuyến nghị sử dụng | Khi nào nên dùng QUIC, khi nào nên dùng HTTP/2 | Cả 2 | Cuối tuần 8 | Khuyến nghị |

---

### GIAI ĐOẠN 4: VIẾT BÁO CÁO VÀ HOÀN THIỆN (Tuần 9-10)

#### Tuần 9: Viết báo cáo

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Viết chương 1: Giới thiệu | Đặt vấn đề, mục tiêu, phạm vi nghiên cứu | Thành viên 1 | Giữa tuần 9 | Chương 1 |
| Viết chương 2: Cơ sở lý thuyết | Tổng quan về QUIC và HTTP/2 | Thành viên 2 | Giữa tuần 9 | Chương 2 |
| Viết chương 3: Phương pháp thử nghiệm | Mô tả môi trường và quy trình thử nghiệm | Thành viên 1 | Cuối tuần 9 | Chương 3 |
| Viết chương 4: Kết quả và phân tích | Trình bày kết quả, biểu đồ, phân tích | Thành viên 2 | Cuối tuần 9 | Chương 4 |

#### Tuần 10: Hoàn thiện và nộp bài

| Công việc | Mô tả chi tiết | Người thực hiện | Deadline | Output |
|-----------|----------------|-----------------|----------|--------|
| Viết chương 5: Kết luận | Tổng kết, hạn chế, hướng phát triển | Cả 2 | Giữa tuần 10 | Chương 5 |
| Review và chỉnh sửa | Đọc lại, sửa lỗi, format | Cả 2 | Giữa tuần 10 | Báo cáo hoàn chỉnh |
| Chuẩn bị slide thuyết trình | Thiết kế slide trình bày | Thành viên 1 | Cuối tuần 10 | Slide |
| Demo và thuyết trình thử | Tập thuyết trình, chuẩn bị demo | Cả 2 | Cuối tuần 10 | Demo ready |
| Nộp báo cáo cuối cùng | Submit báo cáo và tài liệu | Cả 2 | Cuối tuần 10 | Hoàn thành |

---

## 📊 Bảng tổng hợp phân công theo thành viên

### Thành viên 1 - Trưởng nhóm

| STT | Nội dung công việc | Giai đoạn | Tuần |
|-----|-------------------|-----------|------|
| 1 | Nghiên cứu lịch sử phát triển giao thức Internet | GĐ1 | 1 |
| 2 | Nghiên cứu kiến trúc QUIC | GĐ1 | 2 |
| 3 | Nghiên cứu cơ chế xử lý lỗi và khôi phục | GĐ1 | 2 |
| 4 | Nghiên cứu Stream multiplexing trong HTTP/2 | GĐ1 | 3 |
| 5 | Thiết lập server QUIC | GĐ2 | 4 |
| 6 | Thiết lập môi trường mạng giả lập | GĐ2 | 4 |
| 7 | Đo lường thời gian handshake | GĐ2 | 5 |
| 8 | Đo lường latency | GĐ2 | 5 |
| 9 | Thử nghiệm multiplexing | GĐ2 | 6 |
| 10 | Thử nghiệm 0-RTT resumption | GĐ2 | 6 |
| 11 | Xử lý và làm sạch dữ liệu | GĐ3 | 7 |
| 12 | Phân tích kết quả handshake time | GĐ3 | 7 |
| 13 | Đánh giá ưu điểm của QUIC | GĐ3 | 8 |
| 14 | Viết chương 1: Giới thiệu | GĐ4 | 9 |
| 15 | Viết chương 3: Phương pháp thử nghiệm | GĐ4 | 9 |
| 16 | Chuẩn bị slide thuyết trình | GĐ4 | 10 |

### Thành viên 2

| STT | Nội dung công việc | Giai đoạn | Tuần |
|-----|-------------------|-----------|------|
| 1 | Nghiên cứu tổng quan về TCP và UDP | GĐ1 | 1 |
| 2 | Nghiên cứu cơ chế bảo mật của QUIC | GĐ1 | 2 |
| 3 | Nghiên cứu QUIC packet format | GĐ1 | 2 |
| 4 | Nghiên cứu kiến trúc HTTP/2 | GĐ1 | 3 |
| 5 | Thiết lập server HTTP/2 | GĐ2 | 4 |
| 6 | Chuẩn bị công cụ đo lường | GĐ2 | 4 |
| 7 | Đo lường throughput | GĐ2 | 5 |
| 8 | Thử nghiệm trong điều kiện mất gói | GĐ2 | 5 |
| 9 | Thử nghiệm trong điều kiện mạng không ổn định | GĐ2 | 6 |
| 10 | Tạo biểu đồ so sánh | GĐ3 | 7 |
| 11 | Phân tích kết quả throughput/latency | GĐ3 | 7 |
| 12 | Đánh giá hạn chế của QUIC | GĐ3 | 8 |
| 13 | Viết chương 2: Cơ sở lý thuyết | GĐ4 | 9 |
| 14 | Viết chương 4: Kết quả và phân tích | GĐ4 | 9 |

### Công việc chung (Cả 2 thành viên)

| STT | Nội dung công việc | Giai đoạn | Tuần |
|-----|-------------------|-----------|------|
| 1 | Tìm kiếm và tổng hợp tài liệu tham khảo | GĐ1 | 1 |
| 2 | So sánh sơ bộ QUIC vs HTTP/2 | GĐ1 | 3 |
| 3 | Viết báo cáo giai đoạn 1 | GĐ1 | 3 |
| 4 | Ghi chép và tổng hợp dữ liệu | GĐ2 | 6 |
| 5 | So sánh tổng thể QUIC vs HTTP/2 | GĐ3 | 8 |
| 6 | Đưa ra khuyến nghị sử dụng | GĐ3 | 8 |
| 7 | Viết chương 5: Kết luận | GĐ4 | 10 |
| 8 | Review và chỉnh sửa | GĐ4 | 10 |
| 9 | Demo và thuyết trình thử | GĐ4 | 10 |
| 10 | Nộp báo cáo cuối cùng | GĐ4 | 10 |

---

## 📈 Biểu đồ Gantt (Timeline)

```
Tuần     1    2    3    4    5    6    7    8    9    10
GĐ1     ████ ████ ████
GĐ2                    ████ ████ ████
GĐ3                                   ████ ████
GĐ4                                             ████ ████
```

**Chú thích:**
- GĐ1: Nghiên cứu lý thuyết
- GĐ2: Triển khai và thử nghiệm
- GĐ3: Phân tích và so sánh
- GĐ4: Viết báo cáo và hoàn thiện

---

## 📚 Danh sách deliverables

| Tuần | Deliverable | Người phụ trách |
|------|-------------|-----------------|
| 1 | Tài liệu tổng hợp về lịch sử giao thức | Thành viên 1 |
| 1 | Tài liệu so sánh TCP/UDP | Thành viên 2 |
| 1 | Danh sách tài liệu tham khảo | Cả 2 |
| 2 | Sơ đồ kiến trúc QUIC | Thành viên 1 |
| 2 | Tài liệu bảo mật QUIC | Thành viên 2 |
| 3 | Sơ đồ kiến trúc HTTP/2 | Thành viên 2 |
| 3 | Bảng so sánh sơ bộ | Cả 2 |
| 3 | Báo cáo giai đoạn 1 | Cả 2 |
| 4 | Server QUIC hoạt động | Thành viên 1 |
| 4 | Server HTTP/2 hoạt động | Thành viên 2 |
| 6 | File dữ liệu thử nghiệm | Cả 2 |
| 7 | Biểu đồ so sánh | Thành viên 2 |
| 8 | Bảng so sánh chi tiết | Cả 2 |
| 9 | Draft báo cáo | Cả 2 |
| 10 | Báo cáo hoàn chỉnh | Cả 2 |
| 10 | Slide thuyết trình | Thành viên 1 |

---

## 🔧 Công cụ và tài nguyên cần thiết

### Phần mềm
- **QUIC Implementation:** quiche (Cloudflare), aioquic (Python), quinn (Rust)
- **HTTP/2 Server:** nginx, Apache với mod_http2, h2o
- **Network Emulation:** tc/netem, mininet
- **Monitoring:** Wireshark, tcpdump
- **Benchmarking:** curl, wrk, h2load, quiche-client

### Tài liệu tham khảo
- RFC 9000: QUIC: A UDP-Based Multiplexed and Secure Transport
- RFC 9001: Using TLS to Secure QUIC
- RFC 7540: Hypertext Transfer Protocol Version 2 (HTTP/2)
- RFC 7541: HPACK: Header Compression for HTTP/2
- Google QUIC documentation
- Chromium QUIC implementation

---

## 📋 Quy định làm việc nhóm

1. **Họp định kỳ:** 2 lần/tuần (thứ 3 và thứ 7)
2. **Báo cáo tiến độ:** Cuối mỗi tuần
3. **Công cụ quản lý:** GitHub Issues, Google Drive
4. **Liên lạc:** Zalo/Messenger group
5. **Code review:** Peer review trước khi merge

---

## ✅ Checklist kiểm tra tiến độ

### Giai đoạn 1
- [ ] Hoàn thành nghiên cứu lịch sử giao thức
- [ ] Hoàn thành nghiên cứu kiến trúc QUIC
- [ ] Hoàn thành nghiên cứu kiến trúc HTTP/2
- [ ] Hoàn thành bảng so sánh sơ bộ
- [ ] Nộp báo cáo giai đoạn 1

### Giai đoạn 2
- [ ] Thiết lập thành công server QUIC
- [ ] Thiết lập thành công server HTTP/2
- [ ] Hoàn thành thử nghiệm handshake time
- [ ] Hoàn thành thử nghiệm throughput
- [ ] Hoàn thành thử nghiệm latency
- [ ] Hoàn thành thử nghiệm packet loss
- [ ] Thu thập đủ dữ liệu

### Giai đoạn 3
- [ ] Xử lý xong dữ liệu
- [ ] Tạo xong biểu đồ
- [ ] Hoàn thành phân tích
- [ ] Hoàn thành bảng so sánh chi tiết

### Giai đoạn 4
- [ ] Viết xong chương 1
- [ ] Viết xong chương 2
- [ ] Viết xong chương 3
- [ ] Viết xong chương 4
- [ ] Viết xong chương 5
- [ ] Review và chỉnh sửa xong
- [ ] Hoàn thành slide
- [ ] Nộp báo cáo cuối cùng

---

*Cập nhật lần cuối: 29/01/2026*

*Người tạo: Nhóm NT531.Q21-QUIC*
