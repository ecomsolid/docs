> [!note]
> Document dưới đây là cách sử dụng và các lưu ý về addons

## Upsell Quantity Discount V2

### Element Type

<img width="20%" src="/images/ecomsolid/addons/element_type.png">

Addon được chia thành 4 loại:

- `Section Product`: addon được đặt trong các section product detail
- `Product Page`: addon trông giống như 1 section và được đặt trong product page
- `Cart Drawer`: addon dùng để upsell cho từng cart item trong cart drawer. Addon phải chuyển thành `global addon` thì mới dùng được trong cart drawer
- `Section Cart`: tương tự như trong cart drawer, addon dùng để upsell cho từng cart item trong cart page. Addon phải ở trong cart page

> [!note]
> Chức năng chi tiết của từng loại sẽ đươc mô tả ở phần presets bên dưới

### Presets

> Mỗi Element Type sẽ có nhiều Presets khác nhau.

#### Section Product

##### Preset 1

<img width="40%" src="/images/ecomsolid/addons/uqd_section_prod_preset_1.png">

Với preset này, khi click button atc sẽ add vào cart số lượng items tương tứng. Trong setting của button atc sẽ đc ẩn đi setting actions.

Khách có thể chọn `Action Buy Redirect` và bật tắt `Variants Selector` ở setting của addons

<img width="20%" src="/images/ecomsolid/addons/action_buy_redirect.png">

Giá `price` hiển thị trên từng discount item là giá sau khi đã được giảm. Giá `compare_price` bên cạnh là giá khi chưa được giảm tính theo `original_price` của product

> [!note]
> Với preset này có thể add được item kèm theo properties mà khách custom trong section product

##### Preset 2

<img width="40%" src="/images/ecomsolid/addons/uqd_section_prod_preset_2.png">

Khi chọn 1 discount item thì quantity của section product sẽ được thay đổi theo số lượng tương ứng.

Ngoài ra khi thay đổi số lượng của ô input quantity trong section product thì addon sẽ tự động active đúng discount item theo số lượng tương ứng.

Các tag: `Most Popular`, `Most Value` được setting trong phần `Tag` khi tạo discount trong control discount manager

<img width="50%" src="/images/ecomsolid/addons/discount_tag.png">

#### Product Page

##### Preset 1

<img width="60%" src="/images/ecomsolid/addons/prod_preset.png">

Product được add vào cart là product của product page đó. Khách không phải pick product mà sẽ tự động theo product page.

Setting về appearance của discount item 1 và item 3 sẽ giống nhau. Item 2 sẽ setting riêng

Hiện tại Preset này chỉ được đặt trong Product Page. Có thể thay đổi setting snippet để hiển thị ở các page khác nếu khách có nhu cầu (phần này sẽ được thay đổi sau)

> [!note]
> Hiện tại addons chỉ support show tối đa 3 discounts

#### Cart page

##### Preset 1

<img width="50%" src="/images/ecomsolid/addons/cart_preset.png">

Với mỗi item trong cart, addon sẽ show upsell tương ứng với discount khách đã setting trong discount manager.

Khi click atc trong addon thì cart page sẽ được reload để render lại và tính toán giá tiền

> [!note]
> Nếu đã có sản phẩm trong cart rồi thì addon sẽ chỉ show số lượng item cần thêm để đủ discount chứ ko fixed quantity. <br /> Nếu đã đủ số lượng của sản phẩm đó trong cart rồi thì addon sẽ ẩn item discount đó đi.

#### Cart Drawer

##### Preset 1

<img width="40%" src="/images/ecomsolid/addons/cart_drawer_preset.png">

Logic hiển thị trong cart drawer giống hệt như hiển thị trong cart page

Khi click atc trong addon thì thay vì reload lại như cart page, cart drawer sẽ tự render và tính toán lại mà không cần reload

> [!note]
> Cần move addon lên global addon để có thể hoạt động được trong cart drawer

## Dành cho developers

> Các lưu ý về addon cho developers

### Upsell Quantity Discount V2

#### Discounts data sẽ được lưu ở đâu?

Thay vì lưu discount data ở trong biến window.SOLID.discounts và thêm đoạn code này vào theme.min.js (addon sẽ không hoạt động được khi sử dụng ở PB) => cần thay đổi cấu trúc lưu discounts data.

Cụ thể, hiện tại discounts data script sẽ đươc lưu vào 1 file riêng `ecomsolid-discounts.liquid` và được gắn vào `head` của `theme.liquid`

Bên trong `ecomsolid-discounts.liquid` lưu 1 đoạn js để push discount data vào `esDiscountsData` và discount data đã được format theo discount cũ để tính toán trong libs `gtCartDiscountV5` vào `discountsV2` trong `window.SOLID.store`

Addon UQDV2 dùng data ở `esDiscountsData` trong store để render thay vì dùng value của snippets như ở bản cũ. Vì bây giờ control discount manager được xử lí global nên không thể lưu discount data vào value của từng addon (local) mà phải lưu ở global. Để chỉ cần update discount trong discount manager thì tất cả các addon khác sẽ được update theo vì dùng data global

#### Lưu ý với presets của cart page và cart drawer

Với preset cho cart page và cart drawer, để addon hoạt động được thì cần thêm class `gt_cart-item` hoặc `gt_items--content` vào tag (div) wrapper của từng cart item. Đồng thời thêm các attribute: `data-product-id="{{ cart_item.product_id }}" data-product-handle="{{ cart_item.product.handle }}"` vào attribute của wrapper đó.
