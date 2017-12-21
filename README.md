# Sane default configuration for [stylelint](https://github.com/stylelint/stylelint) with SCSS

Stylelint is used for linting and fixing CSS, including preprocessor syntaxes like Sass, SCSS, SugarCSS, Less.

## Installation

There are two installation options:

1. Via [@sane-defaults/stylelint](https://www.npmjs.com/package/@sane-defaults/stylelint) package:
    1. Install it and add as a dev-dependency
        ```shell
        yarn add @sane-defaults/stylelint --dev
        # or
        npm install @sane-defaults/stylelint --save-dev
        ```
    2. Create your [local configuration](https://stylelint.io/user-guide/configuration/) and set it to extend this one:
        ```json
        {
          "extends": "@sane-defaults/stylelint"
        }
        ```
2. Download and move `.stylelintrc.js` file to your project root.

Next, install stylelint and its plugins:

```shell
yarn add stylelint stylelint-order stylelint-scss --dev
# or
npm install stylelint stylelint-order stylelint-scss --save-dev
```

## Usage

* Install a plugin for your code editor.
* Run:
    ```shell
    stylelint **/*.scss **/*.vue
    # or
    stylelint **/*.scss **/*.vue --fix
    ```

## Rules summary

This set of rules is opinionated and designed to be sane, not strict.
Still, you might run into situations when you need to break a rule, e.g. because you extend a third-party stylesheet. For those rare cases, instead of removing a rule, it's better to explicitly ignore it in the code:

```css
button:disabled {
    /* stylelint-disable-next-line declaration-no-important */
    background: #f5f5f5 !important;
}
```

### Syntax

* Use 4 spaces for indentation.
* File must end with empty line.
* All statements must end with a semicolon.
* Trailing whitespaces are [not allowed](http://www.dinduks.com/why-are-trailing-whitespaces-bad/).
* Maximum of 1 empty line between blocks is allowed.
* Use [the one true brace style](https://en.wikipedia.org/wiki/Indentation_style#Variant:_1TBS_.28OTBS.29).
* Use double quotes for strings (e.g. `input[type="radio"]`).
* Use leading zeros in decimals (e.g. `0.5em`).
* No units for zero lengths (e.g. `margin: 0`).

### Declarations

* Custom properties (variables) must be hyphenated and lowercased.
* Properties, colours, units, pseudo-classes, and -elements must be lowercased.
* Properties must be ordered as described in [SMACSS](https://smacss.com/book/formatting#grouping). Order configuration taken from [scss-lint](https://github.com/brigade/scss-lint/blob/master/data/property-sort-orders/smacss.txt).
* Shorthands must be used where possible (e.g. `margin: 1em` instead of `margin: 1em 1em`).
* Colours in hex must use long notation (e.g. `#ff00dd`).
* A generic family name must be provided in font-family (e.g. `sans-serif`).
* Use numeric notation for font-weight (e.g. `400`).
* No duplicate or redundant property declarations.
* No vendor prefixes (use [autoprefixer](https://github.com/postcss/autoprefixer)).
* No `!important`.

### Selectors

* Class selectors must be hyphenated and lowercased, or follow [BEM convention](http://getbem.com/naming/).
* Id selectors must be hyphenated and lowercased.
* One selector per line.
* Attribute selectors must use quotes (e.g. `input[type="search"]`).
* Selectors must not be repeated in the same file (should be merged).
* No more than 5 levels of selectors.

### SCSS

* Variables, mixins, placeholders, and functions must be hyphenated and lowercased.
* Calls with no arguments must not use parentheses (e.g. `@include mixin-name`).
* Operators must be surrounded by spaces (e.g. `$a * $b`).
* No redundant parent selector (`&`) when nesting (e.g. `p { > a { } }`).
