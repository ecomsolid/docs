## Class mở rộng
### Responsive Design
```css
.gt_text { // Màn hình rộng
  font-size: 16px
}
.md:gt_text { // Laptop nhỏ
  font-size: 16px
}
.sm:gt_text { // Máy tính bảng
  font-size: 16px
}
.xs:gt_text { // Điện thoại
  font-size: 14px
}
```

## Danh sách class global
Có sự tham khảo và flow theo thư viện: <a href="https://tailwindcss.com/docs" target="_blank">Tailwindcss</a>
### Layout
#### Container - v1.0
```css
.gt_container {
  margin: 0px auto;
  padding: 0px 15px;
  width: ${widthContainer};
}
.gt_container--full {
  padding: 0px 15px;
  margin: 0px auto;
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_container
```
```html
gt_container--full
```
#### Display
```css
.gt_block {
  display: block;
}
.gt_inline-block {
  display: inline-block;
}
.gt_inline {
  display: inline;
}
.gt_inline-flex {
  display: inline-flex;
}
.gt_flex {
  display: flex;
}
.gt_hidden {
  display: hidden;
}
```
#### Overflow
```css
.gt_overflow--auto {
  overflow: auto;
}
.gt_overflow--hidden {
  overflow: hidden;
}
.gt_overflow-x--hidden {
  overflow-x: hidden;
}
.gt_overflow-y--hidden {
  overflow-y: hidden;
}
```
#### Position
```css
.gt_static {
  position: static;
}
.gt_fixed {
  position: fixed;
}
.gt_absolute {
  position: absolute;
}
.gt_relative {
  position: relative;
}
.gt_sticky {
  position: sticky;
}
```
#### Visibility
```css
.gt_visible {
  visibility: visible;
}
.gt_invisible {
  visibility: hidden;
}
```

#### Z-Index
```css
.gt_z--0 {
  z-index: 0;
}
.gt_z--10 {
  z-index: 10;
}
.gt_z--20 {
  z-index: 20;
}
.gt_z--30 {
  z-index: 30;
}
.gt_z--40 {
  z-index: 40;
}
.gt_z--50 {
  z-index: 50;
}
```
### Flexbox
### Flex
#### Flex Wrap
```css
.gt_flex-wrap {
  flex-wrap: wrap;
}
.gt_flex-wrap--reverse {
  flex-wrap: wrap-reverse;
}
.gt_flex-wrap--nowrap {
  flex-wrap: nowrap;
}
```
#### Flex Direction
```css
.gt_flex--row {
  flex-direction: row;
}
.gt_flex--row-reverse {
  flex-direction: row-reverse;
}
.gt_flex--column {
  flex-direction: column;
}
.gt_flex--column-reverse {
  flex-direction: column-reverse;
}
```
### Box Alignment
#### Justify Content
```css
.gt_justify--start {
  justify-content: flex-start;
}
.gt_justify--end {
  justify-content: flex-end;
}
.gt_justify--center {
  justify-content: center;
}
.gt_justify--space-between {
  justify-content: space-between;
}
```
#### Align Items
```css
.gt_items--start {
  align-items: flex-start;
}
.gt_items--end {
  align-items: flex-end;
}
.gt_items--center {
  align-items: center;
}
.gt_items--baseline {
  align-items: baseline;
}
.gt_items--stretch {
  align-items: stretch;
}
```
### **Spacing**
#### Margin
##### None = 0px
```css
.gt_m--none {
  margin: 0px;
}
.gt_mt--none {
  margin-top: 0px;
}
.gt_mb--none {
  margin-bottom: 0px;
}
.gt_ml--none {
  margin-left: 0px;
}
.gt_mr--none {
  margin-right: 0px;
}
.gt_mx--none {
  margin-right: 0px;
  margin-left: 0px;
}
.gt_my--none {
  margin-top: 0px;
  margin-bottom: 0px;
}
```
##### Extra Small

