---
name: canvas
description: Thao tác canvas Orauria đang mở trên web — đọc node, vùng chọn, tạo text, tạo luồng generate, nối node hoặc kích hoạt generate.
---

# Orauria Canvas

Bạn đang giúp user thao tác canvas web Orauria. Khi cần hiểu hoặc sửa canvas, ưu tiên dùng tool MCP `orauria-canvas` đã cấu hình; đừng bắt user copy JSON, URL hay token thủ công.

## Quy trình

- Nếu user chưa mở hoặc chưa kết nối canvas web, dùng skill `open-canvas` để mở Orauria Canvas; đừng yêu cầu copy URL/token thủ công.
- Trước khi thao tác, dùng `canvas_get_state` đọc canvas hiện tại; nếu user nhắc nội dung đang chọn, node hiện tại hoặc “cái này”, dùng `canvas_get_selection` trước.
- Tạo một nội dung text: ưu tiên `canvas_create_text_node`.
- Tạo nội dung generate: ưu tiên `canvas_generate_text`, `canvas_generate_image`, `canvas_generate_video`, `canvas_generate_audio`.
- Cần nối prompt, config và node generate thành luồng: dùng `canvas_create_generation_flow` hoặc tool luồng có sẵn.
- Batch thêm/xóa/sửa, di chuyển, nối node hoặc chỉnh viewport: dùng `canvas_apply_ops`.
- Không giả lập click chuột; không bắt user copy JSON.
- Thao tác ghi canvas sẽ được sidebar web xác nhận lần hai; tiếp tục theo kết quả tool hiện tại.

## Phong cách

- Văn bản trên trang và nội dung node canvas mặc định dùng tiếng Việt, trừ khi user yêu cầu ngôn ngữ khác.
- Node generate, config và prompt cần cấu trúc rõ, dễ chỉnh tiếp.
- Khi tạo nhiều node, chừa khoảng cách; đừng xếp chồng cùng một vị trí.
- Node media (ảnh/video/audio) giữ tỷ lệ gốc; chỉ đổi tỷ lệ khi user yêu cầu tự do biến dạng.
- Luồng generate càng gọn càng tốt, để user nhìn một phát hiểu quan hệ giữa các node.
