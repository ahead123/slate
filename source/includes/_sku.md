# Sku

## mapSku()


```javascript

mapSku = (arrayOfSelectors) => {
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

mapSku(["Enter comma separated css selectors here"])

//example
mapSku(["span.product_id"])

"1345YLU67TR5"

```

The mapSku function expects an array of comma separated CSS selectors,
and returns a single sku value string.

The SteelHouse(SH) tracking pixel also fires a SH Facebook(FB) pixel and a common issue that occurs is special characters in the sku mapping are not properly escaped which cause syntax errors to fire in the SH FB pixel.

The mapSku funciton will remove all special characters and whitespace preventing this error from triggering in the SH FB pixel.

> copy this code block to use in pixel dashboard

> mapSku = (arrayOfSelectors) => { let sku = null; let aA = arrayOfSelectors; let r = /[a-zA-Z0-9]+/g; for (let i = 0; i < aA.length; i++) { if (document.querySelector(aA[i])) { sku = document.querySelector(aA[i]).textContent.match(r).join("").trim(); } } return sku }; mapSku(["Enter comma separated css selectors here"])

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | a single or multiple css path(s) to an html element containing some sku vlaue i.e. a <code>```<span class="product_id">```</code> element.
