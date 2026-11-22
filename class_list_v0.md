# Danh sách lớp v0 — Phạm Hải · G06

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person.seatbelt` | `worn_correct` / `worn_incorrect` / `not_worn` / `unknown` | Nhận biết trạng thái sử dụng dây an toàn | Có khi dây nhìn rõ; bị che thì `unknown` |
| 2 | `face.eye_left` / `face.eye_right` | `open` / `closed` / `unknown` | Theo dõi tình trạng mở/nhắm mắt theo từng khung hình | Có nếu thấy được mí mắt |
| 3 | `face.glasses` | `none` / `clear` / `sun` / `unknown` | Xác định tình trạng đeo kính và khó khăn khi quan sát mắt | Hạn chế; kính râm có thể trông trong suốt trên NIR |
| 4 | `face.gaze_zone` | `road` / `mirror_l` / `mirror_r` / `mirror_c` / `cluster` / `center` / `lap` / `other` | Phân loại vùng tài xế đang nhìn để phân tích mức tập trung | Có khi kết hợp được hướng đầu và mắt |
| 5 | `face13` | 13 keypoint; `occluded` / `outside` | Mô tả hình học khuôn mặt, hỗ trợ phân tích vị trí mắt và hướng đầu | Có khi mặt đủ rõ; điểm che phải đánh cờ |
| 6 | `hand.on_wheel` | `yes` / `no` / `unknown` | Biết tay có đang chạm vô lăng hay không | Có nếu nhìn thấy tay và vô lăng |
| 7 | `face` | Box mặt tài xế | Xác định vùng mặt để theo dõi mắt và hướng đầu | Có nếu mặt nhìn rõ |
| 8 | `phone.state` | `held` / `mounted` / `lap` | Phân biệt điện thoại cầm tay, trên giá và trên đùi khi theo dõi việc dùng điện thoại | Có nếu thấy rõ hình dạng máy |
| 9 | `frame_meta.camera_blocked` | `yes` / `no` | Biết camera bị che để tránh kết luận từ ảnh không dùng được | Có; cần phân biệt bị che với ảnh tối |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person.seat` | `rear_left` / `rear_middle` / `rear_right` | Xác định vị trí người ngồi trên hàng ghế sau | Có dựa trên hình dáng và vị trí |
| 2 | `person.seatbelt` | `not_worn` / `unknown` (trên SVIRO) | Theo dõi việc dùng dây an toàn, tránh đoán khi không nhìn thấy | Có nếu dây nhìn được |
| 3 | `child_seat.occupied` | `unknown` / `no` / `yes` (theo schema coach cập nhật) | Nhận biết ghế trẻ em có vật/người chiếm chỗ hay không | Có khi quan sát rõ lòng ghế |
| 4 | `infant_seat.facing` | `rear` / `front` | Nhận biết hướng lắp ghế em bé trong xe | Có dựa trên cấu trúc và hướng ghế |
| 5 | `object.type` | `other` / `bag` / `box` / `cup` | Phân biệt đồ vật trên ghế với người và ghế trẻ em | Có theo hình dạng, không dựa vào màu |
| 6 | `person` | Box người; kèm `seat` và `seatbelt` | Phát hiện người để xác định ghế có người ngồi | Có nếu thấy được hình dáng người |
| 7 | Metadata khung hình | `modality` / `light` / `camera_id` (theo bản nháp slide 54) | Phân biệt loại ảnh, ánh sáng và camera để kiểm tra kết quả theo từng điều kiện | Không suy hết từ ảnh; `camera_id` lấy từ thông tin bộ dữ liệu |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. Câu hỏi: Có nên dùng ma-nơ-canh thay người thật trong dữ liệu huấn luyện OMS không? Nếu cùng gán `occupied=yes`, có cần thêm thuộc tính phân biệt ma-nơ-canh với người thật để model không học nhầm không?
   Khung ví dụ: S03_rgb.png.
   Bạn tạm gán thế nào và vì sao: Em giữ `child_seat.occupied=yes` theo xác nhận của coach; không thêm `person` cho ma-nơ-canh. Em ưu tiên an toàn cho trẻ em nên không dùng ma-nơ-canh để thay hoàn toàn dữ liệu người thật. Ma-nơ-canh có thể dùng để thử tình huống nguy hiểm, nhưng cần phân biệt rõ trong dữ liệu và không lấy kết quả đó làm bằng chứng hệ thống đã nhận diện tốt trẻ thật.
2. Câu hỏi: Với ảnh DMS xoay 90°, ngưỡng mặt rộng 60 px được đo theo chiều ngang ảnh hay theo chiều rộng khuôn mặt sau khi tính hướng đầu?
   Khung ví dụ: D02.png.
   Bạn tạm gán thế nào và vì sao: Em giữ `face13` ở D02 vì cả hai chiều box mặt đều trên 60 px. Với mặt sát ngưỡng trong ảnh xoay, em cần coach xác nhận hướng đo để gán thống nhất.
