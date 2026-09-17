# Báo cáo Day 5 — điền trực tiếp trong fork của bạn

- Mã học viên theo lớp: [2A202602252]
- Ngày / CVAT local: 17/09/2026 / CVAT local của lớp
- Công cụ đã dùng: Brush / Polygon

## 1. Bài đã nộp

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Tất cả ZIP đã được đặt đúng tên theo mã task trong thư mục submissions và đã được kiểm nhận trong notebook. Nếu có task nào còn thiếu trong lúc nộp chính thức, sẽ ghi rõ trạng thái tương ứng.

## 2. Một quyết định trước khi dùng gợi ý

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: Ảnh đầu tiên của medium_instance, vị trí ở vùng trung tâm dưới của khung hình; object đầu tiên được vẽ thủ công trước khi dùng bất kỳ gợi ý nào.
- Class và quy tắc tôi dùng để chọn biên: class phù hợp với object đang nhìn thấy; biên được chọn theo phần vật thật sự xuất hiện, không đoán phần bị che hoặc phần nền không thuộc object.
- Nếu dùng gợi ý sau đó: không dùng gợi ý tự động trong bước đầu; nếu có dùng sau đó, tôi sẽ kiểm lại class, số object và ranh biên trước khi giữ vùng đề xuất.
- Nếu không dùng gợi ý: không dùng; tôi vẫn giữ quy tắc chọn biên theo phần nhìn thấy và không mở rộng ra nền hoặc vật che.

## 3. Một lỗi tôi tìm thấy và sửa

- Task/ảnh/vùng: medium_instance / ảnh đầu tiên / vùng có hai object sát nhau
- Lỗi thuộc loại: gộp-tách
- Bằng chứng tôi nhìn thấy: hai vật cùng lớp ở gần nhau đã bị gộp thành một mask trong quá trình vẽ ban đầu; vùng giữa hai vật quá nhỏ hoặc không rõ.
- Quy tắc và hành động sửa: theo quy tắc instance, hai vật sát nhau nhưng tách biệt về đối tượng phải thành hai mask riêng; tôi xác định ranh giữa hai object, tách lại, Save và export lại.
- Sau sửa đã Save và export lại chưa? Đã Save và export lại rồi.

Nếu xem Summary tự đánh giá hoặc chạy script, tôi sẽ ghi kết quả cụ thể tại task đó, chưa có điểm tuyệt đối chưa có phản hồi chính thức từ coach.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| cp4_curb / ranh giữa road và sidewalk | road hoặc sidewalk | Quy tắc chức năng bó vỉa và vùng mặt đường; không chỉ dựa vào màu sắc | Chọn theo ranh chức năng của bó vỉa, giữ vùng phù hợp với phần nhìn thấy |
| cp3_thin / cột hoặc biển báo mảnh | background hay thin structure | Dùng brush nhỏ, xét phần vật thật sự hiện diện; không bỏ sót nét mảnh | Giữ phần cột/biển báo với brush 2–3px, loại background |
| cp2_slice / hai xe sát nhau | một object hoặc hai object | Quy tắc instance yêu cầu tách nếu là hai xe riêng, dù sát nhau | Tách thành hai object riêng để tránh gộp |


