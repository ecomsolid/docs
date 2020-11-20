## Cấu trúc chuẩn

### Các lưu ý

### Cấu trúc

#### Settings

>[!note]
> Sections/widgets hoặc atoms đều có những setting riêng. Eg: Icon thì có pickIcon, Image thì có uploadImage

#### Design
Design sẽ cần flow theo chuẩn chung để giúp khách hàng quen thuộc hơn khi sử dụng Editor. Điều này cũng giúp việc code giảm thiểu hơn khi có thể copy code cũ đề đưa vào sections/atoms mới sau đó optimize lại cho phù hợp hơn.
##### Size


## Thuộc tính mở rộng
------------------------
### Định nghĩa plans
------------------------
### Chia Tabs ở Settings
------------------------

## Danh sách control
------------------------

### Cơ bản
------------------------
#### Tree
------------------------
Ảnh hiển thị:

<img src="https://gemthemes.s3.amazonaws.com/docs/production/521fa9dd-2947-4765-8dba-2686938ea112.png" alt="screen shot 2019-07-22 at 08.30.25.png">

Snippet định nghĩa:

```json
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
      "clone": true,
      "advanced": true,
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
```
Value của tree là một mảng định nghĩa các atom bên HTML.

**Các thuộc tính giúp định nghĩa một atom:**
- `"attribute": "contentWapper"`: Định danh cho atom.
- `"atom": "Box"`: Định nghĩa atom sử dụng, `Box` sẽ tương ứng với HTML tag.
- `"title": "Box"`: Hiển thị bên Left Side Bar.
- `"children": []`: Định nghĩa con của atom hiện tại.
- `"clone": true`: Có thể thêm xoá di chuyển phần tử con, giống với khái niệm tabs
- `"advanced": true`: chỉ xuất hiện atom khi khách bật Advaced Mode


#### Input
------------------------
##### Input text
------------------------
Ảnh hiển thị:

<img src="https://gemthemes.s3.amazonaws.com/docs/production/521fa9dd-2947-4765-8dba-2686938ea112.png" alt="screen shot 2019-07-22 at 08.30.25.png">

Snippet định nghĩa:

```json
{
 "id": "textSubHeading",
 "attribute": "textSubHeading",
 "title": "Sub Heading",
 "reference": "html",
 "value": "100% SATISFACTION",
 "type": "input"
}
```

### Shopify
------------------------

### Customize
------------------------

## Thuộc tính tối ưu
------------------------
