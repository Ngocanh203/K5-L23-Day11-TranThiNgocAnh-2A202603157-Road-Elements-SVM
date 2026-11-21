# Phiếu QC 1 — Road v1.0

- **Lô được kiểm (học viên)** — Tam (tên tài khoản chủ Job 19 trong XML, họ tên chưa xác nhận).
- **Người kiểm (học viên)** — Trần Thị Ngọc Ánh (2A202603157).
- **Ngày** — 21/11/2026.
- **Phiên bản guideline** — Road v1.0.
- **File được kiểm** — `annotations(1).xml`, CVAT XML 1.1, Job 19. Revision bàn giao chưa xác định vì chưa có manifest.
- **Số ảnh kiểm** — 6 ảnh mẫu (A05–A10), sàng lọc cấu trúc XML trên 22 ảnh còn lại. Chưa đối chiếu ảnh gốc.
- **Số nhãn đã kiểm (shape + tag)** — 103 nhãn của mẫu, gồm 79 shape và 24 tag, ở mức dữ liệu XML. Toàn lô có 359 nhãn trên 28 ảnh.

## Tổng hợp theo mã

Số mục kiểm dưới đây chỉ tính các phép kiểm đã thực hiện trên mẫu 6 ảnh. Số lỗi là các lỗi đã xác nhận theo guideline. Các dấu hiệu cần đối chiếu ảnh được ghi ở bảng Ca mơ hồ.

| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
|---|---|---|---|---|
| QC1-01 tag camera | Sai thuộc tính / bỏ sót | 6 tag, so với nhóm tên ảnh | 0 trong XML | Nặng |
| QC1-02 đủ L1, R1 | Bỏ sót | 6 ảnh, kiểm sự hiện diện theo thuộc tính | Chờ đối chiếu 4 ảnh | Nặng |
| QC1-03 position | Sai thuộc tính / thừa | 12 vạch, kiểm giá trị khai báo | 0 giá trị không hợp lệ. A09 cần xem ảnh. | Nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | Sai phạm vi / bỏ sót | 12 vạch, sàng lọc chiều theo tọa độ đầu–cuối | 0 dấu hiệu đảo chiều theo trục dọc. Chưa kiểm tâm và điểm dừng. | Chính |
| QC1-05 vạch đứt, che | Sai phạm vi / sai thuộc tính | 0 đối chiếu ảnh | Chưa đánh giá | Chính |
| QC1-06 style, color, kind | Sai thuộc tính | 12 vạch, kiểm giá trị khai báo | 0 giá trị không hợp lệ. A09 cần xem ảnh. | Chính |
| QC1-07 vùng lái | Sai phạm vi / bỏ sót / thừa | 8 polygon, kiểm tọa độ và area_type | 0 điểm ngoài khung hoặc area_type không hợp lệ. Chưa kiểm biên thực tế. | Chính |
| QC1-08 đèn, màu | Bỏ sót / sai phạm vi / sai thuộc tính | 16 hộp, kiểm tọa độ, chiều cao và giá trị màu | 0 lỗi cấu trúc hoặc hộp dưới 8 px. Chưa kiểm màu sáng và độ đầy đủ. | Nặng / Chính |
| QC1-09 facing, type, group, biển phụ | Sai thuộc tính | 46 hộp, kiểm giá trị khai báo | 0 giá trị không hợp lệ. Chưa kiểm hướng, loại và biển phụ theo ảnh. | Chính |
| QC1-10 hình in, đủ biển | Bỏ sót / sai phạm vi | 30 hộp biển, đo chiều cao | 3 hộp dưới 8 px, chờ xác nhận chiều cao biển thật | Chính |
| QC1-11 fisheye | Sai phạm vi / sai thuộc tính | 0 ảnh fisheye trong mẫu. Kiểm bổ sung position của 2 vạch trên B06 và B08. | Cả hai là other. Chưa kiểm cung và edge_zone. | Chính |
| QC1-12 file | Lỗi file | 1 XML, kiểm phiên bản, khả năng đọc, tag và giá trị thuộc tính | 0 lỗi ở các mục đã kiểm. ZIP và manifest chưa được kiểm. | Nhẹ / Nặng |

