# Exit ticket — Ngày 12

Làm cá nhân, không mở slide, khoảng 10 phút. Ghi đáp án ngay dưới mỗi câu.

**Họ tên:** Đoàn Thị Ánh Hậu · **Mã:** G07

---

**Câu 1 · Chọn một.** Camera DMS trên nhiều xe tự chiếu đèn LED cận hồng ngoại khoảng 940 nm lên mặt tài xế. Lý do chính là gì?

- A. Để đo nhiệt độ da và phát hiện tài xế bị sốt
- B. Để có ảnh mặt ổn định cả ngày lẫn đêm mà không làm chói mắt tài xế
- C. Để có ảnh màu đẹp hơn cho cuộc gọi video
- D. Để camera nhìn xuyên qua mọi loại kính râm

Đáp án: **B** — Cận hồng ngoại hỗ trợ thu ảnh khuôn mặt ổn định trong điều kiện sáng và tối, đồng thời không gây chói đáng kể cho tài xế.

**Câu 2 · Số, 2 chữ số thập phân.** Camera DMS chạy 30 khung hình/giây. Model ước lượng yaw của đầu tài xế lớn hơn 30° liên tục từ khung hình số 240 đến khung hình số 314, **tính cả khung 240 và khung 314**. Tài xế không nhìn đường trong bao nhiêu giây?

Đáp án: **2.50 s** — Có 314 − 240 + 1 = 75 khung hình; 75 ÷ 30 = 2.50 giây.

**Câu 3 · Chọn tất cả đáp án đúng.** Những câu nào đúng về dữ liệu cabin so với dữ liệu camera ngoài xe?

- A. Không thể làm mờ mặt tài xế như làm mờ mặt người qua đường, vì model DMS cần chính khuôn mặt.
- B. Ban đêm, ảnh cabin thường là ảnh hồng ngoại đen trắng, nên thuộc tính màu áo không gán được.
- C. Camera OMS nhìn về phía sau xe, nên ghế ở bên trái ảnh là ghế bên phải của xe.
- D. Vật trong cabin thường ở xa và nhỏ, nhiều vật trong một ảnh.
- E. Cảnh cabin cố định nên không cần guideline hay QC riêng.

Đáp án: **A, B, C**.

- **A đúng:** DMS cần các đặc trưng khuôn mặt như mắt và hướng nhìn để theo dõi trạng thái, sự chú ý của tài xế. Làm mờ mặt sẽ che mất thông tin hình ảnh mà model cần phân tích.
- **B đúng:** Ảnh hồng ngoại ban đêm thường đơn sắc, không giữ màu áo như ảnh RGB; vì vậy không thể gán màu áo đáng tin cậy từ ảnh IR.
- **C đúng:** Camera OMS nhìn từ phía trước về phía sau xe. Do góc nhìn ngược hướng với người ngồi trong xe nhìn về phía trước, bên trái ảnh tương ứng với bên phải xe.
- **D sai:** Vật trong cabin thường ở gần camera và có thể hiện lớn trong ảnh; vật ngoài xe thường ở xa hơn và nhỏ hơn.
- **E sai:** Dù bối cảnh cabin có tính lặp lại, vẫn cần guideline và QC để xử lý quy ước ghế, trái/phải, che khuất, nhãn `unknown` và khác biệt giữa RGB với IR.

