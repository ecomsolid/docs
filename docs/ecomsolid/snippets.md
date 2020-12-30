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

#### Sticky Settings
>[!note]
> Một số Sections/widgets sẽ có sự thay đổi từ trạng thái position *relative -> absolute/sticky* nên trong Atom cần có các setting cho trạng thái việc chuyển đổi trạng thái đó (Quy đinh là: *stickySettings*) và cần cho phép ẩn hiện tuỳ vào Section/Widgets.

Mặc định các stickySettings trong Atom cần được ẩn, truyền settings qua snippet gọi Atom trong Section để hiện stickySettings 
<!-- tabs:start -->
###### ** Snippets Atom Menu **

```json
[
  {
    "id": "content",
    "settings": [],
  },
  {
    "id": "design",
    "settings": [
      {
        "id": "stickySettings",
        "attribute": "stickySettings",
        "value": false,
        "type": "switch",
        "readonly": false,
        "noRender": true, // Thuộc tính này cho phép control sẽ không được hiển thị trên sidebar
        "links": [
          {
            "value": true,
            "snippet": {
              "ids": [
                "attribute1",
                "attribute2"
              ],
              "hide": false,
            }
          }
        ]
      },
      {
        "id": "attribute1",
        "attribute": "attribute1",
        "value": "value",
        ...
      },
      ,
      {
        "id": "attribute2",
        "attribute": "attribute2",
        "value": "value",
        ...
      }
    ]
  }
]
```

###### ** Snippets Section (Enable Sticky Settings)**

```json
{
  "attribute": "headerMenu",
  "atom": "Menu",
  "title": "Menu",
  "value": [],
  "settings": {
    "stickySettings": true,
  }
}
```
<!-- tabs:end -->

#### Settings

````json
{
  "id": "boxSettings",
  "title": "Settings",
  "extend": true,
  "items": []
}
````

>[!note]
> Sections/widgets hoặc atoms đều có những setting riêng. Eg: Icon thì có pickIcon, Image thì có uploadImage

#### Design
Design sẽ cần flow theo chuẩn chung để giúp khách hàng quen thuộc hơn khi sử dụng Editor. Điều này cũng giúp việc code giảm thiểu hơn khi có thể copy code cũ đề đưa vào sections/atoms mới sau đó optimize lại cho phù hợp hơn.
##### Size
<!-- tabs:start -->
###### ** Snippets **

```json
{
  "id": "boxSize",
  "title": "Size",
  "extend": true,
  "items": [
    {
      "id": "widthActive",
      "attribute": "widthActive",
      "title": "Width (On/Off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "width"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "width",
      "attribute": "width",
      "title": "Width",
      "reference": "css",
      "value": "100%",
      "type": "input:unit",
      "units": [
        "px",
        "%"
      ],
      "min": 0,
      "screens": [
        {
          "id": "lg",
          "value": "100%"
        },
        {
          "id": "md",
          "value": "100%"
        },
        {
          "id": "sm",
          "value": "100%"
        },
        {
          "id": "xs",
          "value": "100%"
        }
      ]
    },
    {
      "id": "heightActive",
      "attribute": "heightActive",
      "title": "Height (On/Off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "height"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "height",
      "attribute": "height",
      "title": "Height",
      "reference": "css",
      "value": "100%",
      "type": "input:unit",
      "units": [
        "px",
        "%"
      ],
      "min": 0,
      "screens": [
        {
          "id": "lg",
          "value": "100%"
        },
        {
          "id": "md",
          "value": "100%"
        },
        {
          "id": "sm",
          "value": "100%"
        },
        {
          "id": "xs",
          "value": "100%"
        }
      ]
    }
  ]
}
```

###### ** Styles **

