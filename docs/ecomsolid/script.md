
## Cấu trúc chuẩn
### Lưu ý
Trong script sẽ có sẵn các biến: 
- `store` : window.SOLID.store
- `$element` : element của script như atom, addon hoặc section được lấy từ elementClassName

Syntax:  
- Có keyword `export default` để khởi tạo script.
- Phải có đầy đủ dấu `,` và các `block` trong script .

### Cấu trúc
Cấu trúc của script sẽ gồm các block: data, init, store, events, methods, destroy được sắp xếp đúng thứ tự

```js
export  default  {
	data()  {},
	init()  {},
	store:  {},
	events:  {},
	methods:  {},
	destroy()  {},
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

>[!note]
> Trong Data Block luôn phải có 2 biến id và elementClassName

#### Init Block
Init Block bao gồm các câu lệnh khởi tạo có trong script như khởi tạo biến, khởi tạo carousel

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
		cart: cart
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
function destroy()  {
	for (var i = 0; i < unsubscribes.length; i++) {
		unsubscribes[i]();
	}
}	
```

#### Events Block
Events	 Block có cấu trúc như code bên dưới, dùng để tạo ra các sự kiện trên DOM,  bao gồm:
- `"element"`: class, id, attribute, ... của element cần thêm sự kiện
- `event`: click, change, input, .... tên của sự kiện cần thêm
- `method`:  method được tạo ra trong Methods Block
```js
events:  {
	".gt_main-icon-search":  {
		click: openSearchPopup,
	},
	".gt_close":  {
		click: closeSearchPopup,
	},
},
```
Đoạn code trên sẽ được render như sau: 

```js
var $elements_1 = $element.querySelectorAll(".gt_main-icon-search");
for(var idxElEvent0 = 0; idxElEvent0 < $elements_1.length; idxElEvent0++) {
	$elements_1[idxElEvent0].addEventListener("click",openSearchPopup);
}
var $elements_2 = $element.querySelectorAll(".gt_close");
for(var idxElEvent0 = 0; idxElEvent0 < $elements_2.length; idxElEvent0++) {
	$elements_2[idxElEvent0].addEventListener("click", closeSearchPopup);
}
```

#### Methods Block
Methods	 Block có cấu trúc như code bên dưới, dùng để tạo ra các methods của chương trình,  bao gồm:
- `"element"`: class, id, attribute, ... của element cần thêm sự kiện
- `event`: click, change, input, .... tên của sự kiện cần thêm
- `method`:  method được tạo ra trong Methods Block

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
var unsubscribeDestroy = store.subscribe(id + "-destroy", function() {
	console.log("destroy");
	destroy();
	unsubscribeDestroy();
});
```

### Ví dụ
- Script
```js
export default {
	data() {
		var id = "<%=id%>";
		var elementClassName = ".gt_atom-<%=id%>";
		var $popups;
		var openPopupTimeout;
	},
	init() {
		$popups = $element.querySelectorAll(".gt_atom-nav-search");
	},
	store:  {
		getState:  {
			cart: cart,
		},
		subscribe:  {
			cart: openSearchPopup,
			addToCartSuccess: openCartDrawer,
		},
	},
	events:  {
		".gt_main-icon-search":  {
			click: openSearchPopup,
		},
		".gt_close":  {
			click: closeSearchPopup,
		},
	},
	methods:  {
		openSearchPopup()  {
			console.log("open search popup");
		},
		closeSearchPopup()  {
			console.log("close search popup");
		},
		openCartDrawer()  {
			console.log("open cart drawer");
		},
	},
	destroy()  {},
}
```
- Compile Script

```js
(function  ()  {
	var  id  =  "<%=id%>";
	var  elementClassName  =  ".gt_atom-<%=id%>";
	var  $elements  =  document.querySelectorAll(elementClassName);
	var  store  =  window.SOLID.store;
	if (!$elements.length) {
		return;
	}
	for (var  indexEl  =  0;  indexEl  <  $elements.length;  indexEl++) {
		var  $element  =  $elements[indexEl];
		/* data block script */
		var  $popups;
		var  openPopupTimeout;
		/* methods block script */
		function  openSearchPopup()  {
			console.log("opensearchpopup");
		}
		function  closeSearchPopup()  {
			console.log("closesearchpopup");
		}
		function  openCartDrawer()  {
			console.log("opencartdrawer");
		}
		/* init block script */
		$popups  =  $element.querySelectorAll(".gt_atom-nav-search");
		/* store block script */
		var  unsubscribes  = [];
		var  cart  =  store.getState("cart") ||  {};
		var  unsubscribe_1  =  store.subscribe("cart",  openSearchPopup);
		unsubscribes.push(unsubscribe_1);
		var  unsubscribe_2  =  store.subscribe("addToCartSuccess",  openCartDrawer);
		unsubscribes.push(unsubscribe_2);
		function  destroy()  {
			for (var  i  =  0;  i  <  unsubscribes.length;  i++) {
				unsubscribes[i]();
			}
		}
		/* events block script */
		var  $elements_1  =  $element.querySelectorAll(".gt_main-icon-search");
		for (var  idxElEvent0  =  0;  idxElEvent0  <  $elements_1.length;  idxElEvent0++) {
			$elements_1[idxElEvent0].addEventListener("click",  openSearchPopup);
		}
		var  $elements_2  =  $element.querySelectorAll(".gt_close");
		for (var  idxElEvent0  =  0;  idxElEvent0  <  $elements_2.length;  idxElEvent0++) {
			$elements_2[idxElEvent0].addEventListener("click",  closeSearchPopup);
		}
		var  unsubscribeDestroy  =  store.subscribe(id  +  "-destroy",  function  ()  {
			console.log("destroy");
			destroy();
			unsubscribeDestroy();
		});
	}
})();
```
