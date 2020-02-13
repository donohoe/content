# PHP I Keep Returning Too
#### February 13th 2020

Nothing earth shattering, just a collection of code fragments and functions I keep re-writing and re-using...

### Basic compression of CSS for output 
```javascript
// Remove comments
$cssText = preg_replace('!/\*[^*]*\*+([^/][^*]*\*+)*/!', '', $custom_css_field);

// Remove space after colons
$cssText = str_replace(': ', ':', $cssText);

// Remove whitespace
$cssText = str_replace(array("\r\n", "\r", "\n", "\t", '  ', '    ', '    '), '', $cssText);

print "/* custom css */\n\t\t" . $cssText . "\n";
```
