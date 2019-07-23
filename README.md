# @considonet/stylelint-config-bem

> Default [`stylelint`](https://github.com/stylelint/stylelint) ruleset for BEM methodology-based stylesheets in ConsidoNet projects.

## Rules

This config is built upon [`stylelint-selector-bem-pattern`](https://github.com/simonsmith/stylelint-selector-bem-pattern).

After some tweaks the following rules are applied:

* [Two Dashes style](https://en.bem.info/methodology/naming-convention/#two-dashes-style) naming scheme -
  `block__element--modifier`.
* Optional (and recommended for Considonet projects) [namespaced naming scheme](https://medium.com/@wenukagtx/bem-namespaces-81a5868e725c) supported - `c-block__element--modifier`  
* One block (component) per one file (except utilities)
* Block names consistent with filenames (minus extension, optional namespace and optional `_` filename prefix for Sass/SCSS).
* `svg` and `img` can be styled by tag name.
* [No namespace](https://en.bem.info/methodology/naming-convention/#no-namespace-style) modifiers are accepted for component state - `-is-` and `-has` prefixed classnames (_for example `.c-block.-is-active`_).  

## Installation

Using npm:

```sh
npm install --save-dev @considonet/stylelint-config-bem
```

or using yarn:

```sh
yarn add @considonet/stylelint-config-bem --dev
```

## Usage

In your .stylelintrc.js file extend your config:

```json
{ 
  "extends": "@considonet/stylelint-config-bem"
}
```

### Implicit components

By default all linted stylesheets are treated as implicit components. It means that component
names used for linting are based on the filenames. Although [plugin config allows to narrow down
implicit components](https://github.com/postcss/postcss-bem-linter#define-components-and-utilities-implicitly-based-on-their-filename),
[stylelint does not allow to merge nested options](https://github.com/stylelint/stylelint/blob/master/docs/user-guide/faq.md#if-i-use-extends-within-my-configuration-object-will-the-options-for-each-rule-be-merged-or-overridden).
It means that to disable it for some files, `stylelint-disable` comment is required. Example:

```css
/* not-bem.css */
/* stylelint-disable plugin/selector-bem-pattern */
a {
    color: inherit;
}
/* stylelint-enable plugin/selector-bem-pattern */
```

### Usage with other configs

**This config contains only rules for BEM and probably you don't want to use it standalone.**
We recommend to use `@considonet/stylelint-config-bem` with at least [`@considonet/stylelint-config-scss`](https://github.com/considonet/stylelint-config-scss) or any other general ruleset.

See [popular `stylelint` configs](https://www.npmjs.com/search?q=stylelint-config&ranking=popularity) for more inspirations.

Example usage with other our packages:

```json
{
  "extends": [
    "@considonet/stylelint-config-bem",
    "@considonet/stylelint-config-scss",
    "@considonet/stylelint-config-order"
  ]
}
```

You can also use our default preset which includes this configuration - [`@considonet/stylelint-config-default`](https://github.com/considonet/stylelint-config-default).
