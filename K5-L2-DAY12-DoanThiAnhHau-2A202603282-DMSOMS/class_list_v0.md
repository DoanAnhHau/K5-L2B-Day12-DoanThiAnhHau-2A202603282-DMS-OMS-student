# Danh sách lớp v0 — Đoàn Thị Ánh Hậu · G07

Các lớp dưới đây bám theo schema Cabin v1.0 và các khung G07. Giá trị `unknown` dùng khi ảnh không cho phép kết luận chắc chắn; ảnh OMS `_ir` của SVIRO là IR mô phỏng, còn D01–D06 là NIR thật.

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person.seatbelt` | `worn_correct` / `worn_incorrect` / `not_worn` / `unknown` | Kiểm tra người lái có thắt dây an toàn đúng cách; hỗ trợ nhắc nhở an toàn. | Thường thấy dây và vị trí dây trên NIR, nhưng vùng tối/che khuất phải là `unknown`. |
| 2 | `face.eye_left`, `face.eye_right` | `open` / `closed` / `unknown` | Theo dõi trạng thái từng mắt để phát hiện dấu hiệu nhắm mắt kéo dài, hỗ trợ cảnh báo buồn ngủ. | Có thể thấy trên NIR; phản xạ kính, kính râm, che khuất hoặc mặt nhỏ làm trạng thái thành `unknown`. |
| 3 | `face.glasses` | `none` / `clear` / `sun` / `unknown` | Nhận biết kính làm thay đổi độ tin cậy của việc theo dõi mắt và hiệu chỉnh xử lý mắt. | Kính có thể hiện hình nhưng loại kính khó phân biệt trên NIR; kính râm có thể trông trong, không chắc thì `unknown`. |
| 4 | `face.gaze_zone` | `road` / `mirror_l` / `mirror_r` / `mirror_c` / `cluster` / `center` / `lap` / `other` | Xác định người lái đang nhìn đường, gương hay rời vùng chú ý để hỗ trợ cảnh báo mất tập trung. | Ước lượng được từ hướng mặt/mắt khi thấy rõ; NIR không đảm bảo thấy tròng mắt, nên dùng `other` khi không chắc. |
| 5 | `hand.on_wheel` | `yes` / `no` / `unknown` | Phát hiện tay người lái có đặt trên vô lăng, hỗ trợ giám sát mức độ sẵn sàng điều khiển. | Bàn tay và vô lăng thường thấy trên NIR; tay bị che hoặc nằm ngoài khung thì `unknown`. |
| 6 | `phone.state` | `held` / `mounted` / `lap` | Phát hiện việc sử dụng điện thoại khi lái xe để hỗ trợ cảnh báo xao nhãng. | Có thể nhận ra hình dáng/vị trí trên NIR; vật nhỏ hoặc bị tay che khó phân biệt, chỉ gán khi thấy rõ điện thoại. |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person.seat` | `rear_left` / `rear_middle` / `rear_right` (và các ghế khác theo schema) | Xác định ghế nào có người để hiển thị tình trạng chiếm chỗ và gắn đúng người với vùng ghế. | Có thể thấy hình người trên IR-sim; khi ảnh tối/che khuất cần dựa hình dạng và vị trí, không đoán theo màu. |
| 2 | `child_seat.occupied` | `no` / `unknown` theo guideline v1.0 | Phân biệt ghế trẻ em trống với tình trạng chưa xác định, hỗ trợ kiểm tra chỗ ngồi và cảnh báo an toàn. | Hình ghế thường nhận ra được trên IR-sim; việc có vật/người bên trong có thể bị che, khi đó `unknown`. |
| 3 | `infant_seat.facing` | `rear` / `front` | Xác định hướng lắp ghế em bé để hỗ trợ kiểm tra cấu hình ghế và an toàn ghế trước. | Thường suy ra được từ hình dáng và hướng tựa của ghế trên IR-sim; góc nhìn/che khuất có thể làm không rõ. |
| 4 | `object.type` | `bag` / `box` / `cup` / `other` | Nhận biết hành lý hoặc đồ vật trong cabin để quản lý vật cản và tình trạng khoang hành khách. | Có thể phân loại vật lớn theo hình dạng trên IR-sim; màu sắc không đáng tin, vật tối/nhỏ có thể chỉ xác định `other` hoặc không gán. |
| 5 | `person.seatbelt` | `worn_correct` / `worn_incorrect` / `not_worn` / `unknown` | Theo dõi dây an toàn của từng người ngồi, hỗ trợ cảnh báo nếu chưa thắt hoặc thắt sai. | Dây có thể thấy trên IR-sim khi tương phản đủ; bóng tối và dây bị che khiến trạng thái `unknown`. |
| 6 | `child_seat.seat` / `infant_seat.seat` | `rear_left` / `rear_middle` / `rear_right` (theo vị trí trên xe) | Định vị ghế trẻ em/ghế em bé để hệ thống biết vị trí cần kiểm tra hoặc cảnh báo. | Nhìn hình ghế và vị trí trên IR-sim; camera nhìn về phía sau nên bên trái ảnh là `rear_right` của xe. |

## 2 câu hỏi leo thang

1. Câu hỏi: Khi một vật hoặc phần cơ thể che một phần ghế trẻ em, tiêu chí nào phân biệt `occupied = no` với `unknown`? Schema Cabin v1.0 hiện có giá trị `yes`, nhưng hướng dẫn yêu cầu không dùng `yes` cho `child_seat`.  
   Khung ví dụ: **G07 S08_rgb.png** có người ngồi cạnh ghế em bé; cần làm rõ người ngồi cạnh có ảnh hưởng cách xác định tình trạng ghế hay không khi phần lòng ghế bị che.  
   Bạn tạm gán thế nào và vì sao: Chỉ gán box `child_seat` nếu nhận ra ghế; dùng `unknown` nếu không quan sát được lòng ghế, dùng `no` khi thấy rõ ghế trống. Theo hướng dẫn hiện tại không gán `yes`, đồng thời ghi lại mâu thuẫn schema để hỏi coach.

2. Câu hỏi: Với vùng mắt bị phản xạ/che một phần trên NIR, khi nào landmark `face13` được đánh dấu `occluded`, và khi nào bỏ điểm bằng `outside`? Có cần tiêu chí áp dụng thống nhất theo từng loại che khuất không?  
   Khung ví dụ: **G07 D01.png** có vùng mặt và mắt chịu ảnh hưởng phản xạ NIR; cần thống nhất ngưỡng để hai người gán không đặt điểm theo suy đoán khác nhau.  
   Bạn tạm gán thế nào và vì sao: Gán `occluded` khi vị trí mốc có thể ước lượng chắc từ phần mặt còn thấy; dùng `outside` khi không thể định vị đáng tin cậy. Không đặt điểm cho đủ và không suy trạng thái mắt từ ảnh khác.

