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
| 2 | Triển khai và thử nghiệm | Tuần 3-5 | 3 tuần | 20 giờ |
| 3 | Phân tích kết quả và so sánh | Tuần 6-7 | 2 tuần | 15 giờ |
| 4 | Viết báo cáo và hoàn thiện | Tuần 8 | 1 tuần | 20 giờ |
| **TỔNG** | | **8 tuần** | | **~140 giờ/người** |

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

---

## 🗓️ TUẦN 5: THỬ NGHIỆM NÂNG CAO (20 giờ/người)

### Thành viên 1 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 5.1 | Thử nghiệm Packet Loss | - QUIC vs HTTP/2 với packet loss 1%, 5%, 10%<br>- Đo throughput và latency<br>- File 1MB, 100 lần mỗi điều kiện | 8 | Data CSV |
| 5.2 | Thử nghiệm High Latency | - RTT 50ms, 100ms, 200ms, 500ms<br>- Đo handshake, throughput<br>- So sánh QUIC vs HTTP/2 | 6 | Data CSV |
| 5.3 | Thử nghiệm Connection Migration | - Simulate IP change<br>- Kiểm tra QUIC có maintain connection<br>- Ghi nhận behavior | 4 | Notes + evidence |
| 5.4 | Review và validate data | - Kiểm tra data integrity<br>- Chạy lại test nếu cần<br>- Document anomalies | 2 | Validation report |

### Thành viên 2 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 5.1 | Thử nghiệm Multiplexing | - 5, 10, 20 concurrent streams<br>- Đo total completion time<br>- So sánh QUIC (no HOL) vs HTTP/2 | 8 | Data CSV |
| 5.2 | Thử nghiệm với Jitter | - Network jitter 20ms, 50ms<br>- Đo throughput stability<br>- QUIC vs HTTP/2 | 5 | Data CSV |
| 5.3 | Thử nghiệm Real-world simulation | - Simulate mobile network (4G profile)<br>- Mixed conditions: latency + loss + jitter<br>- Đo overall performance | 5 | Data CSV |
| 5.4 | Tổng hợp tất cả dữ liệu | - Merge tất cả data từ Tuần 4-5<br>- Organize theo categories<br>- Chuẩn bị cho phân tích | 2 | Complete dataset |

### 📋 Deliverables cuối Tuần 5:
- [ ] Data Packet Loss experiments (TV1)
- [ ] Data High Latency experiments (TV1)
- [ ] Data Multiplexing experiments (TV2)
- [ ] Complete dataset cho phân tích (TV2)

---

## 🗓️ TUẦN 6: PHÂN TÍCH DỮ LIỆU (15 giờ/người)

### Thành viên 1 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 6.1 | Phân tích Handshake Time | - Tính mean, median, std deviation<br>- So sánh QUIC 1-RTT vs TCP+TLS<br>- Phân tích improvement % | 4 | Báo cáo phân tích |
| 6.2 | Phân tích 0-RTT | - So sánh 0-RTT vs 1-RTT<br>- Tính improvement %<br>- Phân tích use cases | 3 | Báo cáo phân tích |
| 6.3 | Phân tích Latency | - So sánh TTFB theo điều kiện mạng<br>- Phân tích tác động của RTT<br>- QUIC vs HTTP/2 comparison | 4 | Báo cáo phân tích |
| 6.4 | Phân tích Packet Loss Recovery | - Phân tích hiệu năng với packet loss<br>- So sánh khả năng recovery<br>- QUIC stream independence | 4 | Báo cáo phân tích |

### Thành viên 2 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 6.1 | Xử lý và làm sạch dữ liệu | - Remove outliers (>3 std dev)<br>- Handle missing data<br>- Validate data ranges | 3 | Clean dataset |
| 6.2 | Tạo biểu đồ Handshake & Latency | - Bar chart: Handshake time comparison<br>- Line chart: Latency vs RTT<br>- Annotate key findings | 4 | 3-4 biểu đồ |
| 6.3 | Tạo biểu đồ Throughput | - Line chart: Throughput vs file size<br>- Bar chart: Throughput comparison<br>- Impact of network conditions | 4 | 3-4 biểu đồ |
| 6.4 | Phân tích Throughput & Multiplexing | - Analyze throughput patterns<br>- Multiplexing efficiency<br>- HOL blocking impact | 4 | Báo cáo phân tích |

### 📋 Deliverables cuối Tuần 6:
- [ ] Báo cáo phân tích Handshake & Latency (TV1)
- [ ] Báo cáo phân tích Packet Loss (TV1)
- [ ] Tất cả biểu đồ (TV2)
- [ ] Báo cáo phân tích Throughput (TV2)

