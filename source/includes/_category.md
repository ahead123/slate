# Category

## mapCategory()


```javascript

mapCategory = (cssPath) => {
  let cat=""; 
  let aA=document.querySelectorAll(cssPath); 
  for(let i = 0; i < aA.length; i++){ 
    cat+=","+aA[i].textContent.trim(); 
  };
  cat=cat.substring(1, cat.length); 
  return cat
};

mapCategory("Enter CSS selector here").

//example
mapCategory("#crumb > span > a");

shpc: "Home, Mens, Shoes, Running, Addidas"

```

The mapCategory function expects a CSS selector ( most commonly a breadcrumb ),
and returns a comma separated string.

> copy this code block to use in pixel dashboard

> mapCategory = (cssPath) => { let cat=""; let aA=document.querySelectorAll(cssPath); for(let i = 0; i < aA.length; i++){ cat+=","+aA[i].textContent.trim(); }; cat=cat.substring(1, cat.length); return cat }; mapCategory("Enter CSS selector here")

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
cssPath | exactly one CSS selector in string format | a css path to an html element containing text i.e. a category breadcrumb element


## mapMobileDesktopCategory()

```javascript

mapMobileDesktopCategory = (mobileUrlTerm=null, mobilePath=null, desktopPath=null) => {
     
    let cat = "", aA = null, isMobile = false, url = window.location.href, checkVersion=false;
    if(mobileUrlTerm){checkVersion=true}
    if(mobileUrlTerm && url.indexOf(mobileUrlTerm)>-1){
      isMobile = true;
        aA=document.querySelectorAll(mobilePath)
    }else{
    aA=document.querySelectorAll(desktopPath)
    }

    for (let i = 0; i < aA.length; i++) {
        cat += "," + aA[i].textContent.trim();
    }
    cat = cat.substring(1, cat.length);
    if (isMobile) {
        cat = cat + ",MOBILE"
    } else if(checkVersion && !isMobile){
        cat = cat + ",DESKTOP"
    } else {
    cat = cat
    }
    return cat
}

mapMobileDesktopCategory("mobile url term","mobile CSS path","desktop CSS path")

//example
mapMobileDesktopCategory("/mobile/","mobile > css > path", "desktop > css > path");

shpc: "Home, Mens, Shoes, Running, Addidas, Desktop"

//or

shpc: "Home, Mens, Shoes, Running, Addidas, Mobile"

```

The mapMobileDesktopCategory function should be used when a site has both a desktop URL and mobile URL.

The mapMobileDesktopCategory will return a comma separated category string appended with either ",MOBILE" or ",DESKTOP".

> copy this code block to use in pixel dashboard

```javascript
mapMobileDesktopCategory = (mobileUrlTerm=null, mobilePath=null, desktopPath=null) => { let cat = "", aA = null, isMobile = false, url = window.location.href, checkVersion=false; if(mobileUrlTerm){checkVersion=true} if(mobileUrlTerm && url.indexOf(mobileUrlTerm)>-1){ isMobile = true; aA=document.querySelectorAll(mobilePath) }else{ aA=document.querySelectorAll(desktopPath) } for (let i = 0; i < aA.length; i++) { cat += "," + aA[i].textContent.trim(); } cat = cat.substring(1, cat.length); if (isMobile) { cat = cat + ",MOBILE" } else if(checkVersion && !isMobile){ cat = cat + ",DESKTOP" } else { cat = cat } return cat }; mapMobileDesktopCategory("Enter mobile term from url","Enter mobile CSS selector","Enter desktop CSS selector")
```

### Parameters - should be entered in order 

Parameter | Default | Description
--------- | ------- | -----------
mobileUrlTerm | null | url identifier to identify the mobile site - i.e. "/mobile/"
mobilePath | null | css selector path from the mobile site
desktopPath | required - desktop css path | css selector path from the desktop site

