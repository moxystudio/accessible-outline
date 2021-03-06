# keyboard-only-outlines

[![NPM version][npm-image]][npm-url] [![Downloads][downloads-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Coverage Status][codecov-image]][codecov-url] [![Dependency status][david-dm-image]][david-dm-url] [![Dev Dependency status][david-dm-dev-image]][david-dm-dev-url]

[npm-url]:https://npmjs.org/package/@moxy/keyboard-only-outlines
[downloads-image]:https://img.shields.io/npm/dm/@moxy/keyboard-only-outlines.svg
[npm-image]:https://img.shields.io/npm/v/@moxy/keyboard-only-outlines.svg
[travis-url]:https://travis-ci.org/moxystudio/js-keyboard-only-outlines
[travis-image]:https://img.shields.io/travis/moxystudio/js-keyboard-only-outlines/master.svg
[codecov-url]:https://codecov.io/gh/moxystudio/js-keyboard-only-outlines
[codecov-image]:https://img.shields.io/codecov/c/github/moxystudio/js-keyboard-only-outlines/master.svg
[david-dm-url]:https://david-dm.org/moxystudio/js-keyboard-only-outlines
[david-dm-image]:https://img.shields.io/david/moxystudio/js-keyboard-only-outlines.svg
[david-dm-dev-url]:https://david-dm.org/moxystudio/js-keyboard-only-outlines?type=dev
[david-dm-dev-image]:https://img.shields.io/david/dev/moxystudio/js-keyboard-only-outlines.svg

Disable outlines displayed when using navigation methods other than keyboard navigation (e.g.: tab).

By default, some browsers, such as Firefox and Edge, set input borders on focus according to the host Operating System theme.
This package does not disable borders, as it may interfere with the user's own styles.
This is only apparent when users don't explicitly define a border for their inputs.

You can see it working in the [demo](https://moxystudio.github.io/js-keyboard-only-outlines/demo/) page.


## Installation

```sh
$ npm install @moxy/keyboard-only-outlines
```

This library is written in modern JavaScript and is published in both CommonJS and ES module transpiled variants. If you target older browsers please make sure to transpile accordingly.


## Usage

```js
import keyboardOnlyOutlines from '@moxy/keyboard-only-outlines'

const dispose = keyboardOnlyOutlines()
// dispose will be a function which deactivates this behaviour and can be called at any time

```

The function may also be invoked with the following options:

```js
keyboardOnlyOutlines({ styles: ..., stylesheetTarget: ... })
```

Where `styles` represents the styles to apply when a focus event is caused by mouse navigation, and `stylesheetTarget` is the node which will receive the aforementioned style. The latter option is particularly useful when dealing with ShadowDOMs.

These options have the following default values:

```js
const defaultOptions = {
    styles: `
*:focus {
    outline: none !important;
}
*::-moz-focus-inner {
    border: none !important;
}`,
    stylesheetTarget: document.head,
};
```


## Tests

```sh
$ npm test
$ npm test -- --watch # during development
```


## License

Released under the [MIT License](https://www.opensource.org/licenses/mit-license.php).
