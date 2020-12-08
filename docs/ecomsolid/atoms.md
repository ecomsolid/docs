## Giới thiệu về Atoms

Atom được hiểu đơn giản là phần tử bé nhất của một website. Nếu bạn đã nghe đến Atomic Design thì ở EcomSolid sẽ áp dụng nguyên lý này để trở thành nền tảng cho sections.

*Tư tưởng về kiến trúc trong EcomSolid*

<img src="/images/ecomsolid/atomicdesign.jpeg">

- Atoms (nguyên tử): Là thành phần bé nhất. => **Atom cơ bản**
- Molecules (phân tử): Là một dạng atom nâng cấp gồm nhiều atom hợp lại. => **Atom có thể chứa đươc atom khác**
- Organisms (sinh vật): Là một thể thống nhất gồm nhiều phân tử và nguyên tử hợp lại => **Đây chính là Section**


## Danh sách atoms
>[!tip]
>Danh sách atom giúp bạn có thể chọn các atom phù hợp để sử dụng trong section. Nếu bạn cần thêm bất kỳ atom nào chuyên biệt thì có thể order thêm cho đội FrontEnd. Đội FrontEnd chính là những người tạo ra các atom.
><br>Nếu bạn thích trải nghiệm: Có thể liên hệ với Leader để tạo cho mình một atom theo ý muốn, nó khá đơn giản và cách thực hiện gần giống section.
### Box
------------------------
> Box là một atom dạng Molecule nên có thể chứa được các Atom/HTML khác bên trong.

#### HTML cơ bản
```html
<Box attribute="boxWapper">
  <h1>Heading</h1>
</Box>
```
#### Settings cơ bản
```json
"settings: {
}
```
### Button
------------------------

### Text
------------------------

### Icon
------------------------

### Image
------------------------

### Shopify
------------------------

#### Product
------------------------

##### Product Price
------------------------

##### Product Title
------------------------

##### Product Quantity
------------------------

##### Product Swatches
------------------------

##### Product Variants
------------------------

##### Product Add To Cart
------------------------

##### Product Buy Now
------------------------

##### Product Vendor
------------------------

##### Product Sku
------------------------

#### Collection
------------------------

#### Blog
------------------------

#### Article
------------------------

## Hướng dẫn tạo một atom mới (FrontEnd)

>[!warning]
>Nếu bạn không thuộc đội FrontEnd thì không nên đọc phần này.

### Các trường dữ liệu
------------------------


#### Name
------------------------

Định nghĩa HTML tag của atoms.

<strong>Bắt buộc:</strong>
- Viết in hoa chữ cái đầu.
- Các từ nối với nhau bằng chữ in hoa - (eg: ProductTitle).

#### Icon
------------------------

#### Keyword
------------------------

Là định danh của atom, nó là duy nhất và sẽ được bảo toàn mãi mãi.

<strong>Bắt buộc:</strong>
- Không viết in hoa
- Các từ nối với nhau bằng ký tự - (eg: product-title).

#### Snippets
------------------------

#### Html
------------------------

#### Style
------------------------

#### Script
------------------------

#### Libs
------------------------

#### Thumbnail
------------------------

#### Publish
------------------------

Trạng thái *"public - private"* sẽ giúp quyết định việc có sử dụng được atom này không

### Các bước thực hiện
------------------------

#### Bước 1: Định nghĩa HTML
------------------------
```html
<div class="gt_atom-<%-id%> gt_transition" id="a-<%-id%>" data-name="<%=name%>">
  <slot></slot> 
</div>
``` 

>[!warning]
> Cần thêm ID theo id của atom để có thể ghi đè style của section

>[!tip]
> Cần tìm hiểu thêm về cách viết HTML ở đây. (<a href="#/ecomsolid/html" target="_blank">Hướng dẫn chi tiết</a>)

>[!tip]
> Cần tìm hiểu thêm về những class global ở đây. (<a href="#/ecomsolid/class-global" target="_blank">Hướng dẫn chi tiết</a>)

#### Bước 2: Định nghĩa Snippets
------------------------
```json
[
  {
    "id": "content",
    "settings": []
  },
  {
    "id": "design",
    "settings": []
  }
]
```
>[!warning]
> Cần lưu ý snippets của design cần flow theo chuẩn chung (<a href="#/ecomsolid/snippets" target="_blank">Hướng dẫn chi tiết</a>)


>[!tip]
> Cần tìm hiểu thêm về cách viết Snippets ở đây. (<a href="#/ecomsolid/snippets?id=tree" target="_blank">Hướng dẫn chi tiết</a>)
#### Bước 3: Tạo Style
------------------------
```scss
#a-<%-id%> {

}
```
>[!warning]
> Với atom, chúng ta sử dụng ID để style với mục tiêu ghi đè style của section


>[!tip]
> Tìm hiểu về responsive. (<a href="#" target="_blank">Hướng dẫn chi tiết</a>)
