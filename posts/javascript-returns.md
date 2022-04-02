# Javascript I Keep Returning Too
#### May 25th 2020

Nothing earth shattering, just a collection of code fragments and functions I keep re-writing and re-using...

### Base
```javascript
(function(){
  class App {
    constructor() {
      this.test = {}
      this.run()
    }
    run() {
      console.log( 'Hello' )
    }
  }
  window.addEventListener('DOMContentLoaded', () => {
    new App
  });
})();
```

### Load JS into HEAD
```javascript
function loadScript( id, src, callback ) {
  if ( !src ) {
    return;
  }
  const head  = document.getElementsByTagName( 'head' )[0];
  const script  = document.createElement( 'script' );
  if ( id ) {
    script.id = id;
  }
  if ( callback ) {
    script.onload = callback();
  };
  script.src = src;
  head.appendChild(script);
}
```

### Load CSS LINK
```javascript
loadCSS( href, callback ) {
  const cssId = href.replace(/\W/g, '').substr(-16, 16);
  if (!document.getElementById( cssId )) {
    const link = document.createElement( 'LINK' );
    link.id = cssId;
    link.rel = 'stylesheet';
    link.type = 'text/css';
    link.media = 'all';
    if (callback) {
      link.onload = callback();
    };
    link.href = href;
    document.getElementsByTagName( 'head' )[0].appendChild( link );
  }
}
```

### Viewport Width and Height
```javascript
const vw = Math.max( document.documentElement.clientWidth, window.innerWidth || 0 );
const vh = Math.max( document.documentElement.clientHeight, window.innerHeight || 0 );
```

### Insert DIV after Element
```javascript
function insertDivVAfter( targetEl, id, html ) {
  const div = document.createElement( 'DIV' );
  div.id = id;
  div.className = 'placement';
  div.innerHTML = [
    '<div class="wrapper">',
      html || '',
     '</div>'
  ].join('');
  targetEl.parentNode.insertBefore( div, targetEl.nextSibling );
}
```

### Get paramaters from URL
```javascript
  getUrlVars () {
    let vars = {};
    const p = window.location.href.replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m,k,v) {
      vars[k] = v;
    });
    return vars;
  }
```

### Simple Ajax request for Text and JSON
```javascript
function requestJSON( url, callback ) {
  const r = new XMLHttpRequest();
  r.addEventListener('load', function() {
    if (!callack) {
      return
    }
    const responseText = this.responseText || ''
    if (responseText) {
      try {
        json = JSON.parse( responseText );
        callback( json )
      } catch(e) {
        console.warn( 'Invalid JSON response', responseText );
      }
    }
  });
  r.open( 'GET', url );
  r.send();
}

function requestText( url, callback ) {
  const r = new XMLHttpRequest();
  r.addEventListener('load', function() {
    if (!callback) {
      return
    }
    callback( this.responseText || '' )
  });
  r.open( 'GET', url );
  r.send();
}
```

### Add commas to numbers for readability
```javascript
const num = 12345678.9;
const str = num.toLocaleString("en-US");
```

### Get random item from array
```javascript
const list = [ 'a', 'b', 'c', 'd', 'e' ];
const item = list[ Math.floor(Math.random() * list.length) ];
```

### Get unique values from an array / remove duplicates
```javascript
const list = [ 'a', 'b', 'c', 'd', 'e', 'a', 'c', 100, 200, 100 ];
const unique = list.filter((v, i, a) => a.indexOf(v) === i);
```

### Get random item from array (without getting length)
```javascript
[ 9731, 8486, 9730, 9733, 9760, 9832, 9874, 9988, 9996, 10006 ].sort(function() {
  return .5 - Math.random();
})[0];
```

### Return a random number within a range
```javascript
rand: function(min, max) {
  const min = min || 0;
  const max = max || 10;
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

### Shuffle an array
```javascript
shuffle: function( array ) {
  let i = array.length, t, r;
  while (0 !== i) {
    r = Math.floor( Math.random() * i );
    i -= 1;
    t = array[i];
    array[i] = array[r];
    array[r] = t;
  }
  return array
}
```

### Fastest loop with length caching
```javascript
const list = [ 'a', 'b', 'c', 'd', 'e' ];
for (var i = 0, l = list.length; i < l; i++) {
  // Things
}
```

### Replace multiple strings with multiple other strings
```javascript
var str = "t1 comes first, quickly followed by t2, but before t4 you will find t3. T2 is still T2.";

var map = {
    't1': 'test 1',
    't2': 'test 2',
    't3': 'test number 3',
    't4': 'test 4',
};

var reg = new RegExp( Object.keys(map).join('|'), 'g');
str = str.replace(reg, function(m){
    return map[m];
});

console.log(str);
// test 1 comes first, quickly followed by test 2, but before test 4 you will find test number 3. T2 is still T2.
```

### Check for slow connection on Andorid/Chrome and Opera
https://caniuse.com/#feat=netinfo

```javascript
let is2G = false;
const connection = navigator.connection || false;
if (connection && connection.effectiveType.indexOf('2g') > -1 ) {
    is2G = true;
}
```

### Placeholder index.html for new directory
```html
<html>
  <head>
    <meta name="viewport" content="width=device-width,user-scalable=no,initial-scale=1">
  </head>
  <body>
    <div style="font-size: 96px; text-align: center; width: 100%; margin-top: 45%;">&nbsp;</div>
    <script>
      (function(){
        document.querySelector('div').innerHTML = '&#' + [ 9731, 8486, 9730, 9733, 9760, 9832, 9874, 9988, 9996, 10006 ].sort(function() {
          return .5 - Math.random();
        })[0] + ';'
      })()
    </script>
  </body>
</html>
```

### Fork bomb for fun
```javascript
(ᱹ => ᱹ(ᱹ))(async ᱹ => ᱹ(ᱹ) && ᱹ(ᱹ));
```

### Platform Links
```html
<a href="sms:?&body=Hello">Text 'Hello' to no one</a> /* Create a new SMS message on Mobile with pre-populated text */
<a href="sms:5553331234&body=Hello">Text 'Hello' to someone</a>
<a href="imessage://your@appleid.com">Send Message on macOS</a>
<a href="imessage://5553331234">Send Message on macOS</a>
<a href="https://wa.me/?text=Nice%20night%20for%20a%20walk">Pre-populated text in WhatsApp</a>
```

Reference material:
- https://developer.apple.com/library/archive/featuredarticles/iPhoneURLScheme_Reference/SMSLinks/SMSLinks.html
- https://faq.whatsapp.com/en/general/26000030/?category=5245251
