# Javascript I Keep Returning Too
#### January 25th 2020

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

### Simple AJav for text and JSON
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


### Get random item from array
```javascript
const list = [ 'a', 'b', 'c', 'd', 'e' ];
const item = list[ Math.floor(Math.random() * list.length) ];
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
shuffle: function(array) {
  let currentIndex = array.length, temporaryValue, randomIndex;
  while (0 !== currentIndex) {
    randomIndex = Math.floor(Math.random() * currentIndex);
    currentIndex -= 1;
    temporaryValue = array[currentIndex];
    array[currentIndex] = array[randomIndex];
    array[randomIndex] = temporaryValue;
  }
  return array;
}
```

### Fastest loop with length caching
```javascript
const list = [ 'a', 'b', 'c', 'd', 'e' ];
for (var i = 0, l = list.length; i < l; i++) {
  // Things
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