```scss
#gt_atom-1 {
  /*<% if(widthActive) { %>*/
    /*width: <%-width%>;*/
  /*<% } %>*/
  /*<% if(heightActive) { %>*/
    /*height: <%-height%>;*/
  /*<% } %>*/
  @media (max-width: 1200px) {
    /*<% if(widthActive) { %>*/
      /*width: <%-width_md%>;*/
    /*<% } %>*/
    /*<% if(heightActive) { %>*/
      /*height: <%-height_md%>;*/
    /*<% } %>*/
  }
  @media (max-width: 992px) {
    /*<% if(widthActive) { %>*/
      /*width: <%-width_sm%>;*/
    /*<% } %>*/
    /*<% if(heightActive) { %>*/
      /*height: <%-height_sm%>;*/
    /*<% } %>*/
  }
  @media (max-width: 576px) {
    /*<% if(widthActive) { %>*/
      /*width: <%-width_xs%>;*/
    /*<% } %>*/
    /*<% if(heightActive) { %>*/
      /*height: <%-height_xs%>;*/
    /*<% } %>*/
  }
}
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
#gt_atom-1 {
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
{
  "id": "boxTypography",
  "title": "Typography",
  "extend": true,
  "items": [
    {
      "id": "textSizeActive",
      "attribute": "textSizeActive",
      "title": "Font Size (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "textSize"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "textSize",
      "attribute": "textSize",
      "title": "Font Size",
      "reference": "css",
      "value": "16px",
      "type": "range:unit",
      "min": 0,
      "max": 100,
      "changing": 1,
      "units": [
        "em",
        "px"
      ],
      "initial": true,
      "inherit": "themeTextFontSize",
      "screens": [
        {
          "id": "lg",
          "value": "16px"
        },
        {
          "id": "md",
          "value": "16px"
        },
        {
          "id": "sm",
          "value": "16px"
        },
        {
          "id": "xs",
          "value": "16px"
        }
      ]
    },
    {
      "id": "textColorActive",
      "attribute": "textColorActive",
      "title": "Text (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": false,
          "snippet": {
            "ids": [
              "textColor"
            ],
            "hide": true
          }
        }
      ]
    },
    {
      "id": "textColor",
      "attribute": "textColor",
      "title": "Text",
      "desc": "",
      "reference": "css",
      "value": "#ff00ff",
      "type": "colorpicker",
      "readonly": false,
      "popup": true,
      "initial": true,
      "inherit": "themeTextColor"
    },
    {
      "id": "textHoverColorActive",
      "attribute": "textHoverColorActive",
      "title": "Hover Text (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": false,
          "snippet": {
            "ids": [
              "textHoverColor"
            ],
            "hide": true
          }
        }
      ]
    },
    {
      "id": "textHoverColor",
      "attribute": "textHoverColor",
      "title": "Hover Text",
      "reference": "css",
      "value": "#ff00ff",
      "type": "colorpicker",
      "readonly": false,
      "popup": true,
      "initial": true,
      "inherit": "themeTextColor"
    },
    {
      "id": "textAlignActive",
      "attribute": "textAlignActive",
      "title": "Align (on/off)",
      "reference": "css",
      "value": true,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "textAlign"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "textAlign",
      "attribute": "textAlign",
      "title": "Align",
      "reference": "css",
      "value": "left",
      "type": "select",
      "options": [
        {
          "text": "Left",
          "value": "left"
        },
        {
          "text": "Right",
          "value": "right"
        },
        {
          "text": "Center",
          "value": "center"
        },
        {
          "text": "Justify",
          "value": "justify"
        }
      ]
    },
    {
      "id": "textDecorationActive",
      "attribute": "textDecorationActive",
      "title": "Decoration (on/off)",
      "reference": "css",
      "value": true,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "textDecoration"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "textDecoration",
      "attribute": "textDecoration",
      "title": "Decoration",
      "reference": "underline",
      "value": "left",
      "type": "select",
      "options": [
        {
          "text": "Overline",
          "value": "overline"
        },
        {
          "text": "Line Through",
          "value": "line-through"
        },
        {
          "text": "Underline",
          "value": "underline"
        },
        {
          "text": "Underline Overline",
          "value": "underline overline"
        }
      ]
    }
  ]
}
```

###### ** Styles **

```css
#gt_atom-1 {
  <% if (textColorActive) { %>
    color: <%-textColor%>;
  <% } %>
  <% if (textSizeActive) { %>
    font-size: <%-textSize%>;
  <% } %>
  <% if (textAlignActive) { %>
    text-align: <%-textAlign%>;
  <% } %>
  <% if (textDecorationActive) { %>
    text-decoration: <%-textDecoration%>;
  <% } %>
}

#gt_atom-1:hover, #gt_atom-1.gt_hover {
  <% if (textHoverColorActive) { %>
    color: <%-textHoverColor%>;
  <% } %>
}

@media (max-width: 1200px) {
  #gt_atom-1 {
    <% if (textSizeActive) { %>
      font-size: <%-textSize_md%>;
    <% } %>
  }
}
@media (max-width: 992px) {
  #gt_atom-1 {
    <% if (textSizeActive) { %>
      font-size: <%-textSize_sm%>;
    <% } %>
  }
}
@media (max-width: 576px) {
  #gt_atom-1 {
    <% if (textSizeActive) { %>
      font-size: <%-textSize_xs%>;
    <% } %>
  }
}

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
#gt_atom-1 {
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

#gt_atom-1:hover, #gt_atom-1.gt_hover {
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
{
  "id": "boxBorder",
  "title": "Border",
  "extend": true,
  "items": [
    {
      "id": "borderRadiusActive",
      "attribute": "borderRadiusActive",
      "title": "Radius (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "borderRadius"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "borderRadius",
      "attribute": "borderRadius",
      "title": "Radius",
      "reference": "css",
      "value": "0px",
      "type": "input:unit",
      "units": [
        "px",
        "%"
      ],
      "min": 0
    },
    {
      "id": "turnOnBorder",
      "attribute": "turnOnBorder",
      "title": "Border (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "borderWidth",
              "borderColor",
              "hoverBorderColor",
              "borderStyle",
              "borderDirection"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "borderWidth",
      "attribute": "borderWidth",
      "title": "Border Width",
      "reference": "css",
      "value": 1,
      "type": "input:number",
      "min": 0
    },
    {
      "id": "borderColor",
      "attribute": "borderColor",
      "title": "Color",
      "reference": "css",
      "value": "unset",
      "type": "colorpicker",
      "readonly": false,
      "popup": true
    },
    {
      "id": "hoverBorderColor",
      "attribute": "hoverBorderColor",
      "title": "Hover Color",
      "reference": "css",
      "value": "unset",
      "type": "colorpicker",
      "readonly": false,
      "popup": true
    }
  ],
  "more": [
    {
      "id": "borderStyle",
      "attribute": "borderStyle",
      "title": "Style",
      "reference": "css",
      "value": "solid",
      "type": "select",
      "options": [
        {
          "text": "Solid",
          "value": "solid"
        },
        {
          "text": "Dashed",
          "value": "dashed"
        },
        {
          "text": "Dotted",
          "value": "dotted"
        },
        {
          "text": "Double",
          "value": "double"
        }
      ]
    },
    {
      "id": "borderDirection",
      "attribute": "borderDirection",
      "title": "Direction",
      "reference": "css",
      "value": "all",
      "type": "select",
      "options": [
        {
          "text": "All",
          "value": "all"
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
              "borderDirectionX",
              "borderDirectionY"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "borderDirectionX",
      "attribute": "borderDirectionX",
      "title": "Direction X",
      "reference": "css",
      "value": "left",
      "type": "select",
      "options": [
        {
          "text": "Unset",
          "value": "unset"
        },
        {
          "text": "Left",
          "value": "left"
        },
        {
          "text": "Right",
          "value": "right"
        },
        {
          "text": "Left + Right",
          "value": "left+right"
        }
      ]
    },
    {
      "id": "borderDirectionY",
      "attribute": "borderDirectionY",
      "title": "Direction Y",
      "reference": "css",
      "value": "top",
      "type": "select",
      "options": [
        {
          "text": "Unset",
          "value": "unset"
        },
        {
          "text": "Top",
          "value": "top"
        },
        {
          "text": "Bottom",
          "value": "bottom"
        },
        {
          "text": "Top + Bottom",
          "value": "top+bottom"
        }
      ]
    }
  ]
}
```
###### ** Styles **

