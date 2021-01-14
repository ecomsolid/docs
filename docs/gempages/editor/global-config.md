## Global config là gì
Một object dạng
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
Được lấy từ API `api/admin/me` với tham số `global_configs=true`.
Thông tin này được gắn vào `store` khi khi load `Editor`.
## Cách dùng
### Tạo dữ liệu (`stagging-develop`)
1. <a href="https://gempagesv5.web.app/gp_configs/" target="_blank">Vào đường dẫn</a>, chọn mục **Global Config**
<img width="80%" src="/images/gempages/global-config-link.png">
2. Thêm `Objec item` với ý nghĩa:
  - `key`: định danh (*`camelCase`*)
  - `value`: Tên các shop muốn áp dụng (*`Array<string>`*)
    - ký tự `*` được hiểu là áp dụng cho tất cả (`["*"]`)
    - mảng rỗng (`[]`) được hiểu là không áp dụng

*Ví dụ*
> Áp dụng `Atom Button` cho các shop bắt đầu bằng chữ cái `g` và shop có tên là `hungdinh.myshopify.com`.
Ta sẽ tạo 1 `Objec item` như sau:
```json
"atomButton": ["g","hungdinh.myshopify.com"]
```

>[!note]
>Lưu ý dữ liệu phải đúng định dạng JSON object.
### Đọc dữ liệu từ API
1. Import utility function 
```javascript
import { checkKeyValid } from "@/app/utils/checkRoleApply.ts";
```
2. Kiểm tra điều kiện áp dụng:
```javascript
if( checkKeyValid("keyName") ){
  // do something 1
} else{
  // do something 2
}
```
Function này trả về `true/false` tức là chức năng muốn áp dụng có phù hợp với shop hiện tại hay không.
## Lợi ích
- Kiểm soát rủi do đối với những tính năng mới.
- Tăng tốc độ phát triển sản phẩm.
- Dễ dàng phản ứng với lỗi trong quá trình phát triển. (*Thay đổi thông tin config từ phí server mà không cần update lại code client*)
