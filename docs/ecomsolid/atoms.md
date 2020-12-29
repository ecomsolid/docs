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
#### Snippets
>[!note]
> Khi khai báo trong section cần quy định trạng thái hiển thị của Box thông qua setting **"displayType"**. Mặc định Box sẽ có css **display: block !important;**
```json
{
  "attribute": "boxWapper",
  "atom": "Box",
  "title": "Box",
  "settings": {
    "displayType": "row",  // row,column,unset
    "displayType_ld": "row",
    "displayType_md": "row",
    "displayType_sm": "row",
    "displayType_xs": "row"
  }
}
```
### Box Absolute
------------------------
> Là atom hoạt động tương tự atom Box nhưng ở chế độ absolute.
#### HTML cơ bản
```html
<BoxAbsolute attribute="boxAbsolute">
  <h1>Heading</h1>
</BoxAbsolute>
```
#### Snippets
```json
{
  "attribute": "boxAbsolute",
  "atom": "BoxAbsolute",
  "title": "Box Absolute"
}
```

### Button Link
------------------------
#### HTML cơ bản
```html
<ButtonLink attribute="buttonLink"></ButtonLink>
```
#### Snippets
```json
{
  "attribute": "buttonLink",
  "atom": "ButtonLink",
  "title": "Button Link",
  "value": "Get It Now!"
}
```

### Text
------------------------
#### HTML cơ bản
```html
<Text attribute="text"></Text>
```
#### Snippets
```json
{
  "attribute": "text",
  "atom": "Text",
  "title": "Text",
  "value": "Wellcome to Ecomsolid"
}
```

### Icon
------------------------
#### HTML cơ bản
```html
<Icon attribute="icon"></Icon>
```
#### Snippets
```json
{
  "attribute": "icon",
  "atom": "Icon",
  "title": "Icon",
  "value": {
    "content": "<svg></svg>",
    "type": "svg",
    "name": "check"
  }
}
```

### Image
------------------------
#### HTML cơ bản
```html
<Image attribute="image"></Image>
```
#### Snippets
```json
{
  "attribute": "image",
  "atom": "Image",
  "title": "Image",
  "value": "https://d3dfaj4bukarbm.cloudfront.net/staging/images/admin/36e00baf-fa3e-415b-ae10-de7160a67323.png",
  "settings": {
    "imageAlt": "",
    "imageTitle": ""
  }
}
```

### Rating
------------------------
#### HTML cơ bản
```html
<Rating attribute="image"></Rating>
```
#### Snippets
```json
{
  "attribute": "image",
  "atom": "Rating",
  "title": "Rating",
  "value": 5 // from 1 to 5
}
```

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

**Bắt buộc:**
- Viết in hoa chữ cái đầu.
- Các từ nối với nhau bằng chữ in hoa - (eg: ProductTitle).

#### Icon
Định nghĩa icon hiển thị bên left side bar của atom.

Danh sách icon đang có:

<svg width="24" height="24" viewBox="0 0 24 24" fill="none">
  <path d="M9.4 3H4.6C3.71634 3 3 3.71634 3 4.6V9.4C3 10.2837 3.71634 11 4.6 11H9.4C10.2837 11 11 10.2837 11 9.4V4.6C11 3.71634 10.2837 3 9.4 3Z" fill="currentColor"/>
  <path d="M19.4 3H14.6C13.7163 3 13 3.71634 13 4.6V9.4C13 10.2837 13.7163 11 14.6 11H19.4C20.2837 11 21 10.2837 21 9.4V4.6C21 3.71634 20.2837 3 19.4 3Z" fill="currentColor"/>
  <path d="M9.4 13H4.6C3.71634 13 3 13.7163 3 14.6V19.4C3 20.2837 3.71634 21 4.6 21H9.4C10.2837 21 11 20.2837 11 19.4V14.6C11 13.7163 10.2837 13 9.4 13Z" fill="currentColor"/>
  <path d="M19.4 13H14.6C13.7163 13 13 13.7163 13 14.6V19.4C13 20.2837 13.7163 21 14.6 21H19.4C20.2837 21 21 20.2837 21 19.4V14.6C21 13.7163 20.2837 13 19.4 13Z" fill="currentColor"/>
</svg>

```bash
group
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M6 5H18C21.312 5 24 8.136 24 12C24 15.864 21.312 19 18 19H6C2.688 19 0 15.864 0 12C0 8.136 2.688 5 6 5ZM3 12C3 14.2133 4.78667 16 7 16C9.21333 16 11 14.2133 11 12C11 9.78667 9.21333 8 7 8C4.78667 8 3 9.78667 3 12Z" fill="currentColor"/>
</svg>

```bash
button
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M3.10482 20.0729L9.5642 4.26214C9.87515 3.50214 10.6525 3 11.5006 3C12.3487 3 13.1119 3.50214 13.437 4.26214L19.8964 20.0729C20.278 20.9957 19.5572 22 18.5254 22C17.9034 22 17.3522 21.6336 17.1402 21.0771L15.9105 17.9286H7.07656L5.86101 21.0771C5.63486 21.6336 5.08362 22 4.47585 22C3.42991 22 2.72319 20.9957 3.10482 20.0729ZM11.5012 6.62354L8.1372 15.2142H14.8651L11.5012 6.62354Z" fill="currentColor"/>
</svg>

