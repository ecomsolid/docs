## Cấu trúc chuẩn

### Các lưu ý

### Cấu trúc

#### Wapper

<!-- tabs:start -->


##### ** HTML **

```html
<div class="gt_atom-<%-id%> gt_transition" id="a-<%-id%>" data-name="<%=name%>">
  <slot></slot> 
</div>

```
##### ** Snippets **

```json
[
  {
    "id": "content",
    "settings": [

    ]
  },
  {
    "id": "design",
    "settings": [

    ]
  }
]
```

<!-- tabs:end -->

>[!note]
> Wapper là dạng chia tabs để chứa settings và design


#### Settings

>[!note]
> Sections/widgets hoặc atoms đều có những setting riêng. Eg: Icon thì có pickIcon, Image thì có uploadImage

#### Design
Design sẽ cần flow theo chuẩn chung để giúp khách hàng quen thuộc hơn khi sử dụng Editor. Điều này cũng giúp việc code giảm thiểu hơn khi có thể copy code cũ đề đưa vào sections/atoms mới sau đó optimize lại cho phù hợp hơn.
##### Size
<!-- tabs:start -->
###### ** Snippets **

```json
CODE
```

###### ** Styles **

```scss
CODE
```

<!-- tabs:end -->

##### Display
<!-- tabs:start -->
###### ** Snippets **

```json
{
  "id": "boxDisplay",
  "title": "Display",
  "items": [
    {
      "id": "displayTypeActive",
      "attribute": "displayTypeActive",
      "title": "Type (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "displayType",
              "alignItemsActive",
              "justifyContentActive",
              "flexDirectionReverse"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "displayType",
      "attribute": "displayType",
      "title": "Type",
      "reference": "css",
      "value": "row",
      "type": "segment",
      "options": [
        {
          "text": "Row",
          "value": "row"
        },
        {
          "text": "Column",
          "value": "column"
        }
      ]
    },
    {
      "id": "flexDirectionReverse",
      "attribute": "flexDirectionReverse",
      "title": "Direction Reverse",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false
    },
    {
      "id": "alignItemsActive",
      "attribute": "alignItemsActive",
      "title": "Align Items (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "alignItems"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "alignItems",
      "attribute": "alignItems",
      "title": "Align Items",
      "reference": "css",
      "value": "unset",
      "type": "select",
      "options": [
        {
          "text": "Start",
          "value": "flex-start"
        },
        {
          "text": "Center",
          "value": "center"
        },
        {
          "text": "End",
          "value": "flex-end"
        }
      ]
    },
    {
      "id": "justifyContentActive",
      "attribute": "justifyContentActive",
      "title": "Justify Content (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "justifyContent"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "justifyContent",
      "attribute": "justifyContent",
      "title": "Justify Content",
      "reference": "css",
      "value": "unset",
      "type": "select",
      "options": [
        {
          "text": "Start",
          "value": "flex-start"
        },
        {
          "text": "Center",
          "value": "center"
        },
        {
          "text": "End",
          "value": "flex-end"
        },
        {
          "text": "Space Between",
          "value": "space-between"
        }
      ]
    }
  ]
}
```

###### ** Styles **

```css
#a-<%-id%> {
  <% if (displayTypeActive) { %>
    display: flex;

    <% if (flexDirectionReverse) { %>
      flex-direction: <%-displayType%>-reverse;
    <% } else { %>
      flex-direction: <%-displayType%>;
    <% } %>

    <% if (alignItemsActive) { %>
      align-items: <%-alignItems%>;
    <% } %>
    
    <% if (justifyContentActive) { %>
      justify-content: <%-justifyContent%>;
    <% } %>
  <% } %>
}
```

<!-- tabs:end -->

##### Typography
<!-- tabs:start -->
###### ** Snippets **

```json
CODE
```

###### ** Styles **

```css
CODE
```

<!-- tabs:end -->


##### Background
<!-- tabs:start -->
###### ** Snippets **

