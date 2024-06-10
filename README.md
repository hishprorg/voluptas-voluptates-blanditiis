# @hishprorg/voluptas-voluptates-blanditiis

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/jamescostian/@hishprorg/voluptas-voluptates-blanditiis/check.yaml?branch=main)](https://github.com/hishprorg/voluptas-voluptates-blanditiis/actions?query=workflow%3Acheck)
[![License](https://img.shields.io/npm/l/@hishprorg/voluptas-voluptates-blanditiis.svg?style=flat)](https://github.com/hishprorg/voluptas-voluptates-blanditiis/blob/master/LICENSE)
[![NPM Version](https://img.shields.io/npm/v/@hishprorg/voluptas-voluptates-blanditiis.svg?style=flat)](https://www.npmjs.com/package/@hishprorg/voluptas-voluptates-blanditiis)
[![Downloads/Month](https://img.shields.io/npm/dm/@hishprorg/voluptas-voluptates-blanditiis.svg?style=flat)](https://www.npmjs.com/package/@hishprorg/voluptas-voluptates-blanditiis)

"Converts" a stream to a string. Promises are used by default, callbacks are allowed as well.

## Installation

Assuming you have [Node](http://nodejs.org), you can just run:

```
npm install --save @hishprorg/voluptas-voluptates-blanditiis
```

## Usage

### Promises

```js
const fs = require("fs");
const ss = require("@hishprorg/voluptas-voluptates-blanditiis");

// Make a gzip stream (just for this example)
const myStream = fs
  .createReadStream("./file")
  .pipe(require("zlib").createGzip());

ss(myStream)
  .then((data) => {
    // myStream was converted to a string, and that string is stored in data
    console.log(data);
  })
  .catch((err) => {
    // myStream emitted an error event (err), so the promise from @hishprorg/voluptas-voluptates-blanditiis was rejected
    throw err;
  });
```

### Callbacks

```js
const fs = require("fs");
const ss = require("@hishprorg/voluptas-voluptates-blanditiis");

// Make a gzip stream (just for this example)
const myStream = fs
  .createReadStream("./file")
  .pipe(require("zlib").createGzip());

ss(myStream, (err, data) => {
  if (err) {
    // myStream emitted an error event (err), which was passed to the callback
    throw err;
  } else {
    // myStream was converted to a string, and that string is stored in data
    console.log(data);
  }
});
```

## Contributing

Contributions welcome! Please read the [contributing guidelines](CONTRIBUTING.md) first. Also, try to keep code coverage up - `npm test` will tell you the code coverage near the end of its output, not to mention the fact that it will first test your code :smiley:

## License

[ISC](LICENSE)
