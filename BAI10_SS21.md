
# Đánh Giá Đa Giải Pháp Quy Trình Khắc Phục Sự Cố Kỹ Thuật

## **Lập bảng So sánh Trade-off Toàn diện**

| Tiêu chí đánh giá | Phương án 1: Hỗ trợ Cảm tính / Nhóm Chat | Phương án 2: Troubleshooting 4 Chặng Chuẩn hóa |
| --- | --- | --- |
| 1. Thời gian xử lý sự cố (Downtime) | Kéo dài, phụ thuộc vào việc Senior Dev có rảnh để trả lời hay không | Rút ngắn 80 phần trăm, tự giải quyết tại chỗ trong 5 đến 10 phút đầu tiên |
| 2. Áp lực và Chi phí cho Senior Devs | Rất cao, bị phân tâm liên tục bởi các câu hỏi lỗi cơ bản lặp lại | Tối ưu, Senior chỉ tiếp nhận các ca lỗi phức tạp có Bug Report chuẩn |
| 3. Năng lực và Tính tự chủ của KTV | Thụ động, sợ hãi thông báo lỗi tiếng Anh, không tiến bộ nghề nghiệp | Chủ động, tư duy phân tích sắc bén, làm chủ trọn vẹn máy tính trạm |
| 4. Khả năng lưu vết tri thức (Knowledge Base) | Thất thoát, tin nhắn trôi mất trên Zalo, người sau gặp lại lỗi cũ | Lưu trữ tập trung, tích lũy tài liệu Wiki sửa lỗi nội bộ công ty |

### Kết luận lựa chọn: Vì sao phải chọn Phương án 2

- Ban Giám đốc VoltCharge bắt buộc phải chọn Phương án 2 nếu muốn mở rộng lên 1000 trạm sạc.
- Phương án 1 không mở rộng được: 1000 trạm mà mỗi lỗi đều chờ Senior Dev thì Downtime nhân lên, thiệt hại 500000 VNĐ trên giờ trên mỗi trụ, uy tín thương hiệu giảm mạnh.
- Phương án 2 biến KTV thành tuyến đầu tự xử lý lỗi cơ bản, Senior Dev chỉ làm việc khó và phát triển tính năng mới.
- Phương án 2 tạo ra Knowledge Base, lỗi cũ chỉ cần sửa một lần, cả hệ thống dùng lại, chi phí hỗ trợ không tăng theo số trạm.

## Phần 2: Sơ đồ Luồng Ra Quyết Định Gỡ Lỗi Kiosk

### Bắt đầu: Kiosk gặp sự cố, hiện Error Pop-up

**Chặng 1: Bóc tách từ khóa và Googling với toán tử**

- Bước 1: Đọc kỹ Error Pop-up, ghi lại mã lỗi, tên phần mềm, tên hệ điều hành.
- Bước 2: Tách thành 3 đến 4 từ khóa chính, bỏ từ thừa.
- Bước 3: Gõ Google theo công thức: mã lỗi + tên phần mềm + site để giới hạn nguồn.
- Bước 4: Dùng toán tử trừ để loại từ gây nhiễu, dùng toán tử cụm từ chính xác để tìm đúng câu lỗi.
- Nếu có kết quả phù hợp: Chuyển sang Chặng 2.
- Nếu không có kết quả: Chuyển sang Chặng 3.

**Chặng 2: Thẩm định bài viết StackOverflow / GitHub Issues**

- Bước 1: Đọc lướt trong 30 giây: Tiêu đề, mã lỗi, phiên bản có khớp với máy của mình không.
- Bước 2: Kiểm tra Tích xanh là đáp án được chấp nhận, kiểm tra Upvote cao, kiểm tra ngày đăng còn mới.
- Bước 3: Đọc bình luận phản biện, không áp dụng ngay nếu có người báo cách đó gây lỗi khác.
- Bước 4: Thử giải pháp số 1 trên Kiosk, kiểm tra kết quả.
- Nếu sửa được: Ghi lại vào Wiki nội bộ và kết thúc.
- Nếu chưa sửa được: Thử giải pháp số 2, nếu vẫn lỗi thì chuyển sang Chặng 3.

**Chặng 3: Prompt AI giải mã thông báo tiếng Anh**

- Gửi Prompt 3 thành phần cho Trợ lý AI:
- Thành phần 1: Bối cảnh: Đang chạy Kiosk VoltCharge, hệ điều hành, phiên bản phần mềm.
- Thành phần 2: Mã lỗi nguyên văn: Dán toàn bộ thông báo lỗi tiếng Anh.
- Thành phần 3: Yêu cầu đầu ra: Giải thích bằng tiếng Việt, đưa ra 2 giải pháp an toàn nhất theo thứ tự, không xóa dữ liệu.
- Bước 1: Thử giải pháp 1 của AI, kiểm tra kết quả.
- Bước 2: Nếu thất bại, thử giải pháp 2 của AI, kiểm tra kết quả.
- Nếu sửa được: Ghi lại vào Wiki nội bộ và kết thúc.
- Nếu thử 2 giải pháp vẫn thất bại sau 15 phút: Chuyển sang Chặng 4.

**Chặng 4: Lập phiếu Bug Report chuẩn gửi về IT Helpdesk**

- Điền phiếu Bug Report chuẩn 4 bước:
- Bước 1: Môi trường: Mã trạm, mã trụ, hệ điều hành, phiên bản phần mềm, thời gian lỗi.
- Bước 2: Các bước tái hiện lỗi: Đã bấm gì, đã thử gì, kết quả ra sao.
- Bước 3: Kết quả mong đợi và kết quả thực tế: Kèm ảnh chụp Error Pop-up và log.
- Bước 4: Đã thử giải pháp nào: Link StackOverflow, GitHub, giải pháp của AI, kết quả từng cách.
- Gửi phiếu về phòng IT Helpdesk, giữ Kiosk ở trạng thái chờ, không tự sửa thêm để tránh mất log.
- Kết thúc quy trình, chờ phản hồi từ cấp 2.

### Sơ đồ tóm tắt dạng dòng chảy

- Kiosk lỗi -> Bóc tách từ khóa -> Google với toán tử
- Có kết quả StackOverflow, GitHub -> Kiểm tra Tích xanh và Upvote -> Thử sửa
- Sửa được -> Ghi Wiki -> Kết thúc
- Không sửa được -> Hỏi AI bằng Prompt 3 thành phần -> Thử 2 giải pháp trong 15 phút
- Sửa được -> Ghi Wiki -> Kết thúc
- Vẫn lỗi -> Gửi Bug Report 4 bước về IT Helpdesk -> Kết thúc
