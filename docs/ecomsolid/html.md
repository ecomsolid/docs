# HTML

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
#### HTML với snippets chưa clone
------------------------
Định nghĩa snippets của tree có chứa clone:
```json
{
  "attribute": "tabs",
  "atom": "Box",
  "title": "Box",
  "clone": true, // <- thuộc tính clone
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

HTML tương ứng với snippets:
```html
<Box attribute="tabs">
  <% for(let i = 0; i < tabs; i++) { %>
    <Box attribute="itemTab" index="<%-i%>">
      <Button attribute="buttonItem"/>
    </Box>
  <% } %>
</Box>
```
- `tabs`: Biến tabs ở vòng for ứng với số lượng con của `"attribute": "tabs"`. Eg: nếu có 3 phần tử con thì `tabs=3`
- `index="<%-i%>"`: Cần gắn index vào phần tử con bao ngoài cùng. Điều này là bắt buộc

>[!tip]
>Để an toàn hơn bạn có thể kiểm tra `if (tabs && tabs.length) { for }` trước khi for

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

### bgImage
------------------------

### attr
------------------------

### icon
------------------------