```bash
text
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M12.0001 17.5195L16.1501 20.0295C16.9101 20.4895 17.8401 19.8095 17.6401 18.9495L16.5401 14.2295L20.2101 11.0495C20.8801 10.4695 20.5201 9.36952 19.6401 9.29952L14.8101 8.88952L12.9201 4.42952C12.5801 3.61952 11.4201 3.61952 11.0801 4.42952L9.19007 8.87952L4.36007 9.28952C3.48007 9.35952 3.12007 10.4595 3.79007 11.0395L7.46007 14.2195L6.36007 18.9395C6.16007 19.7995 7.09007 20.4795 7.85007 20.0195L12.0001 17.5195Z" fill="currentColor"/>
</svg>

```bash
icon
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M3 3H21C22.1 3 23 3.9 23 5V19C23 20.1 22.1 21 21 21H3C1.9 21 1 20.1 1 19V5C1 3.9 1.9 3 3 3ZM4 12C4 15.31 7.58 18 12 18C16.42 18 20 15.31 20 12C20 8.69 16.42 6 12 6C7.58 6 4 8.69 4 12Z" fill="currentColor"/>
</svg>

```bash
background
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M4.5 9H6.5C7.05 9 7.5 8.55 7.5 8V6C7.5 5.45 7.05 5 6.5 5H4.5C3.95 5 3.5 5.45 3.5 6V8C3.5 8.55 3.95 9 4.5 9ZM6.5 14H4.5C3.95 14 3.5 13.55 3.5 13V11C3.5 10.45 3.95 10 4.5 10H6.5C7.05 10 7.5 10.45 7.5 11V13C7.5 13.55 7.05 14 6.5 14ZM6.5 19H4.5C3.95 19 3.5 18.55 3.5 18V16C3.5 15.45 3.95 15 4.5 15H6.5C7.05 15 7.5 15.45 7.5 16V18C7.5 18.55 7.05 19 6.5 19ZM19.5 14H9.5C8.95 14 8.5 13.55 8.5 13V11C8.5 10.45 8.95 10 9.5 10H19.5C20.05 10 20.5 10.45 20.5 11V13C20.5 13.55 20.05 14 19.5 14ZM9.5 19H19.5C20.05 19 20.5 18.55 20.5 18V16C20.5 15.45 20.05 15 19.5 15H9.5C8.95 15 8.5 15.45 8.5 16V18C8.5 18.55 8.95 19 9.5 19ZM8.5 8V6C8.5 5.45 8.95 5 9.5 5H19.5C20.05 5 20.5 5.45 20.5 6V8C20.5 8.55 20.05 9 19.5 9H9.5C8.95 9 8.5 8.55 8.5 8Z" fill="currentColor"/>
</svg>

```bash
list
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M21 5V19C21 20.1 20.1 21 19 21H5C3.9 21 3 20.1 3 19V5C3 3.9 3.9 3 5 3H19C20.1 3 21 3.9 21 5ZM11 16.51L8.9 13.98C8.69 13.73 8.31 13.74 8.12 14L5.63 17.2C5.37 17.53 5.6 18.01 6.02 18.01H18.01C18.42 18.01 18.66 17.54 18.41 17.21L14.9 12.53C14.7 12.26 14.3 12.26 14.1 12.52L11 16.51Z" fill="currentColor"/>
</svg>

```bash
image
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path fill-rule="evenodd" clip-rule="evenodd" d="M2.5 5V4C2.5 3.45 2.95 3 3.5 3H20.5C21.05 3 21.5 3.45 21.5 4V5C21.5 5.55 21.05 6 20.5 6H3.5C2.95 6 2.5 5.55 2.5 5ZM20.5 8H3.5C2.95 8 2.5 8.45 2.5 9V15C2.5 15.55 2.95 16 3.5 16H20.5C21.05 16 21.5 15.55 21.5 15V9C21.5 8.45 21.05 8 20.5 8ZM3.5 21H20.5C21.05 21 21.5 20.55 21.5 20V19C21.5 18.45 21.05 18 20.5 18H3.5C2.95 18 2.5 18.45 2.5 19V20C2.5 20.55 2.95 21 3.5 21Z" fill="currentColor"/>
</svg>

```bash
section
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M20 19.59V8L14 2H6C4.9 2 4.01 2.9 4.01 4L4 20C4 21.1 4.89 22 5.99 22H18C18.45 22 18.85 21.85 19.19 21.6L14.76 17.17C13.96 17.69 13.02 18 12 18C9.24 18 7 15.76 7 13C7 10.24 9.24 8 12 8C14.76 8 17 10.24 17 13C17 14.02 16.69 14.96 16.17 15.75L20 19.59ZM9 13C9 14.66 10.34 16 12 16C13.66 16 15 14.66 15 13C15 11.34 13.66 10 12 10C10.34 10 9 11.34 9 13Z" fill="currentColor"/>
</svg>

