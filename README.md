# Grid-System

## Wrappers

Wrappers are **required when using our default grid system**.
In general, you may only need 2 `.wrapper` classes only:

- On the element that will hold all of your page content(either on the <body> element or in a parent <div> element).
- On the <main> element if you are using semantic HTML tags(and I think you are).

Wrappers are used to contain, pad, and position the content within them using the power of CSS Grid.

```html
<body class="wrapper">
  <header></header>

  <main class="wrapper">
    <section class="hero | row"></section>
    <section class="about | row"></section>
    <section class="cta | row"></section>
  </main>

  <footer></footer>
</body>
```

```html
<body>
  <div class="wrapper">
    <header></header>

    <main class="wrapper">
      <section class="hero | row"></section>
      <section class="about | row"></section>
      <section class="cta | row"></section>
    </main>

    <footer></footer>
  </div>
</body>
```

You will find a set of custom properties used for a `.wrapper`:

- `--col-count`: Number of our grid system columns
- `--content-max-width`: Maximum width of the content area (same as `max-width` applied to classic `.container`)
- `--min-inline-gutter`: An inline gutter to space out the content (same as `padding-inline` applied to classic `.container`)
- `--content-col-width`: Width of a single column

## Rows

- Use `.row` class to have a row with 12 columns
- Direct children of a `.wrapper` will be full-width by default (starting at column 1 and ending at column -1) but you can easily change that using the `--cols-start` property or utility modifiers like: `.breakout`, `.breakout-start`, `.breakout-end` and `.content`.
- Direct children of a `.wrapper` will have by default an inline padding to center its content in the `content` area of the main wrapper, this is done by using a `--row-inline-gutter` property that you can override easily using modifiers: `.no-gutter`, `.no-start-gutter` and `.no-end-gutter` or just setting a custom `padding-inline`
- You can modify the content area width for wrappers and their direct children using utility classes: `.cols-sm`, `.cols-md`, ... (same as `.container-sm`, `.container-md`, ...)
- Use `.row-cols-*` classes to quickly set the number of columns directly from the parent `.row` as a shortcut.
- Gaps between columns are maintained using a `--gap`, `--gap-row` and `--gap-col` properties.
- You can have nested rows as much as you want

```html
<section class="cards | row cols-3">
  <div></div>
  <div></div>
  <div></div>
</section>
```

## Columns

- There are 12 template columns per row, by default
- You can create different combinations of elements that span any number of columns
- Use `.col-*` classes to set the number of template columns to span
- Setting a column width is mainly done using a `--col-total-width` property
- `--col-size` property is used to easily offseting columns: it represents a single column width added to a column gap
- For columns offsets, `--offset-start` and `--offset-end` properties are used

```html
<section class="cards | row">
  <div class="col-7"></div>
  <div class="col-3"></div>
  <div class="col-2"></div>
</section>
```

```html
<section class="cards | row">
  <div class="col-6 offset-end-1"></div>
  <div class="col-3"></div>
  <div class="col-2"></div>
</section>
```
## Responsive Classes
- Our grid is mobile-first and supports 5 responsive breakpoints: `sm`, `md`, `lg`, `xl` and `xxl`
- Breakpoints are based on min-width media queries, meaning they affect that breakpoint and all those above it (e.g., .sm-col-2 applies to sm, md, lg, xl, and xxl). This means you can control container and column sizing and behavior by each breakpoint.

## Custom Properties
- To make it more flexible and maintainable, we use custom properties to define almost every paramter for our grid: rows starts, columns widths, gaps, offsets, so feel free to either use utility classes or updating custom properties in your CSS custom file