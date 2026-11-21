# Tự đánh giá — Dương Mạnh Huy · G01

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb, S01_ir | `infant_seat.facing` (`rear_right`) | `guess` | Lúc đầu ghi `front` do suy luận sai hướng nôi; xem lại thì đầu nôi hướng về camera nên là `rear` | Có (trước `export_final.zip`) |
| S04_rgb, S04_ir | `face` của người lớn ở `rear_middle` | `extra` | Đã vẽ box `face` dù tóc che gần hết mặt, không thấy mắt và mũi; GUIDE 4.5 nói trường hợp này không vẽ | Có (trước `export_final.zip`) |
| D04 | `face13` mắt trái + `hand` trái | `flag`, `box` | Đổi `eye_left = open` nhưng quên tắt cờ `occluded` ở 4 điểm `left_eye_*` (cabin_check WARN); box tay trái lệch sang cẳng tay | Có: cờ sửa trước `export_final.zip`, box sửa ở `export_final_v2.zip` |
| D06 | `hand` trái | `missing` | Bàn tay trái đưa sát camera bị cháy sáng, mình tưởng là tay áo nên không vẽ; review chéo mới phát hiện | Có (`export_final_v2.zip`) |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: đánh cờ điểm `face13` (`flag`) không khớp với cái thấy. Lỗi này lặp ở 3 khung D##: miệng D01 và D04, mũi D02 bị đánh `occluded` dù không có gì che; ngược lại mắt trái D04 đã thấy rõ (`open`) mà 4 điểm vẫn để `occluded`.

Vì sao mình mắc: mình dùng cờ `occluded` theo nghĩa "mình không chắc vị trí điểm" thay vì "điểm bị vật khác che". Khi đổi thuộc tính mắt trên box `face`, mình quên đổi cờ của các điểm đi kèm.

Lần sau tránh bằng cách: với từng điểm, tự hỏi "có vật gì đang che điểm này không?" (tay, chai, đốm phản xạ, tròng kính tối, chính khuôn mặt khi quay đi). Có thì `occluded` hoặc `outside`, không có thì tắt cờ. Mỗi lần đổi `eye_*` thì kiểm lại ngay 4 điểm mắt cùng bên. Chạy `cabin_check` sau mỗi khung D## vì script bắt được mâu thuẫn giữa `eye_*` và cờ điểm.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: dòng `D06.png | hand | box | chỉ có ở peer`. Phạm Minh Quân vẽ thêm bàn tay trái mà mình bỏ sót vì vùng đó bị cháy sáng trắng trên ảnh NIR. Mình học được rằng vùng bão hòa trên ảnh IR thật vẫn có thể là một vật cần gán: phải xem ở độ sáng gốc (không tăng Brightness) để thấy đường viền ngón tay, và không coi khối trắng là nền hay tay áo.
