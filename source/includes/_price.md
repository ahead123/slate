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
      break;
    }
  }
  return price
};

mapPrice(["Enter comma separated css selectors here"])

//example
mapPrice(["#priceCopy","#priceArea > p.price"])

"15.00"

```

The mapPrice function expects an array of comma separated CSS selectors,
and returns a single price string without any commas or currency symbols.


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | a single or multiple css path(s) to an html element containing some text i.e. a <code>```<p class="price">```</code> element.
