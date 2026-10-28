# skepfield-site

Trang giới thiệu tĩnh của **Skepfield**, game logic tổ ong cho iPhone (repo game: `skepfield`). Chữ trên trang là
tiếng Anh. Địa chỉ: https://nguyenvanlamm.github.io/skepfield-site/

- `index.html`: trang chính (một file, CSS nội tuyến, không JS). Font Alegreya 800 và Alegreya Sans 400/500/700/800
  tự host trong `assets/fonts/` (bộ ký tự latin, file woff2 lấy từ Google Fonts, giấy phép SIL OFL 1.1 kèm theo), nên
  trang không gửi request nào tới máy chủ bên thứ ba.
- `privacy.html`: chính sách quyền riêng tư (Privacy Policy URL cho App Store Connect).
- `support.html`: trang hỗ trợ (Support URL cho App Store Connect).
- `404.html`: trang lỗi (noindex, link tuyệt đối `/skepfield-site/...` vì GitHub Pages trả nó ở mọi đường dẫn sai).
- `assets/`: ảnh màn hình thật của game (WebP, `home.webp` cắt bỏ phần có giá), `share-card.jpg` (1200×630, ảnh
  Open Graph/Twitter của cả ba trang), `og-game.png` (ảnh màn chơi gốc dùng để dựng share card), `logo-mark.svg`.
  `favicon.svg` và `apple-touch-icon.png` (180 px, từ `icon-1024.png`) nằm ở gốc.
- SEO và bot AI: `sitemap.xml`, `llms.txt`, JSON-LD (`VideoGame` + `MobileApplication`, không có `offers` hay rating
  vì game chưa phát hành) trong `index.html`, `WebPage`/`ContactPage` trong hai trang kia. `robots.txt` ở đây chỉ để
  ghi lại chính sách: crawler chỉ đọc `https://nguyenvanlamm.github.io/robots.txt` (repo `nguyenvanlamm.github.io`),
  nơi phải có dòng `Sitemap: https://nguyenvanlamm.github.io/skepfield-site/sitemap.xml`. Báo cáo kiểm tra nằm trong
  `.reports/` (Jekyll không xuất bản thư mục bắt đầu bằng dấu chấm).

Chưa có trên App Store: trang ghi "Coming soon to the App Store", không có link hay badge, không ghi giá. Khi game lên
store thì thêm link App Store vào `index.html` và `support.html`, thêm `offers` vào JSON-LD và cập nhật `llms.txt`.

GitHub Pages phục vụ nhánh `main`, thư mục `/` (gốc repo). Không có build, không có GitHub Actions.
