# Long-term Memory

Memory dài hạn cho Bột trên dự án này. Mỗi entry khi có thay đổi cơ chế, sự cố hay bài học đều ghi vào đây. Đọc MEMORY.md trước mọi task lớn để không lặp lại lỗi cũ.

Cập nhật lần cuối: 2026-10-02 — bootstrap instruction files + xây dựng landing page Công ty TNHH WarmDream.

---

## 0. Quy tắc cố định (không theo task, theo SOUL.md/AGENTS.md/TOOLS.md)

- Dự án là static HTML/CSS thuần — KHÔNG thêm framework, build step, dependencies runtime khi chưa được Sếp duyệt.
- Số liệu pháp lý (MST 3101159641, địa chỉ, người đại diện, ngày hoạt động, mã ngành) khớp nguồn `masothue.com/3101159641-cong-ty-tnhh-warmdream`. KHÔNG bịa.
- Token CSS trong `assets/styles.css` là nguồn sự thật; KHÔNG hardcode giá trị ngoài token ở view mới.
- Brand assets (`assets/warm-dream-*.{png,svg}`) dùng lại bộ từ `diepxuan/warmdream`; chỉ thay khi Sếp phê duyệt asset mới.
- Workspace root `/data/warmdream-org/`; remote `https://github.com/diepxuan/warmdream.org.git`, branch `main`; mỗi task = 1 branch = 1 PR, không commit thẳng `main`, không tự push/PR/merge.
- CNAME chưa cấu hình; không tự tạo file CNAME — chờ Sếp.

---

## 1. Nhật ký thay đổi

### Khởi tạo bộ 8 file instruction

- Sếp yêu cầu dựa trên cấu trúc `warmdream` (đã có bộ 8 file instruction hoàn chỉnh) để tạo bộ file tương ứng cho dự án này.
- Template generic, giữ persona Bột dùng chung Portal / dsh-zero-trust / warmdream / everon.
- Phần project-specific đặt placeholder `[FILL: ...]` để Sếp hoặc agent riêng từng dự án bổ sung sau.
- 8 file: SOUL.md, USER.md, IDENTITY.md, TOOLS.md, AGENTS.md, MEMORY.md, HEARTBEAT.md, CLAUDE.md.

---

## 2. Tasks done

### 2026-10-02 — Bootstrap PR #1 (merged)

- Tạo branch `codex/bootstrap-instruction-files` từ `main`, push + mở PR #1.
- Nội dung: 8 file instruction mới (AGENTS, CLAUDE, HEARTBEAT, IDENTITY, MEMORY, SOUL, TOOLS, USER) — 452 dòng, 0 xóa.
- Không động `LICENSE` và `README.md`.
- PR URL: https://github.com/diepxuan/warmdream.org/pull/1
- Trạng thái: MERGED vào main lúc 2026-10-01T17:28:13Z (squash, merge commit `b319a15`).
- Branch `codex/bootstrap-instruction-files` đã xóa trên remote.

### 2026-10-02 — Xây dựng landing page Công ty TNHH WarmDream (PR #3)

- Review thương hiệu WDR tại `/data/warmdream` (CNAME `warmdream.diepxuan.com`, repo `diepxuan/warmdream`).
- Xây dựng website tĩnh về Công ty TNHH WarmDream (pháp nhân riêng, thuộc sở hữu Sếp), workspace `/data/warmdream-org`, repo `diepxuan/warmdream.org`.
- Thông tin pháp lý lấy từ nguồn `masothue.com/3101159641`:
  - Tên: CÔNG TY TNHH WARMDREAM
  - MST: 3101159641
  - Địa chỉ: 241 Trần Hưng Đạo, Phường Đồng Hới, Tỉnh Quảng Trị
  - Người đại diện: Trần Ngọc Đức
  - Ngày hoạt động: 2026-08-24
  - Loại hình: Công ty TNHH 2 thành viên trở lên
  - Ngành chính: Sản xuất thảm, chăn, đệm (mã 1393)
- Files thêm mới: `index.html`, `assets/styles.css`, `assets/warm-dream-{logo,brand,favicon}.{png,svg}`, `LICENSE`, `CHANGELOG.md`, `README.md` (đã thay từ placeholder 1 dòng sang README đầy đủ).
- Files cập nhật: `AGENTS.md`, `IDENTITY.md`, `TOOLS.md` (điền placeholder project-specific).
- 4 sections: `#top` (hero + stats + brand card) / `#brand` (định vị + hồ sơ pháp lý) / `#contact` (CTA Điệp Xuân).
- KHÔNG tạo CNAME (Sếp chưa cấu hình).
- Branch: `feat/warmdream-static-site`.

---

## 3. Bài học rút ra

### 3.1 Khi web_search fail, dùng web_fetch với URL cụ thể

- `web_search` (DeepSeek) có thể fail với API key invalid; lúc đó dùng `web_fetch` với URL cụ thể từ masothue.com, diepxuan.com hoặc nguồn sếp cung cấp.
- Bài học: nếu Sếp nói "em tự tìm kiếm" mà web_search fail, hỏi Sếp cung cấp URL cụ thể thay vì tự nghĩ ra số liệu.

### 3.2 File write yêu cầu đọc file hiện có trước

- Với file đã tồn tại, tool write đòi đọc file trong cùng turn trước khi overwrite.
- Bài học: nếu đã đọc ở turn trước, vẫn cần đọc lại (limit 1–5 dòng là đủ) trong turn sẽ ghi.

---

## 4. Backlog / Open questions

### 4.1 Bật GitHub Pages

- Sếp cần bật Pages cho repo `diepxuan/warmdream.org` (Settings → Pages → Source: main / root).
- Sau khi bật, kiểm chứng tại `https://diepxuan.github.io/warmdream.org/`.

### 4.2 CNAME

- Sếp sẽ bổ sung CNAME khi có kế hoạch domain riêng; em không tự tạo file `CNAME`.
- Khi CNAME được thêm, cập nhật lại `README.md` §Triển khai GitHub Pages và `TOOLS.md` §Môi trường dự án.

### 4.3 Catalogue sản phẩm

- Site hiện landing giới thiệu + hồ sơ pháp lý; chưa có catalogue sản phẩm WarmDream.
- Khi có ảnh và dữ liệu sạch từ Điệp Xuân, mở rộng thêm section catalogue (chờ Sếp yêu cầu).

### 4.4 Tích hợp Memory directory

- `memory/` chưa có. Khi cần ghi daily context, tạo `memory/YYYY-MM-DD.md` theo format chuẩn.
