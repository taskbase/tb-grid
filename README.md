# tb-grid

<img width="805" alt="Screenshot 2021-04-29 at 23 17 07 " src="https://user-images.githubusercontent.com/10352805/116619655-07936280-a941-11eb-921b-0da6cc9001af.png">


## Why `tb-grid`?

Bootstrap is well known for its grid system. However, introducing an extra library into your project for something that could be achieved with a couple lines of code seems like overkill. And even though you can use bootstrap in a modular fashion, it will confuse your devs that you only use the grid system of bootstrap. Furthermore it has some design flaws:
- Annoying layers of nesting: Why do you need to wrap the stuff in a container? I think that stems from legacy when there was no css grid.
- no scoping: a prefix would have been much appreciated instead of just using `.container`...

## What is `tb-grid`?

`tb-grid` is a reverse engineered bootstrap 12 column grid with **modern css**. This means it's utilizing features such as css variables and css grid. This means we can write the entire bootstrap column system in less than 100 lines of scss.

Here it goes:

```
$breakpoints: (
  "sm": 600px,
  "md": 800px,
  "lg": 1000px
);

.tb-grid {
  display: grid;
  column-gap: 15px;
  row-gap: 15px;
  grid-template-columns: repeat(12, 1fr);
  > * {
    grid-column-start: span 12;
  }
  @each $breakpoint-name, $breakpoint-value in $breakpoints {
    @media (min-width: #{$breakpoint-value}) {
      @for $i from 1 through 12 {
        .tb-#{$breakpoint-name}-#{$i} {
          grid-column-start: span #{$i};
        }
      }
    }
  }
}
```

## Usage
```
<div class="tb-grid">
  <div class="tb-sm-6">
    Item 1
  </div>
  <div class="tb-sm-6">
    Item 2
  </div>
  <div class="tb-sm-4 tb-lg-6">
    Item 3
  </div>
  <div class="tb-sm-8 tb-lg-6">
    Item 4
  </div>
</div>
```

## Demo
https://jsfiddle.net/bersling/af07cw94/275/

