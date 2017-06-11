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
mapPrice(["#priceCopy","#priceArea > span:nth-child(2)"])

"15.00"

```

The mapPrice function expects an array of comma separated CSS selectors,
and returns a single price string without any commas or currency symbols.


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one selector | returns single price string.
