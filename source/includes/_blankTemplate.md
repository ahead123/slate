# Template 
- mapping name - i.e. Category

## function name -  i.e - mapCategory()

```javascript
// Put your Javascript code between the 3 tick marks and reference the language 
// - i.e. javascript


// Function Invoking Example - 
Provide an example of how the function would look invoked with selectors.

i.e - mapCategory("#crumb > span > a");

// Provide an example of how the mapping should look in the pixel - 
i.e - shpc: "Home, Mens, Shoes, Running, Addidas"

```
***** Please provide a detailed explanation about the mapping and what "type" it takes to function.

i.e - The mapCategory function expects a CSS selector ( most commonly a breadcrumb ),
and returns a comma separated string.

> Creates a bold block for reference 
- i.e - Copy the code block below to use in pixel dashboard

```javascript
"Place the unspaced version of your code here" - 
i.e - 
mapCategory = (cssPath) => { let cat=""; let aA=document.querySelectorAll(cssPath); for(let i = 0; i < aA.length; i++){ cat+=","+aA[i].textContent.trim(); }; cat=cat.substring(1, cat.length); return cat }; mapCategory("Enter CSS selector here");
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
cssPath |Exactly one CSS selector in string format | A css path to an html element containing text i.e. (a category breadcrumb element)