# Bản đồ Chu kỳ Kinh tế

Trang web tĩnh (một file `index.html`, không cần build), chia thành nhiều trang qua menu (định tuyến bằng `#hash`):

| Trang | Hash | Nội dung |
|---|---|---|
| Tổng quan | `#tong-quan` | Sơ đồ chu kỳ động, 3 loại chu kỳ, 7 bài học |
| Dòng thời gian | `#dong-thoi-gian` | So sánh 1945–2026 cho Mỹ, châu Âu, Nhật, Hàn, Đài Loan, Trung Quốc, Singapore, Thái Lan và Việt Nam; nút “Phát lịch sử” |
| Bản đồ | `#ban-do` | Bản đồ thế giới (ECharts) tô màu theo pha của từng năm, có nút phát |
| Từng quốc gia | `#quoc-gia` | Toàn bộ giai đoạn và bài học của một nước |
| Công cụ kế hoạch | `#ke-hoach` | Slider: thu nhập, chi tiêu, tăng lương, lạm phát, lợi suất, quỹ khẩn cấp, mô phỏng khủng hoảng, mua nhà |
| Cẩm nang | `#cam-nang` | Làm gì ở mỗi pha, 5 tín hiệu cần theo dõi, kế hoạch theo tuổi, checklist 90 ngày |

Thư viện ngoài: ECharts 4.9.0 và bản đồ `world.js` từ jsDelivr (cần mạng).

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
