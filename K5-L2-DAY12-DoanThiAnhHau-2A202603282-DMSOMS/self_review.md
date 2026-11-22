# Tự đánh giá — Đoàn Thị Ánh Hậu · G07

## 1. Tự rà soát toàn bộ ảnh đã gán

Tự rà soát trong phạm vi task chính gồm 22 ảnh: S01–S08 (RGB và IR-sim) cùng D01–D06. Không đưa ảnh mở rộng S09–S10 hoặc việc task/export thừa ảnh vào bảng lỗi. Bốn lỗi dưới đây là lỗi thuộc ảnh trong phạm vi chính; đã sửa theo xác nhận của mình.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S06_rgb | `frame_meta` | missing | Ảnh không có tag `frame_meta`; mỗi ảnh cần đúng một tag. | Có — đã thêm tag |
| S07_rgb | `frame_meta` | missing | Ảnh không có tag `frame_meta`; mỗi ảnh cần đúng một tag. | Có — đã thêm tag |
| S03_rgb | `infant_seat.seat` | wrong_class | Gán `driver` dù ảnh SVIRO chỉ chụp hàng ghế sau; cần gán một trong `rear_left`, `rear_middle`, `rear_right` theo vị trí ghế trên xe. | Có — đã sửa ghế theo xe |
| S03_rgb | `object.seat` | wrong_class | Gán `driver` dù vật nằm ở hàng ghế sau; cần gán ghế sau tương ứng theo vị trí trên xe. | Có — đã sửa ghế theo xe |

**Ghi chú riêng về `child_seat.occupied = yes`:** Không đưa giá trị này vào bốn lỗi tự đánh giá ở trên. `labels_cabin_v1.json` ở thư mục gốc có giá trị `yes`, trong khi `scripts/cabin_schema.py` và schema kèm G07 chỉ chấp nhận `unknown`, `no`, nên cabin_check báo lỗi validator do hai schema không thống nhất. Đây là gap giữa các phiên bản schema/validator, không phải lỗi box hay bằng chứng đủ để kết luận nhãn nội dung sai. Tuy vậy GUIDE §4.8 hiện ghi không dùng `yes`; trường hợp không nhìn rõ bên trong ghế phải theo hướng dẫn/coach và dùng `unknown`.

Các kết quả kiểm tra đã dán còn phản ánh trạng thái trước/sau chỉnh sửa khác nhau; cần chạy lại export hiện tại với `--expect 22` để xác nhận bốn lỗi trên đã hết. Các WARN khác như `light` của ảnh SVIRO, ghế `driver` ở những ảnh khác và landmark mắt cần được xét hoặc giải thích riêng; chúng không nằm trong bốn lỗi được chọn ở bảng.
## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Gán ghế `driver` cho vật/ghế trẻ em ở ảnh OMS SVIRO, dù camera chỉ nhìn hàng ghế sau.

Vì sao mình mắc: Mình nhầm tên vị trí theo ảnh hoặc chọn giá trị mặc định thay vì xác định ghế theo xe.

Lần sau tránh bằng cách: Với mỗi ảnh OMS, xác định trước hướng xe và vị trí ghế; camera nhìn về phía sau nên bên trái ảnh là `rear_right`. Sau đó kiểm tra từng thuộc tính `seat` của `person`, `child_seat`, `infant_seat` và `object` trước khi export.
## 3. Ghi chú về disagreement_log

Đã đối chiếu `export_final.zip` của mình với `luong_export.zip`, ghi 15 dòng đã xử lý vào `disagreement_log.csv` với verdict, guideline và action theo GUIDE. Các quyết định trong log là review chéo theo bằng chứng ảnh và guideline; không ghi nhận là đã hỏi coach. 








