# vietesg-si-nap — bãi trung chuyển nạp dữ liệu SI (tạm thời, công khai)

Repo này chỉ là **bãi trung chuyển**: Lovable Cloud không cấp Service Role Key, nên cơ sở dữ liệu VietESG SI tự KÉO file ở đây
qua URL raw (extension `http` của Postgres, hàm `si_nap_*` trong `vietesg-si-brain/migration-si/009_nap_tu_url.sql`).

- `nap/A/<nam>.jsonl` — chuỗi lưu ký (sha256, byte_size, mime) cho kho báo cáo có sẵn; **dữ liệu không nhạy cảm**, để nguyên văn. Sinh bởi `nap_sha256.py` (phiên Code).
- `nap/C/*.jsonl.gpg.b64` — tri thức đọc tài liệu (brain_*), **mã hoá AES-256 (gpg symmetric) + base64**; khoá nằm ngoài repo. Sinh bởi `nap_brain.py --xuat` rồi gpg.

Sau khi nạp xong, repo này có thể xoá. Không chứa khoá, không chứa toàn văn tài liệu.
