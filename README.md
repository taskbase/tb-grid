# tb-grid

[![][license img]][license]
[![][npm version]][npmversion]

![tb-grid-2](https://user-images.githubusercontent.com/10352805/116756778-fc0d6d80-aa0c-11eb-840a-0bbb3a92ca9c.gif)

## 👉 Demos & Playground

Have a look at those examples:

- Main Demo: https://jsfiddle.net/bersling/af07cw94/324/
- Demo with Cars & Cards: https://jsfiddle.net/bersling/n2tqd85h/37/
- Bootstrap example, where grid is replaced with `tb-grid`: https://codepen.io/bersling/pen/RwKzdgV (Original: https://codepen.io/WeeHorse/pen/PQydzW)

Simply fork the demos if you want to play around with `tb-grid`.

## 🤔 Why `tb-grid`?

Bootstrap's grid system is awesome. With very little code you can add responsiveness to your html in a declarative manner. The use of 12 columns make the grid system extremely versatile since you can divide it into nice fractions (12/2, 12/3, 12/4, 12/6 - they all produce integers!).

However, there are also some things bootstrap didn't get right.

1. It requires too much nesting: `.container` > `.row` > `.col`. It would be great if we could drop the `.container`.
2. Being able to change guttes (aka. gaps) on a case-by-case basis is important, but it's a bit cumbersome in bootstrap.
3. The classes aren't scoped or namespaced. Furthermore `.container` and `.row` aren't that exotic that there would be no accidental collisions.
4. While at 50kb minified the grid system isn't huge, it's not exactly tiny either.

`tb-grid` addresses all those gripes with bootstrap and frankly with all other grid systems we know (foundation, skeleton, ...).

## 🤯 What is `tb-grid`?

`tb-grid` is a reverse engineered bootstrap 12 column grid built with **CSS grid**. CSS grid allows us to build a solution in around 50 lines of scss, which translates into less than 500 lines of css (~1kb gzipped). It also allows us to drop one level of nesting that was required in bootstrap, since css grid supports gutters out of the box. Finally we made sure that everything lives under the `tb-grid-` prefix, so you'd have to be really unlucky for someone to accidentally use a class declared by this library.

## 🚀 How can I install `tb-grid`?

There are a couple of ways how you can get `tb-grid`, choose what suits you best.

### Option 1: SCSS
Copy the code from `tb-grid.scss` to your project.

### Option 2: CSS
Copy the code from `tb-grid.css` to your project.

### Option 3: npm
`npm install tb-grid` and include the scss or css file from there. (`node_modules/tb-grid/tb-grid.scss` or `node_modules/tb-grid/tb-grid.css`)

### Option 4: npm CDN (unpkg)
You could use unkpg to get the file: `<link rel="stylesheet" href="https://unpkg.com/tb-grid@0.0.2/tb-grid.css">`

## 🎨 How can I use `tb-grid`?

It is pretty similar to bootstrap, with the exception that it's simpler yet with better scoping:

- Add the class `.tb-grid` to an HTML element.
- Add classes of the form `.tb-grid-<breakpoint>-<cols>`, like `.tb-grid-sm-6` or `.tb-grid-md-8` to the direct children. The breakpoints are the same ones as in bootstrap (`sm: 576px, md: 768px, lg: 992px, xl: 1200px, xxl: 1400px`). The column argument can be between `1` and `12`.
- Add `.tb-grid-gap-<gap size>` to define the `gap size`. Here, `<gap-size>` can be a value between (and including) `1` and `50`.

Complete example:

```
<div class="tb-grid tb-grid-gap-10">
  <div class="tb-grid-sm-6">
    Item 1
  </div>
  <div class="tb-grid-sm-6">
    Item 2
  </div>
  <div class="tb-grid-sm-4 tb-grid-lg-6">
    Item 3
  </div>
  <div class="tb-grid-sm-8 tb-grid-lg-6">
    Item 4
  </div>
</div>
```

No `tb-grid-gap-<px>` value means no gaps / gutters, since that's the only default that is not arbitrary, and it's really easy to add a gap. We currently only support symmetrical gaps up `50px` to keep the bundle size small, but you can easily add your own classes to extend the functionality. For example `.custom-gap-100 {row-gap: 60px; column-gap: min(20px, 8%)}`.

**Note:** When the `tb-grid` parent is smaller than `column-gap * 12`, the `column-gap` will be squished together to prevent overflows. For example, a `column-gap` of `30px` becomes problematic when the `tb-grid` parent is `360px`. That's why the `tb-grid-gap-<px>` classes use `column-gap: min(<px>, 8%)`, to squish the column gutters when it gets too tight.

## ✋ What limitations does `tb-grid` have?

- It doesn't support old browsers (IE): https://caniuse.com/?search=grid . 95% of people are using browsers that support CSS grid as of April 2021. It's up to you to decide whether this is sufficient for your project.

## 💯 What's the status of the project?

- The project is to be considered experimental and non-battle tested at this point
- The "API" (class names, css property names) are not to be considered stabled. Rather it is a working draft, and we'd love to receive feedback on it. This is also reflected in the npm version below `1.0.0`.
- Initial prototype is working well, see demos / playground above.
- We are planning to replace Bootstrap with `tb-grid` in our own codebase
- We would be thrilled to hear your opinions & suggestions on `tb-grid`! Why don't you just give it a spin and let us know what you think?

[license]:LICENSE
[license img]:https://img.shields.io/badge/license-MIT-blue.svg
[npmversion]:NPMVERSION
[npm version]:https://img.shields.io/npm/v/tb-grid?color=%238B00F7
