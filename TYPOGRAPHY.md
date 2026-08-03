# Chuẩn chữ & màu — CFO Morning Brief

`style.css` là bản CSS chuẩn. Mỗi ấn bản hàng ngày PHẢI dùng lại nguyên khối
`<style>` của `index.html` hiện hành (đồng nhất với file này), không tự viết CSS mới.

## Giao diện: CHỈ NỀN SÁNG
Bản tin không có dark mode. Không thêm `:root[data-theme="dark"]`, không thêm
`@media (prefers-color-scheme: dark)`, không thêm nút đổi nền. `:root` khai báo
`color-scheme: light only` để trình duyệt/hệ điều hành không tự đảo màu.

## Font
- Serif (tiêu đề + văn xuôi): `"Noto Serif", Cambria, "Palatino Linotype", "Times New Roman", Times, serif`
  — KHÔNG dùng font thiếu glyph tiếng Việt: chữ có dấu bị rơi font giữa dòng.
  Quy tắc này áp dụng cả cho thuộc tính `font-family` bên trong `<svg>`.
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

## Bảng màu (theo lối The Guardian)

| Biến | Mã | Dùng ở đâu |
|---|---|---|
| `--brand` | #052962 | măng-sét, tiêu đề bảng, tab đang mở, chân trang |
| `--accent` | #c70000 | kicker, tin xếp hạng 1–3, số thứ tự câu hỏi, chiều xấu |
| `--hl` | #ffe500 | bút dạ đánh dấu, viền trích dẫn, khối CFO Action |
| `--down-good` | #077a3c | chiều tốt |
| `--c1..--c6` | 6 màu | dải màu đầu mỗi section, luân phiên tự động |
| `--paper` / `--surface` | #f6f6f4 / #fff | nền trang / nền thẻ |

Section tự đổi màu theo thứ tự nhờ `section.sec:nth-of-type(6n+k)` — không cần
thêm class. `.feat`, `.gcard`, `.next > div` cũng tự nhận màu theo vị trí.

## Class đánh dấu điểm nhấn (dùng có chọn lọc)

- `.hl` — bút dạ vàng cho **con số/cụm từ quyết định**. Tối đa 4–6 lần mỗi tab;
  bôi vàng khắp nơi thì không còn là điểm nhấn.
- `.badge` + `.crit` (đỏ, tin nóng) / `.new` (xanh, chính sách mới) /
  `.watch` (hổ phách, cần theo dõi) / `.ok` (xanh lá, cơ hội) / `.mark` (vàng, làm ngay).
- `.dev.key` — tô nền vàng nhạt cho DÒNG TIN QUAN TRỌNG NHẤT trong Top 7 (chỉ 1 dòng).
- `.dev[data-p]` — hạng 1–3 tự có vạch đỏ bên trái, hạng 4–5 vạch xanh.
- `tr.key` — tô vàng nhạt một dòng bảng cần chú ý.
- `.tag` + `.rev` / `.risk` / `.cash` / `.fx` — nhãn Financial Impact có màu riêng.
- `.card.accent` — thêm vạch màu section trên đầu thẻ.

## Hiệu ứng
Nhẹ và có mục đích, không phô trương: thẻ nhấc nhẹ khi rê chuột, gạch chân tab
chạy ngang, tab và accordion hiện dần, dòng bảng đổi nền khi rê, các section hiện
dần khi cuộn tới (`.reveal` + IntersectionObserver). Toàn bộ tự tắt khi người đọc
bật "giảm chuyển động" (`prefers-reduced-motion`).

## Quy tắc
- Không đặt style inline. Mọi thành phần dùng class có sẵn.
- Số liệu: `font-variant-numeric: tabular-nums`.
- Màu không đứng một mình: Impact luôn có chấm màu + nhãn chữ; badge luôn có chữ.
- SVG tự vẽ dùng đúng mã màu trong bảng trên, có `aria-label`.