```bash
search
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M7 18C5.9 18 5.01 18.9 5.01 20C5.01 21.1 5.9 22 7 22C8.1 22 9 21.1 9 20C9 18.9 8.1 18 7 18ZM1 2V4H3L6.6 11.59L5.25 14.04C5.09 14.32 5 14.65 5 15C5 16.1 5.9 17 7 17H19V15H7.42C7.28 15 7.17 14.89 7.17 14.75L7.2 14.63L8.1 13H15.55C16.3 13 16.96 12.59 17.3 11.97L20.88 5.48C20.96 5.34 21 5.17 21 5C21 4.45 20.55 4 20 4H5.21L4.27 2H1ZM17 18C15.9 18 15.01 18.9 15.01 20C15.01 21.1 15.9 22 17 22C18.1 22 19 21.1 19 20C19 18.9 18.1 18 17 18Z" fill="currentColor"/>
</svg>

```bash
cart
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M3 5V19C3 20.1 3.89 21 5 21H19C20.1 21 21 20.1 21 19V5C21 3.9 20.1 3 19 3H5C3.89 3 3 3.9 3 5ZM15 9C15 10.66 13.66 12 12 12C10.34 12 9 10.66 9 9C9 7.34 10.34 6 12 6C13.66 6 15 7.34 15 9ZM6 17C6 15 10 13.9 12 13.9C14 13.9 18 15 18 17V18H6V17Z" fill="currentColor"/>
</svg>

```bash
contact
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M17 16L13 12V8.82C14.16 8.4 15 7.3 15 6C15 4.34 13.66 3 12 3C10.34 3 9 4.34 9 6C9 7.3 9.84 8.4 11 8.82V12L7 16H3V21H8V17.95L12 13.75L16 17.95V21H21V16H17Z" fill="currentColor"/>
</svg>

```bash
share
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M12 2C6.48 2 2 6.48 2 12C2 17.52 6.48 22 12 22C17.52 22 22 17.52 22 12C22 6.48 17.52 2 12 2ZM10 16.5V7.5L16 12L10 16.5Z" fill="currentColor"/>
</svg>

```bash
video
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M20 4H4C2.9 4 2.01 4.9 2.01 6L2 18C2 19.1 2.9 20 4 20H20C21.1 20 22 19.1 22 18V6C22 4.9 21.1 4 20 4ZM20 8L12 13L4 8V6L12 11L20 6V8Z" fill="currentColor"/>
</svg>

```bash
email
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M12 12C14.21 12 16 10.21 16 8C16 5.79 14.21 4 12 4C9.79 4 8 5.79 8 8C8 10.21 9.79 12 12 12ZM12 14C9.33 14 4 15.34 4 18V20H20V18C20 15.34 14.67 14 12 14Z" fill="currentColor"/>
</svg>

```bash
user
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M2 20H4C4.55 20 5 19.55 5 19V10C5 9.45 4.55 9 4 9H2V20ZM21.83 12.88C21.94 12.63 22 12.36 22 12.08V11C22 9.9 21.1 9 20 9H14.5L15.42 4.35C15.47 4.13 15.44 3.89 15.34 3.69C15.11 3.24 14.82 2.83 14.46 2.47L14 2L7.59 8.41C7.21 8.79 7 9.3 7 9.83V17.67C7 18.95 8.05 20 9.34 20H17.45C18.15 20 18.81 19.63 19.17 19.03L21.83 12.88Z" fill="currentColor"/>
</svg>

```bash
like
```

----------------------------

<svg width="24" height="24" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg">
  <path d="M18 8C18 4.69 15.31 2 12 2C8.69 2 6 4.69 6 8C6 12.5 12 19 12 19C12 19 18 12.5 18 8ZM10 8C10 6.9 10.9 6 12 6C13.1 6 14 6.9 14 8C14 9.1 13.11 10 12 10C10.9 10 10 9.1 10 8ZM5 20V22H19V20H5Z" fill="currentColor"/>
</svg>

```bash
pin-drop
```

#### Keyword
------------------------

Là định danh của atom, nó là duy nhất và sẽ được bảo toàn mãi mãi.

**Bắt buộc:**
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
