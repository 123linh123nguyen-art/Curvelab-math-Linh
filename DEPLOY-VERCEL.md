# Triển khai CurveLab lên Vercel

CurveLab là web tĩnh. Cấu hình `vercel.json` đã đặt thư mục xuất bản là `dist`, bỏ qua bước cài đặt và không chạy lệnh build.

## Cách 1 — Vercel Dashboard

1. Đưa toàn bộ thư mục dự án này lên một repository GitHub, GitLab hoặc Bitbucket.
2. Vào https://vercel.com/new và chọn **Import Git Repository**.
3. Chọn repository CurveLab.
4. Giữ **Root Directory** là thư mục chứa `vercel.json`. Nếu repository chứa riêng thư mục `curvelab-site`, chọn `curvelab-site` làm Root Directory.
5. Vercel sẽ đọc cấu hình tự động. Kiểm tra:
   - Framework Preset: **Other**
   - Build Command: để trống
   - Output Directory: `dist`
   - Install Command: để trống
6. Bấm **Deploy**.

Trang chính là `/`; bàn làm việc hình học là `/studio.html#surface`.

## Cách 2 — Vercel CLI

Cài CLI một lần:

```powershell
npm install --global vercel
```

Mở PowerShell tại thư mục chứa `vercel.json`, đăng nhập và triển khai:

```powershell
vercel login
vercel
```

Khi bản xem thử hoạt động đúng, đưa lên production:

```powershell
vercel --prod
```

Ở lần đầu, chọn tạo project mới và đặt tên `curvelab` nếu tên này còn khả dụng trong tài khoản/nhóm của bạn. Vercel tự tạo địa chỉ dạng `curvelab.vercel.app` khi tên khả dụng; nếu đã có người dùng tên đó, Vercel sẽ yêu cầu tên khác.

## Tên miền riêng

Trong Vercel, mở **Project → Settings → Domains**, thêm tên miền bạn sở hữu và làm theo bản ghi DNS Vercel hiển thị. Việc đặt `name` trong `vercel.json` không giữ chỗ tên miền nên cấu hình này không khai báo tên project cứng.

## Cập nhật về sau

- Nếu dùng Git: mỗi lần push sẽ tạo một Preview Deployment; push vào nhánh production sẽ cập nhật production theo cấu hình project.
- Nếu dùng CLI: chạy lại `vercel --prod` tại thư mục này.
- Không cần biến môi trường, database hoặc server cho phiên bản hiện tại.

Tài liệu chính thức: https://vercel.com/docs/project-configuration/vercel-json và https://vercel.com/docs/cli
