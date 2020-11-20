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
{
  "id": "txtTypography",
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
#a-<%-id%> {
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

#a-<%-id%>:hover, #a-<%-id%>.gt_hover {
  <% if (textHoverColorActive) { %>
    color: <%-textHoverColor%>;
  <% } %>
}

@media (max-width: 1200px) {
  #a-<%-id%> {
    <% if (textSizeActive) { %>
      font-size: <%-textSize_md%>;
    <% } %>
  }
}
@media (max-width: 992px) {
  #a-<%-id%> {
    <% if (textSizeActive) { %>
      font-size: <%-textSize_sm%>;
    <% } %>
  }
}
@media (max-width: 576px) {
  #a-<%-id%> {
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

#a-<%-id%>:hover, #a-<%-id%>.gt_hover {
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
#a-<%-id%> {
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

#a-<%-id%>:hover, #a-<%-id%>.gt_hover {
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
#a-<%-id%> {
  <% if (marginActive) { %>
    margin: <%-margin%>;
  <% } %>

  <% if (paddingActive) { %>
    padding: <%-padding%>;
  <% } %>
}

@media (max-width: 1200px) {
  #a-<%-id%> {
    <% if (marginActive) { %>
      margin: <%-margin_md%>;
    <% } %>
    <% if (paddingActive) { %>
      padding: <%-padding_md%>;
    <% } %>
  }
}
@media (max-width: 992px) {
  #a-<%-id%> {
    <% if (marginActive) { %>
      margin: <%-margin_sm%>;
    <% } %>
    <% if (paddingActive) { %>
      padding: <%-padding_sm%>;
    <% } %>
  }
}
@media (max-width: 576px) {
  #a-<%-id%> {
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
#a-<%-id%> {
  <% if (opacityActive) { %>
    opacity: <%-opacity%>;
  <% } %>
  <% if (boxShadowActive) { %>
    <% if (boxShadow) { %>
      box-shadow: <%-boxShadow%>;
    <% } %>
  <% } %>
}

#a-<%-id%>:hover, #a-<%-id%>.gt_hover {
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
