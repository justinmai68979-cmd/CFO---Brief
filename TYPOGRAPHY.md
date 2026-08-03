# Chuẩn chữ nghĩa — CFO Morning Brief

`style.css` là bản CSS chuẩn. Mỗi ấn bản hàng ngày PHẢI dùng lại nguyên khối
`<style>` của `index.html` hiện hành (đồng nhất với file này), không tự viết CSS mới.

## Font
- Serif (tiêu đề + văn xuôi): `"Noto Serif", Cambria, "Palatino Linotype", "Times New Roman", Times, serif`
  — KHÔNG dùng Georgia: thiếu glyph tiếng Việt, chữ có dấu bị rơi font giữa dòng.
- Sans (bảng biểu, nhãn, chú thích): `system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif`

## Thang cỡ chữ (chỉ dùng 9 bậc này, qua biến CSS)
11 (--t-micro, nhãn chữ hoa) · 12 (--t-xs) · 13 (--t-sm, bảng) · 15 (--t-base)
· 17 (--t-body, văn xuôi) · 19 (--t-h4) · 22 (--t-h3) · 26 (--t-h2)
· headline: clamp(25px,3.2vw,34px) · măng-sét: clamp(32px,5.6vw,50px)

## Thang khoảng cách
4 · 8 · 12 · 16 · 24 · 32 · 44 (--sp1..--sp7). Không dùng giá trị lẻ ngoài thang.

## Nhịp dòng
văn xuôi 1.62 · tiêu đề 1.28 · bảng/UI 1.5 · nhãn 1.4

## Nhãn chữ hoa
Chỉ một công thức: sans, 700, letter-spacing .08em, cỡ 11px.

## Quy tắc
- Không đặt style inline. Mọi thành phần dùng class có sẵn.
- Số liệu: `font-variant-numeric: tabular-nums`.
- Màu không đứng một mình: Impact luôn có chấm màu + nhãn chữ.
