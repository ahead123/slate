# Cart Quantity

## mapCartQuantityFromIcon()


```javascript

mapCartQuantityFromIcon = (arrayOfSelectors) => {
  let quant = null;
  let aA = arrayOfSelectors;
  for (let i = 0; i < aA.length; i++) {
    if (document.querySelector(aA[i])) {
        quant = document.querySelector(aA[i]).textContent.trim();
    }
  }
  return quant
};

mapCartQuantityFromIcon(["Enter comma separated css selectors here"])

//example
mapCartQuantityFromIcon(["#minibaskettext","#span.cart-icon"])

shcq: "4"

```

The mapCartQuantityFromIcon function expects an array of comma separated CSS selectors,
and returns a single cart quantity string without any special characters.

> copy this code block to use in pixel dashboard

> mapCartQuantityFromIcon = (arrayOfSelectors) => {let quant=null; let aA=arrayOfSelectors; for(let i = 0; i < aA.length; i++){if(document.querySelector(aA[i])){quant=document.querySelector(aA[i]).textContent.trim();}}return quant};mapCartQuantityFromIcon(["Enter comma separated","CSS selectors here"])


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | single or multiple css path(s) to an html element containing some text i.e. a <code>```<span class="cart-icon">```</code> element.
