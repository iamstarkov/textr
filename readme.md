# textr

[![NPM version][npm-image]][npm-url]
[![Build Status][travis-image]][travis-url]
[![Coveralls Status][coveralls-image]][coveralls-url]
[![Dependency Status][depstat-image]][depstat-url]
[![DevDependency Status][depstat-dev-image]][depstat-dev-url]

> Tiny and extendable text transforming framework

Superslim text transforming framework. With `textr` you can easy
to create modular typographers with your very own text transformation logic
to use it on many cases like just fix quotes or even convert your text
from markdown to html.


## Install

```
npm install --save textr
```


## Usage

```js
var textr    = require('textr');
var ellipses = require('typographic-ellipses');
var spaces   = require('typographic-single-spaces');

// you can wrap plugins to partial apply their options
// basically for possible locale parameter
var _quotes  = require('typographic-quotes');
var quotes   = function (text) { return _quotes(text, 'ru' ); };

// Create new text transformer
// and register your plugins
tf = textr()
  .use(ellipses)
  .use(spaces)
  .use(quotes);

// then just send some text to the transformer
tf('Hello "world"...'); // Hello “world”…
```

## Textr plugins

All textr plugins are available on npm, labelled with [typographic][typographic]
keyword.

Also you can easily create new one. Don’t be scared. Each plugin is just
a function that get text, transform it and return result of processing.
For example this is the source of the [`typographic-ellipses`](ellipses) plugin:

```js
module.exports = function(input) { return input.replace(/\.{3}/gim, '…'); }
```

[typographic]: https://www.npmjs.com/browse/keyword/typographic
[ellipses]: https://github.com/matmuchrapna/typographic-ellipses


## License

MIT © [Shuvalov Anton](http://shuvalov.info)


[npm-url]: https://npmjs.org/package/textr
[npm-image]: http://img.shields.io/npm/v/textr.svg

[travis-url]: https://travis-ci.org/shuvalov-anton/textr
[travis-image]: http://img.shields.io/travis/shuvalov-anton/textr.svg

[coveralls-url]: https://coveralls.io/r/shuvalov-anton/textr
[coveralls-image]: http://img.shields.io/coveralls/shuvalov-anton/textr.svg

[depstat-url]: https://david-dm.org/shuvalov-anton/textr
[depstat-image]: https://david-dm.org/shuvalov-anton/textr.svg

[depstat-dev-url]: https://david-dm.org/shuvalov-anton/textr
[depstat-dev-image]: https://david-dm.org/shuvalov-anton/textr/dev-status.svg
