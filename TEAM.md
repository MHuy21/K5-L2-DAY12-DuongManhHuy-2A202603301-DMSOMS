# TEAM — Ngày 12

Mã bộ ảnh: **G01** · Hình thức: cá nhân

| Họ tên         | MSSV        | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
| -------------- | ----------- | ----------------- | --------------------------- | ----------------------------- |
| Dương Mạnh Huy | 2A202603301 | có                | Phạm Minh Quân (G01)        | 74/74                         |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- G01 D03 · `face.gaze_zone` (tài xế cúi nhìn khóa dây an toàn ở hông): mình `center`, Quân `cluster`; đề xuất `lap` hoặc `other`.
- G01 S03_rgb / S03_ir · `object.type` ở ghế `rear_middle` (vật mềm, phẳng, có dây đeo): mình `other`, Quân `bag`.
- (Đã hỏi coach trước đó) G01 S02, S03, S05, S07, S08 có trẻ em ngồi trong ghế trẻ em / ghế em bé: coach hướng dẫn không gán trẻ em và cái ghế đó, người và đồ vật vẫn gán bình thường.

## Cá nhân

### DuongManhHuy-2A202603301

- Phần mình làm (ngoài 22 ảnh của mình): review chéo với Phạm Minh Quân (diff 74 dòng: 51 mình đúng, 16 Quân đúng, 4 cả hai sai, 3 mơ hồ); sửa 20 điểm trên bản của mình thành `export_final_v2.zip`.
- Điều mình học được hôm nay: gán nhãn cabin phải theo hệ quy chiếu của xe và của người (ghế gọi theo xe, mắt và tay gọi theo người, kể cả khi ảnh xoay 90°), và "không thấy thì `unknown`" quan trọng hơn cố đoán cho đủ. Ảnh IR thật có những hiện tượng IR mô phỏng không có (đốm phản xạ LED trên kính, vật sát camera bị cháy sáng); review chéo giúp mình phát hiện bàn tay bị bỏ sót ở D06.