```css
#gt_atom-1 {
  <% if (borderRadiusActive) { %>
    border-radius: <%-borderRadius%>;
  <% } %>

  <% if (turnOnBorder) { %>
    <% if (borderDirection == "all") { %>
      border: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
    <% } %>
    <% if (borderDirection == "custom") { %>
      <% if (borderDirectionX == "left") { %>
        border-left: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
      <% } else if (borderDirectionX == "right") { %>
        border-right: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
      <% } else if (borderDirectionX == "left+right") { %>
        border-left: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
        border-right: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
      <% } %>
      <% if (borderDirectionY == "top") { %>
        border-top: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
      <% } else if (borderDirectionY == "bottom") { %>
        border-bottom: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
      <% } else if (borderDirectionY == "top+bottom") { %>
        border-top: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
        border-bottom: <%-borderStyle%> <%-borderWidth%>px <%-borderColor%>;
      <% } %>
    <% } %>
  <% } %>
}

#gt_atom-1:hover, #gt_atom-1.gt_hover {
  <% if (turnOnBorder) { %>
    border-color: <%-hoverBorderColor%>;
  <% } %>
}
```

<!-- tabs:end -->


##### Spacing
<!-- tabs:start -->
###### ** Snippets **

```json
{
  "id": "boxSpacing",
  "title": "Spacing",
  "extend": true,
  "items": [
    {
      "id": "marginActive",
      "attribute": "marginActive",
      "title": "Margin (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "margin"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "margin",
      "attribute": "margin",
      "title": "Margin",
      "reference": "css",
      "type": "margin",
      "value": "0px 0px 0px 0px",
      "screens": [
        {
          "id": "lg",
          "value": "0px 0px 0px 0px"
        },
        {
          "id": "md",
          "value": "0px 0px 0px 0px"
        },
        {
          "id": "sm",
          "value": "0px 0px 0px 0px"
        },
        {
          "id": "xs",
          "value": "0px 0px 0px 0px"
        }
      ]
    },
    {
      "id": "paddingActive",
      "attribute": "paddingActive",
      "title": "Padding (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "padding"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "padding",
      "attribute": "padding",
      "title": "Padding",
      "reference": "css",
      "type": "padding",
      "value": "0px 0px 0px 0px",
      "screens": [
        {
          "id": "lg",
          "value": "0px 0px 0px 0px"
        },
        {
          "id": "md",
          "value": "0px 0px 0px 0px"
        },
        {
          "id": "sm",
          "value": "0px 0px 0px 0px"
        },
        {
          "id": "xs",
          "value": "0px 0px 0px 0px"
        }
      ]
    }
  ]
}
```
###### ** Styles **

```css
#gt_atom-1 {
  <% if (marginActive) { %>
    margin: <%-margin%>;
  <% } %>

  <% if (paddingActive) { %>
    padding: <%-padding%>;
  <% } %>
}

@media (max-width: 1200px) {
  #gt_atom-1 {
    <% if (marginActive) { %>
      margin: <%-margin_md%>;
    <% } %>
    <% if (paddingActive) { %>
      padding: <%-padding_md%>;
    <% } %>
  }
}
@media (max-width: 992px) {
  #gt_atom-1 {
    <% if (marginActive) { %>
      margin: <%-margin_sm%>;
    <% } %>
    <% if (paddingActive) { %>
      padding: <%-padding_sm%>;
    <% } %>
  }
}
@media (max-width: 576px) {
  #gt_atom-1 {
    <% if (marginActive) { %>
      margin: <%-margin_xs%>;
    <% } %>
    <% if (paddingActive) { %>
      padding: <%-padding_xs%>;
    <% } %>
  }
}
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
{
  "id": "boxEffects",
  "title": "Effects",
  "extend": true,
  "items": [
    {
      "id": "opacityActive",
      "attribute": "opacityActive",
      "title": "Opacity (on/off)",
      "reference": "css",
      "value": true,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "opacity"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "opacity",
      "attribute": "opacity",
      "title": "Opacity",
      "reference": "css",
      "value": 1,
      "type": "range",
      "min": 0,
      "max": 1,
      "changing": 0.1
    },
    {
      "id": "boxShadowActive",
      "attribute": "boxShadowActive",
      "title": "Shadow (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "boxShadow"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "boxShadow",
      "attribute": "boxShadow",
      "title": "Shadow",
      "reference": "css",
      "type": "shadow",
      "value": "0px 0px 0px 0px #ccc",
      "readonly": false
    },
    {
      "id": "hoverBoxShadowActive",
      "attribute": "hoverBoxShadowActive",
      "title": "Hover Shadow (on/off)",
      "reference": "css",
      "value": false,
      "type": "switch",
      "readonly": false,
      "links": [
        {
          "value": true,
          "snippet": {
            "ids": [
              "hoverBoxShadow"
            ],
            "hide": false
          }
        }
      ]
    },
    {
      "id": "hoverBoxShadow",
      "attribute": "hoverBoxShadow",
      "title": "Hover Shadow",
      "reference": "css",
      "type": "shadow",
      "value": "0px 0px 0px 0px #ccc",
      "readonly": false
    }
  ]
}
```

