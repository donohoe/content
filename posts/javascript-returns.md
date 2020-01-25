# Javascript I Keep Returning Too
#### January 25th 2020

Nothing earth shattering, just a collection of code fragments and functions I keep re-writing and re-using...

### Base
```javascript
(function(){
  class App {
    constructor() {
      this.test = {};
      this.run()
    }
    run() {
    //  Hello
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
  const head  = document.getElementsByTagName('head')[0];
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
### Insert DIV after Element
```javascript
function insertDivVAfter( targetEl, id ) {
  const div = document.createElement('div');
  div.id = id;
  div.className = 'placement';
  targetEl.parentNode.insertBefore( div, targetEl.nextSibling );
}

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

### Get random item from array
```javascript
const list = [ 'a', 'b', 'c', 'd', 'e' ];
const item = list[ Math.floor(Math.random() * list.length) ];
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
