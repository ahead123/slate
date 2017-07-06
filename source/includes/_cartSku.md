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
    let cart_sku = "",
        aA = null,
        isMobile = false,
        url = window.location.href,
        r = /[,A-Za-z0-9]+/g;
    if (mobileUrlTerm && url.indexOf(mobileUrlTerm) > -1) {
        isMobile = true;
        aA = document.querySelectorAll(mobilePath);
    } else {
        aA = document.querySelectorAll(desktopPath);
    }
    for (let i = 0; i < aA.length; i++) {
        if (isMobile) {
            cart_sku += "," + aA[i].textContent.toLowerCase().trim() + "MOBILE"
        } else {
            cart_sku += "," + aA[i].textContent.toLowerCase().trim() + "DESKTOP"
        }

    }
    if (cart_sku != "") {
        cart_sku = cart_sku.substring(1, cart_sku.length).match(r).join("")
    }


    return cart_sku;
}

mapMobileDesktopCartSku("Enter mobileUrlTerm", "Enter mobilePath", "Enter desktopPath")

//example
mapMobileDesktopCartSku("m.something","div > span > a.cart_product_id","span > a.cart-product-id");

shcp: "greenshoesDESKTOP,blueshoesDESKTOP,proteinpowderDESKTOP,horweenbeltDESKTOP"

or

shcp: "greenshoesMOBILE,blueshoesMOBILE,proteinpowderMOBILE,horweenbeltMOBILE"

```

The mapMobileDesktopCartSku function expects a a mobile identifier from the mobile site URL, and a mobile CSS path, and a desktop CSS path.
The mapMobileDesktopCartSku function returns a comma separated string of cart skus with either MOBILE or DESKTOP appended to each sku depending on the verison of the site.

The SteelHouse(SH) tracking pixel also fires a SH Facebook(FB) pixel and a common issue that occurs is special characters in the sku mapping are not properly escaped which cause syntax errors to fire in the SH FB pixel.

The mapMobileDesktopCartSku funciton will remove all special characters and whitespace preventing this error from triggering in the SH FB pixel.

> copy the code block below to use in pixel dashboard

```javascript
mapMobileDesktopCartSku = (mobileUrlTerm = null, mobilePath = null, desktopPath = null) => { let cart_sku = "", aA = null, isMobile = false, url = window.location.href, r = /[,A-Za-z0-9]+/g; if (mobileUrlTerm && url.indexOf(mobileUrlTerm) > -1) { isMobile = true; aA = document.querySelectorAll(mobilePath); } else { aA = document.querySelectorAll(desktopPath); } for (let i = 0; i < aA.length; i++) { if (isMobile) { cart_sku += "," + aA[i].textContent.toLowerCase().trim() + "MOBILE" } else { cart_sku += "," + aA[i].textContent.toLowerCase().trim() + "DESKTOP" } } if (cart_sku != "") { cart_sku = cart_sku.substring(1, cart_sku.length).match(r).join("") } return cart_sku; } mapMobileDesktopCartSku("Enter mobileUrlTerm", "Enter mobilePath", "Enter desktopPath")
```
### Parameters

Parameter | Default | Description
--------- | ------- | -----------
mobileUrlTerm | null | a term from the URL that identifies the mobile site - i.e. "m.somesite" or "somesite.com/mobile/"
mobilePath | null | single css path(s) to an html elements on cart page, containing some sku vlaue i.e. a <code>```<tr class="product_id">```</code> element.
desktopPath | null | single css path(s) to an html elements on cart page, containing some sku vlaue i.e. a <code>```<tr class="product_id">```</code> element.
