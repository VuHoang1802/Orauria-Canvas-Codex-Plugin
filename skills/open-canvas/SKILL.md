---
name: open-canvas
description: Mở Orauria Canvas online hoặc local, rồi tự kết nối local Canvas Agent. Dùng khi user yêu cầu mở, khởi chạy, vào hoặc dùng canvas Orauria.
---

# Mở Orauria Canvas

Mặc định mở bản online (`https://canvas.orauria.com`). Chỉ khởi động frontend local khi user yêu cầu rõ ràng dùng dự án local.

## Bản online

1. Khởi động local Canvas Agent và giữ terminal chạy:

```bash
npx -y @basketikun/canvas-agent@latest
```

2. Lấy `Local URL` và `Connect token` từ output khởi động.

3. Mở trong trình duyệt bên phải Codex:

```text
https://canvas.orauria.com/canvas?mode=new#agentUrl=<Local URL>&agentToken=<Connect token>
```

## Bản local

1. Trong repo Orauria Canvas, khởi động frontend và dùng địa chỉ `Local` của Vite:

```bash
cd web
npm install
npm run dev
```

2. Khởi động local Canvas Agent:

```bash
npx -y @basketikun/canvas-agent@latest
```

3. Lấy `Local URL` và `Connect token`, mở:

```text
<Vite Local URL>/canvas?mode=new#agentUrl=<Local URL>&agentToken=<Connect token>
```

## MCP và địa chỉ kết nối

Khi task Codex mới load plugin, sẽ tự chạy `npx -y @basketikun/canvas-agent@latest mcp`. Process MCP này chỉ cung cấp tool canvas, không cung cấp dịch vụ kết nối web.

Process Canvas Agent thường (không có `mcp`) cung cấp `Local URL` và `Connect token`. Hai process đọc cùng cấu hình local nên không cần user dán địa chỉ/token thủ công.

## Chế độ mở

Khi user không chỉ định, luôn dùng `mode=new` để tạo canvas mới. Chỉ đổi khi user yêu cầu rõ:

- Canvas gần đây: `mode=recent`
- Tự chọn: `mode=choose`
