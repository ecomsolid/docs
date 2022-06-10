## Editor Event
- render-html-{atom.section/widget_parent_id}-{atom.attribute}
  - Emit event khi atom render lại html
  - Return: true/false
- trigger-slider-{atomSliderId}
  - Emit event khi active setting 1 atom trong slider widget
  - Return: { 'sliderIndex': sliderIndex  }
- optimal-{section/widget id}-{snippet.attribute}
  - Emit event khi change setting của snippet có trigger js
  - Return: Value setting của snippet
- editor-section-refresh-html
  - Emit event khi section/widget/element render Html
  - Return: section/widget/element
- editor-section-refresh-css
  - Emit event khi section/widget/element render Css
  - Return: section/widget/element
- component-${id}-destroy
  - Emit event khi section/widget hidden or remove
  - Return: true
## Cấu trúc chuẩn

### Lưu ý

> [!note]
> Mọi người tạo file `es-script.ejs.js` và viết script kiểu mới ở trong đó
> Code được biên dịch ra sẽ được tự động lưu trong file `script-backup.ejs.js` để backup lại script sau khi đã được dịch

Trong script sẽ có sẵn các biến:

- `id` : id của section/widget/atom
- `elementClassName` : class của section/widget/atom
- `store` : window.SOLID.store
- `$element` : element của script như atom, addon hoặc section được lấy từ elementClassName

Syntax:

- Có keyword `module.exports` để khởi tạo script.
- Phải có đầy đủ dấu `,` và các `block` trong script .

### Cấu trúc

Cấu trúc của script sẽ gồm các block: data, init, store, events, methods, destroy được sắp xếp đúng thứ tự

```js
module.exports = {
  data() {},
  init() {},
  store: {},
  events: {},
  methods: {},
  destroy() {},
};
```

#### Data Block

Data Block bao gồm các variables có trong script

```js
data() {
	var id = "<%=id%>";
	var elementClassName =  ".gt_atom-<%=id%>";
	var $popups;
	var openPopupTimeout;
},
```

> [!note]
> Trong Data Block luôn có sẵn 2 biến id = "<%=id%>" và elementClassName =".gt_atom-<%=id%>" hoặc ".gt_widget-<%=id%>" hoặc ".gt_section-<%=id%>" tùy từng repo

#### Init Block

Init Block bao gồm các câu lệnh khởi tạo có trong script như khởi tạo biến, khởi tạo carousel, khởi tạo event cho window, .....

```js
init()  {
	$popups = $element.querySelectorAll(".gt_atom-nav-search");
	$owl = new Owl();
},
```

#### Store Block

Store Block có cấu trúc như code bên dưới, bao gồm:

- `getState`: định danh ra các state sẽ được lấy ra trong store.
- `subscribe`: subscribe event khi state thay đổi

```js
store:  {
	getState:  {
    cart: cart,
    discount: discount,
	},
	subscribe:  {
		cart: openSearchPopup,
		addToCartSuccess: openCartDrawer,
	},
},
```

Đoạn code trên sẽ được render như sau:

```js
var cart = store.getState("cart") || {};
var unsubscribe_1 = store.subscribe("cart", openSearchPopup);
unsubscribes.push(unsubscribe_1);
var unsubscribe_2 = store.subscribe("addToCartSuccess", openCartDrawer);
unsubscribes.push(unsubscribe_2);
function destroy() {
  for (var i = 0; i < unsubscribes.length; i++) {
    unsubscribes[i]();
  }
}
```

#### Events Block

Events Block có cấu trúc như code bên dưới, dùng để tạo ra các sự kiện trên DOM, bao gồm:

- `"element"`: class, id, attribute, ... của element cần thêm sự kiện
- `event`: click, change, input, .... tên của sự kiện cần thêm
- `method`: method được tạo ra trong Methods Block

```js
events:  {
	".gt_main-icon-search":  {
    click: openSearchPopup,
    change: inputChange,
	},
	".gt_close":  {
    click: closeSearchPopup,
    input: textareaChange,
	},
},
```

Đoạn code trên sẽ được render như sau:

