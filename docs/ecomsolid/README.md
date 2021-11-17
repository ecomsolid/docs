## Bắt đầu với EcomSolid
> EcomSolid là một app trên shopify giúp khách hàng dễ dàng tạo một website theo ý thích bằng việc ghép các section.

### Dành cho đội HTML/CSS/JS và đội FrontEnd

Công việc code sections/add-ons là một tiến trình trong EcomSolid. Công việc hiểu đơn giản là code một section/add-on bằng HTML, SCSS, CSS, JS để khách hàng có thể sử dụng. Nhưng nếu chỉ như vậy thì code tạo ra sẽ không linh hoạt và không đáp ứng nhu cầu của nhiều người được.

EcomSolid giúp việc giải quyết việc đó bằng cách sinh ra một đối tượng là: Snippets. Nó giúp code của bạn chở nên linh hoạt hơn khi đến tay khách hàng.

*Một ví dụ đơn giản chúng ta có thể thay đổi vị trí của image trong section **Banner**:*

<img width="49%" src="/images/ecomsolid/banner-left.png">
<img width="49%" src="/images/ecomsolid/banner-right.png">

#### Cài đặt công cụ

**1. Cài đặt Git**

```bash
https://git-scm.com/downloads
```

> Bạn vào địa chỉ trên để tải git về máy rồi cài đặt. Nếu cảm thấy không cài được hãy xem video trước: <a href="https://www.youtube.com/watch?v=5KGY1OdhMIY" target="_blank">LINK VIDEO</a>

**2. Cài đặt NodeJS**

```bash
https://nodejs.org/en/
```

#### Làm quen với việc tạo section đầu tiên

> Ghé thăm và tìm hiểu về section: <a href="#/ecomsolid/sections?id=hướng-dẫn-tạo-một-section-mới">Tại đây</a>


### Dành cho đội Backend

#### Quy chuẩn khi code

- Không hardcode. Tạo các biến const cho các giá trị không đổi như các giá trị enum cho các db field (type, status,...)
  ```go
  // ví dụ file models/shop.go
  const (
      ShopStatusActive = "active"
      ShopStatusClosed = "closed"
  )
  ...
  ```
- Chia subfolder, không để 1 folder có quá nhiều file
- Chia nhỏ file, nhóm các hàm vào file theo tính chất từng hàm
- Tách nhỏ hàm, hàm làm đúng chức năng. Ví dụ hàm GetShop thì chỉ get shop, không thêm code tạo shop trong hàm
- Luôn check error hàm trả ra (nếu có)
- Lỗi có thể xử lý bằng code thì xử lý bằng code, không thì bắt lỗi bằng <a href="https://docs.sentry.io/platforms/go/" target="_blank">Sentry</a>
- Viết doc trên mỗi hàm, mô tả mục đích, logic xử lý trong hàm và ý nghĩa các tham số đầu vào
- Viết comment trên các block code mô tả block làm cái gì, tại sao phải làm như thế (tùy độ phức tạp)
- Gắn function vào struct type khi có thể, nhằm dễ xác định scope và quản lý hàm
  ```go
  type User struct {
      ID uint
      FirstName string
      LastName string
  }

  func (u *User) GetFullName() string {
      return fmt.Sprintf("%s %s", u.FirstName, u.LastName)
  }
  ```
- Không truyền request object vào các hàm, vì như vậy rất khó tái sử dụng hàm
- Dùng pointer khi có thể:
  - Vì khi truyền các giá trị qua các hàm, các giá trị sẽ được copy, tức là sẽ dùng thêm RAM
  - Khi giá trị biến truyền vào hàm không được phép thay đổi thì không dùng pointer
  - Khi hàm được thay đổi giá trị biến truyền vào thì dùng pointer (cách gorm dùng để trả ra kết quả query)
- List APIs luôn có `page_size` (client quy định 1 page bao nhiêu record) và `page_size_limit` (server quy định page size tối đa không được vượt quá)
- Xử lý db transaction khi kết hợp gọi 3rd party APIs (đối với các API thay đổi dữ liệu)
  - Nếu có thể thì gom chung các lệnh insert/update dữ liệu vào một chỗ và mở transaction ở đó, tránh mở một transaction quá lâu
  - Cần lưu ý việc khi nào gọi API, trước hay sau db transaction
  - Tránh gọi API trong db transaction, vì sau khi gọi mà transaction bị rollback thì khó xử lý
  - Nếu phải gọi API trong db transaction thì phải có cơ chế rollback lệnh gọi API
  - Dùng hàm `db.Transaction()` để sử dụng db transaction thay vì khởi tạo transaction manually bằng `db.Begin()`
