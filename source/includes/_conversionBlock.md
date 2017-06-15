# Conversion Duplicate Block

## findDuplicateConversions()


```javascript
findDuplicateConversions = (AID) => {
  let block = null, check = false, aA = document.querySelectorAll("script");
  for (let i = 0; i < aA.length; i++) {
      if (aA[i].getAttribute("src")) {
          if (aA[i].getAttribute("src").indexOf("st?fdx=1&conv=1&shaid=" + AID) > -1) {
              check = true;
              break;
          }
      }
  };
  if (check) {
      block = "sh_conversion=SHBLOCK"
  };
  return block
};
findDuplicateConversions("ENTER AID HERE");


//example
findDuplicateConversions("10392")

shadditional: "sh_conversion=SHBLOCK"

```

The findDuplicateConversions function expects and AID, and searches through the DOM for the SteelHouse conversion pixel containing the same AID. It will not block itself, however if it finds a duplicate instance of itself than one of the conversions will be blocked, so that only one conversion registers.

> copy the code block below to use in pixel dashboard

```javascript
findDuplicateConversions = (AID) => { let block = null, check = false, aA = document.querySelectorAll("script"); for (let i = 0; i < aA.length; i++) { if (aA[i].getAttribute("src")) { if (aA[i].getAttribute("src").indexOf("st?fdx=1&conv=1&shaid=" + AID) > -1) { check = true; break; } } }; if (check) { block = "sh_conversion=SHBLOCK" }; return block }; findDuplicateConversions("ENTER AID HERE");
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
AID | minimum of one AID | a single AID entered as a string value
