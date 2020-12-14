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
window.SOLID.library.loadSource("https://d3dfaj4bukarbm.cloudfront.net/production/static/client/libs/owl.carousel.min.js",
  function () { 
    console.log("run script!");
  }
);

```
