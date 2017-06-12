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

> copy this code block to use in pixel dashboard

> mapImage = (arrayOfSelectors) => { let image = null; let aA = arrayOfSelectors; for (let i = 0; i < aA.length; i++) { if (document.querySelector(aA[i])) { image = document.querySelector(aA[i]).src; } } return image }; mapImage(["Enter CSS Selectors"])

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
mapImage()

shpi: "https://goo.gl/HrwVyt"

```

The mapImageFromMeta function defaults to checking the meta tags in the html head.
The mapImageFromMeta function checks to ensure the page is a product page, and then
pulls image from the meta tag with the value "og:image".

> copy this code block to use in pixel dashboard

> mapImageFromMeta = () => { let image = null; let isProductPage = false; let aA = document.querySelectorAll("meta"); for (let i = 0; i < aA.length; i++) { if (aA[i].getAttribute("property")) { if (aA[i].getAttribute("property") == "og:type" && aA[i].getAttribute("content") == "product") { isProductPage = true; } } } if (isProductPage) { for (let x = 0; x < aA.length; x++) { if (aA[x].getAttribute("property")) { if (aA[x].getAttribute("property") == "og:image") { image = aA[x].getAttribute("content"); break; } } } } return image }; mapImageFromMeta()

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
none | meta | defaulted to use the meta tag with og:image i.e. <code>```<meta property="og:image" content="imageUrl" />```</code> element.
