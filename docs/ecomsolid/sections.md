## Hướng dẫn tạo một section mới

### Giới thiệu sơ lược
------------------------

#### Section là gì?

Một một thành phần hoạt động độc lập được gọi là section. Section bao gồm: HTML, CSS, JS, Snippets, Library, Atoms

*Ví dụ về section: Banner, Feature Product, Header, Footer... chính là những section*

<img width="50%" src="/images/ecomsolid/section.png">

#### Sections trong Editor của EcomSolid trông như nào?

<img width="50%" src="/images/ecomsolid/section-in-editor.png">

> Bên tay trái còn rất nhiều sections khác, các sections sẽ được lặp ghép với nhau để tạo thành một templates hoàn thiện

#### Cơ chế hoạt động của Sections

<img width="50%" src="/images/ecomsolid/section-work.png">

**Các bước render một sections:**

**Bước 1:** Snippets sẽ được parse sang settings dạng
```json
{
  "textHeading": "This is value text Heading",
  "sizeHeading": "14px",
}
```
**Bước 2:** Settings sẽ được render cùng HTML, CSS, JS bằng template engine EJS
```js
EJS.render(html: "<div style='font-size:<%-sizeHeading%>'><%-textHeading%></div>", settings: {
  "textHeading": "This is value text Heading",
  "sizeHeading": "14px",
})
```
> Các biến `textHeading` và `sizeHeading` sẽ được replace vào vị trí mong muốn.
> Và kết quả là: `<div style='font-size:14px'>This is value text Heading</div>`

**Bước 3:** Thư viện(library) được thêm vào
> Các Link của thư viện sẽ được thêm vào website để script có thể bắt đầu thực thi

**Bước 4:** Append CSS/HTML/JS lần lượt theo thứ tự vào Editor
> Đối với việc publish template lên shopify thì sẽ có sự thay đổi. Chúng ta sẽ đưa HTML/CSS/JS lên Shopify qua API

#### Lập trình EJS cơ bản

Trong EcomSolid chúng ta sử dụng template engine là EJS để code section.

Tại sao tôi lại chọn EJS?

- EJS là một template engine khá giống php, nó có thể viết linh hoạt lồng trong HTML, CSS, JS.
- Nó có cú pháp của Javascript nên việc các bạn đã có sẵn kiến thức cơ bản dễ dàng tiếp cận.
- Nó giúp bạn biết thêm về NodeJS để nếu có muốn học ở tương lai thì khá dễ dàng.
- EJS là một template engine phổ biến ở NodeJS và khá thân thuộc với nhiều người nên đó là một lợi thế lớn khi có thành viên mới.

**Cú pháp:**

1, Câu lệnh điều kiện IF

```js
<% let name = "EcomSolid"  %>
<% if (name) { %>
  <h2><%- name %></h2>
<% } %>
```
2, Vòng lặp For
```js
<% let users = ["Thành", "Vinh", "Trang"] %>
<% for (let i = 0; i < users.length; i++) { %>
  <h1><%- users[i] %></h1>
<% } %>
```

>[!tip]
>Chúng ta sẽ có một bài dài hơn về EJS tại đây.

### Sơ lược về quy trình
------------------------

**Các bước thực hiện tạo một section thường chia làm 5 giai đoạn:**
- Giai đoạn 1: Hoàn thiện base section. Giúp người code định hình được layout ban đầu cho section của mình.
  - Tạo một HTML base
  - Tạo một Snippets base
- Giai đoạn 2: Style cho section. Khi chúng ta có cấu trúc html hoàn thiện của section, thì việc triển khai style sẽ làm rõ hơn về hình dáng của section.
  - Gắn class vào bên HTML
  - Viết SCSS để định nghĩa style
  - Định nghĩa thêm Snippets
- Giai đoạn 3: Bổ xung tính năng cho Snippets nếu cần.
- Giai đoạn 4: Test lại toàn bộ chức năng của Snippets với Style và cấu trúc HTML hiện tại để đảm bảo mọi options đều hoạt động bình thường.
- Giai đoạn 5: Deploy lên server DEV và yêu cầu người review.


### Tạo một section cơ bản
------------------------

#### Bước 1: Tạo base HTML
------------------------

```html
<section class="gt_section-<%=id%> <%=extraClass%>" data-name="<%=name%>">
  <Box attribute="contentWapper">
    <Button attribute="buttonAddToCart"/>
  </Box>
</section>
```
- `gt_section-<%=id%>`: giúp định nghĩa class duy nhất của section.
- `<%=extraClass%>`: Định nghĩa các class custom của section như: Animation, Visibility...
- `data-name="<%=name%>"`: Hiển thị tên tương ứng trong Editor để giúp kiểm tra lỗi dễ dàng hơn.
- `Box, Button`: Tên của các atoms (<a href="#/ecomsolid/atoms?id=danh-sách-atoms" target="_blank">thông tin chi tiết</a>)
- `attribute="contentWapper"`: Định nghĩa này sẽ ánh xạ tương ứng đến bên snippets

>[!tip]
> Tìm hiểu thêm về HTML kết nối với snippets (<a href="/#/ecomsolid/html?id=làm-việc-với-atoms" target="_blank">Hướng dẫn chi tiết</a>)

#### Bước 2: Tạo base Snippets
------------------------
```json
[
  {
    "id": "content",
    "settings": [
      {
        "id": "tree",
        "attribute": "tree",
        "type": "tree",
        "reference": "html",
        "value": [
          {
            "attribute": "contentWapper",
            "atom": "Box",
            "title": "Box",
            "children": [
              {
                "attribute": "buttonAddToCart",
                "atom": "Button",
                "title": "Button",
                "value": "Add To Cart"
              }
            ]
          }
        ]
      }
    ]
  },
  {
    "id": "design",
    "settings": []
  }
]
```
Bạn cần tìm hiểu cấu tạo của snippets (<a href="#/ecomsolid/snippets" target="_blank">hướng dẫn chi tiết</a>)

#### Bước 3: Style cho bộ khung đã được tạo ra bằng HTML + Snippets
------------------------
```scss
.gt_section-1 {
  /* width: <%=sizeIcon%>;*/
  /* height: <%=sizeIcon%>;*/
  .gt_icon {
    display: flex;
    align-items: center;
    width: 100%;
    height: 100%;
    /* color: <%=iconColor%>; */
  }
  &:hover {
    .gt_icon {
      /* color: <%=iconHoverColor%>; */
    }
  }
}

```
Bạn cần xem trước cách để tạo style cho section (<a href="#" target="_blank">Hướng dẫn chi tiết</a>)

**Lưu ý:**
- Bạn cần ưu tiên dùng class global đã được định nghĩa (<a href="#" target="_blank">Thông tin về class global</a>)
- Bạn có thể gắn thêm class để style
- Không được sử dụng ID trong HTML