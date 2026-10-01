# Công ty TNHH WarmDream

Website giới thiệu Công ty TNHH WarmDream — đơn vị sản xuất chăn ga gối đệm kế thừa kinh nghiệm Công ty TNHH Điệp Xuân từ năm 1991. Repo chứa bản website tĩnh, tối ưu cho GitHub Pages hoặc static hosting.

## Về Công ty TNHH WarmDream

Công ty TNHH WarmDream (MST 3101159641) hoạt động trong ngành sản xuất thảm, chăn, đệm — mã ngành 1393 theo hệ thống ngành kinh tế Việt Nam. Công ty được đăng ký hoạt động tại 241 Trần Hưng Đạo, Phường Đồng Hới, Tỉnh Quảng Trị; người đại diện pháp luật là Trần Ngọc Đức.

Thương hiệu WarmDream hiện thuộc sở hữu của Công ty TNHH Điệp Xuân — đơn vị có tiền thân là cửa hàng Điệp Xuân, hoạt động trong lĩnh vực chăn ga gối đệm và nội thất phòng ngủ tại Quảng Bình từ năm 1991. Trong tương lai, nhãn hiệu WarmDream sẽ được chuyển nhượng cho Công ty TNHH WarmDream để chuẩn hoá đơn vị vận hành.

Thông tin tham khảo:

- Hồ sơ pháp lý trên [masothue.com/3101159641](https://masothue.com/3101159641-cong-ty-tnhh-warmdream)
- Website Công ty TNHH Điệp Xuân: [diepxuan.com](https://www.diepxuan.com/)
- Trang thương hiệu WarmDream trên Điệp Xuân: [diepxuan.com/warmdream.html](https://www.diepxuan.com/warmdream.html)

## Mục đích

Trang này dùng để giới thiệu Công ty TNHH WarmDream, trình bày hồ sơ pháp lý, ngành nghề hoạt động và liên hệ qua hệ thống Điệp Xuân trong giai đoạn chuyển nhượng nhãn hiệu.

## Cách sử dụng

Mở trực tiếp file:

```bash
open index.html
```

Hoặc chạy static server đơn giản:

```bash
python3 -m http.server 8080
```

Sau đó truy cập:

```text
http://localhost:8080
```

## Cấu trúc file

```text
.
├── index.html                              # Nội dung landing page
├── assets/
│   ├── styles.css                          # Giao diện và responsive layout
│   ├── warm-dream-logo.png                 # Logo chữ Warm Dream
│   ├── warm-dream-brand.png                # Biểu tượng thương hiệu dự phòng
│   ├── warm-dream-brand.svg                # Brand icon dùng trong header
│   └── warm-dream-favicon.svg              # Favicon
├── LICENSE
├── CHANGELOG.md
└── README.md
```

## Hồ sơ pháp lý

Thông tin pháp lý của Công ty TNHH WarmDream lấy từ nguồn [masothue.com/3101159641](https://masothue.com/3101159641-cong-ty-tnhh-warmdream):

| Trường | Giá trị |
|--------|---------|
| Tên đầy đủ | CÔNG TY TNHH WARMDREAM |
| Tên quốc tế | WARMDREAM COMPANY LIMITED |
| Tên viết tắt | WARMDREAM CO., LTD |
| Mã số thuế | 3101159641 |
| Ngày hoạt động | 2026-08-24 |
| Loại hình | Công ty TNHH 2 thành viên trở lên |
| Người đại diện | Trần Ngọc Đức |
| Địa chỉ | 241 Trần Hưng Đạo, Phường Đồng Hới, Tỉnh Quảng Trị |
| Cơ quan thuế | Thuế cơ sở 1 tỉnh Quảng Trị |
| Ngành chính | Sản xuất thảm, chăn, đệm (mã 1393) |

Trước khi đổi bất kỳ trường nào, đối chiếu nguồn gốc và xác nhận với Sếp.

## Dependencies

Không có dependency runtime. Trang dùng HTML và CSS thuần.

## Triển khai GitHub Pages

Với repo `diepxuan/warmdream.org`, URL GitHub Pages mặc định sẽ là:

```text
https://diepxuan.github.io/warmdream.org/
```

Cách bật:

1. Vào `Settings` của repo.
2. Chọn `Pages`.
3. Source: `Deploy from a branch`.
4. Branch: `main`.
5. Folder: `/ root`.
6. Save và chờ GitHub build.

Custom domain (CNAME) hiện chưa cấu hình; Sếp sẽ bổ sung sau khi có kế hoạch domain riêng.

## Tùy chỉnh nội dung

Các phần cần chỉnh trong `index.html`:

- Nội dung hero thương hiệu tại section `#top`
- Hồ sơ pháp lý tại section `#brand`
- Lịch sử nhãn hiệu tại section `#trademark`
- Liên hệ tại section `#contact`

## Quyết định thiết kế

- Dùng HTML/CSS thuần để triển khai nhanh, dễ host trên GitHub Pages.
- Không dùng framework để giảm độ phức tạp và tránh build step.
- Thiết kế responsive theo hướng mobile-first fallback.
- Màu sắc lấy theo nhận diện WarmDream (nâu/xanh), phù hợp sản phẩm phòng ngủ.
- Token CSS trong `assets/styles.css` là nguồn sự thật; KHÔNG hardcode giá trị ngoài token ở view mới.

## Trade-offs

- Không có CMS, chỉnh nội dung bằng code.
- Không có form backend; CTA hiện dùng link ngoài tới `diepxuan.com`.
- Bước hiện tại tập trung vào landing pháp lý + giới thiệu; phần catalogue sản phẩm sẽ bổ sung ở bước tiếp theo khi có ảnh và dữ liệu sạch.
- Thương hiệu WarmDream hiện thuộc Điệp Xuân; nhãn hiệu sẽ chuyển nhượng cho WarmDream trong tương lai — site sẽ cập nhật khi hoàn tất.

## Troubleshooting

### Trang không hiện trên GitHub Pages

Kiểm tra:

- Repo đã bật Pages chưa.
- Branch Pages có đúng `main` không.
- Folder có đúng `/ root` không.
- File `index.html` nằm ở root repo chưa.

### CSS không load

Kiểm tra file `assets/styles.css` có tồn tại và đường dẫn trong `index.html` là:

```html
<link rel="stylesheet" href="assets/styles.css">
```
