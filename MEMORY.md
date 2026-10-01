# Long-term Memory

Memory dài hạn cho Bột trên dự án này. Mỗi entry khi có thay đổi cơ chế, sự cố hay bài học đều ghi vào đây. Đọc MEMORY.md trước mọi task lớn để không lặp lại lỗi cũ.

Cập nhật lần cuối: [FILL: ngày khởi tạo] — bootstrap bộ instruction files.

---

## 0. Quy tắc cố định (không theo task, theo SOUL.md/AGENTS.md/TOOLS.md)

[FILL: sau khi agent riêng từng dự án bổ sung — kiểu dự án, ràng buộc nội dung, ràng buộc thương hiệu, remote, branch policy, v.v.]

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

---

## 3. Bài học rút ra

[FILL: ghi nhận sau khi có sự cố hoặc quyết định quan trọng]

---

## 4. Backlog / Open questions

[FILL: câu hỏi chưa giải quyết, task chưa làm]