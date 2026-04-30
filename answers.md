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

## PHẦN C — SUY LUẬN

### Câu C1 — Thiết kế cấu trúc HTML cho trang chi tiết sản phẩm

```html
<header>
    <nav>...</nav> 
</header>

<nav aria-label="breadcrumb">
    <ol>
        <li><a href="/">Trang chủ</a></li>
        <li><a href="/dien-thoai">Điện thoại</a></li>
        <li>iPhone 16</li>
    </ol>
</nav>

<main>
    <article>
        <section id="gallery">
            <figure>
                </figure>
        </section>

        <section id="info">
            <h1>Tên sản phẩm</h1>
            <p>Giá và mô tả...</p>
        </section>

        <section id="specs">
            <table>
                <tbody>
                    <tr>
                        <th>Màn hình</th>
                        <td>6.1 inch</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="reviews">
            </section>
    </article>

    <aside>
        <h2>Sản phẩm tương tự</h2>
        </aside>
</main>

<footer>
    <p>© 2026 ShopTLU</p>
</footer>

### Câu C2 — So sánh & Tranh luận (Semantic HTML vs thẻ div)

Việc chỉ sử dụng thẻ <div> cho mọi thành phần rồi định dạng bằng class (hay còn gọi là "div soup") là một thói quen lập trình không tốt. Việc học và sử dụng Semantic HTML mang lại những lợi ích kỹ thuật không thể thay thế:

1. Tối ưu hóa SEO (Search Engine Optimization):
Các bot tìm kiếm của Google không thể hiểu được class CSS. Nếu dùng <div class="header">, bot chỉ xem đó là một khối trống rỗng. Nhưng nếu dùng thẻ <header> hoặc <article>, bot sẽ lập tức phân tích và nhận diện được đâu là nội dung quan trọng nhất của trang để ưu tiên lập chỉ mục, giúp website xếp hạng cao hơn.

2. Hỗ trợ Accessibility (Khả năng tiếp cận):
Người khiếm thị lướt web bằng phần mềm đọc màn hình (Screen Reader). Ví dụ cụ thể: Nếu ta tạo một nút bấm bằng <div class="btn" onclick="...">, phần mềm sẽ chỉ đọc nó là văn bản bình thường. Nhưng nếu ta dùng đúng thẻ semantic là <button>, máy đọc sẽ phát âm là "Nút bấm" và cho phép người dùng tương tác bằng phím Enter.

3. Khi nào thì dùng thẻ <div>?
Thẻ <div> sinh ra là một thẻ vô nghĩa (non-semantic tag), nên trường hợp thực tế dùng nó hợp lý nhất là khi ta cần một "cái bọc" để gom nhóm các phần tử lại với mục đích dàn layout bằng CSS (như dùng Flexbox, Grid để chia cột) mà khối đó không mang bất kỳ ý nghĩa nào về mặt nội dung.

## PHẦN A — KIỂM TRA ĐỌC HIỂU

### Câu A1 — HTTP & Browser
* **Nguồn tham chiếu:**
  - Lời giải 1: File `tuan_1_html5/01_introduction_html_universe.md` — Mục "1.2. HTTP — Ngôn ngữ để Client và Server hiểu nhau" và "1.3. Browser Rendering — Từ Code thành Hình ảnh".
  - Lời giải 2: File `tuan_1_html5/01_introduction_html_universe.md` — Mục "4.3. Developer Tools (F12) — Kính hiển vi cho website".

**1. 5 bước xảy ra theo thứ tự khi truy cập https://shopee.vn:**
1. **DNS Lookup:** Trình duyệt tìm IP máy chủ của Shopee dựa trên tên miền.
2. **TCP Handshake:** Thiết lập kết nối với máy chủ của Shopee thông qua giao thức TCP.
3. **TLS Negotiation:** Xác thực chứng chỉ bảo mật SSL/TLS để mã hóa dữ liệu.
4. **HTTP Request & Response:** Trình duyệt gửi yêu cầu (Request) HTTP, máy chủ xử lý và trả về file HTML (mã 200 OK).
5. **Browser Rendering:** Trình duyệt Parse HTML, Parse CSS, Execute JS và vẽ giao diện lên màn hình.

**2. Phân tích DevTools (Tab Network):**
* Tab Network cho biết thông tin về mọi luồng giao tiếp giữa trình duyệt và máy chủ: các file được tải xuống, mã trạng thái (Status Code), dung lượng, và tổng thời gian tải trang.
* *(Hình ảnh minh họa đánh dấu Status 200, thời gian load và file CSS xem tại: `screenshots/a1_network.jpg`)*

### Câu A2 — Semantic HTML
* **Nguồn tham chiếu:** File `tuan_1_html5/04_semantic_html.md` — Mục "Semantic HTML là gì?" và "Các thẻ Semantic HTML5 cơ bản".

**Tại sao trang web bị đánh giá SEO thấp?** Trang web đang lạm dụng thẻ `<div>` vô nghĩa. Google Bot khi quét qua sẽ không nhận diện được đâu là thanh điều hướng, đâu là nội dung sản phẩm hay chân trang, làm giảm thứ hạng tìm kiếm.

**4 lỗi Semantic và cách sửa:**
1. `<div class="header">` ➡️ Sửa thành thẻ `<header>`
2. `<div class="menu">` ➡️ Sửa thành thẻ `<nav>`
3. `<div class="main">` ➡️ Sửa thành thẻ `<main>`
4. `<div class="product">` ➡️ Sửa thành thẻ `<article>`

**Đoạn code đã được sửa lại:**
```html
<header>
    <div class="logo">ShopTLU</div>
    <nav>
        <div><a href="/">Trang chủ</a></div>
        <div><a href="/products">Sản phẩm</a></div>
    </nav>