###### ** Styles **

```css
#gt_atom-1 {
  <% if (opacityActive) { %>
    opacity: <%-opacity%>;
  <% } %>
  <% if (boxShadowActive) { %>
    <% if (boxShadow) { %>
      box-shadow: <%-boxShadow%>;
    <% } %>
  <% } %>
}

#gt_atom-1:hover, #gt_atom-1.gt_hover {
  <% if (hoverBoxShadowActive) { %>
    <% if (hoverBoxShadow) { %>
        box-shadow: <%-hoverBoxShadow%>;
    <% } %>
  <% } %>
}
```

<!-- tabs:end -->

## Thuộc tính mở rộng
------------------------

### AdvancedMode: Định nghĩa snippet nâng cao

Thuộc tính này giúp xác định đây là một control nâng cao, chỉ khi khách hàng bật chức năng **Advanced Mode** trong editor thì control này mới xuất hiện

```json
"advancedMode": true
```


### PlanId: Định nghĩa snippet cho các plan khác nhau

Thuộc tính này giúp xác định đây là một control cho một plan nào đó. Khi khách hàng nâng cấp plan thì control sẽ xuất hiện

```json
"planId": 2
```
- Nếu không có thuộc tính này thì tất cả plan đều được sử dụng
- `2` nếu control này cho plan Professional trở nên
- `3` nếu control này cho plan Premium trở nên

>[!note]
>Bạn có thể dụng planId với tab **design** để khoá toàn bộ tab design đối với khách hàng `free`

### Plans: Định nghĩa sự thay đổi thuộc tính theo plan

Thuộc tính này giúp khóa một tính năng hoặc giới hạn tính năng cho từng plan cụ thể:
```json
"plans": [
  {
    "plan": "free",
    "max": 1
  },
  {
    "plan": "professional",
    "max": 99999999
  }
],
```
Nhìn vào  đoạn code trên ta hiểu:

- Với plan "free" giới hạn là 1

- Với plan "professional" không giới hạn

Thuộc tính *max* được định nghĩa bởi control tương ứng. Nên bạn có thể custom rất nhiều thứ như sau:

```json
"plans": [
  {
    "plan": "free",
    "lock": true,
    "title": "Feature for Free"
  },
  {
    "plan": "professional",
    "lock": false,
    "title": "Feature for Pro"
  }
],
```

### Chia Tabs ở Settings

Trong setting của một section chúng ta có thể chia rõ ràng 2 tab là content và design để phục vụ hiện thị rõ ràng hơn
```json
[
  {
    "id": "content",
    "settings": [
      {
        "id": "textHeading",
        "title": "Text Heading",
        "desc": "",
        "attribute": "textHeading",
        "reference": "html",
        "value": "GIVE US YOUR BEST SHOT",
        "type": "input"
      }
    ]
  },
  {
    "id": "design",
    "settings": [
      {
        "id": "bgOverlay",
        "attribute": "bgOverlay",
        "title": "Background Overlay",
        "desc": "",
        "reference": "css",
        "value": "0.4",
        "type": "range",
        "min": 0,
        "max": 1,
        "changing": 0.01
      }
    ]
  }
]
```

### Kế thừa value từ global

Chúng ta có thể lấy dữ liệu global làm value mặc định cho snipepts. Điều này sẽ giúp màu sắc, font chữ được đồng bộ hơn với theme.
```json
{
  "id": "topbarFontFamily",
  "title": "Font",
  "attribute": "topbarFontFamily",
  "reference": "css",
  "value": "Montserrat",
  "type": "font",
  "initial": true,
  "inherit": "themeFontFamilySecondary"
}
```

- Thuộc tính: `"initial": true` thể hiện nó là dữ liệu ban đầu chưa bị thay đổi.
- Thuộc tính: `"inherit": "themeFontFamilySecondary"` nói rằng nó đang kế thừa dữ liệu ở attribute `themeFontFamilySecondary`

> Ngoài ra chúng ta có thể sử dụng cú pháp EJS để thêm global style vào value của snippet như sau:

```json
{
  "id": "marginHeading",
  "title": "Margin",
  "attribute": "marginHeading",
  "reference": "css",
  "value": "<%-themeSpacingMedium_lg%>px 0px <%-themeSpacingMedium_lg%>px 0px",
  "type": "margin",
  "screens":{
    "lg": "<%-themeSpacingMedium_lg%>px 0px <%-themeSpacingMedium_lg%>px 0px",
    "md": "<%-themeSpacingMedium_md%>px 0px <%-themeSpacingMedium_md%>px 0px",
    "sm": "<%-themeSpacingMedium_sm%>px 0px <%-themeSpacingMedium_sm%>px 0px",
    "xs": "<%-themeSpacingMedium_xs%>px 0px <%-themeSpacingMedium_xs%>px 0px"
  }
}
```
### Hide: Ẩn hiện control

Thuộc tính `"hide": true` giúp ẩn một control nào đó.
```json
{
  "id": "labelPrice",
  "attribute": "labelPrice",
  "reference": "html",
  "title": "Label Price",
  "type": "input",
  "value": "Price",
  "hide": true
}
```

