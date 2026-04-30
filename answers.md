### Trả lời Bài B3: Debug HTML
Dưới đây là danh sách 10 lỗi em đã tìm ra và sửa lại:

1. **Lỗi 1: Dòng 1** — Khai báo thiếu chữ "html" — Cần sửa thành `<!DOCTYPE html>`
2. **Lỗi 2: Dòng 4** — Thẻ `<title>` bị thiếu thẻ đóng — Sửa thành `<title>Trang web</title>`
3. **Lỗi 3: Dòng 5** — Khai báo charset sai chuẩn (`utf8`) — Sửa thành `<meta charset="UTF-8">`
4. **Lỗi 4: Dòng 8** — Thẻ `<h1>` đóng sai cú pháp (thiếu dấu `/`) — Sửa thành `</h1>`
5. **Lỗi 5: Dòng 12** — Thẻ `<a>` đóng sai cú pháp (thiếu dấu `/`) — Sửa thành `</a>`
6. **Lỗi 6: Dòng 19** — Lỗi link ảnh thiếu ngoặc kép và thiếu thuộc tính Semantic `alt` — Sửa thành `<img src="iphone.jpg" alt="iPhone 16 Pro">`
7. **Lỗi 7: Dòng 21** — Các thẻ đóng lồng nhau sai thứ tự (`<b>` mở sau nhưng lại đóng sau thẻ `<p>`). Ngoài ra thẻ `<b>` không chuẩn Semantic — Sửa thành `<strong>25.990.000đ</strong></p>`
8. **Lỗi 8: Dòng 27, 28** — Hàng tiêu đề của bảng lại dùng thẻ `<td>` là sai ngữ nghĩa — Đổi thành thẻ `<th>`
9. **Lỗi 9: Dòng 38** — Lỗi Semantic cực nặng vì 1 trang HTML chỉ được phép có 1 thẻ `<main>`, nội dung "Sidebar" không được để trong main — Sửa `<main>` thứ hai thành `<aside>`
10. **Lỗi 10: Dòng 43** — Thẻ `<p>` thiếu thẻ đóng tương ứng — Sửa thành `<p>Copyright 2026</p>`

### Bài B4 — Phân tích trang web thật (Shopee.vn)

**1. Phân tích thẻ Semantic:** * (Ảnh chứng minh: `screenshots/b4_semantic.jpg`)
* **3 thẻ semantic được sử dụng:**
  - `<header>`: Nằm ở phần đầu trang, chứa logo, thanh tìm kiếm và menu điều hướng.
  - `<footer>`: Nằm ở phần chân trang, chứa thông tin hỗ trợ khách hàng và địa chỉ công ty.
  - `<main>`: Dùng để bọc toàn bộ khu vực nội dung hiển thị chính của sản phẩm.
* **2 thẻ dùng chưa chuẩn semantic:**
  - Lạm dụng thẻ `<div>` lồng nhau quá nhiều để tạo layout (div soup).
  - Rất nhiều nút bấm có tính tương tác để chọn phân loại hàng lại dùng thẻ `<div>` gắn sự kiện click bằng JavaScript thay vì dùng chuẩn thẻ `<button>`.

**2. Phân tích Table (Bảng Hướng dẫn chọn Size):** * (Ảnh chứng minh: `screenshots/b4_table.jpg`)
* **Table hiển thị nội dung gì:** Bảng được sử dụng để hiển thị các số đo quy đổi kích cỡ lót giày (Size US tương ứng với Chiều dài bàn chân tính bằng cm).
* **Có dùng `<thead>`, `<tbody>` không?:** Có sử dụng đầy đủ. Khung bảng được bọc bởi `<table class="NJNrcs">`. Thẻ `<thead>` chứa các hàng `<tr>` và ô tiêu đề cột `<th>`. Bên dưới là thẻ `<tbody>` để chứa dữ liệu các size tương ứng. 

**3. Phân tích Form (Ô tìm kiếm sản phẩm):** * (Ảnh chứng minh: `screenshots/b4_form.jpg`)
* **Thuộc tính action và method:** Form tìm kiếm sử dụng method ngầm định là `GET` (để đẩy từ khóa lên thanh URL chia sẻ).
* **Input types được dùng:** Sử dụng thẻ `<input class="shopee-searchbar-input" autocomplete="off">` (loại mặc định text) để người dùng nhập từ khóa tìm kiếm.