# tb-grid

[![][license img]][license]

## Demo
https://jsfiddle.net/bersling/af07cw94/275/

## Why `tb-grid`?

Bootstrap's grid system is awesome. With very little code you can add responsiveness to your html in a declarative manner. The use of 12 columns make the grid system extremely versatile since you can divide it into nice fractions (12/2, 12/3, 12/4, 12/6 - they all produce integers!).

However, there are also some thing bootstrap didn't get right.

1. The classes aren't scoped or namespaced. And `.container` and `.row` aren't that exotic that there would be no accidental collisions.
2. It requires too much nesting: `.container` > `.row` > `.col`. It would be great if we could drop the `.container`.
3. At 50kb minified (only the gridsystem!), it's not exactly small

`tb-grid` addresses all those gripes with bootstrap.

## What is `tb-grid`?

`tb-grid` is a reverse engineered bootstrap 12 column grid built with **modern css**. This means it's utilizing features such as css grid and css variables. Like that we can reverse enginineer bootstrap's column system in less than 100 lines of scss, which translates into roughly 300 lines of css - around 7kb!

## How can I install `tb-grid`?

Option 1 (SCSS): Copy the code from `tb-grid.scss` to your project.

Option 2 (CSS): Copy the code from `tb-grid.css` to your project.

Option 3 npm (not available yet): `npm install tb-grid` and include the scss or css file from there.

Option 4 (CSS): Include the css through a css import by pointing it to the github raw file.

## How can I use `tb-grid`?

It is pretty similar to bootstrap, with the exception that it's simpler yet with better scoping:

```
<div class="tb-grid">
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

If you don't want gutters add the `.tb-grid-no-gutters` class.

You can also override the gutters for each breakpoint by using CSS variables. The defaults currently are the following:

```
:root {
  --tb-grid-column-gap-xs: min(10px, 8%);
  --tb-grid-row-gap-xs: 10px;
  --tb-grid-column-gap-sm: min(15px, 8%);
  --tb-grid-row-gap-sm: 15px;
  --tb-grid-column-gap-md: min(15px, 8%);
  --tb-grid-row-gap-md: 15px;
  --tb-grid-column-gap-lg: min(20px, 8%);
  --tb-grid-row-gap-lg: 20px;
  --tb-grid-column-gap-xl: min(20px, 8%);
  --tb-grid-row-gap-xl: 20px;
  --tb-grid-column-gap-xxl: min(20px, 8%);
  --tb-grid-row-gap-xxl: 20px;
}
```

## What limitations does `tb-grid` have?

- It doesn't support old browsers (IE): https://caniuse.com/?search=grid, https://caniuse.com/?search=css%20custom%20properties . 95% of people are using browsers that support CSS grid and CSS custom properties (variables) as of April 2021. It's up to you to decide whether this is sufficient for your project.
- If the `column-gap` is a fixed value it starts to overflow when the `tb-grid` parent reaches the size of `column_gap * 12`. For example, a `column_gap` of `30px` becomes problematic when the `tb-grid` parent is `360px`. That's why the defaults use `min(..., 8%)`, to squish the gutters when it gets too tight.

## What's the status of the project?

- Initial prototype is working well, see demo below
- We are planning to replace Bootstrap with `ts-grid` in our own codebase
- We would be thrilled to hear your opinions & suggestions on this small project! Why don't you just give it a spin and let us know what you think?

[license]:LICENSE
[license img]:https://img.shields.io/badge/license-MIT-blue.svg

