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

mapCategory("Enter CSS selector here")

//example
mapCategory("#crumb > span > a");

"Home, Mens, Shoes, Running, Addidas"

```

The mapCategory function expects a CSS selector ( most commonly a breadcrumb ),
and returns a comma separated string.


### Parameters

Parameter | Default | Description
--------- | ------- | -----------
CSS Selector | minimum of one selector | returns a comma separated string.


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

mapMobileDesktopCategory("Enter mobile term from url","Enter mobile CSS selector","Enter desktop CSS selector")

//example
mapMobileDesktopCategory("/mobile/","mobile > css > path", "desktop > css > path");

"Home, Mens, Shoes, Running, Addidas, Desktop"

//or

"Home, Mens, Shoes, Running, Addidas, Mobile"

```

The mapMobileDesktopCategory function should be used when a site has both a desktop URL and mobile URL.

The mapMobileDesktopCategory will return a comma separated category string appended with either ",MOBILE" or ",DESKTOP".

### Parameters - should be entered in order 

Parameter | Default | Description
--------- | ------- | -----------
mobileUrlTerm | null | url identifier to identify the mobile site.
mobilePath | null | css selector path from the mobile site
desktopPath | null | css selector path from the desktop site

