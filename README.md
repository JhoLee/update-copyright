# update-copyright [![NPM version](https://img.shields.io/npm/v/update-copyright.svg?style=flat)](https://www.npmjs.com/package/update-copyright) [![NPM downloads](https://img.shields.io/npm/dm/update-copyright.svg?style=flat)](https://npmjs.org/package/update-copyright) [![Build Status](https://img.shields.io/travis/jonschlinkert/update-copyright.svg?style=flat)](https://travis-ci.org/jonschlinkert/update-copyright)

Update a copyright statement with the current year. Also makes minor corrections.

## Install

Install with [npm](https://www.npmjs.com/):

```sh
$ npm install update-copyright --save
```

## Usage

```js
copyright(string, options);
```

Pass a string with a copyright statement to update, and it will be parsed and updated.

```js
var copyright = require('update-copyright');

copyright('Copyright (c) 2015, Jon Schlinkert.');
//=> 'Copyright (c) 2015-2016, Jon Schlinkert.'

copyright('Copyright (c) 2012, 2015, Jon Schlinkert.');
//=> 'Copyright (c) 2012, 2015-2016, Jon Schlinkert.'
```

The [current year](https://github.com/jonschlinkert/update-year) is updated/appended to existing years. The rest of the information will stay the same unless new information is passed.

### Lazy mode

If you're too lazy to pass anything at all, that's okay! You get a free copyright statement with the current year, using data from package.json!

```js
copyright();
//=> 'Copyright (c) 2016, Jon Schlinkert.'
```

### Optionally fills in author

**Example**

If the author is missing it will be filled in with the author from package.json.

```js
copyright('Copyright (c) 2014.');
//=> 'Copyright (c) 2014-2015, Jon Schlinkert.'
```

### Fixes Misspellings

It will use the author from package.json if a misspelling seems obvious (according to its [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance)):

```js
copyright('Copyright (c) 2014, Jon Shlinert');
//=> 'Copyright (c) 2014, 2016, Jon Schlinkert.'
```

See [the tests](./tests.js) for more examples.

## Options

A template is used to create the new copyright statement, and the options object is merged with the context that is passed to the template.

### context

1. The (context) object is populated with data from the parsed (old) copyright statement
2. The object is then updated with the current year, author from package.json, and any other data you pass on the options.

**Custom context**

This is what the context object looks like. To override anything on the context just pass the property and value on the options:

```js
{ year: '2015',
  prefix: 'Copyright',
  symbol: '(c)',
  template: '<%= prefix %><%= symbol ? (" " + symbol + " ") : "" %><%= years %>, <%= authors %>.',
  statement: 'Copyright (c) 2015, Jon Schlinkert',
  dateRange: '2014',
  latest: '2014',
  author: 'Jon Schlinkert' }
```

**Example**

Pass any custom data (as shown above) on the options:

```js
copyright('Copyright (c) 2015.', {author: 'Foo Bar'});
//=> 'Copyright (c) 2015-2016, Foo Bar.'
```

## Related projects

You might also be interested in these projects:

* [copyright-regex](https://www.npmjs.com/package/copyright-regex): Regex for matching and parsing copyright statements. | [homepage](https://github.com/regexps/copyright-regex)
* [parse-copyright](https://www.npmjs.com/package/parse-copyright): Parse copyright statement(s) into an array of copyright objects. | [homepage](https://github.com/jonschlinkert/parse-copyright)
* [update-year](https://www.npmjs.com/package/update-year): Update or add the current year to a range of years in a string. | [homepage](https://github.com/jonschlinkert/update-year)
* [year](https://www.npmjs.com/package/year): Simple utility to get the current year with 2 or 4 digits. | [homepage](https://github.com/jonschlinkert/year)
* [update](https://www.npmjs.com/package/update): Easily keep anything in your project up-to-date by installing the updaters you want to use… [more](https://www.npmjs.com/package/update) | [homepage](https://github.com/update/update)

## Contributing

Pull requests and stars are always welcome. For bugs and feature requests, [please create an issue](https://github.com/jonschlinkert/update-copyright/issues/new).

## Building docs

Generate readme and API documentation with [verb](https://github.com/verbose/verb):

```sh
$ npm install verb && npm run docs
```

Or, if [verb](https://github.com/verbose/verb) is installed globally:

```sh
$ verb
```

## Running tests

Install dev dependencies:

```sh
$ npm install -d && npm test
```

## Author

**Jon Schlinkert**

* [github/jonschlinkert](https://github.com/jonschlinkert)
* [twitter/jonschlinkert](http://twitter.com/jonschlinkert)

## License

Copyright © 2016, [Jon Schlinkert](https://github.com/jonschlinkert).
Released under the [MIT license](https://github.com/jonschlinkert/update-copyright/blob/master/LICENSE).

***

_This file was generated by [verb](https://github.com/verbose/verb), v0.9.0, on May 05, 2016._