Thuộc tính `hideOnScreens` giúp ẩn một control nào đó trên các màn hình cụ thể.

```json
{
  "id": "labelPrice",
  "attribute": "labelPrice",
  "reference": "html",
  "title": "Label Price",
  "type": "input",
  "value": "Price",
  "hideOnScreens": {
    "xs": true
  }
}

"hideOnScreens": {
  "lg": true,
  "md": true,
  "sm": true,
  "xs": true
}
```

### Links: Lập trình điều kiện cho control

Tại sao cần thuộc tính "links"?

Thuộc tính links giúp chúng ta liên kết các snippets với nhau một cách dễ dàng.

*Ví dụ: Ta có một nút Switch bật tắt trạng thái hiển thị text và một input điền nội dung text. Ta có thể dùng links để ẩn hiện input theo switch. Điều đó làm người dùng dễ hiểu hơn.*

<img width="20%" src="/images/ecomsolid/snippets/links-turn-off.png">
<img width="20%" src="/images/ecomsolid/snippets/links-turn-on.png">

```json
[
  {
    "id": "turnOnText",
    "attribute": "turnOnText",
    "title": "Switch",
    "reference": "html",
    "value": true,
    "type": "switch",
    "links": [
      {
        "value": true,
        "snippet": {
          "ids": [
            "contentText",
            "contentText2"
          ],
          "hide": false
        }
      },
      {
        "value": "auto",
        "snippet": {
          "id": "paddingProduct",
          "inherit": "themeFontFamilySecondary"
        }
      },
      {
        "value": "auto",
        "snippet": {
          "id": "paddingProduct",
          "value": "10px 10px 10px 10px"
        }
      },
      {
        "value": "auto",
        "snippet": {
          "id": "paddingProduct",
          "screens": [
            {
              "id": "lg",
              "value": "Xin chao"
            },
            {
              "id": "md",
              "value": "Xin chao"
            }
          ]
        }
      }
    ]
  },
  {
    "id": "contentText",
    "attribute": "contentText",
    "title": "Content Text",
    "reference": "html",
    "value": "Hello",
    "type": "input"
  }
]
```


### No Apply: Không ảnh hưởng đến iframe

Thuộc tính `"noApply": true` sẽ giúp control không apply sang iframe của người dùng.

Nó kết hợp với thuộc tính `links` giúp tạo các trường hợp đóng mở khác nhau phục vụ ẩn/hiện control.

```json
{
  "id": "labelPrice",
  "attribute": "labelPrice",
  "reference": "html",
  "title": "Label Price",
  "type": "input",
  "value": "Price",
  "noApply": true
}
```


### No Render: Không render control bên left side bar

Thuộc tính `"noRender": true` sẽ giúp control không được hiển thị ra ở left side bar.

Nó kết hợp với thuộc tính `links` giúp tạo các trường hợp ẩn hiện các trạng thái setting `hover`, `sticky`.

```json
{
  "id": "stickySetting",
  "attribute": "stickySetting",
  "value": false,
  "type": "switch",
  "readonly": false,
  "noRender": true,
  "links": [
    {
      "value": true,
      "snippet": {
        "ids": [
          "iconMenuSizeStickyActive",
          "iconMenuSizeSticky"
        ],
        "hide": false
      }
    }
  ]
}
```

### Reference: Định nghĩa phạm vị ảnh hưởng

reference giúp cho editor biết phạm vị ảnh hưởng của control này đến các vùng code khác nhau.

reference có thể là một chuỗi: "html", "css", "js"
```json
{
    "reference": "html"
}
```

**reference** cũng có thể là mảng
```json
{
    "reference": [
        "html",
        "css",
        "js"
    ]
}
```

### Items: Tạo nhóm snippets

Giúp việc nhóm các snippets có liên quan lại với nhau.

Thuộc tính `"items": []` trong đó sẽ chứa nhiều snippets.
```json
[
  {
    "id": "box1",
    "title": "Box 1",
    "items": [
      {
        "id": "height",
        "title": "Height",
        "attribute": "height",
        "reference": "css",
        "value": "24px",
        "units": [
          "px"
        ],
        "type": "input:unit"
      }
    ]
  }
]
```

### Collapse/extend: Chế độ đóng mở nhóm snippets
```json
{
    "id": "themeNotifiColors",
    "title": "Notifi Colors",
    "collapse": true,
}
```
or
```json
{
    "id": "themeNotifiColors",
    "title": "Notifi Colors",
    "extend": true,
}
```

### More/advanced: Tạo nhóm snippets nâng cao

Thuộc tính này giúp việc đưa các snippets phức tạp giấu vào trong để user cơ bản không cần quan tâm đến. Việc này vừa làm đơn giản hoá cũng như giúp phân cấp khách hàng tốt hơn

```json
{
  "id": "promo",
  "title": "Title Promo Bar",
  "items": [
    {
      "id": "textPromoBar",
      "title": "Heading",
      "desc": "",
      "attribute": "textPromoBar",
      "reference": "html",
      "value": "Get FREE SHIPPING on all orders over $50",
      "type": "input"
    }
  ],
  "more": [
    {
      "id": "bgColor",
      "title": "Background Color",
      "desc": "",
      "attribute": "bgColor",
      "reference": "css",
      "value": "#209a9a",
      "type": "colorpicker",
      "popup": true,
      "initial": true,
      "inherit": "themePrimaryColor"
    }
  ],
  "advanced": [
    {
      "id": "padding",
      "title": "Padding",
      "desc": "",
      "attribute": "padding",
      "reference": "css",
      "value": "10px 0",
      "type": "padding"
    }
  ]
}
```

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
##### Input text
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/input.png">

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

