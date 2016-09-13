# asar - Electron Archive

[![dependencies](http://img.shields.io/david/scottwey/asar.svg?style=flat-square)](https://david-dm.org/scottwey/asar)
[![npm version](http://img.shields.io/npm/v/original-fs-asar.svg?style=flat-square)](https://npmjs.org/package/original-fs-asar)

Asar is a simple extensive archive format, it works like `tar` that concatenates
all files together without compression, while having random access support.

## Features

* Support random access
* Use JSON to store files' information
* Very easy to write a parser

## Command line utility

### Install

```bash
$ npm install original-fs-asar
```

### Usage

Only runs inside of Electron.

## Using programatically

### Example

```js
var asar = require('original-fs-asar');

var src = 'some/path/';
var dest = 'name.asar';

asar.createPackage(src, dest, function() {
  console.log('done.');
})
```

Please note that there is currently *no* error handling provided!

### Transform
You can pass in a `transform` option, that is a function, which either returns
nothing, or a `stream.Transform`. The latter will be used on files that will be
in the `.asar` file to transform them (e.g. compress).

```js
var asar = require('original-fs-asar');

var src = 'some/path/';
var dest = 'name.asar';

function transform(filename) {
  return new CustomTransformStream()
}

asar.createPackageWithOptions(src, dest, { transform: transform }, function() {
  console.log('done.');
})
```
