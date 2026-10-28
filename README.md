# skepfield-site

Trang giới thiệu tĩnh của **Skepfield**, game logic tổ ong cho iPhone (repo game: `skepfield`). Chữ trên trang là
tiếng Anh. Địa chỉ: https://nguyenvanlamm.github.io/skepfield-site/

- `index.html`: trang chính (một file, CSS nội tuyến, không JS, font Alegreya qua Google Fonts).
- `privacy.html`: chính sách quyền riêng tư (Privacy Policy URL cho App Store Connect).
- `support.html`: trang hỗ trợ (Support URL cho App Store Connect).
- `assets/`: ảnh màn hình thật của game (WebP, `home.webp` cắt bỏ phần có giá), `og-game.png` cho Open Graph,
  `logo-mark.svg`. `favicon.svg` và `apple-touch-icon.png` (180 px, từ `icon-1024.png`) nằm ở gốc.

Chưa có trên App Store: trang ghi "Coming soon to the App Store", không có link hay badge, không ghi giá. Khi game lên
store thì thêm link App Store vào `index.html` và `support.html`.

GitHub Pages phục vụ nhánh `main`, thư mục `/` (gốc repo). Không có build, không có GitHub Actions.
