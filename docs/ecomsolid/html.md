## Các thuộc tính cơ bản
------------------------

## Quy tắc chung
------------------------

### Làm việc với atoms
#### HTML cơ bản
------------------------
```html
<section class="gt_section-<%=id%> <%=extraClass%>" data-name="<%=name%>">
  <Box attribute="contentWapper">
    <Button attribute="buttonAddToCart"/>
  </Box>
</section>
```
#### HTML với snippets chứa clone
------------------------
Định nghĩa snippets của tree có chứa clone:
```json
{
  "attribute": "tabs",
  "atom": "Box",
  "title": "Box",
  "clone": true, // <- thuộc tính clone cho phép children cấp 1 có thể clone/remove...
  "children": [
    {
      "attribute": "itemTab",
      "atom": "Box",
      "title": "Box",
      "children": [
        {
          "attribute": "buttonItem",
          "atom": "Button",
          "title": "Button",
          "value": "Item 1"
        }
      ]
    }
  ]
}
```

#### HTML chứa data shopify (product, collection, aricle, blog)
------------------------
Việc thêm `data-cache` giúp editor hiểu dữ liệu này dùng các biến của shopify và từ đó render tốt hơn.
`data-cache` có thể dùng cả với element
```html
<h1 class="gt_atom-<%-id%>" id="a-<%-id%>" data-name="<%-name%>" data-cache="{'shopify-product-id': '{{product.id}}'}">
  {{product.title}}
</h1>
```
>[!note]
> Dữ liệu bên trong `data-cache` phải là một object

Ngoài ra chúng ta còn có thể sử dụng các thuộc tính khác như:
```html
shopify-product-id
shopify-collection-id
shopify-blog-id
shopify-aricle-id
...
```

#### Thêm code trên dưới một atom
------------------------

Bạn có thể viết `liquid` `html` hoặc bất cứ thứ gì bạn muốn vào trong thẻ `Before` và `After`

```html
<Before>
  Code Here
</Before>
<ProductPrice />
<After>
  Code Here
</After>
```

### Quy tắc sử dụng class
------------------------
```html
<div class="gt_flex gt_header-content">
```
- Class global luôn nằm trong cùng để có sức mạnh thấp nhất


### Làm việc với Product
------------------------

### Tạo hook trong Section
------------------------

```html
<%- hook({
    name: "Before Product",
    style: "width: 100%; height: 50px;"
}) %>
```

## Các hàm phụ trợ từ EJS
------------------------
### text
------------------------
```html
<% if (headingText != ""){ %>
   <h2>
        <%-text({
            text: headingText,
            snippet: {
                attribute: "headingText",
                //index: i
            },
        })%>
    </h2>
<% } %>

// index trong menu
index = i1(level 1) + "|" i2(level 2)
```

Nếu sử dụng hàm Text và hàm Html thì sẽ không cần sử dụng optimize cho các control nữa

> [!Tip]
>  i chính là số thứ tự trong tabs. Nếu không có thì bỏ qua thuộc tính index

### image
------------------------
```html
<div class="gt_herobanner-image">
    <%-image({
        src: imageBackground,
        snippet: {
            attribute: "imageBackground",
            //index: i
        },
        class: "product_image gt_lazyload",
        size: "100x",
        attr: {
            "alt": texHeading,
        }
    })%>
</div>
```

> [!Tip]
>  i chính là số thứ tự trong tabs. Nếu không có thì bỏ qua thuộc tính index

### bgImage
------------------------
```html
<div <%-bgImage({
    src: imageBackground,
    snippet: {
        attribute: "imageBackground",
        //index: i
    },
    class: "gt_herobanner-image gt_lazyload",
    size: "100x"
})%> >
    <span></span>
</div>
```

> [!Tip]
>  i chính là số thứ tự trong tabs. Nếu không có thì bỏ qua thuộc tính index

### attr
------------------------
```html
<% if (headingText != ""){ %>
   <a <%-attr([{
        placeholder: placeholderText,
        snippet: {
            attribute: "placeholderText",
            //index: i
        },
    },
    {
        title: titleText,
        snippet: {
            attribute: "titleText",
            //index: i
        },
    }])%> ></a>
<% } %>
```

### icon
------------------------
```html
<h1 class="wapper">
  <%-icon({
    iconData: sectionIcon,
    snippet: {
        attribute: "sectionIcon",
        //index: i
    },
  })%>
</h1>
```