```json
{
  "id": "boxBackground",
  "title": "Background",
  "extend": true,
  "items": [
    {
      "id": "backgroundTypeActive",
      "attribute": "backgroundTypeActive",
      "title": "Background (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "backgroundType"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundType",
      "attribute": "backgroundType",
      "title": "Type",
      "reference": "css",
      "value": "color",
      "type": "segment",
      "options": [
        {
          "text": "Color",
          "value": "color"
        },
        {
          "text": "Image",
          "value": "image"
        }
      ],
      "links": [
        {
          "value": "color",
          "snippet": {
            "ids": [
              "backgroundColor",
              "hoverBackgroundColor"
            ],
            "hide": false
          }
        },
        {
          "value": "image",
          "snippet": {
            "ids": [
              "backgroundImage",
              "backgroundFixed",
              "backgroundRepeat",
              "backgroundPosition"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundColor",
      "attribute": "backgroundColor",
      "title": "Color",
      "reference": "css",
      "value": "#fff",
      "type": "colorpicker",
      "readonly": false,
      "popup": true
    },
    {
      "id": "hoverBackgroundColor",
      "attribute": "hoverBackgroundColor",
      "title": "Hover Color",
      "reference": "css",
      "value": "#fff",
      "type": "colorpicker",
      "readonly": false,
      "popup": true
    },
    {
      "id": "backgroundImage",
      "attribute": "backgroundImage",
      "title": "Image",
      "reference": "css",
      "type": "imageuploader",
      "value": ""
    }
  ],
  "more": [
    {
      "id": "backgroundFixedActive",
      "attribute": "backgroundFixedActive",
      "title": "Fixed (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "backgroundFixed"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundFixed",
      "attribute": "backgroundFixed",
      "title": "Fixed",
      "reference": "css",
      "value": "fixed",
      "type": "select",
      "options": [
        {
          "text": "Fixed",
          "value": "fixed"
        },
        {
          "text": "Initial",
          "value": "Initial"
        }
      ]
    },
    {
      "id": "backgroundSizeActive",
      "attribute": "backgroundSizeActive",
      "title": "Size (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "backgroundSize"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundSize",
      "attribute": "backgroundSize",
      "title": "Size",
      "reference": "css",
      "value": "cover",
      "type": "select",
      "options": [
        {
          "text": "Auto",
          "value": "auto"
        },
        {
          "text": "Cover",
          "value": "cover"
        },
        {
          "text": "Contain",
          "value": "contain"
        },
        {
          "text": "Custom",
          "value": "custom"
        }
      ],
      "links": [
        {
          "value": "custom",
          "snippet": {
            "ids": [
              "backgroundSizeCustom"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundSizeCustom",
      "attribute": "backgroundSizeCustom",
      "title": "Custom Size",
      "reference": "css",
      "value": "100%",
      "type": "input:unit",
      "units": [
        "px",
        "%"
      ],
      "min": 0
    },
    {
      "id": "backgroundRepeatActive",
      "attribute": "backgroundRepeatActive",
      "title": "Repeat (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "backgroundRepeat"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundRepeat",
      "attribute": "backgroundRepeat",
      "title": "Repeat",
      "reference": "css",
      "value": "no-repeat",
      "type": "select",
      "options": [
        {
          "text": "No-repeat",
          "value": "no-repeat"
        },
        {
          "text": "Repeat",
          "value": "repeat"
        },
        {
          "text": "Repeat-x",
          "value": "repeat-x"
        },
        {
          "text": "Repeat-y",
          "value": "repeat-y"
        }
      ]
    },
    {
      "id": "backgroundPositionActive",
      "attribute": "backgroundPositionActive",
      "title": "Position (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "backgroundPosition"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundPosition",
      "attribute": "backgroundPosition",
      "title": "Position",
      "reference": "css",
      "value": "center center",
      "type": "select",
      "options": [
        {
          "text": "Center Center",
          "value": "center center"
        },
        {
          "text": "Center Top",
          "value": "center top"
        },
        {
          "text": "Center Bottom",
          "value": "center bottom"
        },
        {
          "text": "Left Top",
          "value": "left top"
        },
        {
          "text": "Left Center",
          "value": "left center"
        },
        {
          "text": "Left Bottom",
          "value": "left bottom"
        },
        {
          "text": "Right Top",
          "value": "right top"
        },
        {
          "text": "Right Center",
          "value": "right center"
        },
        {
          "text": "Right Bottom",
          "value": "right bottom"
        },
        {
          "text": "Custom",
          "value": "custom"
        }
      ],
      "links": [
        {
          "value": "custom",
          "snippet": {
            "ids": [
              "backgroundPositionX",
              "backgroundPositionY"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "backgroundPositionX",
      "attribute": "backgroundPositionX",
      "title": "PositionX",
      "reference": "css",
      "value": "0%",
      "type": "input:unit",
      "units": [
        "px",
        "%"
      ]
    },
    {
      "id": "backgroundPositionY",
      "attribute": "backgroundPositionY",
      "title": "PositionY",
      "reference": "css",
      "value": "0%",
      "type": "input:unit",
      "units": [
        "px",
        "%"
      ]
    }
  ]
}
```

###### ** Styles **

```css
#a-<%-id%> {
  <% if (backgroundTypeActive) { %>
    <% if (backgroundType == "color") { %>
      background-color: <%-backgroundColor%>;
    <% } %>
    <% if (backgroundType == "image") { %>
      background-image: url("<%-backgroundImage%>");
      <% if (backgroundFixedActive) { %>
        background-attachment: <%-backgroundFixed%>;
      <% } %>
      <% if (backgroundSizeActive) { %>
        <% if (backgroundSize && backgroundSize != "custom") { %>
          background-size: <%-backgroundSize%>;
        <% } %>
        <% if (backgroundSize && backgroundSize == "custom") { %>
          background-size: <%-backgroundSizeCustom%>;
        <% } %>
      <% } %>
      <% if (backgroundRepeatActive) { %>
        background-repeat: <%-backgroundRepeat%>;
      <% } %>
      <% if (backgroundPositionActive) { %>
        <% if (backgroundPosition && backgroundPosition != "custom") { %>
          background-position: <%-backgroundPosition%>;
        <% } %>
        <% if (backgroundPosition && backgroundPosition == "custom") { %>
          background-position: <%-backgroundPositionX%> <%-backgroundPositionY%>;
        <% } %>
      <% } %>
    <% } %>
  <% } %>
}

#a-<%-id%>:hover {
  <% if (backgroundTypeActive) { %>
    <% if (backgroundType == "color") { %>
      background-color: <%-hoverBackgroundColor%>;
    <% } %>
  <% } %>
}
```

<!-- tabs:end -->

##### Border
<!-- tabs:start -->

###### ** Snippets **
```json
CODE
```
###### ** Styles **

```css
CODE
```

<!-- tabs:end -->

##### Animations
<!-- tabs:start -->
###### ** Snippets **

```json
CODE
```

###### ** Styles **

```css
CODE
```

<!-- tabs:end -->

##### Effects
<!-- tabs:start -->
###### ** Snippets **

```json
CODE
```

###### ** Styles **

```css
CODE
```

<!-- tabs:end -->

##### Spacing
<!-- tabs:start -->
###### ** Snippets **

```json
CODE
```

###### ** Styles **

```css
CODE
```

<!-- tabs:end -->

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
