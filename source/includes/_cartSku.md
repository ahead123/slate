# Cart Sku

## mapCartSku()


```javascript

mapCartSku = (cssPath) => {
  let cartSku = "";
  let y = /[0-9a-zA-Z,]+/g;
	let aA = document.querySelectorAll(cssPath);
  for (let i = 0; i < aA.length; i++) {
      cartSku += "," + aA[i].textContent.trim()
  };
  cartSku = cartSku.substring(1, cartSku.length);
  cartSku = cartSku.match(y).join("")
  return cartSku
};

mapCartSku("Enter cart product skus cssPath")

//example
mapCartSku("table > tr > span > a.cart-product-id");

shcp: "greenshoes,blueshoes,proteinpowder,horweenbelt"

```

The mapCartSku function expects a cssPath common to the cart skus
The mapCartSku function returns a comma separated string of cart skus.

The SteelHouse(SH) tracking pixel also fires a SH Facebook(FB) pixel and a common issue that occurs is special characters in the sku mapping are not properly escaped which cause syntax errors to fire in the SH FB pixel.

The mapCartSku funciton will remove all special characters and whitespace preventing this error from triggering in the SH FB pixel.

> copy the code block below to use in pixel dashboard

```javascript
mapCartSku = (cssPath) => { let cartSku = ""; let y = /[0-9a-zA-Z,]+/g; let aA = document.querySelectorAll(cssPath); for (let i = 0; i < aA.length; i++) { cartSku += "," + aA[i].textContent.trim() }; cartSku = cartSku.substring(1, cartSku.length); cartSku = cartSku.match(y).join("") return cartSku }; mapCartSku("Enter cart product skus cssPath")
```
### Parameters

Parameter | Default | Description
--------- | ------- | -----------
cssPath | one css path | single css path(s) to an html elements on cart page, containing some sku vlaue i.e. a <code>```<tr class="product_id">```</code> element.


## mapMobileDesktopCartSku()


```javascript

mapMobileDesktopCartSku = (mobileUrlTerm = null, mobilePath = null, desktopPath = null) => {
    let cart_sku = "";
    let aA = null;
    let isMobile = false;
    let url = window.location.href;
    let r = /[,A-Za-z]+/g;
    checkVersion = false;
    if (mobileUrlTerm) {
        checkVersion = true
    }
    if (mobileUrlTerm && url.indexOf(mobileUrlTerm) > -1) {
        isMobile = true;
        aA = document.querySelectorAll(mobilePath);
        for (let i = 0; i < aA.length; i++) {
        cart_sku += "," + aA[i].textContent.toLowerCase()..trim() + "MOBILE";
        }
    } else {
        aA = document.querySelectorAll(desktopPath);
        for (let i = 0; i < aA.length; i++) {
        cart_sku += "," + aA[i].textContent.toLowerCase().trim() + "DESKTOP";
        }
    }
    cart_sku = cart_sku.substring(1, cart_sku.length);
    if (isMobile) {
        cart_sku = cart_sku;
    } else if (checkVersion && !isMobile) {
        cart_sku = cart_sku;
    } else {
        cart_sku = cart_sku;
    }
    return cart_sku.match(r).join("");
};
mapMobileDesktopCartSku("mobile url", "mobile CSS path", "desktop CSS path");

//example
mapMobileDesktopCartSku("m.swimoutlet", "div.m_view_cart_group_info > div.carttext > a", "div > h2 > a");;

Desktop shcp: "suitswimsuitorangeDESKTOP,formancebackredDESKTOP"
Mobile shcp:  "swimbriefyouthMOBILE,trapswimsuitMOBILE"
```

The mapMobileDesktopCartSku function expects a cssPath common to the cart skus
The mapMobileDesktopCartSku function returns a comma separated string of cart skus.

The SteelHouse(SH) tracking pixel also fires a SH Facebook(FB) pixel and a common issue that occurs is special characters in the sku mapping are not properly escaped which cause syntax errors to fire in the SH FB pixel.

The mapMobileDesktopCartSku function will remove all special characters and whitespace preventing this error from triggering in the SH FB pixel.

> copy the code block below to use in pixel dashboard

```javascript
mapMobileDesktopCartSku = (mobileUrlTerm = null, mobilePath = null, desktopPath = null) => { let cart_sku = ""; let aA = null; let isMobile = false; let url = window.location.href; let r = /[,A-Za-z]+/g; checkVersion = false; if (mobileUrlTerm) { checkVersion = true } if (mobileUrlTerm && url.indexOf(mobileUrlTerm) > -1) { isMobile = true; aA = document.querySelectorAll(mobilePath); for (let i = 0; i < aA.length; i++) { cart_sku += "," + aA[i].textContent.toLowerCase().split("-")[0].trim() + "MOBILE"; } } else { aA = document.querySelectorAll(desktopPath); for (let i = 0; i < aA.length; i++) { cart_sku += "," + aA[i].textContent.toLowerCase().trim() + "DESKTOP"; } } cart_sku = cart_sku.substring(1, cart_sku.length); if (isMobile) { cart_sku = cart_sku; } else if (checkVersion && !isMobile) { cart_sku = cart_sku; } else { cart_sku = cart_sku; } return cart_sku.match(r).join(""); }; mapMobileDesktopCartSku("mobile url", "mobile CSS path", "desktop CSS path");
```
### Parameters

Parameter | Default | Description
--------- | ------- | -----------
Mobile Url | null    | Enter the mobile url in the first parameter. - i.e So for "m.mywebsite.com", you would enter - "m.mywebsite".
Mobile Selector  | null | One mobile html element containing some sku vlaue - i.e. a <code>```<span class="product_sku">```</code> element.
Desktop Selector | null | One desktop html element containing some sku vlaue i.e. a <code>```<span class="product_sku">```</code> element.
