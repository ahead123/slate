# Phantom Pixel

## firePhantom()


```javascript

firePhantom = (AID) => {
  sh_pixel = (AID) => {
      (function() {
          "use strict";
          window.flag = 1;
          var e = null,
              b = "4.0.0",
              n = AID,
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
      })()
  };

 function hashHandler(AID) {
      this.oldHash = window.location.href;
      this.Check;
      var that = this;
      var detect = function() {
          if (that.oldHash != window.location.href) {
              window.newFlag = 1;
              sh_pixel(AID);
              that.oldHash = window.location.href;
          }
      };
      this.Check = setInterval(detect, 100);
  };
  if (!window.flag) {
      var hashDetection = new hashHandler(AID);
  };
}

firePhantom("Enter AID")

//example
firePhantom("10392")

```

The firePhantom function expects a single AID as a string. The firePhantom function creates a listener event that runs every 200ms and checks for URL changes.
On single page application sites, if the URL has changed, the firePhantom function will trigger another pixel fire with the same AID.

> copy the code block below to use in pixel dashboard

```javascript
firePhantom = (AID) => { sh_pixel = (AID) => { (function() { "use strict"; window.flag = 1; var e = null, b = "4.0.0", n = AID, additional = "", t, r, i; try { t = top.document.referer !== "" ? encodeURIComponent(top.document.referrer.substring(0, 2048)) : "" } catch (o) { t = document.referrer !== null ? document.referrer.toString().substring(0, 2048) : "" } try { r = window && window.top && document.location && window.top.location === document.location ? document.location : window && window.top && window.top.location && "" !== window.top.location ? window.top.location : document.location } catch (u) { r = document.location } try { i = parent.location.href !== "" ? encodeURIComponent(parent.location.href.toString().substring(0, 2048)) : "" } catch (a) { try { i = r !== null ? encodeURIComponent(r.toString().substring(0, 2048)) : "" } catch (f) { i = "" } } var l, c = document.createElement("script"), h = null, p = document.getElementsByTagName("script"), d = Number(p.length) - 1, v = document.getElementsByTagName("script")[d]; if (typeof l === "undefined") { l = Math.floor(Math.random() * 1e17) } h = "dx.steelhousemedia.com/spx?" + "dxver=" + b + "&shaid=" + n + "&tdr=" + t + "&plh=" + i + "&cb=" + l + additional; c.type = "text/javascript"; c.src = ("https:" === document.location.protocol ? "https://" : "http://") + h; v.parentNode.insertBefore(c, v) })() }; function hashHandler() { this.oldHash = window.location.href; this.Check; var that = this; var detect = function() { if (that.oldHash != window.location.href) { window.newFlag = 1; sh_pixel(); that.oldHash = window.location.href; } }; this.Check = setInterval(detect, 100); }; if (!window.flag) { var hashDetection = new hashHandler(); }; }; firePhantom("10392")
```

### Parameters

Parameter | Default | Description
--------- | ------- | -----------
AID | empty string | a single AID entered as a string. i.e. "10392"
