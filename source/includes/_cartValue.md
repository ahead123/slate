# Cart Value

## mapCartValue()


```javascript

mapCartValue = (arrayOfSelectors = [], currencySymbol = "$") => {
  let cartVal = null;
  let aA = arrayOfSelectors;
  for (let i = 0; i < aA.length; i++) {
      if (document.querySelector(aA[i])) {
          cartVal = document.querySelector(aA[i]).textContent.trim();
          cartVal = cartVal.indexOf(currencySymbol) > -1 ? /[0-9,.]+/.exec(cartVal)[0] : null;
      }
  }
  return cartVal
};

mapCartValue(["Enter comma separated css selectors here"], "Enter currency - unless USD ")

//example
mapCartValue(["div.basketrow > div.total_cell", "table.order-summary > tr.subtotal"], "$")

shcv: "445.00"

```

The mapCartValue function expects an array of comma separated CSS selectors, and a currency symbol.
The mapCartValu function returns a single value string without any commas or currency symbols.

> copy the code block below to use in pixel dashboard

```javascript
mapCartValue = (arrayOfSelectors = [], currencySymbol = "$") => { let cartVal = null; let aA = arrayOfSelectors; for (let i = 0; i < aA.length; i++) { if (document.querySelector(aA[i])) { cartVal = document.querySelector(aA[i]).textContent.trim(); cartVal = cartVal.indexOf(currencySymbol) > -1 ? /[0-9,.]+/.exec(cartVal)[0] : null; } } return cartVal };mapCartValue(["Enter comma separated css selectors here"], "Enter currency - unless USD ")
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | single or multiple css path(s) to an html element containing some text i.e. a <code>```<p class="subtotal">```</code> element.
currencySymbol | $ - USD | the currency symbol to check for to be removed
