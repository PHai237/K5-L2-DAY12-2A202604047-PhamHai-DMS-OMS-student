# Khai báo dùng AI — Phạm Hải

Không dùng AI thì xóa bảng và ghi: **Không dùng.**

Nhắc lại: không đưa ảnh cabin hay ảnh tài xế (kể cả ảnh chụp màn hình) cho bất kỳ công cụ AI nào.

| # | Công cụ | Bạn hỏi gì (tóm tắt) | Bạn dùng kết quả thế nào | Bạn có kiểm lại không? Bằng gì? |
|---|---|---|---|---|
| 1 | ChatGPT | Giải thích quy tắc `gaze_zone`, `phone.state`, `face13`, `outside`/`occluded` | Tham khảo cách hiểu guideline và tự gán nhãn trên CVAT | Có; so với `GUIDE.md` và trao đổi coach |
| 2 | ChatGPT | Hướng dẫn export CVAT for images 1.1, chạy `cabin_check.py` | Xuất XML không kèm ảnh và kiểm cấu trúc các annotation | Có; dùng báo cáo `check_final.txt`, `check_extra.txt` |
| 3 | ChatGPT | Kiểm annotation/metadata trong gói review Vin-er | Nhận diện điểm cần tự soát, không dùng kết quả làm nhãn tự động | Có; tự kiểm lại CVAT và dùng checker |
| 4 | ChatGPT | Tìm nguyên nhân `occupied=yes` bị checker cũ từ chối | Cập nhật schema theo chấp thuận của lab coach | Có; chạy checker đạt 0 ERROR |
| 5 | ChatGPT | Kiểm repo GitHub và cách hoàn thiện E1–E5 | Đối chiếu yêu cầu nộp và kiểm file còn thiếu | Có; đối chiếu `SUBMISSION.md` |
| 6 | ChatGPT (Codex) | Rà đáp án exit ticket, giải thích cách tính thời gian và kiểm file còn thiếu | Sửa câu 2 thành 2,50 giây, câu 3 thành A/B/C; bổ sung giải thích đáp án và WARN D02 theo tọa độ XML | Đã đối chiếu tài liệu repo, tính 75/30 và chạy checker: 22 ảnh, 0 lỗi, 1 WARN; vị trí điểm trên ảnh cần tự kiểm trong CVAT |
| 7 | ChatGPT (Codex) | Rút gọn giải thích, cập nhật self review và nhóm; giải thích ir_log và disagreement_log | Ghi theo xác nhận cá nhân; cập nhật nhóm 4 người và người review Nguyễn Nhật Hạ | Kết quả tự rà soát do người học cung cấp; quan sát IR và kết quả diff chưa được AI xác minh |
| 8 | ChatGPT (Codex) | Sửa mục cá nhân và hai câu hỏi leo thang, giữ format và dùng cách xưng em | Ghi rõ em tự làm bài riêng; hỏi về ma-nơ-canh và cách đo ngưỡng 60 px trên ảnh xoay | Đối chiếu GUIDE.md mục 4.6, 4.8; câu hỏi là nội dung cần coach làm rõ |
| 9 | ChatGPT (Codex) | Đối chiếu format mẫu và dùng slide 54 trong ZIP bài giảng | Bỏ dòng nhắc xóa ví dụ; bổ sung face, phone, camera_blocked, person và metadata vào danh sách lớp | Đối chiếu templates/class_list_v0.md, nội dung slide 54 và GUIDE.md; giữ bảng 5 cột và cấu trúc hai câu hỏi |
| 10 | ChatGPT (Codex) | Đổi câu hỏi đã được coach giải đáp | Hỏi về việc dùng ma-nơ-canh thay người thật và cách phân biệt trong nhãn; giữ câu hỏi ngưỡng 60 px | Em xác nhận ma-nơ-canh được tính occupied=yes; cách đo ngưỡng chưa được hướng dẫn |
| 11 | ChatGPT (Codex) | Ghi hai câu trả lời đã thống nhất và kiểm phần còn thiếu trước khi nộp | Bổ sung quan điểm về ma-nơ-canh, cách tạm xử lý ngưỡng 60 px; cập nhật TEAM có 5 dòng đã xử lý | Kiểm số dòng và các cột bắt buộc trong CSV; đối chiếu SUBMISSION.md và chạy checker, không xác minh nhãn bằng ảnh |
| 12 | ChatGPT (Codex) | Cập nhật MSSV Hùng, cả nhóm đã làm xong và Hạ cùng xử lý 5 dòng | Điền TEAM theo thông tin em xác nhận; giữ nguyên phần cá nhân | Em cung cấp MSSV và xác nhận tình trạng hoàn thành, review chung với Hạ |
