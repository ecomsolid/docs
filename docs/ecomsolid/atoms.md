## Danh sách atoms
------------------------

### Row
------------------------

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

## Hướng dẫn tạo một atom mới
------------------------

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
<div class="gt_atom-<%-id%>" id="a-<%-id%>" data-name="<%=name%>">
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
