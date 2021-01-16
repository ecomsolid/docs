## Mục Tiêu:
  - Kiểm soát rủi do đối với những tính năng mới.
  - Tăng tốc độ phát triển sản phẩm.
  - Dễ dàng phản ứng với lỗi trong quá trình phát triển.


## Backend
Trả về object dạng
```json
{
  "atomButton": ["g","hungdinh.myshopify.com"],
  "atomImage": ["tr"],
  "atomHeading": ["tr"],
  "atomHeroBanner":["g"],
  "upgradePImage": ["*"],
  "upgradeHeroBanner": ["v"],
  "changeNameQuantity": ["*"],
  "flowActionSetupData": ["tr","ch","gm"]
}
```
Xem thêm tại <a href="#/gempages/editor/global-config" target="_blank">GlobalConfig</a>
## Frontend
- Sử dụng thông tin backend trả về để xác định có thực hiện test hay không.
- Với việc test code trong editor sẽ if else điều kiện để thực hiện
- Với việc test snippet (tempate, script… thay đổi trong getMySnippets.html) sẽ check điều kiện. Và filter lại dữ liệu sau khi GetSnippets từ phía server. (Lưu ý 1 số case khách add thêm snippet từ library…)
- Với việc test lib js (vd: gfv3products.js, gfv1popup.js...). Snippets mới sẽ thêm 1 param(đặt tên riêng, để sau này có thể bỏ đi trong lib) trong options để báo cho lib biết là test với version nào. Trong lib sẽ có code check phần option này để test code mới.

## Ví dụ
- gfV3ProductSwatches truyền thêm **ver301: 1**
- Trường hợp khách bị lỗi với lib => admin sẽ tắt test tính năng đó. Sau đó khách kéo lại snippet (hoặc bỏ phần ver301 trong editcode).

```bash
jQuery(function () {
  var $module = jQuery('#m-{{module-id}}').children('.module');
  var swatchText = $module.attr('data-swatch-text') != undefined ? $module.attr('data-swatch-text') : '1';
  $module.gfV3ProductSwatches({
    ver301: 1,
    swatchText: swatchText,
    onSwatchSelected: function (variant, $swatch) { }
  });
});
```
