## Hướng dẫn tạo một section mới
------------------------

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
- `Box, Button`: Tên của các atoms (<a href="#" target="_blank">thông tin chi tiết</a>)
- `attribute="contentWapper"`: Định nghĩa này sẽ ánh xạ tương ứng đến bên snippets

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
Bạn cần tìm hiểu cấu tạo của snippets (<a href="#" target="_blank">hướng dẫn chi tiết</a>)

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