##### v2.0: 8px
```css
.gt_m2--extra-small {
  margin: #{themeSpacingExtraSmall2};
}
.gt_mt2--extra-small {
  margin-top: #{themeSpacingExtraSmall2};
}
.gt_mb2--extra-small {
  margin-bottom: #{themeSpacingExtraSmall2};
}
.gt_ml2--extra-small {
  margin-left: #{themeSpacingExtraSmall2};
}
.gt_mr2--extra-small {
  margin-right: #{themeSpacingExtraSmall2};
}
.gt_mx2--extra-small {
  margin-right: #{themeSpacingExtraSmall2};
  margin-left: #{themeSpacingExtraSmall2};
}
.gt_my2--extra-small {
  margin-top: #{themeSpacingExtraSmall2};
  margin-bottom: #{themeSpacingExtraSmall2};
}
```
Dùng cho những đoạn text với nhau ở khoảng cách nhỏ và Margin bottom subheading
>[!note]
>Đã tự động hỗ trợ responsive

![themeSpacingExtraSmall](https://d3dfaj4bukarbm.cloudfront.net/staging/images/admin/0ef7d4e0-4efa-420f-bb55-f00bba2b284e.png)

Danh sách class:
```html
gt_m2--extra-small
```
```html
gt_mt2--extra-small
```
```html
gt_mb2--extra-small
```
```html
gt_ml2--extra-small
```
```html
gt_mr2--extra-small
```
##### v1.0: 8px
```css
.gt_m--extra-small {
  margin: #{themeSpacingExtraSmall};
}
.gt_mt--extra-small {
  margin-top: #{themeSpacingExtraSmall};
}
.gt_mb--extra-small {
  margin-bottom: #{themeSpacingExtraSmall};
}
.gt_ml--extra-small {
  margin-left: #{themeSpacingExtraSmall};
}
.gt_mr--extra-small {
  margin-right: #{themeSpacingExtraSmall};
}
.gt_mx--extra-small {
  margin-right: #{themeSpacingExtraSmall};
  margin-left: #{themeSpacingExtraSmall};
}
.gt_my--extra-small {
  margin-top: #{themeSpacingExtraSmall};
  margin-bottom: #{themeSpacingExtraSmall};
}
```
Dùng cho những đoạn text với nhau ở khoảng cách nhỏ
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_m--extra-small
```
```html
gt_mt--extra-small
```
```html
gt_mb--extra-small
```
```html
gt_ml--extra-small
```
```html
gt_mr--extra-small
```
##### Small

##### v2.0: 16px
```css
.gt_m2--small {
  margin: #{themeSpacingSmall2};
}
.gt_mt2--small {
  margin-top: #{themeSpacingSmall2};
}
.gt_mb2--small {
  margin-bottom: #{themeSpacingSmall2};
}
.gt_ml2--small {
  margin-left: #{themeSpacingSmall2};
}
.gt_mr2--small {
  margin-right: #{themeSpacingSmall2};
}
.gt_mx2--small {
  margin-right: #{themeSpacingSmall2};
  margin-left: #{themeSpacingSmall2};
}
.gt_my2--small {
  margin-top: #{themeSpacingSmall2};
  margin-bottom: #{themeSpacingSmall2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

![themeSpacingSmall](https://d3dfaj4bukarbm.cloudfront.net/staging/images/admin/d76e77ff-cde1-4b58-8383-525e51126998.png)

Danh sách class:
```html
gt_m2--small
```
```html
gt_mt2--small
```
```html
gt_mb2--small
```
```html
gt_ml2--small
```
```html
gt_mr2--small
```

##### v1.0: 16px
```css
.gt_m--small {
  margin: #{themeSpacingSmall};
}
.gt_mt--small {
  margin-top: #{themeSpacingSmall};
}
.gt_mb--small {
  margin-bottom: #{themeSpacingSmall};
}
.gt_ml--small {
  margin-left: #{themeSpacingSmall};
}
.gt_mr--small {
  margin-right: #{themeSpacingSmall};
}
.gt_mx--small {
  margin-right: #{themeSpacingSmall};
  margin-left: #{themeSpacingSmall};
}
.gt_my--small {
  margin-top: #{themeSpacingSmall};
  margin-bottom: #{themeSpacingSmall};
}
```
Dùng cho khoảng cách giữa các thành phần trong một box.
Trừ heading, subheading, text, các thành phần này thường sẽ nằm gần nhau và tự có margin bottom của riêng nó. Có một số trường hợp sắp xếp ngược như: text->heading thì lúc đó vẫn cần margin
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_m--small
```
```html
gt_mt--small
```
```html
gt_mb--small
```
```html
gt_ml--small
```
```html
gt_mr--small
```
##### Medium

##### v2.0: 32px
```css
.gt_m2--medium {
  margin: #{themeSpacingMedium2};
}
.gt_mt2--medium {
  margin-top: #{themeSpacingMedium2};
}
.gt_mb2--medium {
  margin2-bottom: #{themeSpacingMedium2};
}
.gt_ml2--medium {
  margin2-left: #{themeSpacingMedium2};
}
.gt_mr2--medium {
  margin2-right: #{themeSpacingMedium2};
}
.gt_mx2--medium {
  margin-right: #{themeSpacingMedium2};
  margin-left: #{themeSpacingMedium2};
}
.gt_my2--medium {
  margin-top: #{themeSpacingMedium2};
  margin-bottom: #{themeSpacingMedium2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

![themeSpacingMedium](https://d3dfaj4bukarbm.cloudfront.net/staging/images/admin/f7d969e5-8009-4778-be07-5caf18142e99.png)

Danh sách class:
```html
gt_m2--medium
```
```html
gt_mt2--medium
```
```html
gt_mb2--medium
```
```html
gt_ml2--medium
```
```html
gt_mr2--medium
```
##### v1.0: 32px
```css
.gt_m--medium {
  margin: #{themeSpacingMedium};
}
.gt_mt--medium {
  margin-top: #{themeSpacingMedium};
}
.gt_mb--medium {
  margin-bottom: #{themeSpacingMedium};
}
.gt_ml--medium {
  margin-left: #{themeSpacingMedium};
}
.gt_mr--medium {
  margin-right: #{themeSpacingMedium};
}
.gt_mx--medium {
  margin-right: #{themeSpacingMedium};
  margin-left: #{themeSpacingMedium};
}
.gt_my--medium {
  margin-top: #{themeSpacingMedium};
  margin-bottom: #{themeSpacingMedium};
}
```
Dùng cho khoảng cách giữa các thành phần trong một section
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_m--medium
```
```html
gt_mt--medium
```
```html
gt_mb--medium
```
```html
gt_ml--medium
```
```html
gt_mr--medium
```
##### Large
###### v2.0: 56px
```css
.gt_m2--large {
  margin: #{themeSpacingLarge2};
}
.gt_mt2--large {
  margin-top: #{themeSpacingLarge2};
}
.gt_mb2--large {
  margin-bottom: #{themeSpacingLarge2};
}
.gt_ml2--large {
  margin-left: #{themeSpacingLarge2};
}
.gt_mr2--large {
  margin-right: #{themeSpacingLarge2};
}
.gt_mx2--large {
  margin-right: #{themeSpacingLarge2};
  margin-left: #{themeSpacingLarge2};
}
.gt_my2--large {
  margin-top: #{themeSpacingLarge2};
  margin-bottom: #{themeSpacingLarge2};
}
```
Thường hay sử dụng cho khoảng cách giữa các thành phần trong mỗi section
>[!note]
>Đã tự động hỗ trợ responsive

![themeSpacingLarge](https://d3dfaj4bukarbm.cloudfront.net/staging/images/admin/1fa7f0d0-eab3-4ea3-8431-4b666d8a3708.png)

Danh sách class:
```html
gt_m2--large
```
```html
gt_mt2--large
```
```html
gt_mb2--large
```
```html
gt_ml2--large
```
```html
gt_mr2--large
```
###### v1.0: 64px
```css
.gt_m--large {
  margin: #{themeSpacingLarge};
}
.gt_mt--large {
  margin-top: #{themeSpacingLarge};
}
.gt_mb--large {
  margin-bottom: #{themeSpacingLarge};
}
.gt_ml--large {
  margin-left: #{themeSpacingLarge};
}
.gt_mr--large {
  margin-right: #{themeSpacingLarge};
}
.gt_mx--large {
  margin-right: #{themeSpacingLarge};
  margin-left: #{themeSpacingLarge};
}
.gt_my--large {
  margin-top: #{themeSpacingLarge};
  margin-bottom: #{themeSpacingLarge};
}
```
Thường hay sử dụng cho khoảng cách giữa các section
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_m--large
```
```html
gt_mt--large
```
```html
gt_mb--large
```
```html
gt_ml--large
```
```html
gt_mr--large
```
##### Extra Large
##### v2.0: 72px
```css
.gt_m2--extra-large {
  margin: #{themeSpacingLarge};
}
.gt_mt2--extra-large {
  margin-top: #{themeSpacingLarge};
}
.gt_mb2--extra-large {
  margin-bottom: #{themeSpacingLarge};
}
.gt_ml2--extra-large {
  margin-left: #{themeSpacingLarge};
}
.gt_mr2--extra-large {
  margin-right: #{themeSpacingLarge};
}
.gt_mx2--extra-large {
  margin-right: #{themeSpacingLarge};
  margin-left: #{themeSpacingLarge};
}
.gt_my2--extra-large {
  margin-top: #{themeSpacingLarge};
  margin-bottom: #{themeSpacingLarge};
}
```
Thường hay sử dụng cho khoảng cách giữa các section
>[!note]
>Đã tự động hỗ trợ responsive

![themeSpacingExtraLarge](https://d3dfaj4bukarbm.cloudfront.net/staging/images/admin/fec19b73-daa4-49d4-bd11-af7369b8815e.png)

Danh sách class:
```html
gt_m2--extra-large
```
```html
gt_mt2--extra-large
```
```html
gt_mb2--extra-large
```
```html
gt_ml2--extra-large
```
```html
gt_mr2--extra-large
```

##### v1.0: no exist
#### Padding
##### None = 0px
```css
.gt_p--none {
  padding: 0px;
}
.gt_pt--none {
  padding-top: 0px;
}
.gt_pb--none {
  padding-bottom: 0px;
}
.gt_pl--none {
  padding-left: 0px;
}
.gt_pr--none {
  padding-right: 0px;
}
.gt_px--none {
  padding-right: 0px;
  padding-left: 0px;
}
.gt_py--none {
  padding-top: 0px;
  padding-bottom: 0px;
}
```
##### Extra Small

##### v2.0: 8px
```css
.gt_p2--extra-small {
  padding: #{themeSpacingExtraSmall2};
}
.gt_pt2--extra-small {
  padding-top: #{themeSpacingExtraSmall2};
}
.gt_pb2--extra-small {
  padding-bottom: #{themeSpacingExtraSmall2};
}
.gt_pl2--extra-small {
  padding-left: #{themeSpacingExtraSmall2};
}
.gt_pr2--extra-small {
  padding-right: #{themeSpacingExtraSmall2};
}
.gt_px2--extra-small {
  padding-right: #{themeSpacingExtraSmall2};
  padding-left: #{themeSpacingExtraSmall2};
}
.gt_py2--extra-small {
  padding-top: #{themeSpacingExtraSmall2};
  padding-bottom: #{themeSpacingExtraSmall2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p2--extra-small
```
```html
gt_pt2--extra-small
```
```html
gt_pb2--extra-small
```
```html
gt_pl2--extra-small
```
```html
gt_pr2--extra-small
```

##### v1.0: 8px
```css
.gt_p--extra-small {
  padding: #{themeSpacingExtraSmall};
}
.gt_pt--extra-small {
  padding-top: #{themeSpacingExtraSmall};
}
.gt_pb--extra-small {
  padding-bottom: #{themeSpacingExtraSmall};
}
.gt_pl--extra-small {
  padding-left: #{themeSpacingExtraSmall};
}
.gt_pr--extra-small {
  padding-right: #{themeSpacingExtraSmall};
}
.gt_px--extra-small {
  padding-right: #{themeSpacingExtraSmall};
  padding-left: #{themeSpacingExtraSmall};
}
.gt_py--extra-small {
  padding-top: #{themeSpacingExtraSmall};
  padding-bottom: #{themeSpacingExtraSmall};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p--extra-small
```
```html
gt_pt--extra-small
```
```html
gt_pb--extra-small
```
```html
gt_pl--extra-small
```
```html
gt_pr--extra-small
```
##### Small

##### v2.0: 16px

```css
.gt_p2--small {
  padding: #{themeSpacingSmall2};
}
.gt_pt2--small {
  padding-top: #{themeSpacingSmall2};
}
.gt_pb2--small {
  padding-bottom: #{themeSpacingSmall2};
}
.gt_pl2--small {
  padding-left: #{themeSpacingSmall2};
}
.gt_pr2--small {
  padding-right: #{themeSpacingSmall2};
}
.gt_px2--small {
  padding-right: #{themeSpacingSmall2};
  padding-left: #{themeSpacingSmall2};
}
.gt_py2--small {
  padding-top: #{themeSpacingSmall2};
  padding-bottom: #{themeSpacingSmall2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p2--small
```
```html
gt_pt2--small
```
```html
gt_pb2--small
```
```html
gt_pl2--small
```
```html
gt_pr2--small
```

##### v1.0: 16px
```css
.gt_p--small {
  padding: #{themeSpacingSmall};
}
.gt_pt--small {
  padding-top: #{themeSpacingSmall};
}
.gt_pb--small {
  padding-bottom: #{themeSpacingSmall};
}
.gt_pl--small {
  padding-left: #{themeSpacingSmall};
}
.gt_pr--small {
  padding-right: #{themeSpacingSmall};
}
.gt_px--small {
  padding-right: #{themeSpacingSmall};
  padding-left: #{themeSpacingSmall};
}
.gt_py--small {
  padding-top: #{themeSpacingSmall};
  padding-bottom: #{themeSpacingSmall};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p--small
```
```html
gt_pt--small
```
```html
gt_pb--small
```
```html
gt_pl--small
```
```html
gt_pr--small
```
##### Medium

##### v2.0: 32px
```css
.gt_p2--medium {
  padding: #{themeSpacingMedium2};
}
.gt_pt2--medium {
  padding-top: #{themeSpacingMedium2};
}
.gt_pb2--medium {
  padding-bottom: #{themeSpacingMedium2};
}
.gt_pl2--medium {
  padding-left: #{themeSpacingMedium2};
}
.gt_pr2--medium {
  padding-right: #{themeSpacingMedium2};
}
.gt_px2--medium {
  padding-right: #{themeSpacingMedium2};
  padding-left: #{themeSpacingMedium2};
}
.gt_py2--medium {
  padding-top: #{themeSpacingMedium2};
  padding-bottom: #{themeSpacingMedium2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p2--medium
```
```html
gt_pt2--medium
```
```html
gt_pb2--medium
```
```html
gt_pl2--medium
```
```html
gt_pr2--medium
```
##### v1.0: 32px
```css
.gt_p--medium {
  padding: #{themeSpacingMedium};
}
.gt_pt--medium {
  padding-top: #{themeSpacingMedium};
}
.gt_pb--medium {
  padding-bottom: #{themeSpacingMedium};
}
.gt_pl--medium {
  padding-left: #{themeSpacingMedium};
}
.gt_pr--medium {
  padding-right: #{themeSpacingMedium};
}
.gt_px--medium {
  padding-right: #{themeSpacingMedium};
  padding-left: #{themeSpacingMedium};
}
.gt_py--medium {
  padding-top: #{themeSpacingMedium};
  padding-bottom: #{themeSpacingMedium};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p--medium
```
```html
gt_pt--medium
```
```html
gt_pb--medium
```
```html
gt_pl--medium
```
```html
gt_pr--medium
```
##### Large

##### v2.0: 56px
```css
.gt_p2--large {
  padding: #{themeSpacingLarge2};
}
.gt_pt2--large {
  padding-top: #{themeSpacingLarge2};
}
.gt_pb2--large {
  padding-bottom: #{themeSpacingLarge2};
}
.gt_pl2--large {
  padding-left: #{themeSpacingLarge2};
}
.gt_pr2--large {
  padding-right: #{themeSpacingLarge2};
}
.gt_px2--large {
  padding-right: #{themeSpacingLarge2};
  padding-left: #{themeSpacingLarge2};
}
.gt_py2--large {
  padding-top: #{themeSpacingLarge2};
  padding-bottom: #{themeSpacingLarge2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p2--large
```
```html
gt_pt2--large
```
```html
gt_pb2--large
```
```html
gt_pl2--large
```
```html
gt_pr2--large
```

##### v1.0: 64px

```css
.gt_p--large {
  padding: #{themeSpacingLarge};
}
.gt_pt--large {
  padding-top: #{themeSpacingLarge};
}
.gt_pb--large {
  padding-bottom: #{themeSpacingLarge};
}
.gt_pl--large {
  padding-left: #{themeSpacingLarge};
}
.gt_pr--large {
  padding-right: #{themeSpacingLarge};
}
.gt_px--large {
  padding-right: #{themeSpacingLarge};
  padding-left: #{themeSpacingLarge};
}
.gt_py--large {
  padding-top: #{themeSpacingLarge};
  padding-bottom: #{themeSpacingLarge};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p--large
```
```html
gt_pt--large
```
```html
gt_pb--large
```
```html
gt_pl--large
```
```html
gt_pr--large
```
##### Extra Large

##### v2.0: 72px
```css
.gt_p2--extra-large {
  padding: #{themeSpacingExtraLarge2};
}
.gt_pt2--extra-large {
  padding-top: #{themeSpacingExtraLarge2};
}
.gt_pb2--extra-large {
  padding-bottom: #{themeSpacingExtraLarge2};
}
.gt_pl2--extra-large {
  padding-left: #{themeSpacingExtraLarge2};
}
.gt_pr2--extra-large {
  padding-right: #{themeSpacingExtraLarge2};
}
.gt_px2--extra-large {
  padding-right: #{themeSpacingExtraLarge2};
  padding-left: #{themeSpacingExtraLarge2};
}
.gt_py2--extra-large {
  padding-top: #{themeSpacingExtraLarge2};
  padding-bottom: #{themeSpacingExtraLarge2};
}
```
>[!note]
>Đã tự động hỗ trợ responsive

Danh sách class:
```html
gt_p2--extra-large
```
```html
gt_pt2--extra-large
```
```html
gt_pb2--extra-large
```
```html
gt_pl2--extra-large
```
```html
gt_pr2--extra-large
```
##### v1.0: non exist

### **Button - v1.0**
```css
.gt_button--small {
  
}
.gt_button {

}
.gt_button--large {

}
```

Danh sách class:
```html
gt_button--small
```
```html
gt_button
```
```html
gt_button--large
```
### **Text - v1.0**
>[!note]
>Đối với base size Medium - 16px và đã tự động hỗ trợ responsive
```css
.gt_text--small {
  font-size: 12px;
}
.gt_text {
  font-size: 16px;
}
.gt_subheading {
  font-size: 21px;
}
.gt_heading--small {
  font-size: 28px;
}
.gt_heading {
  font-size: 38px;
}
.gt_heading--large {
  font-size: 51px;
}
```
Danh sách class:
```html
gt_text--small
```
```html
gt_text
```
```html
gt_subheading
```
```html
gt_heading--small

```
```html
gt_heading

```
```html
gt_heading--large
```
### Typography
#### Font Style
```css
.gt_italic {
  font-style: italic;
}
.gt_not-italic {
  font-style: normal;
}
```
#### Font Weight
```css
.gt_font--light {
  font-weight: light;
}
.gt_font--normal {
  font-weight: normal;
}
.gt_font--medium {
  font-weight: medium;
}
.gt_font--bold {
  font-weight: bold;
}
```
#### Text Alignment
```css
.gt_text--left {
  text-align: left;
}
.gt_text--center {
  text-align: center;
}
.gt_text--right {
  text-align: right;
}
.gt_text--justify {
  text-align: justify;
}
```
#### Text Color
```css
.gt_text--brand {
  color: #{themeBrandColor};
}
.gt_text--highlight {
  color: #{themeHighlightColor};
}
```
>[!warning]
>Không hỗ trợ responsive

#### Text Decoration
```css
.gt_underline {
  text-decoration: underline;
}
.gt_line-through {
  text-decoration: line-through;
}
.gt_no-underline {
  text-decoration: none;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Text Transform
```css
.gt_uppercase {
  text-transform: uppercase;
}
.gt_lowercase {
  text-transform: lowercase;
}
.gt_capitalize {
  text-transform: capitalize;
}
.gt_normal-case {
  text-transform: none;
}
``` 
>[!warning]
>Không hỗ trợ responsive

### Backgrounds
#### Background Color
```css
.gt_bg--brand {
  background-color: #{themeBrandColor};
}
.gt_bg--highlight  {
  background-color: #{themeHighlightColor};
}
.gt_bg--section  {
  background-color: #{themeSectionBackgroundColor};
}
.gt_bg--transparent  {
  background-color: transparent;
}
.gt_bg--current  {
  background-color: currentColor;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Background Position
```css
.gt_bg--center {
  background-position: center;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Background Repeat
```css
.gt_bg--no-repeat {
  background-repeat: no-repeat;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Background Size
```css
.gt_bg--auto {
  background-size: auto;
}
.gt_bg--cover {
  background-size: cover;
}
.gt_bg--contain {
  background-size: contain;
}
```
>[!warning]
>Không hỗ trợ responsive

### Borders
#### Border Radius
```css
.gt_radius {
  border-radius: #{themeSiteRadius};
}
.gt_radius--none {
  border-radius: 0px;
}
.gt_radius--full {
  border-radius: 9999px;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Border Color
```css
.gt_border--brand {
  border-color: #{themeBrandColor};
}
.gt_border--highlight  {
  border-color: #{themeHighlightColor};
}
.gt_border--section  {
  border-color: #{themeSectionBackgroundColor};
}
.gt_border--transparent  {
  border-color: transparent;
}
.gt_border--current  {
  border-color: currentColor;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Border Style
```css
.gt_border--solid {
  border-style: solid;
}
.gt_border--dashed  {
  border-style: dashed;
}
.gt_border--dotted  {
  border-style: dotted;
}
.gt_border--double  {
  border-style: double;
}
.gt_border--none  {
  border-style: none;
}
```
>[!warning]
>Không hỗ trợ responsive

### Transition
```css
.gt_transition--none {
  transition-property: none;
}
.gt_transition--all  {
  transition-property: all;
}
.gt_transition  {
  transition-property: background-color, border-color, color, fill, stroke, opacity, box-shadow, transform;
  transition-timing-function: ${data.themeAnimationTimingFunction};
  transition-duration: #{data.themeAnimationDuration};
}
.gt_transition--colors  {
  transition-property: background-color, border-color, color, fill, stroke;
  transition-timing-function: ${data.themeAnimationTimingFunction};
  transition-duration: #{data.themeAnimationDuration};
}
```

### Form
```css
.gt_input--small {

}
.gt_input {

}
.gt_input--large {

}
.gt_select--small {

}
.gt_select {

}
.gt_select--large {
  
}
```
### Effects
#### Box Shadow
```css
.gt_shadow {

}
```
>[!warning]
>Không hỗ trợ responsive

### Interactivity
#### Cursor
```css
.gt_cursor--auto {
  cursor: auto;
}
.gt_cursor--default {
  cursor: default;
}
.gt_cursor--pointer {
  cursor: pointer;
}
.gt_cursor--text {
  cursor: text;
}
.gt_cursor--not-allowed {
  cursor: not-allowed;
}
```
>[!warning]
>Không hỗ trợ responsive

#### Resize
```css
.gt_resize {
  resize: both;
}
.gt_resize--none {
  resize: none;
}
.gt_resize--y {
  resize: vertical;
}
.gt_resize--x {
  resize: horizontal;
}
```
>[!warning]
>Không hỗ trợ responsive

#### User Select
```css
.gt_user-select--none {
  user-select: none;
}
```
>[!warning]
>Không hỗ trợ responsive