---

## 🗓️ TUẦN 7: SO SÁNH VÀ ĐÁNH GIÁ (15 giờ/người)

### Thành viên 1 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 7.1 | Lập bảng so sánh tổng hợp | - So sánh QUIC vs HTTP/2 theo metrics<br>- Handshake, Latency, Throughput, Loss Recovery<br>- Thêm data thực tế từ experiments | 5 | Bảng so sánh chi tiết |
| 7.2 | Đánh giá ưu điểm của QUIC | - Liệt kê các ưu điểm với evidence<br>- Faster handshake, No HOL blocking, etc.<br>- Quantify improvements | 4 | Báo cáo ưu điểm |
| 7.3 | Phân tích scenarios phù hợp | - Mobile applications<br>- High latency networks<br>- Lossy networks<br>- Streaming applications | 4 | Recommendations |
| 7.4 | Review findings với TV2 | - Thảo luận kết quả<br>- Validate conclusions<br>- Resolve disagreements | 2 | Agreed conclusions |

### Thành viên 2 (15 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 7.1 | Đánh giá hạn chế của QUIC | - UDP blocking by firewalls<br>- CPU overhead<br>- Deployment complexity<br>- Middleware issues | 5 | Báo cáo hạn chế |
| 7.2 | So sánh với real-world data | - Tìm benchmarks từ Google, Cloudflare<br>- So sánh với kết quả của mình<br>- Validate findings | 4 | Comparison report |
| 7.3 | Tổng hợp khuyến nghị | - Khi nào nên dùng QUIC<br>- Khi nào nên giữ HTTP/2<br>- Migration considerations | 4 | Recommendations |
| 7.4 | Chuẩn bị outline báo cáo | - Outline 5 chương<br>- Phân chia nội dung<br>- Timeline viết báo cáo | 2 | Report outline |

### 📋 Deliverables cuối Tuần 7:
- [ ] Bảng so sánh QUIC vs HTTP/2 (TV1)
- [ ] Báo cáo ưu điểm QUIC (TV1)
- [ ] Báo cáo hạn chế QUIC (TV2)
- [ ] Khuyến nghị sử dụng (Cả 2)
- [ ] Outline báo cáo (TV2)

---

## 🗓️ TUẦN 8: VIẾT BÁO CÁO VÀ HOÀN THIỆN (20 giờ/người)

### Thành viên 1 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 8.1 | Viết Chương 1: Giới thiệu | - Đặt vấn đề (500 từ)<br>- Mục tiêu nghiên cứu<br>- Phạm vi và giới hạn | 3 | Chương 1 (2-3 trang) |
| 8.2 | Viết Chương 2: Kiến trúc QUIC | - Lịch sử phát triển<br>- Kiến trúc tổng quan<br>- Các cơ chế chính (từ Tuần 1-2) | 6 | Chương 2 (8-10 trang) |
| 8.3 | Viết Chương 5: Kết luận | - Tóm tắt kết quả<br>- Đóng góp của nghiên cứu<br>- Hướng phát triển | 3 | Chương 5 (2-3 trang) |
| 8.4 | Thiết kế Slide thuyết trình | - 15-20 slides<br>- Key findings<br>- Demo screenshots | 5 | Slide deck |
| 8.5 | Review và chỉnh sửa | - Review Chương 3-4 của TV2<br>- Sửa lỗi, format<br>- Kiểm tra references | 3 | Final review |

### Thành viên 2 (20 giờ)

| STT | Công việc | Chi tiết yêu cầu | Giờ | Output |
|-----|-----------|------------------|-----|--------|
| 8.1 | Viết Chương 3: Phương pháp | - Mô tả môi trường thử nghiệm<br>- Các test cases<br>- Tools và setup | 5 | Chương 3 (5-6 trang) |
| 8.2 | Viết Chương 4: Kết quả | - Trình bày tất cả kết quả<br>- Biểu đồ và bảng số liệu<br>- Phân tích và thảo luận | 8 | Chương 4 (10-12 trang) |
| 8.3 | Format báo cáo | - Thống nhất format<br>- Mục lục, danh mục hình<br>- Tài liệu tham khảo | 3 | Formatted document |
| 8.4 | Review và chỉnh sửa | - Review Chương 1, 2, 5 của TV1<br>- Cross-check data<br>- Final proofreading | 4 | Final review |