</header>
<main>
    <article>
        <h2 class="title">iPhone 16 Pro</h2>
        <div class="price">25.990.000đ</div>
        <figure><img src="iphone.jpg" alt="iPhone 16 Pro"></figure>
    </article>
</main>
<footer>© 2026 ShopTLU</footer>

Câu A3 — Block vs Inline
Nguồn tham chiếu: Kiến thức nền tảng HTML (Phân biệt thuộc tính Block-level và Inline-level).

Mô phỏng kết quả hiển thị:

Plaintext
Hộp 1
Text A Text B
Hộp 2
Text C Text D
Hộp 3
Giải thích:

Thẻ <div> là thẻ Block-level: Nó bắt đầu ở dòng mới và chiếm toàn bộ chiều ngang có thể, đẩy các phần tử khác xuống dòng tiếp theo.
Thẻ <span> và <strong> là thẻ Inline: Chúng chỉ chiếm phần không gian vừa đủ bao bọc chữ, nên sẽ nằm cạnh nhau trên cùng một dòng.

Câu A4 — Table
Nguồn tham chiếu: File tuan_1_html5/05_tables_hyperlinks.md — Mục "Cấu trúc cơ bản của Table" và "Lưu ý khi sử dụng Table".

Sự khác nhau:

<thead>: Định nghĩa nhóm hàng tiêu đề của bảng.

<tbody>: Chứa các hàng dữ liệu chính.

<tfoot>: Nằm dưới cùng, dùng để chốt lại/tổng kết dữ liệu của bảng.

3 lý do KHÔNG NÊN dùng table để tạo layout trang web:

Khó Responsive: Cấu trúc bảng rất cứng nhắc, không tự động co giãn dòng cột linh hoạt khi hiển thị trên màn hình điện thoại nhỏ.

Sai ngữ nghĩa (Accessibility): Các phần mềm đọc màn hình (Screen Reader) của người khiếm thị sẽ bị nhầm lẫn khi đọc một bảng dữ liệu lồng ghép rắc rối chỉ để chia bố cục.

Mã nguồn cồng kềnh: Phải lồng ghép rất nhiều thẻ <tr>, <td> phức tạp, làm file nặng và khó sửa lỗi hơn so với việc dùng CSS hiện đại (Flexbox/Grid).