---
title: API Reference

language_tabs:
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the SteelHouse Pixel Mapping Framework.

Our mappings are all written in, the popular JavaScript language! You can view code examples in the dark area to the right!


# Name

## mapName()


```javascript

mapName = (arrayOfSelectors) => { 
  let name = null; let aA=arrayOfSelectors; 
  for(let i = 0; i < aA.length; i++){
    if(document.querySelector(aA[i])){
      name=document.querySelector(aA[i]).textContent.trim();}
    }
  return name
};

mapName(["Enter comma separated css selectors here"])

//example
mapName(["h1"])

"Blue Suede Shoes"

```

The mapName function expects an array of comma separated CSS selectors,
and returns a single name string.


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one selector | returns single name string.

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
