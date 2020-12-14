## Cơ chế load thư viện mới
Các sections, atom, widget dùng thư viện bên ngoài thì các thư viện đó sẽ được gọi khi init trong các libs dùng các thư viện này. 
Tức là khi nào dùng thì mới load.

### Syntax

```js
window.SOLID.library.loadSource(sources, callback);
```

Trong đó: 
- `sources` : array đường link khi load nhiều thư viện hoặc string đường link khi load 1 thư viện
- `callback` : function sẽ được thực thi khi load xong sources  

### Ví dụ

- Load nhiều thư viện 

```js
window.SOLID.library.loadSource(
  [
    "https://d3dfaj4bukarbm.cloudfront.net/production/static/client/libs/owl.carousel.min.css",
    "https://d3dfaj4bukarbm.cloudfront.net/production/static/client/libs/owl.carousel.min.js",
  ],
  function () {
    console.log("run script!");
  }
);
```

- Load 1 thư viện

```js
window.SOLID.library.loadSource(
  "https://d3dfaj4bukarbm.cloudfront.net/production/static/client/libs/owl.carousel.min.js",
  function () {
    console.log("run script!");
  }
);
```

## Quy trình viết thư viện cho atom

Các thư viện cho atom sẽ được viết ở dạng `class` trong `typescript`

Chia làm 2 dạng:

- `lib base` : Không tương tác với dom, chỉ tính toán
- `lib dom` : tính toán và tương tác với dom

### Chú ý:

- Phải có comment các khu vực public method và private method.
- Khu vực public methods sẽ được viết lên trên private methods để thuận tiện cho việc đọc code thư viện

### Ví dụ

- Lib base

```js
interface Settings {
  key: string;
  endDate: string;
  distance: number;
  countdown: boolean;
}

class Countdown {
  private settings: Settings;

  constructor(options: Settings) {
    this.settings = {...this.settings, options};
  }

  /* public method */
  public calculate() {
    console.log("hello world", this.settings);
    this.getRemainingTime();
  }

  public setTime() {
    console.log("set time");
    this.getTimeBySecond();
  }

  /* private method */
  private getRemainingTime() {
    console.log("get remaining");
  }

  private getTimeBySecond() {
    console.log("get second");
  }
}

/* declare lib */
window.SOLID.Countdown = function(options) {
  return new Countdown(options);
}
```

- Lib dom

```js
interface Settings {
  classBuyNow: string;
}

class GtBuyNow {
  private settings: Settings;
  private $element: any;

  constructor($element: any, options: Settings) {
    this.$element = $element;
    this.settings = {...this.settings, options};
  }

  /* public method */
  public buyNow() {
    this.$element
        .find(this.settings.classBuyNow)
        .off("click.addToCart.ByNow")
        .on("click.addToCart.ByNow", function(e) {
          console.log("buy now");
        });
  }
}

/* declare lib */
window.SOLID.GtBuyNow = function($element, options) {
  return new GtBuyNow($element, options);
}
```
