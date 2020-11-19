## Class mở rộng
### Responsive Design
```css
.lg:gt_text {
  font-size: 16px
}
.md:gt_text {
  font-size: 16px
}
.sm:gt_text {
  font-size: 16px
}
.xs:gt_text {
  font-size: 14px
}
```

## Danh sách class global

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
.gt_display--block {
  display: block;
}
.gt_display--inline-block {
  display: inline-block;
}
.gt_display--inline {
  display: inline;
}
.gt_display--inline-flex {
  display: inline-flex;
}
.gt_display--flex {
  display: flex;
}
.gt_display--hidden {
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
.gt_overflow--visible {
  overflow: visible;
}
.gt_overflow--scroll {
  overflow: scroll;
}
.gt_overflow-x--auto {
  overflow-x: auto;
}
.gt_overflow-y--auto {
  overflow-y: auto;
}
.gt_overflow-x--hidden {
  overflow-x: hidden;
}
.gt_overflow-y--hidden {
  overflow-y: hidden;
}
.gt_overflow-x--visible {
  overflow-x: visible;
}
.gt_overflow-y--visible {
  overflow-y: visible;
}
```
#### Position
```css
.gt_position--static {
  position: static;
}
.gt_position--fixed {
  position: fixed;
}
.gt_position--absolute {
  position: absolute;
}
.gt_position--relative {
  position: relative;
}
.gt_position--sticky {
  position: sticky;
}
```
#### Visibility
```css
.gt_visibility--visible {
  visibility: visible;
}
.gt_visibility--hidden {
  visibility: hidden;
}
```

#### Z-Index
```css
.gt_z-index--0 {
  z-index: 0;
}
.gt_z-index--10 {
  z-index: 10;
}
.gt_z-index--20 {
  z-index: 20;
}
.gt_z-index--30 {
  z-index: 30;
}
.gt_z-index--40 {
  z-index: 40;
}
.gt_z-index--50 {
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
.gt_flex-direction--row {
  flex-direction: row;
}
.gt_flex-direction--row-reverse {
  flex-direction: row-reverse;
}
.gt_flex-direction--column {
  flex-direction: column;
}
.gt_flex-direction--column-reverse {
  flex-direction: column-reverse;
}
```
### Box Alignment
#### Justify Content
```css
.gt_justify-content--start {
  justify-content: flex-start;
}
.gt_justify-content--end {
  justify-content: flex-end;
}
.gt_justify-content--center {
  justify-content: center;
}
.gt_justify-content--space-between {
  justify-content: space-between;
}
.gt_justify-content--space-around {
  justify-content: space-around;
}
.gt_justify-content--space-evenly {
  justify-content: space-evenly;
}
```
#### Align Items
```css
.gt_align-items--start {
  align-items: flex-start;
}
.gt_align-items--end {
  align-items: flex-end;
}
.gt_align-items--center {
  align-items: center;
}
.gt_align-items--baseline {
  align-items: baseline;
}
.gt_align-items--stretch {
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
```
##### Extra Small ~ 8px - v1.0
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
##### Small ~ 16px - v1.0
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
##### Medium ~ 32px - v1.0
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
##### Large ~ 64px - v1.0
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
```
##### Extra Small ~ 8px - v1.0
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
##### Small ~ 16px - v1.0
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
##### Medium ~ 32px - v1.0
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
##### Large ~ 64px - v1.0
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
```css
.gt_text--small {

}
.gt_text {

}
.gt_subheading {

}
.gt_heading {

}
.gt_heading--large {

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
gt_heading

```
```html
gt_heading--large
```
### Typography
#### Font Style
```css
.gt_font-style--italic {
  font-style: italic;
}
.gt_font-style--normal {
  font-style: normal;
}
```
#### Font Weight
```css
.gt_font-weight--light {
  font-weight: light;
}
.gt_font-weight--normal {
  font-weight: normal;
}
.gt_font-weight--medium {
  font-weight: medium;
}
.gt_font-weight--bold {
  font-weight: bold;
}
```
#### Text Alignment
```css
.gt_text-align--left {
  text-align: left;
}
.gt_text-align--center {
  text-align: center;
}
.gt_text-align--right {
  text-align: right;
}
.gt_text-align--justify {
  text-align: justify;
}
```
#### Text Color
```css
.gt_text-color--brand {
  color: #{themeBrandColor};
}
.gt_text-color--highlight {
  color: #{themeHighlightColor};
}
```
#### Text Decoration
```css
.gt_text-decoration--underline {
  text-decoration: underline;
}
.gt_text-decoration--line-through {
  text-decoration: line-through;
}
.gt_text-decoration--none {
  text-decoration: none;
}
```
#### Text Transform
```css
.gt_text-transform--uppercase {
  text-transform: uppercase;
}
.gt_text-transform--lowercase {
  text-transform: lowercase;
}
.gt_text-transform--capitalize {
  text-transform: capitalize;
}
.gt_text-transform--none {
  text-transform: none;
}
``` 
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
#### Background Position
```css
.gt_bg-position--center {
  background-position: center;
}
```
#### Background Repeat
```css
.gt_bg-repeat--no-repeat {
  background-repeat: no-repeat;
}
```
#### Background Size
```css
.gt_bg-size--auto {
  background-size: auto;
}
.gt_bg-size--cover {
  background-size: cover;
}
.gt_bg-size--contain {
  background-size: contain;
}
```
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
#### Border Color
```css
.gt_border-color--brand {
  border-color: #{themeBrandColor};
}
.gt_border-color--highlight  {
  border-color: #{themeHighlightColor};
}
.gt_border-color--section  {
  border-color: #{themeSectionBackgroundColor};
}
.gt_border-color--transparent  {
  border-color: transparent;
}
.gt_border-color--current  {
  border-color: currentColor;
}
```
#### Border Style
```css
.gt_border-style--solid {
  border-style: solid;
}
.gt_border-style--dashed  {
  border-style: dashed;
}
.gt_border-style--dotted  {
  border-style: dotted;
}
.gt_border-style--double  {
  border-style: double;
}
.gt_border-style--none  {
  border-style: none;
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
#### User Select
```css
.gt_user-select--none {
  user-select: none;
}
```

