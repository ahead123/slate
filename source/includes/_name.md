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