```js
var $elements_1 = $element.querySelectorAll(".gt_main-icon-search");
for (var idxElEvent0 = 0; idxElEvent0 < $elements_1.length; idxElEvent0++) {
  $elements_1[idxElEvent0].addEventListener("click", openSearchPopup);
  $elements_1[idxElEvent0].addEventListener("change", inputChange);
}
var $elements_2 = $element.querySelectorAll(".gt_close");
for (var idxElEvent0 = 0; idxElEvent0 < $elements_2.length; idxElEvent0++) {
  $elements_2[idxElEvent0].addEventListener("click", closeSearchPopup);
  $elements_2[idxElEvent0].addEventListener("input", textareaChange);
}
```

#### Methods Block

Methods Block có cấu trúc như code bên dưới, dùng để tạo ra các methods của chương trình, bao gồm:

- `"element"`: class, id, attribute, ... của element cần thêm sự kiện
- `event`: click, change, input, .... tên của sự kiện cần thêm
- `method`: method được tạo ra trong Methods Block

```js
methods: {
	openSearchPopup() {
		console.log("open search popup");
	},
	closeSearchPopup() {
		console.log("close search popup");
	},
	openCartDrawer() {
		console.log("open cart drawer");
	},
},
```

Đoạn code trên sẽ được render như sau:

```js
function openSearchPopup() {
  console.log("opensearchpopup");
}
function closeSearchPopup() {
  console.log("closesearchpopup");
}
function openCartDrawer() {
  console.log("opencartdrawer");
}
```

#### Destroy Block

Destroy Block sẽ thực thi các câu lệnh khi element bị destroy

```js
destroy() {
	console.log("destroy");
},
```

Đoạn code trên sẽ được render như sau:

```js
var unsubscribeDestroy = store.subscribe("component-" + id + "-destroy", function () {
  console.log("destroy");
  destroy();
  unsubscribeDestroy();
});
```

#### Public Functions Block (Optional)

Public Block sẽ public ra các method để các script bên ngoài có thể gọi được.

Các public function sẽ được gắn trong

```js
window.SOLID.public["atom" + "_" + id + "_" + indexEl];
```

- type: atom/widget/section
- id : id của atom/widget/section
- index: index của atom/widget/section

```js
public: {
	  openSearchPopup,
	  closeSearchPopup
},
```

#### Global Block (Optional)

Global Block: các block còn lại đều đang chạy script của từng element. Vậy nên Global block sẽ support chạy script của tất cả các element, sinh ra trong function lớn nhất thay vì trong function script() như các block khác.

Block này thường được sử dụng khi muốn chạy lại script của tất cả các element

```js
(function () {
  var elementClassName = ".gt_atom-<%=id%>";
  var $elements = document.querySelectorAll(elementClassName);
  var store = window.SOLID.store;
  var id = "<%=id%>";
  function script($target) {}
  /* run all script */
  for (var indexEl = 0; indexEl < $elements.length; indexEl++) {
    var $target = $elements[indexEl];
    script($target);
  }
  /* GLOBAL SCRIPT HERE */

  /* END GLOBAL SCRIPT */
})();
```

Cách sử dụng

```js
global() {
	someFuncHere()
},
```

### Ví dụ

- Script

```js
module.exports = {
  data() {
    var id = "<%=id%>";
    var elementClassName = ".gt_atom-<%=id%>";
    var $popups;
    var openPopupTimeout;
  },
  init() {
    $popups = $element.querySelectorAll(".gt_atom-nav-search");
  },
  store: {
    getState: {
      cart: cart,
    },
    subscribe: {
      cart: openSearchPopup,
      addToCartSuccess: openCartDrawer,
    },
  },
  events: {
    ".gt_main-icon-search": {
      click: openSearchPopup,
    },
    ".gt_close": {
      click: closeSearchPopup,
    },
  },
  methods: {
    openSearchPopup() {
      console.log("open search popup");
    },
    closeSearchPopup() {
      console.log("close search popup");
    },
    openCartDrawer() {
      console.log("open cart drawer");
    },
  },
  destroy() {},
  public: {
    openSearchPopup,
    closeSearchPopup,
  },
  global() {
    window.SOLID.store.subscribe("runAllScript", () => {
      for (var indexEl = 0; indexEl < $elements.length; indexEl++) {
        var $target = $elements[indexEl];
        var public = script($target);
        window.SOLID.public = window.SOLID.public || {};
        window.SOLID.public["atom" + "_" + id + "_" + indexEl] = public;
      }
    });
  },
};
```

