# TOOLS.md - Local Notes

File này ghi chú các chi tiết riêng của môi trường dự án này. Skill và protocol dùng chung nằm ở nơi khác; file này chỉ giữ thông tin cần thiết cho workspace này.

## Nguyên tắc

- Không lưu bí mật, token, mật khẩu hoặc dữ liệu nhạy cảm.
- Không ghi lại hướng dẫn chung có thể sống trong skill/plugin.
- Khi thêm tool mới, ghi rõ phạm vi áp dụng và cách nhận diện.

## Môi trường dự án

| Thành phần | Giá trị | Ghi chú |
|------------|---------|---------|
| Loại site | Static HTML/CSS | Không framework, không build step |
| Hosting | GitHub Pages | Build từ `main` (root), chưa bật — Sếp sẽ cấu hình |
| CNAME | chưa có | Sếp bổ sung khi quyết định domain riêng |
| Repo | `https://github.com/diepxuan/warmdream.org.git` | |
| Pages URL mặc định | `https://diepxuan.github.io/warmdream.org/` | dùng khi cần xác minh Pages đang phục vụ |
| Local preview | `python3 -m http.server 8080` từ thư mục dự án, rồi mở `http://localhost:8080` | xem `README.md` mục Cách sử dụng |

## Phân nhóm lệnh theo quyền

**Read-only (KHÔNG cần hỏi Sếp — chạy luôn):**

- `cat`, `head`, `tail`, `grep`, `rg`, `diff`, `ls`, `stat` — đọc/so sánh file
- `git status/log/diff/show/ls-files` — git read-only
- `python3 -m http.server <port>` chạy nền tạm để preview; dừng khi xong
- `curl` GET (không mutate)
- `web_fetch` đọc nguồn sự thật (masothue.com, diepxuan.com, WIPO, v.v.)

**Ghi local trong workspace (KHÔNG cần hỏi Sếp):**

- Tạo/sửa file dự án bằng write/edit tool
- `mkdir`, `cp`, `mv` trong thư mục dự án
- `git checkout -b <new-branch>` — tạo branch mới (local)
- `git add`, `git commit`, `git mv` — staging local

**Ghi cần xin phép Sếp (chỉ chạy khi được approval):**

- `git push`, `gh pr create/edit`, `gh pr merge/close` — thao tác remote/GitHub; chỉ khi Sếp ra lệnh ("push đi", "Em tạo PR đi", "merge")
- `git push origin main` — push trực tiếp lên main
- `git reset --hard`, `git checkout -- <file>`, `git clean -fd` — phá dữ liệu local
- `git push --force`, `git push --force-with-lease` — force push
- `rm` file lớn, `rm -rf` ngoài `/tmp/` hoặc ngoài workspace
- Sửa `LICENSE`, `CNAME`, các asset thương hiệu đã khoanh vùng trong `IDENTITY.md`
- Mọi lệnh ghi ra ngoài workspace của dự án này
- Mọi lệnh cần network ngoài hosting đã khai báo: `npm install`, tải package, gọi API mutation bên ngoài
- Bất kỳ lệnh nào fail do sandbox/network/permission nhưng vẫn cần chạy để hoàn thành task

## Sandbox & Escalation

- Runtime có thể giới hạn ghi trong session workspace mặc định; workspace này thường nằm ngoài vùng đó (ví dụ `/data/<project>/`). Khi thao tác ghi bị từ chối: DỪNG, không né sandbox, retry đúng một lần với cơ chế escalation mà runtime cung cấp (`sandbox_permissions` + justification), chờ Sếp duyệt.
- Justification: tiếng Việt, 1 dòng, nêu rõ lệnh/mục đích/phạm vi, dạng câu hỏi cho Sếp; văn bản thuần, không markdown/code fence.
- Sau khi được duyệt: chỉ chạy đúng phạm vi đã xin; báo lại kết quả (file đổi, exit code, output quan trọng).

### Quy tắc khi lệnh gặp lỗi

- DỪNG, không tự ý retry bằng flag né sandbox.
- Báo cáo Sếp: lệnh đã chạy, exit code, stderr/output quan trọng, nghi vấn nguyên nhân.
- Xin approval escalated nếu vẫn cần chạy để hoàn thành task.

## Lưu ý verify sau khi sửa

- Trang chính: preview local bằng `python3 -m http.server` rồi kiểm tra 3 section (`#top`, `#brand`, `#contact`); kiểm tra asset đúng (`assets/warm-dream-*.{png,svg}`).
- Token CSS: mọi thay đổi màu/typography phải qua token trong `:root` của `assets/styles.css`; KHÔNG hardcode ngoài token.
- Thông tin pháp lý: trước khi đổi, đối chiếu nguồn `https://masothue.com/3101159641-cong-ty-tnhh-warmdream`; Sếp duyệt trước khi commit.
- Liên kết `https://www.diepxuan.com/` (CTA liên hệ) — không phải link nội bộ, chỉ xác nhận còn live khi verify.
