# Thả Diều Đón Noel · Kite Coffee & Souvenirs

Bản demo mini-game Giáng sinh 2026 cho chuỗi Kite Coffee & Souvenirs. Mỗi ván kéo dài 45 giây: người chơi lái cánh diều logo Kite bay qua đêm Noel Hà Nội, hứng các món trong menu và hộp quà, né mây giông và cục than. Điểm đạt được quy đổi ra voucher.

## Chạy thử

Không cần build: mở trực tiếp `index.html` trên trình duyệt, hoặc chạy:

```bash
python3 -m http.server 8765
# rồi mở http://127.0.0.1:8765
```

Game tối ưu cho điện thoại (dọc). Trên máy tính có thể dùng chuột hoặc phím ← → / A D, phím P để tạm dừng.

## Cơ chế

| Vật phẩm | Hiệu ứng |
|---|---|
| Cà phê muối, Bạc xỉu cốt dừa | +10 điểm |
| Matcha kem mặn | +15 điểm |
| Cascara chanh vàng | +20 điểm |
| Hộp quà Noel | +30 điểm |
| Sao may mắn | x2 điểm trong 6 giây |
| Phin cà phê | +3 giây |
| Mây giông, cục than | −5 giây, mất combo |

Hứng liên tục để giữ combo: mỗi combo cộng thêm 5% điểm, tối đa gấp đôi.

**Quà theo mốc điểm (ai chơi cũng có quà):**

| Điểm | Hạng | Quà |
|---|---|---|
| 0+ | Bông Tuyết | Giảm 10% một đồ uống |
| 300+ | Ngôi Sao | Nâng size miễn phí + kem mặn |
| 600+ | Cánh Diều | Giảm 25.000đ cho hoá đơn từ 99.000đ |
| 1000+ | Diều Vàng | Mua 1 tặng 1 + phiếu bốc thăm cốc gốm Đông Hồ |

**Lượt chơi:** 3 lượt miễn phí mỗi ngày, +1 lượt cho mỗi hoá đơn (quét QR), +1 lượt khi chia sẻ (1 lần/ngày). Mỗi số điện thoại nhận tối đa 1 voucher mỗi ngày, giữ hạng cao nhất.

## Giới hạn của bản demo

- Tất cả dữ liệu (lượt chơi, điểm, voucher) chỉ lưu trong `localStorage` của trình duyệt, không gửi đi đâu.
- Bảng xếp hạng dùng tên mẫu. Mã voucher và QR chỉ để minh hoạ.
- Nút "quét QR hoá đơn" chỉ giả lập.
- Mốc điểm, quà và câu chữ là đề xuất, cần Kite duyệt.

## Việc cần làm để chạy thật

1. **Backend:** cấp lượt chơi, kiểm tra điểm phía server (chống gian lận), cấp và đối soát voucher tại POS.
2. **Đăng nhập & CRM:** xác thực bằng OTP số điện thoại hoặc Zalo, gắn với Zalo OA của Kite. Có thể đóng gói thành Zalo Mini App.
3. **QR hoá đơn / tay cầm ly** để cộng lượt.
4. **Pháp lý:** phần bốc thăm quà lớn là khuyến mại mang tính may rủi, phải đăng ký với Sở Công Thương (một tỉnh) hoặc Bộ Công Thương (nhiều tỉnh) theo Nghị định 81/2018 và Nghị định 239/2026. Nộp hồ sơ trước khi chạy 2–3 tuần.

## Công nghệ

Một file HTML duy nhất: HTML5 Canvas, JavaScript thuần, WebAudio cho âm thanh. Font Glory lấy từ Google Fonts. Không có dependency.
