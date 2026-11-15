# Bản đồ Chu kỳ Kinh tế

Trang web tĩnh (một file `index.html`, không cần build), chia thành nhiều trang qua menu (định tuyến bằng `#hash`):

| Trang | Hash | Nội dung |
|---|---|---|
| Tổng quan | `#tong-quan` | Sơ đồ chu kỳ động, 3 loại chu kỳ, 7 bài học |
| Dòng thời gian | `#dong-thoi-gian` | 1700–2026 cho Mỹ, Anh, Đức, Pháp, Ý, Hà Lan, Nga, Nhật, Hàn, Đài Loan, Trung Quốc, Ấn Độ, Singapore, Thái Lan, Indonesia, Việt Nam; thêm các mốc công ty, khoa học kỹ thuật, dân số, khí hậu, vũ khí; nút “Phát lịch sử” |
| Bản đồ | `#ban-do` | Bản đồ thế giới (ECharts) tô màu theo pha của từng năm, chọn quốc gia (nhóm Châu Âu, Châu Á), nút phát, nút ◀ ▶ hoặc phím ← → để đi từng năm |
| Xu hướng dài hạn | `#xu-huong` | Tỷ trọng GDP thế giới 1700–2023, làn sóng công nghệ, dân số, CO₂, nhiệt độ, đầu đạn hạt nhân |
| Từng quốc gia | `#quoc-gia` | Hồ sơ (địa lý, địa chính trị, tôn giáo, nhân chủng, văn hóa), toàn bộ giai đoạn và bài học, nguồn Wikipedia cho từng giai đoạn |
| Việt Nam | `#viet-nam` | VN-Index, tỷ giá USD/VND, vàng SJC, các vòng sốt bất động sản, khủng hoảng trái phiếu 2022 |
| Việc làm tech | `#viec-lam-tech` | Tin tuyển lập trình viên so với mọi ngành, số người bị sa thải, vốn mạo hiểm và lãi suất Fed, nhân sự Big Tech, các đợt cắt giảm lớn, các chu kỳ việc làm tech 1995–2026, kỹ năng bị cắt và được giữ |
| Công cụ kế hoạch | `#ke-hoach` | Slider: thu nhập, chi tiêu, tăng lương, lạm phát, lợi suất, quỹ khẩn cấp, mô phỏng khủng hoảng, mua nhà |
| Cẩm nang | `#cam-nang` | Làm gì ở mỗi pha, 5 tín hiệu cần theo dõi, kế hoạch theo tuổi, checklist 90 ngày |
| Tài liệu | `#tai-lieu` | Video, sách, nguồn dữ liệu, bài viết; lọc theo loại và tìm kiếm |

Dòng thời gian và trang Từng quốc gia có thêm **kịch bản tương lai 2027–2040** (dải sọc chéo, bật tắt được), kèm kịch bản tốt, xấu và tín hiệu cần theo dõi. Dữ liệu ở `FUTURE`, `FUT_GLOBAL`, `SCENARIOS`; tài liệu ở `REFS`.

Thêm vào các trang:

- Tổng quan: “Hôm nay đang ở đâu?”, ảnh chụp tín hiệu Mỹ và Việt Nam có ghi ngày. Cập nhật ở `SNAPSHOT`.
- Xu hướng dài hạn: so sánh các cuộc khủng hoảng (mức giảm, thời gian phục hồi), dữ liệu ở `CRISES`.
- Cẩm nang: bảng tài sản theo từng pha, dữ liệu ở `HEAT`.
- Công cụ kế hoạch: “Kiểu khủng hoảng” chạy lại đường đi thật của VN-Index 2008, S&P 500 2008, Nikkei 1990…, dữ liệu ở `HIST`.

Link chia sẻ giữ đúng trạng thái: `#ban-do?y=2008&c=europe` (hoặc `c=uk,de,vn`), `#quoc-gia?c=vn`.

Thư viện ECharts 4.9.0 và bản đồ `world.js` nằm sẵn trong `vendor/` (không phụ thuộc CDN) và chỉ được tải khi mở trang Bản đồ. Ảnh xem trước khi chia sẻ: `og.png`.

SEO: `<html lang="vi">`, canonical, mô tả, JSON-LD (`WebSite`, `LearningResource`, `FAQPage`), `sitemap.xml`. Cho AI: `llms.txt` tóm tắt các dữ kiện chính (cập nhật khi đổi số liệu). `robots.txt` nằm ở gốc tên miền (repo `tiennhm.github.io`). Biểu tượng: `favicon.svg`, `favicon-32.png`, `apple-touch-icon.png`.

Trang được đăng bằng GitHub Pages từ nhánh `main`: https://tiennhm.io.vn/economic-cycles/

## Chạy

```bash
python -m http.server 5178
```

Mở http://localhost:5178.

## Sửa dữ liệu

- Dòng thời gian: mảng `COUNTRIES` và `GLOBAL` trong `index.html`. Mỗi pha là `[năm bắt đầu, năm kết thúc, loại, nhãn ngắn, tiêu đề, mô tả, bài học?]`.
- Slider: mảng `GROUPS`.
- Mô hình: hàm `simulate()`.

> Dữ liệu lịch sử là bản tóm tắt giản lược, năm và con số mang tính gần đúng. Mô hình tài chính chỉ để học, không phải tư vấn đầu tư.

Di chuột lên các thuật ngữ gạch chân chấm để xem giải thích (bảng `GLOSS_RAW`).
