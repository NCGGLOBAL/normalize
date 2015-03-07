# Normalize

Normalize a string with utf-8 characters.

# Usage

Download: [normalize.js](https://github.com/tehsis/normalize/blob/master/normalize.js) or [normalize.min.js](https://github.com/tehsis/normalize/blob/master/normalize.min.js)

```
$npm install normalize --save
```

or

```
$bower install normalize --save
```

Just pass the string you want to *normalize* as an argument

```javascript
console.log(normalize('Åland')) // Aland
```

You can import it as a commonJS module

```javascript
var n = require('normalize');

console.log(n('Åland')) // Aland
```

or use it as AMD

```javascript
define(['normalize'],
function(n) {
  console.log(n('Åland')) // Aland
});
```

# How it works?

Normalize is based on [Django's urlify](https://github.com/django/django/blob/master/django/contrib/admin/static/admin/js/urlify.js#L122) but supporting a
larger character's map parsed from [http://unicode.org/charts/charindex.html]

# Why?

JS _compares strings according to the utf-8 code of each character_. This means, for example, that *õ comes after z* (i.e. 'õ' > 'z' === true)
and this causes disasters when sorting strings. With normalize, you can correctly fix this issue.
Althought you have available `String.prototype.localCompare` which solve this issue, but is not yet supported on some browsers (i.e. IE10 and below).
