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

> copy the code block below to use in pixel dashboard

```javascript
mapCartQuantityFromIcon = (arrayOfSelectors) => {let quant=null; let aA=arrayOfSelectors; for(let i = 0; i < aA.length; i++){if(document.querySelector(aA[i])){quant=document.querySelector(aA[i]).textContent.trim();}}return quant};mapCartQuantityFromIcon(["Enter comma separated","CSS selectors here"])
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | single or multiple css path(s) to an html element containing some text i.e. a <code>```<span class="cart-icon">```</code> element.


## mapCartQuantityFromCartPage()


```javascript

mapCartQuantityFromCartPage = (cssPath, elementType) => {
  let quant = 0;
    let aA = document.querySelectorAll(cssPath);
  for (let i = 0; i < aA.length; i++) {
      if(elementType=="input"){
		quant+=parseInt(aA[i].value)
	  }else{
		quant += parseInt(aA[i].textContent)
	  }      
  };
 
  return quant
};

mapCartQuantityFromCartPage("Enter css path","Enter element type")

//example
mapCartQuantityFromCartPage("div > span > input","input")

shcq: "2"

```

The mapCartQuantityFromCartPage function expects a CSS path,
and a type reference of the element holding the quantity value. 
The mapCartQuantityFromCartPage function returns a single cart quantity string value.

> copy the code block below to use in pixel dashboard

```javascript
mapCartQuantityFromCartPage = (cssPath, elementType) => { let quant = 0; let aA = document.querySelectorAll(cssPath); for (let i = 0; i < aA.length; i++) { if(elementType=="input"){ quant+=parseInt(aA[i].value) }else{ quant += parseInt(aA[i].textContent) } }; return quant }; mapCartQuantityFromCartPage("div > span > input","input")
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
cssPath | one CSS path | single css path(s) to an html element containing some cart quantity value i.e. an <code>```<input value="4">```</code> element.
elementType | none | the type of element holding the value. i.e. "input"
