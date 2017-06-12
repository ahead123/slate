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

> copy this code block to use in pixel dashboard

> mapCartSku = (cssPath) => { let cartSku = ""; let y = /[0-9a-zA-Z,]+/g; let aA = document.querySelectorAll(cssPath); for (let i = 0; i < aA.length; i++) { cartSku += "," + aA[i].textContent.trim() }; cartSku = cartSku.substring(1, cartSku.length); cartSku = cartSku.match(y).join("") return cartSku }; mapCartSku("Enter cart product skus cssPath")

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
cssPath | one css path | single css path(s) to an html elements on cart page, containing some sku vlaue i.e. a <code>```<tr class="product_id">```</code> element.
