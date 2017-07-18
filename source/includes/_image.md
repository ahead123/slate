# Image

## mapImage()


```javascript

mapImage = (arrayOfSelectors) => {
  let image = null;
  let aA = arrayOfSelectors;
  for (let i = 0; i < aA.length; i++) {
      if (document.querySelector(aA[i])) {
          image = document.querySelector(aA[i]).src;
      }
  }
  return image
};

mapImage(["Enter comma separated css selectors here"])

//example
mapImage(["#productImage","#main > div.main-image"])

shpi: "https://goo.gl/HrwVyt"

```

The mapImage function expects an array of comma separated CSS selectors,
and returns a single image URL string.

> copy the code block below to use in pixel dashboard

```javascript
mapImage = (arrayOfSelectors) => { let image = null; let aA = arrayOfSelectors; for (let i = 0; i < aA.length; i++) { if (document.querySelector(aA[i])) { image = document.querySelector(aA[i]).src; } } return image }; mapImage(["Enter CSS Selectors"])
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
arrayOfSelectors | minimum of one CSS selector inside an array | single or multiple css path(s) to an html element containing an image source i.e. an <code>```<img id="productImage" src="imageUrl" />```</code> element.


## mapImageFromMeta()


```javascript

mapImageFromMeta = () => {
  let image = null;
  let isProductPage = false;
  let aA = document.querySelectorAll("meta");
  for (let i = 0; i < aA.length; i++) {
      if (aA[i].getAttribute("property")) {
          if (aA[i].getAttribute("property") == "og:type" && aA[i].getAttribute("content") == "product") {
              isProductPage = true;
          }
      }
  }
  if (isProductPage) {
      for (let x = 0; x < aA.length; x++) {
          if (aA[x].getAttribute("property")) {
              if (aA[x].getAttribute("property") == "og:image") {
                  image = aA[x].getAttribute("content");
                  break;
              }
          }
      }
  }
  return image
};

mapImageFromMeta()

//example
mapImageFromMeta()

shpi: "https://goo.gl/HrwVyt"

```

The mapImageFromMeta function defaults to checking the meta tags in the html head.
The mapImageFromMeta function checks to ensure the page is a product page, and then
pulls image from the meta tag with the value "og:image".

> copy the code block below to use in pixel dashboard

```javascript
mapImageFromMeta = () => { let image = null; let isProductPage = false; let aA = document.querySelectorAll("meta"); for (let i = 0; i < aA.length; i++) { if (aA[i].getAttribute("property")) { if (aA[i].getAttribute("property") == "og:type" && aA[i].getAttribute("content") == "product") { isProductPage = true; } } } if (isProductPage) { for (let x = 0; x < aA.length; x++) { if (aA[x].getAttribute("property")) { if (aA[x].getAttribute("property") == "og:image") { image = aA[x].getAttribute("content"); break; } } } } return image }; mapImageFromMeta()
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
none | meta | defaulted to use the meta tag with og:image i.e. <code>```<meta property="og:image" content="imageUrl" />```</code> element.

## mapImageByCurrency

```javascript
Put your Javascript code between the 3 tick marks and reference which language you are using.

mapImageByCurrency = (imageSelector = null, priceSelector = null, currencySymbol = null) => {
    let imageSrc = document.querySelector(imageSelector);
    let priceMapping = document.querySelector(priceSelector);
    let currency = currencySymbol, image = null,price;
    if(imageSrc != null && priceSelector != null && currency != null) {
        price = priceMapping.textContent.trim();
        if(price.indexOf(currency)>-1){
            image = imageSrc.src;
        };
    }
    return image;
};
mapImageByCurrency("imageSelector","priceSelector","currencySymbol");

// Function Invoking Example - 
Provide an example of how the function would look invoked with selectors.

i.e - mapCategory("#crumb > span > a");

// Provide an example of how the mapping should look in the pixel - 
i.e - shpi: "http://lsco.scene7.com/is/image/lsco/Levi/clothing/005054886-front-pdp.jpg?$2500x2000$&id=RvLrs0&fmt=jpg&fit=constrain,1&wid=813&hei=650"

```
***** Please provide a detailed explanation about the mapping and what "type" it takes to function.

i.e - The mapImageByCurrency function expects 2 CSS selectors. The first selector has to be an "imageSelector", the second selector has to be a "priceSelector" and the third has to be a "currencySymbol" THIS IS NOT A SELECTOR. You enter the desired currency you want shown on the site.
This mapping takes in 3 arguments and compares the currency symbol you have specified with the currency symbol that is in the price mapping. If they both match, the image mapping is returned. If not the image mapping is null and will not be pulled in.

> Creates a bold block for reference - i.e - Copy the code block below to use in pixel dashboard

```javascript
"Place the unspaced version of your code here" - 
i.e - 
mapImageByCurrency = (imageSelector = null, priceSelector = null, currencySymbol = null) => { let imageSrc = document.querySelector(imageSelector); let priceMapping = document.querySelector(priceSelector); let currency = currencySymbol, image = null,price; if(imageSrc != null && priceSelector != null && currency != null) { price = priceMapping.textContent.trim(); if(price.indexOf(currency)>-1){ image = imageSrc.src; }; } return image; }; mapImageByCurrency("imageSelector","priceSelector","currencySymbol");
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
imageSelector   | Only one CSS selector in string format | A css path to an html element containing text i.e. (name element)
priceSelector   | Only one CSS selector in string format | A css path to an html element containing text i.e. (name element)
currencySymbol   | Manually enter desired currency symbol | You have to manually enter the desired currency symbol in string format i.e. ("$")
