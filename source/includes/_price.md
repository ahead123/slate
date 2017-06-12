# Price

## mapPrice()


```javascript

mapPrice = (arrayOfSelectors) => {
  let price=null; 
  let aA=arrayOfSelectors; 
  for(let i = 0; i < aA.length; i++){
    if(document.querySelector(aA[i])){
      price=document.querySelector(aA[i]).textContent.trim();
      price=/[0-9,.]+/.exec(price)[0];
      price=price.replace(/[,]/g,"") 
      break;
    }
  }
  return price
};

mapPrice(["Enter comma separated css selectors here"])

//example
mapPrice(["#priceCopy","#priceArea > p.price"])

shpp: "15.00"

```

The mapPrice function expects an array of comma separated CSS selectors,
and returns a single price string without any commas or currency symbols.

> copy this code block to use in pixel dashboard

> mapPrice = (arrayOfSelectors) => { let price=null; let aA=arrayOfSelectors; for(let i = 0; i < aA.length; i++){ if(document.querySelector(aA[i])){ price=document.querySelector(aA[i]).textContent.trim(); price=/[0-9,.]+/.exec(price)[0]; break; } } return price }; mapPrice(["Enter comma separated css selectors here"])


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | a single or multiple css path(s) to an html element containing some text i.e. a <code>```<p class="price">```</code> element.


## mapLowestPriceFromMany()


```javascript

mapLowestPriceFromMany = (cssPath) => {
  let price = null;
  let aA = document.querySelectorAll(cssPath);
  for (let i = 0; i < aA.length; i++) {
      let cprice = aA[i].textContent.replace("$", "").trim();
      if (price === null) {
          price = cprice;
      } else if (parseFloat(price) > parseFloat(cprice)) {
          price = cprice;
      }
  };
  return price
};

mapLowestPriceFromMany("Enter CSS path")

//example
mapLowestPriceFromMany("#product-price > p > span.price")

shpp: "115.00"

```

The mapLowestPriceFromMany function expects a CSS path,
and runs a comparison algorithm to check for the lowest price among many prices. 

The mapLowestPriceFromMany function will return the lowest price as a string without
any currency symbols or commas.

> copy this code block to use in pixel dashboard

> mapLowestPriceFromMany = (cssPath) => { let price = null; let aA = document.querySelectorAll(cssPath); for (let i = 0; i < aA.length; i++) {let cprice = aA[i].textContent.replace("$", "").trim();if (price === null) { price = cprice; } else if (parseFloat(price) > parseFloat(cprice)) { price = cprice; } }; return price }; mapLowestPriceFromMany("Enter cssPath")


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
cssPath | minimum of one CSS path | a single path to an html element containing some numeric price values i.e. <code>```<span class="price">```</code> elements.
