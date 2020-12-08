## Giới thiệu về công việc

## Quy trình làm việc
### Hiểu về intercom
### Giao tiếp với Support
### Chốt vấn đề của khách
### Phân loại vấn đề và giải pháp
#### Các loại vấn đề
##### App thứ 3
##### Custom code
##### Thiếu settings / Không tìm thấy settings
##### Conflict themes/apps
### Thực hiện
### Báo lại với Support
### Lưu trữ
#### Export vào Library
#### Viết thành tài liệu
#### Note tại intercom
#### Gắn nhãn tài base

## Tài liệu tham khảo

### App thứ 3
#### Review
#### Recharge
### Custom code
#### Top Bar
#### Header
#### Product

##### Custom giá theo một công thức.
>Thay đổi giá khi variant hoặc quantity thay đổi
```html
<span style="color:#2D8411"><b> em 12x de {{ current_variant.price | times: 1.2049 | divided_by: 12 | round :3 | money }}</b></span>
```
```js
(function() {
    var $priceSplit = $(".price-split");
    var productJson = $priceSplit.closest("[keyword='product']").find(".ProductJson").text();
    try {
        if (productJson) {
            productJson = JSON.parse(productJson)
            var formatMoneyPlugin = function(price) {
                var dataCurrency = window.store.get('dataCurrency');
                var format = __GemSettings.money;
                if (dataCurrency) {
                    price = Shopify.gemFormatMoney(price, dataCurrency.currency, dataCurrency.data);
                } else {
                    price = Shopify.formatMoney(price, format);
                }
                return price
            }
            var changePrice = function(price) {
                var quantity = window.SOLID.store.getState("quantity"+productJson.id)
                var price = $priceSplit.attr("data-price");
                if (!quantity || quantity == 0) {
                    quantity = 1
                }
                price = parseFloat(price)*parseFloat(quantity)
                $priceSplit.html(formatMoneyPlugin(price));
            }
            store.change("quantity"+productJson.id, function(quantity) {
                changePrice()
            })
            store.change("variant" + productJson.id, function(variant) {
                if (variant && variant.id) {
                    var price = variant.price;
                    price = (price*1.2049) / 12
                    price = Math.round(price * 100) / 100;
                    $priceSplit.attr("data-price", price);
                } else {
                    $priceSplit.attr("data-price", "0");
                }
                changePrice()
            });
        }
    } catch (e) {
        console.log(e);
    }
})();
```