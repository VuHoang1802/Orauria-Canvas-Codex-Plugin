# Orauria Canvas — Codex Plugin

Plugin Codex để mở và thao tác [Orauria Canvas](https://canvas.orauria.com).

## Yêu cầu

- [Codex app](https://openai.com/codex/) đã đăng nhập
- [Node.js](https://nodejs.org/) ≥ 18 (để `npx` chạy local Canvas Agent)

## Cài một lần

### Windows (PowerShell)

Nếu lệnh `codex` chưa có trong PATH (Codex app Store):

```powershell
$codex = Get-ChildItem "$env:LOCALAPPDATA\OpenAI\Codex\bin" -Recurse -Filter "codex.exe" |
  Sort-Object LastWriteTime -Descending |
  Select-Object -First 1 -ExpandProperty FullName

& $codex plugin marketplace add VuHoang1802/Orauria-Canvas-Codex-Plugin
& $codex plugin add orauria-canvas@orauria-canvas
```

Nếu đã có CLI `codex` trong PATH:

```powershell
codex plugin marketplace add VuHoang1802/Orauria-Canvas-Codex-Plugin
codex plugin add orauria-canvas@orauria-canvas
```

### macOS / Linux

```bash
codex plugin marketplace add VuHoang1802/Orauria-Canvas-Codex-Plugin
codex plugin add orauria-canvas@orauria-canvas
```

## Dùng

1. Mở Codex → tạo **task mới**
2. Nói: `Mở Orauria Canvas và kết nối Agent`
3. Plugin sẽ khởi động local Agent và mở `https://canvas.orauria.com`

## Gỡ

```bash
codex plugin remove orauria-canvas
codex mcp remove orauria-canvas
```

## Lưu ý

- Đây là **marketplace Git tùy chỉnh**, không phải mục trong OpenAI Plugin Directory chính thức.
- Cài plugin sẽ đăng ký MCP `orauria-canvas` (tốn thêm token context). Chỉ cần Agent không qua Codex thì chạy:

```bash
npx -y @basketikun/canvas-agent@latest
```

rồi dán Local URL + Connect token trên web.
