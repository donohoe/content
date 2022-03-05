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

### Common utility functions
```

function randomItemFrom( $array ) {
  if (is_array($array)) {
    return $array[ rand(0, count($array)-1) ];
  }
  return array();
}

private function startsWith($haystack, $needle){
  return $needle === "" || strpos($haystack, $needle) === 0;
}

private function doesContain($haystack, $needle) {
  $pos = strpos($haystack, $needle);
  if ($pos === false) return false;
  return true;
}

private function containsFromArray($str, array $arr) {
  foreach($arr as $a) {
    if (stripos($str,$a) !== false) return true;
  }
  return false;
}
```

### Basic readable date
```
function get_time_since( $since ) {
    $chunks = array(
        // array(31536000 , 'year'),
        // array(2592000 , 'month'),
        // array(604800, 'week'),
        array(86400 , 'day'),
        array(3600 , 'hour'),
        array(60 , 'minute'),
        array(1 , 'second')
    );
    for ($i = 0, $j = count($chunks); $i < $j; $i++) {
        $name = $chunks[$i][1];
        if (($count = floor($since / $chunks[$i][0])) != 0) {
            break;
        }
    }
    $print = ($count == 1) ? '1 '.$name : "$count {$name}s";
    return $print;
}
$basic_time = get_time_since( time() - strtotime("2022-03-05 14:03:14") );
```
