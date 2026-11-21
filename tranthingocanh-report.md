# Báo cáo cá nhân — Ngày 11

- **Họ tên** — Trần Thị Ngọc Ánh
- **Mã học viên** — 2A202603157
- **Guideline** — Road v1.0
- **Lần nộp** — Revision 1

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| --- | --- | --- |
| 6 label, đúng kiểu | Có, theo XML đã xuất | Polyline cho lane và road_curb. Polygon cho drivable và crosswalk. Rectangle cho traffic_light và traffic_sign. |
| Thuộc tính và giá trị | Đã chạy lint | B06 và B08 đã dùng position=other cho lane. B04 còn cảnh báo gợi ý rà edge_zone. |
| 4 tag ảnh | Có | 28/28 ảnh có đủ camera, timeofday, weather và source. |

- **Kết thúc polyline** — Bấm Done trên thanh công cụ sau khi đặt các điểm.
- **Đặt tag ảnh** — Mở công cụ Tag, chọn tên tag, bấm +, rồi chỉnh value trong Details.

## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| --- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| front | 12 | 36 | 5 | 3 | 24 | 16 | 15 |
| front-extra (4/4) | 4 | 10 | 0 | 3 | 8 | 6 | 5 |
| fisheye | 8 | 6 | 1 | 8 | 6 | 4 | 4 |
| fisheye-extra (4/4) | 4 | 0 | 1 | 4 | 4 | 1 | 0 |

## 3. Bảng ca khó

| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A14 | lane | Gộp hai nét vàng hay vẽ từng nét | Vẽ hai polyline bám từng nét | Thầy hướng dẫn vẽ riêng hai nét sơn. Lint vẫn gợi ý kiểm vì hai đường có cùng position=L1. |
| B06, B08 | lane | Dùng L1/R1 hay other | position=other | Đây là ảnh fisheye từ camera bên. |
| B04 | traffic_sign | Bật edge_zone hay để trống | Bản xuất để trống, cần rà lại | Lint gợi ý tâm hộp nằm ngoài 80% bán kính ảnh fisheye. Cần đối chiếu ảnh gốc. |

## 4. Phiếu QC 1 nhận được

- **Bạn kiểm lô của tôi** — Trương Mỹ Tâm
- **Quyết định nhận được** — Hold

| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
| QC1-02 | 6 cảnh báo | Có, theo kết quả tự kiểm | Có. Bản xuất mới có L1 ở A02 và A07, cả L1 và R1 ở A05, R1 ở A06 và A14. Lint không còn báo QC1-02.|
| QC1-03 | 3 cảnh báo | Có, theo kết quả tự kiểm | Có. Đã đổi position=other cho 2 vạch ở B06 và 1 vạch ở B08 vì đây là ảnh từ camera fisheye bên. Lint không còn báo QC1-03. |

## 5. Kiểm file export

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
| --- | --- | --- | --- | --- |
| tranthingocanh-front.zip | Có, đọc được bằng lint | A01: [đối chiếu Job 14] / 9 | A02: [đối chiếu Job 14] / 8 | Có, 16/16 ảnh |
| tranthingocanh-fisheye.zip | Có, đọc được bằng lint | B01: [đối chiếu Job 14] / 2 | B02: [đối chiếu Job 14] / 3 | Có, 12/12 ảnh |

Bản kiểm có 0 cảnh báo nặng, 11 cảnh báo chính và 3 cảnh báo nhẹ. Mã SHA-256 trong manifest khớp hai ZIP và cả hai chỉ chứa annotations.xml.

## 6. Ảnh chụp màn hình

1. [Chèn ảnh tab Labels của project]
![alt text](image.png)
2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển).
![alt text](image-1.png)
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong.
![alt text](image-2.png)
4. Một đoạn XML có .
![alt text](image-3.png)

## 7. Tự đánh giá

- **Lỗi cần chú ý và cách tránh ở Ngày 20** — QC1-03 xuất hiện trên ba vạch ở B06 và B08 trước khi sửa. Lần sau em sẽ kiểm tag camera trước khi đặt position và rà lại các vạch trên ảnh camera bên.
- **Nhãn đi vào mô hình ở đâu** — Tọa độ polyline và thuộc tính vị trí có thể dùng để tạo đích huấn luyện nhận diện làn. Nếu gán L1/R1 cho vạch trên camera bên thay vì other, các mẫu dùng để học thuộc tính vị trí sẽ mang nhãn sai.