- Compile Script

```js
(function () {
  var elementClassName = ".gt_atom-<%=id%>";
  var $elements = document.querySelectorAll(elementClassName);
  var store = window.SOLID.store;
  var id = "<%=id%>";
  function script($target) {
    var $element = $target;
    /* data block script */
    var $popups;
    var openPopupTimeout;
    /* methods block script */
    function openSearchPopup() {
      console.log("opensearchpopup");
    }
    function closeSearchPopup() {
      console.log("closesearchpopup");
    }
    function openCartDrawer() {
      console.log("opencartdrawer");
    }
    /* init block script */
    $popups = $element.querySelectorAll(".gt_atom-nav-search");
    /* store block script */
    var unsubscribes = [];
    var cart = store.getState("cart") || {};
    var unsubscribe_1 = store.subscribe("cart", openSearchPopup);
    unsubscribes.push(unsubscribe_1);
    var unsubscribe_2 = store.subscribe("addToCartSuccess", openCartDrawer);
    unsubscribes.push(unsubscribe_2);
    function destroy() {
      for (var i = 0; i < unsubscribes.length; i++) {
        unsubscribes[i]();
      }
    }
    /* events block script */
    var $elements_1 = $element.querySelectorAll(".gt_main-icon-search");
    for (var idxElEvent0_1 = 0; idxElEvent0_1 < $elements_1.length; idxElEvent0_1++) {
      $elements_1[idxElEvent0_1].addEventListener("click", openSearchPopup);
    }
    var $elements_2 = $element.querySelectorAll(".gt_close");
    for (var idxElEvent0_2 = 0; idxElEvent0_2 < $elements_2.length; idxElEvent0_2++) {
      $elements_2[idxElEvent0_2].addEventListener("click", closeSearchPopup);
    }
    var unsubscribeDestroy = store.subscribe("component-" + id + "-destroy", function () {
      destroy();
      unsubscribeDestroy();
    });
    return {
      openSearchPopup,
      closeSearchPopup,
    };
  }
  /* run all script */
  for (var indexEl = 0; indexEl < $elements.length; indexEl++) {
    var $target = $elements[indexEl];
    var public = script($target);
    window.SOLID.public = window.SOLID.public || {};
    window.SOLID.public["atom" + "_" + id + "_" + indexEl] = public;
  }
  /* global block script */
  window.SOLID.store.subscribe("runAllScript", () => {
    for (var indexEl = 0; indexEl < $elements.length; indexEl++) {
      var $target = $elements[indexEl];
      var public = script($target);
      window.SOLID.public = window.SOLID.public || {};
      window.SOLID.public["atom" + "_" + id + "_" + indexEl] = public;
    }
  });
})();
```

### Khu vực dev cho mỗi block

Trong mỗi block sẽ có 1 khu vực code chỉ hiện thị trong editor và sẽ được split đi khi update live

#### data block

```js
data() {
	var a = 1;
	dev: {
		var devA = 1;
	}
}
```

#### init block

```js
init() {
	function();
	dev: {
		function1();
	}
}
```

#### events block

```js
events: {
	".gt_main-icon-search":  {
		  click: openSearchPopup,
		  change: inputChange,
	 },
	 dev: {
	 	".gt_main-icon-search-dev":  {
			  click: openSearchPopup1,
		 },
	 }
}
```

#### store block

```js
store: {
	getState:  {
		cart: cart,
		discount: discount,
	},
	subscribe:  {
		cart: openSearchPopup,
		addToCartSuccess: openCartDrawer,
	},
	dev: {
		getState:  {
			cart: cart,
		},
		subscribe:  {
			cart: openSearchPopup,
		},
	}
}
```

#### methods block

```js
methods: {
	getState()  {
		console.log("hello dev");
	},
	dev: {
		helloDev() {
			console.log("welcome");
		}
	}
}
```
