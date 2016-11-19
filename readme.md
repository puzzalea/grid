# Puzzle Grid

#### Just another CSS grid.


## Introduction

Puzzle Grid is a responsive flexbox grid by [Puzzalea](https://github.com/puzzalea) (a.k.a. [caraheacock](https://github.com/caraheacock/)).

I made this grid because I didn't like the other grids. I wanted a flexible grid that was JUST a grid (no other utility classes) and used flexbox. I designed Puzzle Grid with flexibility in mind; many class names, breakpoints, etc. are customizable. You can even change the number of columns if you need to.

## Setup

### Quick Setup

1. Copy the contents of `css/puzzle-grid.min.css` to your project.
2. Go forth and make 12 column layouts.

### Custom Setup

Puzzle Grid was generated using SASS. It was coded to be extremely flexible and can be adapted to any number of columns and any breakpoints.

1. Copy the files in the  `scss` directory to your project.
2. Adjust variables in the `_variables` partial to your needs. There is no need to edit the `_mixins` or `_grid` partials. The `puzzle-grid.scss` file indicates to order you will need to include the partials. In the `_variables` partial, you can change:
  - **The framework prefix** - Maybe you don't need a prefix, just change it to an empty string. Maybe you want to use your own project prefix, idc.
  - **Sizes/breakpoints** - Make more sizes, make less sizes, change the breakpoints, etc. I would advise having at least one "start" breakpoint set to `0` as the base of your grid (by default, this is `xs`).
  - **Number of columns** - By default you have a 12 column grid, but you can change it to whatever you like. Make a 37 column grid, go nuts.
  - **Miscellaneous classes** - Are your designers silly and say things like, "Oh, yeah, I'll design this in a 12 column grid," and then they put 5 things in a row? ¯\\\_(ツ)_/¯ No need to worry, Puzzle Grid offers the ability to create arbitrary classes.
3. Either compile `puzzle-grid.scss` as-is, or include the `_variables`, `_mixins`, and `_grid` partials in your SCSS in that order and compile them with the rest of your styles.

## How to Use

This documentation uses the default number of columns and breakpoints as examples, but these can be adjusted using the Custom Setup directions above.

Puzzle Grid's classes contain the size they take effect and how many columns they span across or push left and right. Sizes currently include "xs" (extra small, which works at all sizes), "sm" (small), "md" (medium), "lg" (large), and "xl" (extra large).

To use these classes, with the except of classes for hiding and showing, divs MUST have the class ".col" and be direct children of a div with the class ".pz-row". The .pz-row container is a flex container, and the .col divs inside employ flexbox to change size.

The most basic usage of the grid system is to determine how wide a div will be at certain widths.

- For example, .xs-12 means the affected div will be full width. .xs-6 means the affected div will be 6 columns wide, or half width.
- A .col with the chained classes .xs-12.md-4 will be full width to start, and shrink to 4 columns wide (one third width) at the medium size.
- A .col with the chained classes .xs-6.xl-8 will be 6 columns to start, and will .pz-row to 8 columns wide at the extra large width.

It is also important to note that these classes are meant to be used mobile-first, which is why "xs" is the start size and can be overridden as the screen becomes larger.

For edge cases where you might not always be working in strictly a 12 column grid, there are additional classes that divide into fifths (one-fifth, two-fifths, three-fifths, and four-fifths) and eighths (one-eighth, three-eighths, five-eighths, and seven-eighths).

- A .col with the class .xs-one-fifth will be 20% wide.
- A .col with the class .xs-three-eighths will be 37.5% wide.

We also have classes for pushing.

- .sm-left-2 means there are 2 empty columns to the left of the .col at the small size (pushing the .col itself to the right).
- .lg-right4 means there are 4 empty columns to the right of the affected div at the large size, which will push over any content immediately following.

If you only have one .col in a .pz-row, you can use the center and uncenter classes.

- .sm-center means the div will be centered at the small width.
- A div with the chained classes .xs-center.lg-uncenter means the div will be centered at the beginning but will uncenter (align left) at the large width.

You can use the fill class to have a .col fill the remaining space. This is handy if you want a .col to fill the remaining space in a.pz-row regardless of the size of other elements.

- .xs-fill means the .col will .pz-row to fill the remaining space in a .pz-row.
- A .col with the chainined classes .xs-fill.lg-unfill means the div will fill the remaining space to start, and will revert to its automatic size at the large width.

We have utility classes for hiding and showing, which do NOT have to be used strictly on divs with the class ".col".

- An element with the classes .xs-hide.lg-show will be hidden to start and will appear at the large width.

Lastly, there is a utility class called .col-inner which is added as needed for inner margin/padding. Margin/padding is not directly applied to .col divs (except left and right pushes) to allow us to nest.pz-rows and columns within.pz-rows and columns if needed, without chaining the effects of margin and padding.

## Questions? Comments?

Make an issue if you need anything. ✧･ﾟ:*╰(◕‿◕｡╰)
