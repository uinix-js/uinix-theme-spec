# uinix-theme-spec

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][bundle-size-badge]][bundle-size]

The default [`uinix-theme`][uinix-theme] spec.

## Contents

- [Install](#install)
- [Use](#use)
- [API](#api)
- [Related](#related)
- [License](#license)

## Install

This package is [ESM-only] and requires Node 12+.

```sh
npm install uinix-theme-spec
```

## Use

```js
import {createTheme} from 'uinix-theme';
import themeSpec from 'uinix-theme-spec';

const theme = createTheme({
  colors: {
    brand: {
      primary: 'red',
      link: 'blue',
    },
  },
  spacings: {
    s: 4,
    m: 8,
    l: 16,
  },
  unsupportedThemeProperty: {}
}, themeSpec);


console.log(theme);
```

Yields the following theme object.

```js
const theme = {
  animations: {},
  backgrounds: {},
  borders: {},
  borderStyles: {},
  borderWidths: {},
  colors: {
    brand: {
      primary: 'red',
      link: 'blue',
    },
  },
  filters: {},
  fontFamilies: {},
  fontSizes: {},
  fontWeights: {},
  keyframes: {},
  letterSpacings: {},
  lineHeights: {},
  opacities: {},
  radii: {},
  shadows: {},
  sizes: {},
  spacings: {
    s: 4,
    m: 8,
    l: 16,
  },
  transforms: {},
  transitions: {},
  zIndices: {},
};
```

Apply the `theme` and `themeSpec` to a theme renderer.

```js
import {createThemeRenderer} from 'uinix-theme';

const renderer = createThemeRenderer({
  theme,
  themeSpec,
});
```

Initialize the renderer and render a themed style.

```js
const style = {
  color: 'brand.primary',
  padding: 'm',
  ':hover > a': {
    color: 'brand.link',
    padding: 's',
  },
};

renderer.renderStyle(style);
```

Yields the following rendered CSS

```css
.x {
  color: red;
  padding: 8px;
}
.x:hover > a {
  color: blue;
  padding: 4px
}
```

See [`uinix-theme`][uinix-theme] for more details.

## API

`uinix-theme-spec` only has a single default export.

### `spec (ThemeSpec)`

A theme spec, usable by a theme renderer.

### Related

- [`uinix-theme`][uinix-theme]
- [`uinix-theme-spec-theme-ui`][uinix-theme-spec-theme-ui]
- [`uinix-ui`][uinix-ui]

### License

[MIT][license] © [Chris Zhou][author]

<!-- project -->

[author]: https://github.com/chrisrzhou
[license]: https://github.com/uinix-js/uinix-theme-spec/blob/main/license
[build]: https://github.com/uinix-js/uinix-theme-spec/actions
[build-badge]: https://github.com/uinix-js/uinix-theme-spec/workflows/main/badge.svg
[coverage]: https://codecov.io/github/uinix-js/uinix-theme-spec
[coverage-badge]: https://img.shields.io/codecov/c/github/uinix-js/uinix-theme-spec.svg
[downloads]: https://www.npmjs.com/package/uinix-theme-spec
[downloads-badge]: https://img.shields.io/npm/dm/uinix-theme-spec.svg
[bundle-size]: https://bundlephobia.com/result?p=uinix-theme-spec
[bundle-size-badge]: https://img.shields.io/bundlephobia/minzip/uinix-theme-spec.svg
[uinix-js]: https://github.com/uinix-js/
[uinix philosophy]: https://github.com/uinix-js#the-uinix-philosophy
[uinix-ui]: https://github.com/uinix-js/uinix-ui

<!-- defs -->
[ESM-only]: https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c
[uinix-theme]: https://github.com/uinix-js/uinix-theme
[uinix-theme-spec-theme-ui]: https://github.com/uinix-js/uinix-theme-spec-theme-ui
[uinix-ui]: https://github.com/uinix-js/uinix-ui
