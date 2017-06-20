# Product Sku

## mapProductSku()

```javascript

mapProductSku = (arrayOfSelectors) => {
  let sku = null;
  let aA = arrayOfSelectors;
  let r = /[a-zA-Z0-9]+/g;
  for (let i = 0; i < aA.length; i++) {
    if (document.querySelector(aA[i])) {
        sku = document.querySelector(aA[i]).textContent.match(r).join("").trim();
    }
  }
  return sku
};

mapProductSku(["Enter comma separated css selectors here"])

//example
mapProductSku(["span.product_id"])

shps: "1345YLU67TR5"

```

The mapProductSku function expects an array of comma separated CSS selectors,
and returns a single sku value string.

The SteelHouse(SH) tracking pixel also fires a SH Facebook(FB) pixel and a common issue that occurs is special characters in the sku mapping are not properly escaped which cause syntax errors to fire in the SH FB pixel.

The mapProductSku function will remove all special characters and whitespace preventing this error from triggering in the SH FB pixel.

> copy the code block below to use in pixel dashboard

```javascript
mapProductSku = (arrayOfSelectors) => { let sku = null; let aA = arrayOfSelectors; let r = /[a-zA-Z0-9]+/g; for (let i = 0; i < aA.length; i++) { if (document.querySelector(aA[i])) { sku = document.querySelector(aA[i]).textContent.match(r).join("").trim(); } } return sku }; mapProductSku(["Enter comma separated css selectors here"])
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | a single or multiple css path(s) to an html element containing some sku vlaue i.e. a <code>```<span class="product_id">```</code> element.

## mapMobileDesktopProductSku()

```javascript

mapMobileDesktopProductSku = (mobileUrlTerm = null, mobilePath = null, desktopPath = null) => {
	let prod_sku = "";
	let aA = null;
	let isMobile = false;
	let url = window.location.href;
	let r = /[A-Za-z0-9]+/g;
    let checkVersion = false;
    if (mobileUrlTerm) {
        checkVersion = true
    }
    if (mobileUrlTerm && url.indexOf(mobileUrlTerm) > -1) {
        isMobile = true;
        aA = document.querySelectorAll(mobilePath)
    } else {
        aA = document.querySelectorAll(desktopPath)
    }
    for (let i = 0; i < aA.length; i++) {
        prod_sku += aA[i].textContent.trim();
    }
    if (isMobile) {
        prod_sku = prod_sku.toLowerCase() + "MOBILE"
    } else if (checkVersion && !isMobile) {
        prod_sku = prod_sku.toLowerCase() + "DESKTOP"
    } else {
        prod_sku = prod_sku
    }
    return prod_sku.match(r).join("").trim();
};
mapMobileDesktopProductSku("m.swimoutlet", "div.prod-header-product > h1", "div.pro-viewinfo > h1");

//example
mapMobileDesktopProductSku("m.swimoutlet", "div.prod-header-product > h1", "div.pro-viewinfo > h1");

Desktop shps: "1345YLU67TR5DESKTOP"
Mobile shps:  "16HGY67TR57TMOBILE"
```

The mapMobileDesktopProductSku function 3 different values: a mobile url (m.sitename.com), a mobile CSS path and a desktop CSS path.

The SteelHouse(SH) tracking pixel also fires a SH Facebook(FB) pixel and a common issue that occurs is special characters in the sku mapping are not properly escaped which cause syntax errors to fire in the SH FB pixel. This is why we use regex. "let r = /[A-Za-z0-9]+/g;"

The mapMobileDesktopProductSku function will remove all special characters and whitespace preventing this error from triggering in the SH FB pixel.

> copy the code block below to use in pixel dashboard

```javascript
mapMobileDesktopProductSku = (mobileUrlTerm = null, mobilePath = null, desktopPath = null) => { let prod_sku = ""; let aA = null; let isMobile = false; let url = window.location.href; let r = /[A-Za-z0-9]+/g; let checkVersion = false; if (mobileUrlTerm) { checkVersion = true } if (mobileUrlTerm && url.indexOf(mobileUrlTerm) > -1) { isMobile = true; aA = document.querySelectorAll(mobilePath) } else { aA = document.querySelectorAll(desktopPath) } for (let i = 0; i < aA.length; i++) { prod_sku += aA[i].textContent.trim(); } if (isMobile) { prod_sku = prod_sku.toLowerCase() + "MOBILE" } else if (checkVersion && !isMobile) { prod_sku = prod_sku.toLowerCase() + "DESKTOP" } else { prod_sku = prod_sku } return prod_sku.match(r).join("").trim(); }; mapMobileDesktopProductSku("m.swimoutlet", "div.prod-header-product > h1", "div.pro-viewinfo > h1");
```

### Parameters

Parameter  | Default | Description
---------  | ------- | -----------
Mobile Url | null    | Enter the mobile url in the first parameter. - i.e So for "m.mywebsite.com", you would enter - "m.mywebsite".
Mobile Selector  | null | One mobile html element containing some sku vlaue i.e. a <code>```<span class="product_sku">```</code> element.
Desktop Selector | null | One desktop html element containing some sku vlaue i.e. a <code>```<span class="product_sku">```</code> element.