### 📋 Deliverables cuối Tuần 8:
- [ ] Báo cáo hoàn chỉnh (30-35 trang)
- [ ] Slide thuyết trình (15-20 slides)
- [ ] Source code và scripts
- [ ] Raw data và processed data

---

## 📊 BẢNG TỔNG HỢP PHÂN CÔNG THEO THÀNH VIÊN

### Thành viên 1 - Trưởng nhóm (Kiến trúc QUIC, Connection, Handshake)

| Tuần | Công việc chính | Giờ |
|------|----------------|-----|
| 1 | Lịch sử QUIC + Kiến trúc tổng quan + RFC 9000 (1-5) | 15 |
| 2 | Connection Establishment + 0-RTT + Stream Multiplexing + Migration | 15 |
| 3 | Cài đặt QUIC server + Scripts đo Handshake/Latency | 20 |
| 4 | Đo Handshake QUIC/HTTP/2 + Latency + 0-RTT test | 20 |
| 5 | Packet Loss + High Latency + Connection Migration | 20 |
| 6 | Phân tích Handshake + 0-RTT + Latency + Packet Loss | 15 |
| 7 | Bảng so sánh + Ưu điểm QUIC + Scenarios | 15 |
| 8 | Chương 1, 2, 5 + Slide + Review | 20 |
| **TỔNG** | | **140 giờ** |

### Thành viên 2 (Thử nghiệm hiệu năng, Phân tích dữ liệu)

| Tuần | Công việc chính | Giờ |
|------|----------------|-----|
| 1 | TCP analysis + So sánh QUIC/TCP/UDP + RFC 9000 (6-10) + HTTP/3 | 15 |
| 2 | TLS 1.3 + Packet Protection + Loss Detection + Congestion Control | 15 |
| 3 | Cài đặt HTTP/2 + Network Emulation + Benchmark tools | 20 |
| 4 | Đo Throughput (all sizes) + Tổng hợp data | 20 |
| 5 | Multiplexing + Jitter + Real-world simulation + Dataset | 20 |
| 6 | Xử lý data + Biểu đồ + Phân tích Throughput | 15 |
| 7 | Hạn chế QUIC + Real-world comparison + Khuyến nghị + Outline | 15 |
| 8 | Chương 3, 4 + Format + Review | 20 |
| **TỔNG** | | **140 giờ** |

---

## 📈 Biểu đồ Gantt chi tiết

```
Tuần        1         2         3         4         5         6         7         8
           |---------|---------|---------|---------|---------|---------|---------|---------|
TV1        [Lý thuyết][Thiết kế][Setup   ][Test    ][Test    ][Phân    ][So sánh ][Báo cáo ]
           [QUIC    ][QUIC    ][QUIC    ][cơ bản  ][nâng cao][tích    ][đánh giá][Ch1,2,5 ]
           |---------|---------|---------|---------|---------|---------|---------|---------|
TV2        [TCP/UDP ][Security][Setup   ][Thrput  ][Multi-  ][Biểu đồ][Hạn chế ][Báo cáo ]
           [Compare ][Loss Det][HTTP/2  ][test    ][plexing ][Thrput  ][Khuyến  ][Ch3,4   ]
           |---------|---------|---------|---------|---------|---------|---------|---------|
Chung      [Tài liệu]         [Tools   ]         [Dataset ][Review  ][Bảng SS ][Review  ]
           |---------|---------|---------|---------|---------|---------|---------|---------|
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

### Tuần 5: Thử nghiệm nâng cao
- [ ] Data Packet Loss 1%, 5%, 10% (TV1)
- [ ] Data High Latency 50-500ms (TV1)
- [ ] Data Connection Migration (TV1)
- [ ] Data Multiplexing 5/10/20 streams (TV2)
- [ ] Data Jitter test (TV2)
- [ ] Complete dataset (TV2)

### Tuần 6: Phân tích
- [ ] Báo cáo phân tích Handshake & 0-RTT (TV1)
- [ ] Báo cáo phân tích Latency (TV1)
- [ ] Báo cáo phân tích Packet Loss (TV1)
- [ ] Clean dataset (TV2)
- [ ] Tất cả biểu đồ (TV2)
- [ ] Báo cáo phân tích Throughput & Multiplexing (TV2)

### Tuần 7: So sánh và đánh giá
- [ ] Bảng so sánh QUIC vs HTTP/2 (TV1)
- [ ] Báo cáo ưu điểm QUIC (TV1)
- [ ] Báo cáo hạn chế QUIC (TV2)
- [ ] Khuyến nghị sử dụng (Cả 2)
- [ ] Outline báo cáo (TV2)

### Tuần 8: Báo cáo
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
