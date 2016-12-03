# Puzzle Grid

v.1.3.0

[![Code Climate](https://codeclimate.com/github/puzzalea/grid/badges/gpa.svg)](https://codeclimate.com/github/puzzalea/grid)

Just another CSS grid.

## Introduction

Puzzle Grid is a responsive flexbox grid created by [Puzzalea](https://github.com/puzzalea) (a.k.a. [caraheacock](https://github.com/caraheacock/)).

I made this grid because I didn't like the other grids. I wanted a flexible grid that was JUST a grid (no other utility classes) and used flexbox. I designed Puzzle Grid with flexibility in mind; many class names, breakpoints, etc. are customizable. You can even change the number of columns if you need to.

## Setup

### Quick Setup

1. Copy the contents of `css/puzzle-grid.min.css` to your project.
2. Go forth and make 12 column layouts.

### Custom Setup

Puzzle Grid was generated using SASS. It was coded to be extremely flexible and can be adapted to any number of columns and any breakpoints.

1. Copy the files in the  `scss` directory to your project.
2. Adjust variables in the `_variables` partial to your needs. There is no need to edit the `_grid` partial. The `puzzle-grid.scss` file indicates to order you will need to include the partials. In the `_variables` partial, you can change:
  - `$pz-grid-prefix` - String, the framework prefix. By default the prefix is an empty string, but if you think Puzzle Grid's classees will conflict with your styles or other frameworks, you can add a prefix. For example, if you change it to `pz-`, all Puzzle Grid classes will start with `pz-`, such as `pz-row`, `pz-col`, `pz-xs-12`, etc.
  - `$pz-grid-sizes` - SASS map, sizes/breakpoints for generating grid classes. The keys are the names of the breakpoints, and the values are the breakpoint size. Make more sizes, make less sizes, change the sizes, etc. I would advise having at least one "start" breakpoint set to `0` as the base of your grid (by default, this key is `xs`), and order them from smallest to largest for best mobile-first results.
  - `$pz-grid-max-width` - String, max width of rows.
  - `$pz-grid-col-num` - Integer, number of columns. By default you have a 12 column grid, but you can change it to whatever you like. Make a 37 column grid, go nuts.
  - `$pz-grid-miscellaneous-widths` - SASS map, miscellaneous column widths. Are your designers silly and say things like, "Oh, yeah, I'll design this in a 12 column grid," and then they put 5 things in a row? ¯\\\_(ツ)_/¯ No need to worry, Puzzle Grid offers the ability to create arbitrary classes.
  - `$pz-grid-col-inner-top-bottom-margin`, `$pz-grid-col-inner-left-right-margin`, and `$pz-grid-col-inner-padding` - SASS maps, `col-inner` class margin and padding. You can adjust the margin and padding at various breakpoints for this class. The keys in this map must be present in the `$pz-grid-sizes` map. The values for the `$pz-grid-col-inner-padding` map can be any valid values for the margin and padding CSS properties (e.g. `10px`, `0 15px`, `1rem 2rem`, `5px 10px 15px 0`, etc.). The values for the `$pz-grid-col-inner-top-bottom-margin` and `$pz-grid-col-inner-left-right-margin` must be single units (e.g. `10px`, `1rem`, etc.) due to SASS math performed on these values.
3. Either compile `puzzle-grid.scss` as-is, or include the `_variables` and `_grid` partials in your SCSS in that order and compile them with the rest of your styles.

## How to Use

This documentation uses the default number of columns and breakpoints as examples, but these can be adjusted using the Custom Setup directions above.

### Sizes

Puzzle Grid's classes contain the size they take effect and how many columns they span across or push left and right. Sizes currently include:

- `xs` - extra small, which works at all sizes
- `sm` - small, 480px
- `md` - medium, 660px
- `lg` - large, 850px
- `xl` - extra large, 1024px

To use these classes, with the except of classes for hiding and showing, divs MUST have the class `.col` and be direct children of a div with the class `.row`. The `.row` container is a flex container, and the `.col` divs inside employ flexbox to change size.

### Widths

The most basic usage of the grid system is to determine how wide a div will be at certain widths.

- For example, `.xs-12` means the affected div will be full width. `.xs-6` means the affected div will be 6 columns wide, or half width.
- A `.col` with the chained classes `.xs-12.md-4` will be full width to start, and shrink to 4 columns wide (one third width) at the medium size.
- A `.col` with the chained classes `.xs-6.xl-8` will be 6 columns to start, and will grow to 8 columns wide at the extra large width.

It is also important to note that these classes are meant to be used mobile-first, which is why `xs` is the start size and can be overridden as the screen becomes larger.

For edge cases where you might not always be working in strictly a 12 column grid, there are additional classes that divide into fifths (one-fifth, two-fifths, three-fifths, and four-fifths) and eighths (one-eighth, three-eighths, five-eighths, and seven-eighths).

- A `.col` with the class `.xs-one-fifth` will be 20% wide.
- A `.col` with the class `.xs-three-eighths` will be 37.5% wide.

### Pushing

We also have classes for pushing.

- `.sm-left-2` means there are 2 empty columns to the left of the `.col` at the small size (pushing the `.col` itself to the right).
- `.lg-right4` means there are 4 empty columns to the right of the affected div at the large size, which will push over any content immediately following.

### Centering

If you only have one `.col` in a `.row`, you can use the center and uncenter classes.

- `.sm-center` means the div will be centered at the small width.
- A div with the chained classes `.xs-center.lg-uncenter` means the div will be centered at the beginning but will uncenter (align left) at the large width.

### Filling

You can use the fill class to have a `.col` fill the remaining space. This is handy if you want a `.col` to fill the remaining space in a `.row `regardless of the size of other elements.

- `.xs-fill` means the `.col` will fill the remaining space in a `.row`.
- A `.col` with the chained classes `.xs-fill.lg-unfill` means the div will fill the remaining space to start, and will revert to its automatic size at the large width.

### Show/Hide

We have utility classes for hiding and showing, which do NOT have to be used strictly on divs with the class `.col`.

- An element with the classes `.xs-hide.lg-show` will be hidden to start and will appear at the large width.

### Spacing

There is a utility class called `.col-inner` which is added as needed for inner margin/padding. Margin/padding is not directly applied to `.col` divs (except left and right pushes) to allow us to nest `.row`s and `.col`s within `.row`s and `.col`s if needed, without chaining the effects of margin and padding.

## Questions? Comments?

Make an issue if you need anything. ✧･ﾟ:*╰(◕‿◕｡╰)
