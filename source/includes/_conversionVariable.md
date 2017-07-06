# Conversion Variable Search

## findConversionVariable()


```javascript

findConversionVariable = (variableToCheckFor) => {
  let aA = document.querySelectorAll("script"),
      check = null,
      valueToReturn = null;
  for (let i = 0; i < aA.length; i++) {
      if (aA[i].getAttribute("src")) {
          if (aA[i].getAttribute("src").indexOf("dx.steelhousemedia.com/spx?conv=1") > -1) {
              check = aA[i].getAttribute("src");
              break;
          }
      }
  }
  if (check) {
      valueToReturn = check.split(variableToCheckFor + "=")[1].split("&")[0]
  }
  return valueToReturn
}

findConversionVariable("Enter conversion variable here")

//example
findConversionVariable("shopid")

"PRODUCT IDs"

```

The findConversionVariable function expects a string identifier of a variable in the SteelHouse converison pixel.
The findConversionVariable will return the value of the variable in the SteelHouse conversion pixel.

> copy the code block below to use in pixel dashboard

```javascript
findConversionVariable = (variableToCheckFor) => { let aA = document.querySelectorAll("script"), check = null, valueToReturn = null; for(let i = 0; i < aA.length; i++){ if(aA[i].getAttribute("src")){ if(aA[i].getAttribute("src").indexOf("dx.steelhousemedia.com/spx?conv=1")>-1){ check = aA[i].getAttribute("src"); break; } } } if(check){ valueToReturn=check.split(variableToCheckFor+"=")[1].split("&")[0] }; return valueToReturn };findConversionVariable("shopid")
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
variableToCheckFor | minimum of 1 variable to check for | a single variable found in the conversion pixel, such as "shoamt", "shopid", or "shoid", etc...
