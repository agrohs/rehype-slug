# rehype-slug [![Build Status][travis-badge]][travis] [![Coverage Status][codecov-badge]][codecov]

Add `id`s to headings with [**rehype**][rehype].

## Installation

[npm][]:

```bash
npm install rehype-slug
```

## Usage

Say we have the following file, `fragment.html`:

```html
<h1>Lorem ipsum 😪</h1>
<h2>dolor—sit—amet</h2>
<h3>consectetur &amp; adipisicing</h3>
<h4>elit</h4>
<h5>elit</h5>
```

And our script, `example.js`, looks as follows:

```javascript
var fs = require('fs')
var rehype = require('rehype')
var slug = require('rehype-slug')

rehype()
  .data('settings', {fragment: true})
  .use(slug)
  .process(fs.readFileSync('fragment.html'), function(err, file) {
    if (err) throw err
    console.log(String(file))
  })
```

Now, running `node example` yields:

```html
<h1 id="lorem-ipsum-">Lorem ipsum 😪</h1>
<h2 id="dolorsitamet">dolor—sit—amet</h2>
<h3 id="consectetur--adipisicing">consectetur &#x26; adipisicing</h3>
<h4 id="elit">elit</h4>
<h5 id="elit-1">elit</h5>
```

## API

### `rehype().use(slug)`

Adds `id` properties to h1-h6 headings which don’t already have one.

Uses [**github-slugger**][ghslug] (thus creating GitHub style `id`s).

## Related

*   [`remark-slug`](https://github.com/wooorm/remark-slug)
    — Add slugs to headings in markdown

## Contribute

See [`contributing.md` in `rehypejs/rehype`][contribute] for ways to get
started.

This organisation has a [Code of Conduct][coc].  By interacting with this
repository, organisation, or community you agree to abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

<!-- Definitions -->

[travis-badge]: https://img.shields.io/travis/rehypejs/rehype-slug.svg

[travis]: https://travis-ci.org/rehypejs/rehype-slug

[codecov-badge]: https://img.shields.io/codecov/c/github/rehypejs/rehype-slug.svg

[codecov]: https://codecov.io/github/rehypejs/rehype-slug

[npm]: https://docs.npmjs.com/cli/install

[license]: LICENSE

[author]: http://wooorm.com

[rehype]: https://github.com/rehypejs/rehype

[ghslug]: https://github.com/Flet/github-slugger

[contribute]: https://github.com/rehypejs/rehype/blob/master/contributing.md

[coc]: https://github.com/rehypejs/rehype/blob/master/code-of-conduct.md
