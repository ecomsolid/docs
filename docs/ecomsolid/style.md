## Bem CSS
```css
/* Một Block (khối) độc lập */
.gt_block {}

/* Element (phần tử) con, phụ thuộc vào Block ở trên */
.gt_block__heading {}

/* Modifier (bộ điều chỉnh) thay đổi trạng thái của Block */
.gt_block__heading--white {}
.gt_block__heading--green {}
```
## Media Responsive
Những màn hình tiêu chuẩn. Ngoài ra có thể thêm các màn hình khác để tùy biến với bố cục của mình.

```css
/**
 * Name: Desktop + Laptop
 * Ký hiệu: lg
 * Screens: > 1200px
 */

/**
 * Name: Ipad Pro + Laptop Small
 * Ký hiệu: md
 * Screens: 992px < md <= 1200px
 */
@media (max-width: 1200px) {
}

/**
 * Name: Tablet
 * Ký hiệu: sm
 * Screens: 576px < sm <= 992px
 */
@media (max-width: 992px) {
}
@media (max-width: 768px) {
}

/**
 * Name: Mobile
 * Ký hiệu: xs
 * Screens: xs < 576px
 */
@media (max-width: 576px) {
}
@media (max-width: 480px) {
}
@media (max-width: 360px) {
}
```
## Quy định Class Global

>[!tip]
> Cần tìm hiểu thêm về những class global ở đây. (<a href="#/ecomsolid/class-global" target="_blank">Hướng dẫn chi tiết</a>)