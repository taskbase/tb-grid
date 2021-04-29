# tb-grid


## Why `tb-grid`?

Bootstrap is well known for its grid system. However, introducing an extra library into your project for something that could be achieved with a couple lines of code seems like overkill. And even though you can use bootstrap in a modular fashion, it will confuse your devs that you only use the grid system of bootstrap. Furthermore it has some design flaws:
- Annoying layers of nesting: Why do you need to wrap the stuff in a container? I think that stems from legacy when there was no css grid.
- no scoping: a prefix would have been much appreciated instead of just using `.container`...

## What is `tb-grid`?

`tb-grid` is a reverse engineered bootstrap 12 column grid with **modern css**. This means it's utilizing features such as css variables and css grid. This means we can write the entire bootstrap column system in less than 100 lines of scss.

## How can I install `tb-grid`?

Option 1 (SCSS): Copy the code from `tb-grid.scss` to your project.

Option 2 (CSS): Copy the code from `tb-grid.css` to your project.

Option 3 npm: `npm install tb-grid` and include the scss or css file from there.

Option 4 (CSS): Include the css through a css import by pointing it to the github raw file. This won't be optimal as it's not minified and can't be bundled together with your code.

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

## Demo
https://jsfiddle.net/bersling/af07cw94/275/

