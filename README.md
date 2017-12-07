# Sane default configuration for [stylelint](https://github.com/stylelint/stylelint)

Stylelint is used for linting and fixing CSS, including preprocessor syntaxes like Sass, SCSS, SugarCSS, Less.

## Installation

1. Move `.stylelintrc` to your project root.
2. Run:
    ```shell
    yarn add -D stylelint stylelint-order stylelint-scss
    # or
    npm install -D stylelint stylelint-order stylelint-scss
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
* No leading or trailing zeros in decimals (e.g. `.5em`).
* No units for zero lengths (e.g. `margin: 0`).

### Declarations

* Properties, colours, units, pseudo-classes, and -elements must be lowercased.
* Properties must be ordered as described in [SMACSS](https://smacss.com/book/formatting#grouping). Order configuration taken from [scss-lint](https://github.com/brigade/scss-lint/blob/master/data/property-sort-orders/smacss.txt).
* Shorthands must be used where possible (e.g. `margin: 1em` instead of `margin: 1em 1em`).
* Colours in hex must use long notation (e.g. `#ff00dd`).
* A generic family name must be provided in font-family (e.g. `sans-serif`).
* No duplicate or redundant property declarations.
* No vendor prefixes (use [autoprefixer](https://github.com/postcss/autoprefixer)).
* No `!important`.

### Selectors

* One selector per line.
* Attribute selectors must use quotes (e.g. `input[type="search"]`).
* Selectors must not be repeated in the same file (should be merged).
* No more than 5 levels of selectors.

### SCSS

* Calls with no arguments must not use parentheses (e.g. `@include mixin-name`).
* Operators must be surrounded by spaces (e.g. `$a * $b`).
* No redundant parent selector (`&`) when nesting (e.g. `p { > a { } }`).