##### Input number
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/input.png">

Snippet định nghĩa:

```json
{
  "id": "fontSize",
  "attribute": "fontSize",
  "title": "Font Medium",
  "reference": "css",
  "value": 24,
  "type": "input:number",
  "min": 0 
}
```

##### Input unit
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/input-unit.png">

Snippet định nghĩa:

```json
{
  "id": "fontSize",
  "attribute": "fontSize",
  "title": "Font Medium",
  "reference": "css",
  "value": "24px",
  "type": "input:unit",
  "units": [
    "em",
    "px",
    "rem",
    "%"
  ],
  "min": 0
}
```
##### Input fix content
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/input-fixcontent.png">

Snippet định nghĩa:

```json
{
  "id": "productSaleOff",
  "attribute": "productSaleOff",
  "title": "Product Sale Off",
  "type": "input:fixContent",
  "reference": "html",
  "value": "Sale off [!Profit!] %",
  "screens": [
    {
      "id": "lg",
      "value": "Sale off [!Profit!] %"
    },
    {
      "id": "md",
      "value": "[!Profit!] % Off"
    },
    {
      "id": "sm",
      "value": "[!Profit!] % Off"
    },
    {
      "id": "xs",
      "value": "[!Profit!] % Off"
    }
  ]
}
```

#### Textarera
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/textarera.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": "a string value",
  "type": "textarea",
  "minHeight": 50,
  "maxHeight": 500
}
```

#### Text editor
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/textarera.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Text Editor",
  "reference": "html",
  "value": "This is content",
  "type": "texteditor",
  "options": [
    "bold",
    "italic",
    "underline",
    "foreColor"
  ]
}
```

Các thuộc tính khác:
```json
"createlink",
"insertOrderedList",
"insertUnorderedList",
"justifyLeft",
"justifyCenter",
"justifyRight",
```

