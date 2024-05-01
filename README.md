# @devtea2026/vel-qui-odit-quaerat <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

ES Proposal spec-compliant shim for Promise.allSettled. Invoke its "shim" method to shim `Promise.allSettled` if it is unavailable or noncompliant. **Note**: a global `Promise` must already exist: the [es6-shim](https://github.com/es-shims/es6-shim) is recommended.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment that has `Promise` available globally, and complies with the [proposed spec](https://github.com/tc39/proposal-promise-allSettled).

Most common usage:
```js
var assert = require('assert');
var allSettled = require('@devtea2026/vel-qui-odit-quaerat');

var resolved = Promise.resolve(42);
var rejected = Promise.reject(-1);

allSettled([resolved, rejected]).then(function (results) {
	assert.deepEqual(results, [
		{ status: 'fulfilled', value: 42 },
		{ status: 'rejected', reason: -1 }
	]);
});

allSettled.shim(); // will be a no-op if not needed

Promise.allSettled([resolved, rejected]).then(function (results) {
	assert.deepEqual(results, [
		{ status: 'fulfilled', value: 42 },
		{ status: 'rejected', reason: -1 }
	]);
});
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@devtea2026/vel-qui-odit-quaerat
[npm-version-svg]: http://versionbadg.es/devtea2026/vel-qui-odit-quaerat.svg
[travis-svg]: https://travis-ci.org/devtea2026/vel-qui-odit-quaerat.svg
[travis-url]: https://travis-ci.org/devtea2026/vel-qui-odit-quaerat
[deps-svg]: https://david-dm.org/devtea2026/vel-qui-odit-quaerat.svg
[deps-url]: https://david-dm.org/devtea2026/vel-qui-odit-quaerat
[dev-deps-svg]: https://david-dm.org/devtea2026/vel-qui-odit-quaerat/dev-status.svg
[dev-deps-url]: https://david-dm.org/devtea2026/vel-qui-odit-quaerat#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@devtea2026/vel-qui-odit-quaerat.png?downloads=true&stars=true
[license-image]: http://img.shields.io/npm/l/@devtea2026/vel-qui-odit-quaerat.svg
[license-url]: LICENSE
[downloads-image]: http://img.shields.io/npm/dm/@devtea2026/vel-qui-odit-quaerat.svg
[downloads-url]: http://npm-stat.com/charts.html?package=@devtea2026/vel-qui-odit-quaerat
[codecov-image]: https://codecov.io/gh/devtea2026/vel-qui-odit-quaerat/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/devtea2026/vel-qui-odit-quaerat/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/devtea2026/vel-qui-odit-quaerat
[actions-url]: https://github.com/devtea2026/vel-qui-odit-quaerat/actions
