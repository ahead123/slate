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
mapName(["h1#product-name"])

"Blue Suede Shoes"

```

The mapName function expects an array of comma separated CSS selectors,
and returns a single name string.

> copy this code block to use in pixel dashboard

> mapName = (arrayOfSelectors) => { let name = null; let aA=arrayOfSelectors; for(let i = 0; i < aA.length; i++){ if(document.querySelector(aA[i])){ name=document.querySelector(aA[i]).textContent.trim();} } return name }; mapName(["Enter comma separated css selectors here"])

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | a single or multiple css path(s) to an html element containing some text i.e. an <code>```<h1 id="product-name">```</code> element.
