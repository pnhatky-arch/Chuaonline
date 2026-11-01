# Chùa Sen Vàng Online

Không gian chiêm bái và hành lễ trực tuyến, tập trung vào Chánh điện Đức Phật A Di Đà. Giao diện được thiết kế lại theo bố cục gọn, tương thích máy tính và điện thoại.

## Chức năng chính
- **Dâng hương và đảnh lễ Tam Bái:** nhân vật Phật tử di chuyển lên Chánh điện và thực hiện nghi thức.
- **Thả hoa đăng:** ghi nhận lời nguyện và hiển thị đèn hoa đăng.
- **Thỉnh Đại Hồng Chung, gõ mõ:** phát hiệu ứng âm thanh và hình ảnh tương ứng.
- **Xin xăm / gieo quẻ:** hiển thị quẻ, bài thơ và lời bàn.
- **Dâng hoa sen:** ghi nhận nghi thức dâng lễ.
- **Thống kê công đức:** lưu số lượt hành lễ và bảng ghi nhận thí chủ.
- **Âm thanh:** nhạc nền, tiếng pháp khí và giọng đọc ZeroTTS tiếng Việt.

## Chạy hệ thống
Yêu cầu: Bun.js 1.1+, Python 3.10+ và uv.

```bash
bun install
uv venv .venv
uv pip install --python .venv/bin/python zerotts pillow
bun start
```

Mở `http://localhost:3000`.

## Cấu trúc
- `server.js`: HTTP server, WebSocket và JSON-RPC cho các nghi thức.
- `public/index.html`: giao diện chính.
- `public/css/live.css`: giao diện responsive.
- `public/js/live.js`: điều phối hoạt ảnh và nghi thức.
- `public/js/audio.js`: nhạc nền, âm thanh pháp khí và hàng đợi giọng đọc.
- `public/js/particles.js`: khói hương, hoa sen và hiệu ứng ánh sáng.
- `tts_worker.py`: dịch vụ tổng hợp giọng đọc ZeroTTS.
- `data/`: dữ liệu công đức và bộ đệm âm thanh được tạo khi chạy.

## JSON-RPC
HTTP: `POST /rpc`; WebSocket: `/ws`.

Các phương thức: `temple.getState`, `temple.burnIncense`, `temple.sendPrayer`, `temple.strikeWoodenFish`, `temple.ringBell`, `temple.drawFortune`, `temple.offerGift`, `temple.grandCeremony`, `temple.updateSettings`, `temple.resetMerit` và `temple.speak`.

Dữ liệu công đức được lưu trong `data/merit-state.json`. Giá trị mặc định bắt đầu từ 0; hệ thống không tạo số liệu người tham gia giả lập.