- Sử dụng db session thay vì cookie session. API được thiết kế để tất cả các bên đều có thể sử dụng, nên việc dùng cookie là không hợp lý
- Hạn chế tối đa viết SQL trong code:
  - Sử dụng filter query bằng struct khi có thể (tìm hiểu thêm trên doc của gorm <a href="http://v1.gorm.io/docs/query.html#Query" target="_blank">v1</a>/<a href="https://gorm.io/docs/query.html" target="_blank">v2</a>):
    ```go
    // Inline
    db.First(&user, User{Name: "jinzhu", Age: 20})
    db.Find(&users, User{Name: "jinzhu", Age: 20})
    // AND conditions
    db.Where(User{Name: "jinzhu", Age: 20}).Find(&users)
    // NOT conditions
    db.Not(User{Name: "jinzhu", Age: 20}).Find(&users)
    ```
  - Trong trường hợp phải query với các toán tử khác `=` và `<>` thì vẫn phải viết where query do gorm chưa hỗ trợ
  - Dùng `FirstOrInit` khi cần query 1 row cho trường hợp có thì update, chưa có thì tạo mới
    ```go
    // Nếu không có user tên jinzhu tuổi 20 trong db thì khởi tạo biến user với Name = "jinzhu" và Age = 20
    db.FirstOrInit(&user, User{Name: "jinzhu", Age: 20})
    ```
  - Dùng `FirstOrCreate` khi cần query 1 row và auto tạo nếu chưa có (cú pháp tương tự `FirstOrInit`)
  - Dùng `Update` cùng struct để update đúng field cần update, tránh overwrite khi có nhiều goroutine chạy song song:
    ```go
    db.Model(&user).Update(User{Name: "jinzhu", Age: 20})  // Lưu ý: user phải có ID > 0, nếu không sẽ update cả table
    ```
  - Dùng `FOR UPDATE` option để lock row trong trường hợp không muốn bị goroutine khác overwrite:
    ```go
    db.Set("gorm:query_option", "FOR UPDATE").First(&user, 10)
    ```
- Dùng package <a href="https://github.com/elliotchance/pie" target="_blank">pie</a> để đơn giản hóa thao tác với slice
- Dùng .editorconfig file để đồng bộ indent
    ```yml
    root = true
    
    [*]
    indent_style = space
    indent_size = 4
    end_of_line = lf
    charset = utf-8
    trim_trailing_whitespace = true
    insert_final_newline = true
    
    [*.{yml,json}]
    indent_size = 2
    
    [Makefile]
    indent_style = tab
    ```

#### Test API bằng Postman

Backend sử dụng cookie để lưu user session, nên để có thể dùng Postman test API cần phải lấy được cookie của browser và cấu hình vào request trên postman.
Để làm việc này một cách đơn giản thì cần thực hiện các bước sau:

**1. Cài đặt Chrome extension**

Tìm trên <a href="https://chrome.google.com/webstore/category/extensions?hl=en" target="_blank">Chrome web store</a> extension **Postman Interceptor** và cài đặt.
<img width="60%" src="/images/ecomsolid/postman-interceptor-ext.jpg" style="display:block;margin-left:auto;margin-right:auto;">

**2. Cấu hình Postman**

- Trên giao diện Postman, bấm nút <img src="/images/ecomsolid/postman-capture-icon.jpg"> ở góc trên bên phải
- Trên popup hiện lên chọn tab **Cookies**
- Điền `localhost` vào ô **Domains** và bấm **Add domain** để Postman biết phải bắt cookie của localhost

**3. Bắt cookie để test API**

- Mỗi lần bật Postman để test API, trước khi gửi request cần vào lại popup ở bước 2 và bấm **Capture cookies**
- Sau đó dùng Chrome vào trang app/admin đang chạy trên localhost và đăng nhập. Nếu đã đăng nhập thì chỉ cần reload lại page
