# AGENTS.md - Operating Instructions

Operating instructions cho Bột trên dự án này. Xem SOUL.md cho bản sắc, IDENTITY.md cho chi tiết identity.

---

## 0. Boot Sequence

Mỗi session PHẢI đọc theo boot sequence 9 bước — xem `SOUL.md` §4. Tóm tắt: `SOUL.md` → `USER.md` → `IDENTITY.md` → `TOOLS.md` → `memory/<hôm-nay>.md` → `memory/<hôm-qua>.md` (nếu có) → `MEMORY.md` (chỉ MAIN SESSION) → `README.md` → `CHANGELOG.md`.

KHÔNG chỉ đọc AGENTS.md rồi thao tác luôn. Nếu có xung đột, ưu tiên: chỉ dẫn mới nhất của Sếp → SOUL.md → USER.md → IDENTITY.md → AGENTS.md → tài liệu dự án còn lại.

---

## 1. Code Scope

| Ưu tiên | Vị trí | Ghi chú |
|---------|--------|---------|
| Chính | `index.html` | copy + cấu trúc section |
| Chính | `assets/styles.css` | token màu/typography, responsive |
| Hạn chế | `assets/warm-dream-*.{png,svg}` | chỉ thay khi Sếp duyệt bộ asset mới |
| Hạn chế | `LICENSE` | chỉ Sếp đổi |
| Hạn chế | `CNAME` (chưa có) | chỉ Sếp thêm khi quyết định domain |
| Hạn chế | Thông tin pháp lý trong `index.html` §`#brand` | đối chiếu nguồn `masothue.com/3101159641` |
| Tài liệu | `README.md`, `CHANGELOG.md` | cập nhật khi cấu trúc/cơ chế đổi |

### Quy tắc biên tập nội dung

- Tiếng Việt là ngôn ngữ hiển thị mặc định cho mọi copy người dùng nhìn thấy; thuộc tính `lang="vi"` đã đặt đúng trong `<html>` của `index.html`.
- Số liệu pháp lý (MST, địa chỉ, người đại diện, ngày hoạt động, mã ngành) phải khớp nguồn `masothue.com/3101159641-cong-ty-tnhh-warmdream`; trước khi đổi, đọc file thật và xác nhận với Sếp.
- Không thêm framework, build step, hay dependencies runtime khi chưa có yêu cầu rõ.
- Token CSS trong `assets/styles.css` là nguồn sự thật về màu/typography/radius/shadow — KHÔNG hardcode giá trị ngoài token ở view mới.

---

## 2. Domain Knowledge

- Website giới thiệu Công ty TNHH WarmDream (MST 3101159641), MST cấp ngày 2026-08-24 tại 241 Trần Hưng Đạo, Phường Đồng Hới, Tỉnh Quảng Trị; người đại diện Trần Ngọc Đức.
- Ngành nghề chính: Sản xuất thảm, chăn, đệm (mã 1393). Ngoài ra đăng ký nhiều ngành phụ trợ (sợi, dệt, bán buôn, bán lẻ, thiết kế, v.v.).
- Kinh nghiệm kế thừa từ Công ty TNHH Điệp Xuân — đơn vị có tiền thân là cửa hàng Điệp Xuân tại Quảng Bình, hoạt động từ năm 1991.
- Triển khai GitHub Pages; repo `diepxuan/warmdream.org`; branch `main` (root). CNAME chưa cấu hình — Sếp sẽ bổ sung khi có kế hoạch domain riêng.
- Ba section người dùng nhìn thấy: hero (`#top`), định vị thương hiệu (`#brand`), liên hệ (`#contact`).
- Brand assets (logo, brand icon, favicon) dùng lại bộ nhận diện WarmDream hiện có từ `diepxuan/warmdream`.
- KHÔNG tự ý thêm form backend, CMS, danh mục sản phẩm; phần catalogue sẽ bổ sung ở bước tiếp theo khi có ảnh và dữ liệu sạch.

---

## 3. Git Discipline

- Remote: `https://github.com/diepxuan/warmdream.org.git`. Hosting build từ `main` (root). Branch tracked duy nhất: `main`; các branch phụ chỉ tạo khi cần cho task cụ thể và dọn sau khi merge/close.
- Mỗi task = 1 branch = 1 PR; KHÔNG commit thẳng lên `main`.
- Không tự push / tạo PR / merge; chỉ khi Sếp nói "push đi" / "Em tạo PR đi".
- Merge PR dùng `gh pr merge <N> --squash --delete-branch`, KHÔNG `git merge` local (trừ khi Sếp nói rõ cherry-pick / gộp branch / rebase local).

---

## 4. Task Completion Cycle

Khi nhận task, phải đi hết vòng đời:

1. **Đọc task + source** — `README.md`, `CHANGELOG.md`, file tương ứng
2. **Audit code** — xác định phần copy/structure/CSS bị ảnh hưởng
3. **Implement** — đúng scope, không tự ý thêm dependency hay build step
4. **Self-review** — preview local bằng `python3 -m http.server`, check responsive (mobile + desktop)
5. **Verification** — `python3 -m http.server 8080` mở local kiểm chứng; kiểm tra asset path đúng (relative path); kiểm tra link nav và CTA ngoài
6. **Review loop** — fix theo comment
7. **Documentation** — cập nhật `CHANGELOG.md` khi thay đổi release-worthy; cập nhật `README.md` khi cấu trúc/cơ chế đổi; cập nhật `MEMORY.md` khi rút ra bài học
8. **Báo cáo cuối** — bằng chứng cụ thể

### Guard rails

- Nếu thiếu dữ kiện: đọc source trước; nếu vẫn thiếu thì hỏi Sếp
- Khi gặp lỗi: dừng, phân tích nguyên nhân, không vá mù
- KHÔNG tự chạy các lệnh nhóm "Ghi cần xin phép" trong TOOLS.md (`git push`, `gh pr create/merge`, `rm -rf`, network ngoài hosting)
- Definition of Done: diff sạch, preview local pass, link/asset đúng, `CHANGELOG.md` cập nhật (nếu áp dụng)
- Workspace nằm ở `/data/warmdream-org/` — mọi thao tác ghi phải qua cơ chế escalation, xem TOOLS.md

---

## 5. Sub-Agents

- Gọi là **đệ**
- Mô tả rõ: mục tiêu, input, output, giới hạn quyền
- Đệ không được vượt quyền Bột, KHÔNG được tự push hay thay đổi nội dung thương hiệu
