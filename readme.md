# Evercookie Middleware for Connect/Express JS

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)]()
[![npm version](https://img.shields.io/npm/v/evercookie.svg?style=flat)](https://www.npmjs.com/package/evercookie)
[![Build Status](https://travis-ci.org/truongsinh/node-evercookie.svg?branch=master)](https://travis-ci.org/truongsinh/node-evercookie)
[![Coverage Status](https://img.shields.io/coveralls/truongsinh/node-evercookie/master.svg?style=flat)](https://coveralls.io/github/truongsinh/node-evercookie?branch=master)
[![Dependencies Status](https://david-dm.org/truongsinh/node-evercookie.svg)](https://david-dm.org/truongsinh/node-evercookie)
[![DevDependencies Status](https://david-dm.org/truongsinh/node-evercookie/dev-status.svg)](https://david-dm.org/truongsinh/node-evercookie?type=dev)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]()
[![code style: prettier](https://img.shields.io/badge/code_style-prettier-ff69b4.svg?style=flat-square)](https://github.com/prettier/prettier)

[Express](http://expressjs.com) is a sinatra inspired web development framework for node.js, insanely fast, flexible, and simple.
[Evercookie](http://samy.pl/evercookie/) is a Javascript API that produces extremely persistent cookies in a browser.
It is written in JavaScript and additionally uses a SWF (Flash) object for the Local Shared Objects and,
originally, PHPs for the server-side generation of cached PNGs and ETags.

This middleware port original PHP script to Connect/Express JS

# Support
- Node: 6, 8, 10, 11
- Express: 4.x, 5.x
- See detail at [![Build Status](https://travis-ci.org/truongsinh/node-evercookie.svg?branch=master)](https://travis-ci.org/truongsinh/node-evercookie)

# Usage

## Install
```bash
npm install --save evercookie
```

## In your code
Evercookie backend middleware needs cookie, thus `cookieParser()` middleware must come before Evercookie backend middleware.
In addition, express server must serve front end assets, such as index.html and evercookie.js as well.
```js
var express = require('express');
var evercookie = require('evercookie');
const cookieParser = require('cookie-parser')

var app = express();
app.use(cookieParser());
app.use(evercookie.backend());
app.use(express.cookieParser());
app.use(express.static(__dirname + '/public')); // be careful, you may want to use path.join instead!
```

## Settings
Customized settings can be used, but up to this moment, it makes no sense to change the dafault one,
as all these values are hardcoded in (frontend) `evercookie.js`.
```js
//...
app.use(evercookie.backend({
  pngCookieName: 'evercookie_png',
  etagCookieName: 'evercookie_etag',
  cacheCookieName: 'evercookie_cache',
  pngPath: '/evercookie_png.php',
  etagPath: '/evercookie_etag.php',
  cachePath: '/evercookie_cache.php'
}));
//...
```

# Contributing
- [Contrubuting guideline](./CONTRIBUTING.md)
- [Code of Conduct](./CODE_OF_CONDUCT.md)
- [MIT licensed](./LICENSE)

# Acknowledgement
- [Samy Kamkar](https://github.com/samyk) for his awesome idea and implementation of [Evercookie](http://samy.pl/evercookie/)
- [TJ Holowaychuk](https://github.com/tj) for his awesome [Express framework](http://expressjs.com/)
- Ryan Dahl, Joyent and the whole Node.js community