## Danh sách lỗi (mỗi lỗi một dòng)

Chưa có lỗi được xác nhận bằng ảnh gốc. Các dòng sau là phát hiện từ tọa độ XML cần xác minh trước khi tính vào tổng lỗi. Tệp xuất thiếu ID đối tượng CVAT, nên dùng tọa độ để tìm hộp.

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
|---|---|---|---|---|---|
| 1 | QC1-10 | A08 | traffic_sign, góc trái trên (432.82, 187.65) | Chính nếu xác nhận | Hộp cao 7.94 px. Đo lại biển thật. Nếu biển đủ 8 px, chỉnh hộp sát mép. Nếu biển dưới 8 px, bỏ hộp. |
| 2 | QC1-10 | A10 | traffic_sign, góc trái trên (535.50, 235.00) | Chính nếu xác nhận | Hộp cao 7.68 px. Đo lại biển thật và xử lý theo ngưỡng 8 px. |
| 3 | QC1-10 | A10 | traffic_sign, góc trái trên (440.26, 232.36) | Chính nếu xác nhận | Hộp cao 6.44 px. Đo lại biển thật và xử lý theo ngưỡng 8 px. |

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
|---|---|---|
| A05 | Ảnh có thấy L1 hoặc R1 thuộc phạm vi gán không? XML chưa có cả hai. | Chưa có |
| A06 | Ảnh có thấy L1 hoặc R1 thuộc phạm vi gán không? XML chưa có cả hai. | Chưa có |
| A07 | Ảnh có thấy L1 không? XML có R1 và R2. | Chưa có |
| A08 | Biển tương ứng hộp cao 7.94 px có đạt ngưỡng trên ảnh gốc không? | Chưa có |
| A09 | R1 có nhìn thấy không? Hai đường cùng L2/kind=double là hai nét của một vạch đôi hay hai đối tượng khác nhau? | Chưa có |
| A10 | Hai biển tương ứng hộp cao 7.68 và 6.44 px có đạt ngưỡng trên ảnh gốc không? | Chưa có |
| B06 (kiểm thêm) | Theo kế hoạch fisheye, ảnh này có cần polygon drivable ở phần mặt đường nhìn thấy không? XML chưa có nhãn này. | Chưa có |
| B11 (kiểm thêm) | Hai road_curb ở đoạn cong (một đường ngắn nằm gần đường dài) có bám cùng một mép không? Hai polygon direct có đang gán trùng cùng vùng không? | Chưa có |

## Quyết định

- **Lỗi nặng** — Chưa có lỗi xác nhận. QC1-02 còn chờ ảnh gốc.
- **Lỗi chính** — 0 đã xác nhận / 103 nhãn đã sàng lọc trong mẫu. Tỷ lệ lỗi chính cuối chưa xác định vì chưa đối chiếu ảnh.
- **Lỗi nhẹ** — 0 phát hiện trong phần cấu trúc XML đã kiểm.
- **Ca chờ lead** — 8 dòng, gồm 6 ảnh mẫu và 2 ảnh kiểm thêm.
- **Quyết định** — **Hold**.
- **Lý do** — Còn các ca cần ảnh gốc để xác nhận thiếu vạch, hộp dưới ngưỡng và hình trùng. Chốt lại số lỗi, tỷ lệ và quyết định sau khi đối chiếu. ZIP và manifest cần được kiểm ở bước bàn giao.

Nguồn mẫu: [Phiếu QC 1 — Road v1.0](https://github.com/Ngocanh203/K5-L23-Day11-TranThiNgocAnh-2A202603157-Road-Elements-SVM/blob/main/templates/qc1_form.md).