#### Switch

Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/switch.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": true,
  "type": "switch"
}
```

#### Radio

Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/radio.png">

Snippet định nghĩa:

```json
{
  "id": "themeProductImageRadio",
  "attribute": "themeProductImageRadio",
  "title": "Image Ratio",
  "desc": "Chose the ratio that suits your image library",
  "reference": "css",
  "value": "square",
  "type": "radioGroup",
  "options": [
    {
      "text": "Square 1 : 1",
      "desc": "Used for images with equal ratio",
      "value": "square"
    },
    {
      "text": "Landscape 4 : 3",
      "desc": "Used for horizontal images",
      "value": "landscape"
    },
    {
      "text": "Portrait 3 : 4",
      "desc": "Used for vertical images",
      "value": "portrait"
    }
  ]
}
```

#### Menu
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/menu.png">

Snippet định nghĩa:

```json
{
  "id": "dataMenu",
  "title": "Menu",
  "attribute": "dataMenu",
  "type": "megamenu",
  "definedSettings": [
    {
      "level": 0,
      "settings": [
        {
          "id": "typeMenu",
          "attribute": "typeMenu",
          "title": "Type",
          "value": "mega",
          "type": "segment",
          "options": [
            {
              "text": "Mega",
              "value": "mega"
            },
            {
              "text": "Normal",
              "value": "Normal"
            }
          ]
        }
      ]
    },
    {
      "level": 1,
      "settings": [
        {
          "id": "badgeMenu",
          "attribute": "badgeMenu",
          "title": "Badge",
          "value": "sale",
          "type": "segment",
          "options": [
            {
              "text": "Normal",
              "value": "normal"
            },
            {
              "text": "Sale",
              "value": "Sale"
            }
          ]
        }
      ]
    },
    {
      "level": 2,
      "settings": [
        {
          "id": "picklink",
          "attribute": "picklink",
          "title": "Link",
          "type": "picklink",
          "value": "#"
        }
      ]
    }
  ],
  "value": [
    {
      "title": "Mega Menu",
      "settings": [
        {
          "id": "typeMenu",
          "attribute": "typeMenu",
          "title": "Type",
          "value": "mega",
          "type": "segment",
          "options": [
            {
              "text": "Mega",
              "value": "mega"
            },
            {
              "text": "Normal",
              "value": "Normal"
            }
          ]
        }
      ],
      "items": [
        {
          "title": "New Arrivals",
          "settings": [
            {
              "id": "badgeMenu",
              "attribute": "badgeMenu",
              "title": "Badge",
              "value": "sale",
              "type": "segment",
              "options": [
                {
                  "text": "Normal",
                  "value": "normal"
                },
                {
                  "text": "Sale",
                  "value": "Sale"
                }
              ]
            }
          ],
          "items": [
            {
              "title": "Sweatshirt",
              "settings": [
                {
                  "id": "picklink",
                  "attribute": "picklink",
                  "title": "Link",
                  "type": "picklink",
                  "value": "#"
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

Mặc định level tối đã là 3. Bạn có thể thêm setting để tăng giới hạn này lên:

```json
{
  "levelMax": 3
}
```
>[!warning]
>Bạn cần định nghĩa `definedSettings` để menu có thể hoạt động tốt

#### Select
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/select.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": "value1",
  "type": "select",
  "options": [
    {
      "text": "Option 1",
      "value": "value1"
    },
    {
      "text": "Option 2",
      "value": "value2"
    }
  ]
}
```
#### Segment
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/segment.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": "inset",
  "type": "segment",
  "options": [
    {
      "text": "Inset",
      "value": "inset"
    },
    {
      "text": "Outset",
      "value": "outset"
    }
  ]
}
```
#### Range slider
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/range.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": 0.5,
  "type": "range",
  "min": 0,
  "max": 1,
  "changing": 0.01
}
```
#### Range uint slider
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/range-unit.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": "45px",
  "type": "range:unit",
  "min": 0,
  "max": 100,
  "changing": 1,
  "units": [
    "em",
    "px"
  ]
}
```
#### Color picker
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/colorpicker.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "value": "#ff00ff",
  "type": "colorpicker",
  "popup": true
}
```
#### Padding
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/padding.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "type": "padding",
  "value": "0px 0px 0px 0px"
}
```
#### Margin
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/margin.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "type": "margin",
  "value": "0px 0px 0px 0px"
}
```
#### Box Shadow
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/shadow.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Components title",
  "reference": "css",
  "type": "shadow",
  "value": "0px 0px 0px 0px #ccc"
}
```
#### Icon
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/iconuploader.png">

Snippet định nghĩa:

```json
{
  "id": "sectionIcon",
  "attribute": "sectionIcon",
  "title": "Icon",
  "reference": "html",
  "type": "iconuploader",
  "value": {
    "content": "<svg width=\"100%\" viewBox=\"0 0 640 512\"><path fill=\"currentColor\" d=\"M400 96a48 48 0 1 0-48-48 48 48 0 0 0 48 48zm-4 121a31.9 31.9 0 0 0 20 7h64a32 32 0 0 0 0-64h-52.78L356 103a31.94 31.94 0 0 0-40.81.68l-112 96a32 32 0 0 0 3.08 50.92L288 305.12V416a32 32 0 0 0 64 0V288a32 32 0 0 0-14.25-26.62l-41.36-27.57 58.25-49.92zm116 39a128 128 0 1 0 128 128 128 128 0 0 0-128-128zm0 192a64 64 0 1 1 64-64 64 64 0 0 1-64 64zM128 256a128 128 0 1 0 128 128 128 128 0 0 0-128-128zm0 192a64 64 0 1 1 64-64 64 64 0 0 1-64 64z\"></path></svg>",
    "type": "svg",
    "name": "check"
  }
}
```
#### Tabs
Ảnh hiển thị:

<!-- <img src="/images/ecomsolid/snippets/iconuploader.png"> -->

Snippet định nghĩa:

```json
{
  "id": "tabs",
  "title": "Tabs",
  "attribute": "tabs",
  "reference": "html",
  "type": "tabs",
  "value": [
    {
      "title": "Tablet",
      "settings": [
        {
          "id": "name",
          "attribute": "name",
          "title": "Name",
          "reference": "css",
          "value": "100% SATISFACTION",
          "type": "input"
        }
      ]
    }
  ]
}
```
#### Pick currency
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/pickCurrency.png">

Snippet định nghĩa:

```json
{
  "id": "currency",
  "attribute": "currency",
  "title": "Select Currency",
  "value": [],
  "type": "pickCurrency"
}
```
#### Code editor HTML
Ảnh hiển thị:

<!-- <img src="/images/ecomsolid/snippets/pickCurrency.png"> -->

Snippet định nghĩa:

```json
{
  "id": "codeHTML",
  "attribute": "codeHTML",
  "title": "Code HTML",
  "reference": "html",
  "value": "Custom code",
  "type": "codeEditor:html"
}
```

Các thuộc tính mở rộng:

```json
{
  "width": "100%",
  "height": "200px",
  "checkingSyntax": true
}
```
#### Code editor CSS
Ảnh hiển thị:

<!-- <img src="/images/ecomsolid/snippets/pickCurrency.png"> -->

Snippet định nghĩa:

```json
{
  "id": "codeCSS",
  "attribute": "codeCSS",
  "title": "Code CSS",
  "desc": "",
  "reference": "html",
  "value": "Custom code",
  "type": "codeEditor:css"
}
```

Các thuộc tính mở rộng:

```json
{
  "width": "100%",
  "height": "200px",
  "checkingSyntax": true
}
```

#### Description
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/description.png">

Snippet định nghĩa:

```json
{
  "id": "description",
  "attribute": "description",
  "type": "description",
  "desc": "To change favicon you can do as the image below. You can access the settings faster via the following link: <a href='/theme/settings' target='_blank'>Go to Setting Favicon</a>.<br><br><img width='100%' src='https://d3dfaj4bukarbm.cloudfront.net/production/tutorial/change-favicon.png' />"
}
```
#### Animation Atom

### Shopify

#### Pick product
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/pickproduct.png">

Snippet định nghĩa:

```json
{
  "id": "productHandle",
  "attribute": "productHandle",
  "title": "Product",
  "reference": "html",
  "type": "pickproduct",
  "value": {
    "id": "auto",
    "handle": "auto",
    "title": "auto"
  }
}
```

Cách sử dụng trong HTML:

```html
<% if(productHandle.handle == "auto") { %>
    {%- assign product = collections.all.products | first -%}
<% } else { %>
    {%- assign product = all_products["<%=productHandle.handle%>"] -%} 
<% }%>
```

#### Pick collection
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/pickcollection.png">

Snippet định nghĩa:

```json
{
  "id": "collectionHandle",
  "attribute": "collectionHandle",
  "title": "Collection",
  "reference": "html",
  "type": "pickcollection",
  "value": {
    "id": "auto",
    "handle": "auto",
    "title": "auto"
  },
 "shopify": [
     "collections[collectionHandle].products",
     "collections.all.products"
  ]
}
```

Cách sử dụng trong HTML:

```html
<% if (collectionHandle.handle == "auto") { %>
  {% for product in collections.all.products limit:<%=limit%> %}
<% } else { %>
  {% for product in collections["<%=collectionHandle.handle%>"].products limit:<%=limit%> %}
<% } %>
    <div class="gf_productlist-item">
      <% include "product" %>
    </div>
{% endfor %}
```

#### Pick blog
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/pickblog.png">

Snippet định nghĩa:

```json
{
  "id": "blogHandle",
  "attribute": "blogHandle",
  "title": "Blog",
  "reference": "html",
  "type": "pickblog",
  "value": {
    "id": "auto",
    "handle": "auto",
    "title": "auto"
  }
}
```

Cách sử dụng trong HTML:

```html
{% for article in blog.articles limit:6 %}
    <h4>{{ article.title }}</h4>
{% endfor %}
```

Nếu bạn làm với feature blog thì cần thêm thuộc tính "disableAuto" và nó sẽ giúp tự động lấy blog đầu tiên:
```json
{
  "disableAuto": true,
}
```

#### Pick article
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/pickarticle.png">

Snippet định nghĩa:

```json
{
  "id": "articleHandle",
  "attribute": "articleHandle",
  "title": "Article",
  "reference": "html",
  "type": "pickarticle",
  "value": {
    "id": "auto",
    "handle": "auto",
    "title": "auto",
    "blog_id": "auto"
  }
}
```

Cách sử dụng trong HTML:

```html
<h2>{{ article.title }}</h2>
```

#### Pick link
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/picklink.png">

Snippet định nghĩa:

```json
{
  "id": "linkButton",
  "attribute": "linkButton",
  "title": "Components title",
  "reference": "html",
  "type": "picklink",
  "value": "https://ecomsolid.com"
}
```

#### Upload image
Ảnh hiển thị:

<img src="/images/ecomsolid/snippets/imageuploader.png">

Snippet định nghĩa:

```json
{
  "id": "componentId",
  "attribute": "componentId",
  "title": "Component's title",
  "reference": "html",
  "type": "imageuploader",
  "value": "https://gggg.com/abc.jpg"
}
```
>[!warning]
>Nếu bạn muốn set value default là một ảnh thì bạn cần Upload lên UploadCare để đạt tốc độ tốt hơn và được support lazyload
><br>Hướng dẫn upload image lên UploadCare: <a href="#/ecomsolid/html" target="_blank">Tại đây</a>

#### Campaigns
Ảnh hiển thị:

<!-- <img src="/images/ecomsolid/snippets/pickproduct.png"> -->

Snippet định nghĩa:

```json
{
  "id": "campaignSettings",
  "attribute": "campaignSettings",
  "type": "campaignSettings",
  "value": [],
  "title": "Campaigns Setting",
  "plans": [
    {
      "plan": "free",
      "max": 1
    },
    {
      "plan": "professional",
      "max": 99999999
    }
  ],
  "max": 1,
  "definedSetting": {
    "id": "defaultCampaign",
    "name": "New Campaign",
    "settings": [
      {
        "id": "campaignType",
        "attribute": "campaignType",
        "title": "Campaign type",
        "value": "products",
        "type": "select",
        "options": [
          {
            "text": "All",
            "value": "all"
          },
          {
            "text": "Products",
            "value": "products"
          }
        ],
        "links": [
          {
            "value": "products",
            "snippet": {
              "id": "campaignPickProducts",
              "hide": false
            }
          }
        ]
      },
      {
        "id": "campaignPickProducts",
        "attribute": "campaignPickProducts",
        "title": "Pick products",
        "type": "pickProductList",
        "hide": true,
        "value": []
      },
      {
        "id": "campaignDateTime",
        "attribute": "campaignDateTime",
        "title": "Pick a time",
        "type": "datetime:date",
        "value": []
      }
    ]
  }
}
```

Cách sử dụng trong HTML:

```html
<% if(productHandle.handle == "auto") { %>
    {%- assign product = collections.all.products | first -%}
<% } else { %>
    {%- assign product = all_products["<%=productHandle.handle%>"] -%} 
<% }%>
```
### Customize

## Thuộc tính tối ưu

### Lazy Update

>Khi change giá trị thì iframe mới thay đổi. Thuộc tính này hay đi cùng range slider

```json
{
    "id": "textCenter",
    "title": "Text Center",
    "attribute": "textCenter",
    "reference": "html",
    "value": "FREE SHIPPING ON ORDER OVER 75$",
    "type": "input",
    "minHeight": 80,
    "maxHeight": 100,
    "lazyUpdate": true
}
```
### Replace HTML
```json
"optimize": {
    "type": "html:text",
    "target": ".gf_topbar-text span"
}
```
### Change Data
```json
"optimize": {
    "type": "html:data",
    "target": ".gf_topbar-text span",
    "attribute": "src"
}
```
### Display

```json
"optimize": {
    "type": "html:display",
    "target": ".gf_topbar-text span"
}
```
### Trigger Javascript

**1, Thêm ở Snippets**

```json
"attribute": "changeTypeCart",
"optimize": {
    "type": "js:trigger"
}
```

**2, Thêm ở code Javascript**

```json
/*Comment*/
store.change("optimize-<%=id%>-changeTypeCart", function(value) {
    console.log(value);
})
store.change("optimize-<%=id%>-numberCart", function(value) {
    console.log(value);
})
/*End_Comment*/
```

### Multi Optimize
```json
"optimize": [
    {
        "type": "html:text",
        "target": ".gf_topbar-text span"
    },
    {
        "type": "html:data",
        "target": ".gf_topbar-text span",
        "attribute": "src"
    }
]
```
