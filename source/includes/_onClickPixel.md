# OnClick Pixel

## triggerPixelOnClick()


```javascript

triggerPixelOnClick = (elementID = null, cssPath = null, AID) => {

    let inputID = null, inputClass = null, inputAID = AID;

    elementID != null ? inputID = document.getElementById(elementID) : "";
    cssPath != null ? inputClass = document.querySelector(cssPath) : "";

    sh_pixel = (aid) => {
        (function() {
            "use strict";
            window.flag = 1;
            var e = null,
                b = "4.0.0",
                n = aid,
                additional = "",
                t, r, i;
            try {
                t = top.document.referer !== "" ? encodeURIComponent(top.document.referrer.substring(0, 2048)) : ""
            } catch (o) {
                t = document.referrer !== null ? document.referrer.toString().substring(0, 2048) : ""
            }
            try {
                r = window && window.top && document.location && window.top.location === document.location ? document.location : window && window.top && window.top.location && "" !== window.top.location ? window.top.location : document.location
            } catch (u) {
                r = document.location
            }
            try {
                i = parent.location.href !== "" ? encodeURIComponent(parent.location.href.toString().substring(0, 2048)) : ""
            } catch (a) {
                try {
                    i = r !== null ? encodeURIComponent(r.toString().substring(0, 2048)) : ""
                } catch (f) {
                    i = ""
                }
            }
            var l, c = document.createElement("script"),
                h = null,
                p = document.getElementsByTagName("script"),
                d = Number(p.length) - 1,
                v = document.getElementsByTagName("script")[d];
            if (typeof l === "undefined") {
                l = Math.floor(Math.random() * 1e17)
            }
            h = "dx.steelhousemedia.com/spx?" + "dxver=" + b + "&shaid=" + n + "&tdr=" + t + "&plh=" + i + "&cb=" + l + additional;
            c.type = "text/javascript";
            c.src = ("https:" === document.location.protocol ? "https://" : "http://") + h;
            v.parentNode.insertBefore(c, v)
        })();
    };

    createListener = (element) => {
        element.addEventListener("click", () => {
            if (!window.flag) {
                sh_pixel(inputAID)
            }
        })
    };

    inputID == null ? createListener(inputClass) : createListener(inputID);

};

triggerPixelOnClick("Enter an ID","Enter a CSS path","Enter AID")

//example
triggerPixelOnClick("#download-button","div > span > a.download-now-button","10392")

```

The triggerPixelOnClick function expects a single AID as a string, a DOM element ID, and a DOM CSS path. The triggerPixelOnClick function creates a click listener event on an element in the DOM. Upon the element being clicked, the pixel with the input AID will be re-triggered in the DOM.
This comes in handy when it's necessary to re-triggering the pixel on an ajax shopping cart, or on a sign up form.

> copy the code block below to use in pixel dashboard

```javascript
triggerPixelOnClick = (elementID = null, cssPath = null, AID) => { let inputID = null, inputClass = null, inputAID = AID; elementID != null ? inputID = document.getElementById(elementID) : ""; cssPath != null ? inputClass = document.querySelector(cssPath) : ""; sh_pixel = (aid) => { (function() { "use strict"; window.flag = 1; var e = null, b = "4.0.0", n = aid, additional = "", t, r, i; try { t = top.document.referer !== "" ? encodeURIComponent(top.document.referrer.substring(0, 2048)) : "" } catch (o) { t = document.referrer !== null ? document.referrer.toString().substring(0, 2048) : "" } try { r = window && window.top && document.location && window.top.location === document.location ? document.location : window && window.top && window.top.location && "" !== window.top.location ? window.top.location : document.location } catch (u) { r = document.location } try { i = parent.location.href !== "" ? encodeURIComponent(parent.location.href.toString().substring(0, 2048)) : "" } catch (a) { try { i = r !== null ? encodeURIComponent(r.toString().substring(0, 2048)) : "" } catch (f) { i = "" } } var l, c = document.createElement("script"), h = null, p = document.getElementsByTagName("script"), d = Number(p.length) - 1, v = document.getElementsByTagName("script")[d]; if (typeof l === "undefined") { l = Math.floor(Math.random() * 1e17) } h = "dx.steelhousemedia.com/spx?" + "dxver=" + b + "&shaid=" + n + "&tdr=" + t + "&plh=" + i + "&cb=" + l + additional; c.type = "text/javascript"; c.src = ("https:" === document.location.protocol ? "https://" : "http://") + h; v.parentNode.insertBefore(c, v) })(); }; createListener = (element) => { element.addEventListener("click", () => { if (!window.flag) { sh_pixel(inputAID) } }) }; inputID == null ? createListener(inputClass) : createListener(inputID); };triggerPixelOnClick("Enter an ID","Enter a CSS path","Enter AID")
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
AID | empty string | a single AID entered as a string. i.e. "10392"
elementID | empty string | a single css ID to an html element 
cssPath | empty string | a single css path to an html element entered as a string

