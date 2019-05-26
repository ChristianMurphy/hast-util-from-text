# hast-util-from-text

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

[**hast**][hast] utility to get the plain-text value of a [*node*][node].

This is like the DOMs `Node#innerText` setter.

You’d typically want to use [`hast-util-from-string`][from-string]
(`textContent`), but `hast-util-from-text` (`innerText`) adds `<br>` elements
instead of line breaks.

## Install

[npm][]:

```sh
npm install hast-util-from-text
```

## Usage

```js
var h = require('hastscript')
var fromText = require('hast-util-from-text')

fromText(h('p'), 'Alpha')
// { type: 'element',
//   tagName: 'p',
//   properties: {},
//   children: [ { type: 'text', value: 'Alpha' } ] }

fromText(h('p', [h('b', 'Bravo'), '.']), 'Charlie')
// { type: 'element',
//   tagName: 'p',
//   properties: {},
//   children: [ { type: 'text', value: 'Charlie' } ] }

fromText(h('p'), 'Delta\nEcho')
// { type: 'element',
//   tagName: 'p',
//   properties: {},
//   children:
//    [ { type: 'text', value: 'Delta' },
//      { type: 'element', tagName: 'br', properties: {}, children: [] },
//      { type: 'text', value: 'Echo' } ] }
```

## API

### `fromText(node[, value])`

If the given `node` is a [*literal*][literal], set that to the given `value` or
an empty string.
If the given `node` is a [*parent*][parent], its [*children*][child] are
replaced with new children: [*texts*][text] for every run of text and `<br>`
[*elements*][element] for every line break (a line feed, `\n`; a carriage
return, `\r`; or a carriage return + line feed, `\r\n`).
If no `value` is given (empty string `''`, `null`, or `undefined`), the
literal’s value is set to an empty string or the parent’s children are removed.

## Related

*   [`hast-util-to-text`](https://github.com/syntax-tree/hast-util-to-text)
    — Get the plain-text value (`innerText`)
*   [`hast-util-to-string`](https://github.com/rehypejs/rehype-minify/tree/master/packages/hast-util-to-string)
    — Get the plain-text value (`textContent`)
*   [`hast-util-from-string`][from-string]
    — Set the plain-text value (`textContent`)

## Contribute

See [`contributing.md` in `syntax-tree/.github`][contributing] for ways to get
started.
See [`support.md`][support] for ways to get help.

This project has a [Code of Conduct][coc].
By interacting with this repository, organisation, or community you agree to
abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[build-badge]: https://img.shields.io/travis/syntax-tree/hast-util-from-text.svg

[build]: https://travis-ci.org/syntax-tree/hast-util-from-text

[coverage-badge]: https://img.shields.io/codecov/c/github/syntax-tree/hast-util-from-text.svg

[coverage]: https://codecov.io/github/syntax-tree/hast-util-from-text

[downloads-badge]: https://img.shields.io/npm/dm/hast-util-from-text.svg

[downloads]: https://www.npmjs.com/package/hast-util-from-text

[size-badge]: https://img.shields.io/bundlephobia/minzip/hast-util-from-text.svg

[size]: https://bundlephobia.com/result?p=hast-util-from-text

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/join%20the%20community-on%20spectrum-7b16ff.svg

[chat]: https://spectrum.chat/unified/syntax-tree

[npm]: https://docs.npmjs.com/cli/install

[license]: license

[author]: https://wooorm.com

[contributing]: https://github.com/syntax-tree/.github/blob/master/contributing.md

[support]: https://github.com/syntax-tree/.github/blob/master/support.md

[coc]: https://github.com/syntax-tree/.github/blob/master/code-of-conduct.md

[from-string]: https://github.com/rehypejs/rehype-minify/tree/master/packages/hast-util-from-string

[literal]: https://github.com/syntax-tree/unist#literal

[parent]: https://github.com/syntax-tree/unist#parent

[child]: https://github.com/syntax-tree/unist#child

[hast]: https://github.com/syntax-tree/hast

[node]: https://github.com/syntax-tree/hast#nodes

[text]: https://github.com/syntax-tree/hast#text

[element]: https://github.com/syntax-tree/hast#element