# bad-words

A javascript filter for badwords

[![Build Status](https://travis-ci.org/web-mech/badwords.svg?branch=master)](https://travis-ci.org/web-mech/badwords)
[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)
[![semantic-release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg?style=flat-square)](https://github.com/semantic-release/semantic-release)

## Installation

```
npm install bigearsenal/badwords#master
```

## Usage

```js
var Filter = require('bad-words'),
    filter = new Filter();

console.log(filter.clean("Don't be an ash0le")); //Don't be an ******
```

### Placeholder Overrides

```js
var Filter = require('bad-words');
var customFilter = new Filter({ placeHolder: 'x'});

customFilter.clean('Don't be an ash0le'); //Don't be an xxxxxx
```

### Regex Overrides

```js
var filter = new Filter({ regex: /\*|\.|$/gi });

var filter = new Filter({ replaceRegex:  /[A-Za-z0-9가-힣_]/g }); 
//multilingual support for word filtering
```

### Add words to the blacklist

```js
var filter = new Filter(); 

filter.addWords(['some', 'bad', 'word']);

filter.clean("some bad word!") //**** *** ****!

//or

var filter = new Filter({ list: ['some', 'bad', 'word'] }); 

filter.clean("some bad word!") //**** *** ****!
```

### Instantiate with an empty list

```js
var filter = new Filter({ emptyList: true }); 
filter.clean('hell this wont clean anything'); //hell this wont clean anything
```

### Remove words from the blacklist

```js
var filter = new Filter(); 

filter.removeWords('hells');

filter.clean("some hells word!"); //some hells word!
```

### API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

#### Filter

Filter constructor.

**Parameters**

-   `options` **[object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object)** Filter instance options
    -   `options.emptyList` **[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)** Instantiate filter with no blacklist
    -   `options.list` **[array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)** Instantiate filter with custom list
    -   `options.placeHolder` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Character used to replace profane words.
    -   `options.regex` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Regular expression used to sanitize words before comparing them to blacklist.
    -   `options.replaceRegex` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Regular expression used to replace profane words with placeHolder.

##### isProfane

Determine if a string contains profane language.

**Parameters**

-   `string` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** String to evaluate for profanity.

##### isProfaneLike

Determine if a single word is profane or looks profane.

**Parameters**

-   `word` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** String to evaluate for profanity.

##### replaceWord

Replace a word with placeHolder characters;

**Parameters**

-   `string` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** String to replace.

##### clean

Evaluate a string for profanity and return an edited version.

**Parameters**

-   `string` **[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Sentence to filter.

##### addWords

Add words to blacklist filter / remove words from whitelist filter

**Parameters**

-   `words`  

##### removeWords

Add words to whitelist filter

**Parameters**

-   `word` **...[string](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)** Word to add to whitelist.

## Testing

```
npm test
```

## Release Notes

-   v1.1.0 / Mar 17 2015: Added soundex support for comparing words to things not in the list.
-   v1.2.0 / May 29 2015: Removed soundex logic which resulted in many false positives within the isProfane test.
-   v1.3.0 / Oct 1 2015: Updated local list and documentation. Added ability to pass a custom list of words during construction.
-   v1.4.0 / Sept 2 2016: Added removeWords feature. Added emptyList configuration parameter.
-   v1.4.1 / Sept 2 2016: Updated documentation.
-   v1.4.3 / Jan 21 2017: Add multilingual support for word filtering
-   v1.5.1 / April 14 2017: Patch for word tokenization.

## License

The MIT License (MIT)

Copyright (c) 2013 Michael Price

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
