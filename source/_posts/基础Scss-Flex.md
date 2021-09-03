---
title: Scss练习-Flex
date: 2021-09-03 16:45:48
categories: Scss
---

```scss
@each $var in flex, grid, block, none {
  .#{$var} {
    display: #{$var};
  }
}

@each $item in center, start, end {
  .items-#{$item} {
    @if #{$item} == 'start' {
      align-items: flex-#{$item};
    } @else if #{$item} == 'end' {
      align-items: flex-#{$item};
    } @else {
      align-items: #{$item};
    }
  }
}

@each $var in row, row-reverse, col, col-reverse {
  .flex-#{$var} {
    @if #{$var} == 'col' {
      flex-direction: column;
    } @else if #{$var} == 'col-reverse' {
      flex-direction: column-reverse;
    } @else {
      flex-direction: #{$var};
    }
  }
}


@each $var in center, end, start, between, around, evenly {
  .justify-#{$var} {
    @if #{$var} == 'end' {
      justify-content: flex-end;
    } @else if #{$var} == 'start' {
      justify-content: flex-start;
    } @else if #{$var} == 'between' {
      justify-content: space-between;
    } @else if #{$var} == 'around' {
      justify-content: space-around;
    } @else if #{$var} == 'evenly' {
      justify-content: space-evenly;
    } @else {
      justify-content: #{$var};
    }
  }
}
```
