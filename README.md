# Presentation

Hello, my name is Artyom. In this presentation I will talk about such a module of CSS as a Grid.

<!--  Slide 1 CSS GRID LAYOUT (AKA “GRID”) -->
Start by defining. This CSS module defines a two-dimensional grid-based layout system, optimized for user interface design. In the grid layout model, the children of a grid container can be positioned into arbitrary slots in a predefined flexible or fixed-size layout grid. if you compare with flex boxing, Flexbox is for one-dimensional layouts - anything that needs to be laid out in a straight line (or in a broken line, which would be a single straight line if they were joined back together).

Grid is for two-dimensional layouts.  It can be used as a low-powered
flexbox substitute (we're trying to make sure that a single-column/row
grid acts very similar to a flexbox), but that's not using its full
power.

Flexbox is appropriate for many layouts, and a lot of "page component"
elements, as most of them are fundamentally linear.  Grid is
appropriate for overall page layout, and for complicated page
components which aren't linear in their design.

<!--  Slide 2 BROWSER SUPPORT -->
As we can see, this module is supported by all modern browsers.

<!--  Slide 3 Terminology -->
Before we dive into the concept of Grid, it is important to understand its terminology. Since the terms used here are conceptually similar, they are fairly easy to confuse with each other unless you remember their meanings as defined in the specification from the very beginning.

 - Grid container - set of intersecting horizontal and vertical grid lines that divide the container grid space into grid areas into which grid elements can be placed.

 - Grid lines - The vertical and horizontal lines that divide the grid and separate the columns and rows.

 - Grid cell - A single unit of a CSS grid.

 - Grid area - Rectangular space surrounded by four grid lines. A grid area can contain any number of grid cells.

 - Grid track - The space between two grid lines. This space can be horizontal or vertical.

 - Grid row - A horizontal track of a grid.

 - Grid column - A vertical track of a grid.

<!-- Slide 4 GRID CONTAINER -->
To get started, we need to create a grid-container, thereby setting the formatting context to the grid type, which affects only the children of the grid.

Values:
 - grid - forms a grid as a block;
 - inline-grid - forms a grid as an inline block;
 - subgrid - if your container is also an element (nested grid), then you can use this property to indicate that the sizes of the rows / columns are taken from the parent element, and not define your own;

<!-- Slide 5 EXPLICIT GRID -->
When you create a container grid, the grid by default has one column and one row, which occupy the full size of the container. The grid-template-columns, grid-template-rows and grid-template-areas properties are used to separate the grid container into columns and rows. Using these properties, you can define the grid explicitly.

In the first image A row track is created for each value specified for grid-template-rows. Track size values can be any non-negative, length value (px, %, em, etc.)
Items 1 and 2 have fixed heights of 50px and 100px.
Because only 2 row tracks were defined, heights of items 3 and 4 are defined by the contents of each.

Like rows, a column track is created for each value specified for grid-template-columns.
In the second image items 4, 5 and 6 were placed on a new row track because only 3 column track sizes were defined; and because they were placed in column tracks 1, 2 and 3, their column sizes are equal to items 1, 2 and 3.
Grid items 1, 2 and 3 have fixed widths of 90px, 50px and 120px respectively.

The fr unit helps create flexible grid tracks. It represents a fraction of the available space in the grid container (works like Flexbox’s unitless values).
In the third image, items 1 and 2 take up the first two (of four) sections while item 3 takes up the last two.

fr is calculated based on the remaining space when combined with other length values.
In this example, 3rem and 25% would be subtracted from the available space before the size of fr is calculated, as shown in the last image.

<!-- Slide 6 MINIMUM AND MAXIMUM GRID TRACK SIZES -->
Tracks sizes can be defined to have a minimum and/or maximum size with the minmax() function.
The minmax() function accepts 2 arguments: the first is the minimum size of the track and the second the maximum size. Alongside length values, the values can also be auto, which allows the track to grow/stretch based on the size of the content.
In this example, the first row track is set to have a minimum height of 100px, but its maximum size of auto will allow the row track to grow it the content is taller than 100px.
The first column track has a minimum size of auto, but its maximum size of 50% will prevent it from getting no wider than 50% of the grid container width.

<!-- Slide 7 REPEATING GRID TRACKS -->
Define repeating grid tracks using the repeat() notation. This is useful for grids with items with equal sizes or many items.
The repeat() notation accepts 2 arguments: the first represents the number of times the defined tracks should repeat, and the second is the track definition.

repeat() can also be used within track listings.
In the second image, the first and last column tracks have widths of 30px, and the 3 column tracks in between, created by repeat(), have widths of 1fr each.

<!-- Slide 8 GRID GAPS (GUTTERS) -->
The grid-column-gap and grid-row-gap properties create gutters between columns and rows. Grid gaps are only created in between columns and rows, and not along the edge of the grid container.
1.	Gap size values can be any non-negative, length value (px, %, em, etc.)
2.	grid-gap is shorthand for grid-row-gap and grid-column-gap. If two values are specified, the first represents grid-row-gap and the second grid-column-gap.
3.	One value sets equal row and column gaps.

<!-- Slide 9 POSITIONING ITEMS BY GRID LINE NUMBERS -->
Grid lines are essentially lines that represent the start of, the end of, or between column and row tracks.
Each line, starting from the start of the track and in the direction of the grid, is numbered incrementally starting from 1.

1. In the first image 2-column by 3-row grid results in 3 column lines and 4 row lines. Item 1 was repositioned by row and column line numbers.
If an item spans only one row or column, grid-row/column-end is not necessary.

2.
 - grid-row is shorthand for grid-row-start and grid-row-end.
 - grid-column is shorthand for grid-column-start and grid-column-end.
 - If one value is provided, it specifies grid-row/column-start.
 - If two values are specified, the first value corresponds to grid-row/column-start and the second grid-row/column-end, and must be separated by a forward slash /.

3. grid-area is shorthand for grid-row-start, grid-column-start, grid-row-end and grid-column-end.
If four values are specified, the first corresponds to grid-row-start, the second grid-column-start, the third grid-row-end and the fourth grid-column-end.

<!-- Slide 10 SPANNING ITEMS ACROSS ROWS AND COLUMNS -->
Grid items span only one column and row track by default, but can span multiple row and/or column tracks using the same properties to position them.

1. Set a grid item to span more than one column track by setting grid-column-end to a column line number that is more than one column away from grid-column-start.
2. Grid items can also span across multiple row tracks by setting grid-row-end to more than one row track away.
3. Shorthand properties grid-row and grid-column can also be used to position and span grid items more than one row or column.
4. The keyword span, followed by the # of columns or rows to span, can also be used.

<!-- Slide 11 NAMING GRID LINES -->
Grid lines can be named when defining the grid with the grid-template-rows and grid-template-columns properties. Line names can then be referenced to position grid items.

1.	Assign names to grid lines when defining your grid with the grid-template-rows and grid-template-columns properties.
In line names, avoid keywords that appear in the specification (e.g. span) to not cause confusion.
Assigned line names must be wrapped in square brackets [name-of-line] and placed relative to the grid tracks.

2.	Multiple names can be assigned to grid lines by adding names within square brackets and separating each with a whitespace.
Each line name can then be referenced when positioning grid items by line names.

<!-- Slide 12 POSITIONING ITEMS BY LINE NAMES -->
With named grid lines, items can be positioned by line names and numbers.

1.	Referenced line names should not be wrapped in square brackets.

2.	grid-row and grid-column shorthand properties also support the use of grid line names when positioning items.

<!-- Slide 13 POSITIONING ITEMS BY LINE NAMES -->
Lines can be assigned the same name with the repeat() function. This can save you time from having to name each line in track definitions.

1.	Line name assignments can also be included within the repeat() function. This results in multiple grid lines with the same names. Lines with the same name are also assigned the a line’s position/name’s occurrence number, which allows it to be uniquely identified from another line with the same name.

2.	To position items by lines with the same name, reference the line’s name and position/name’s occurrence number—the name and number should be separated by a whitespace. In this example, item 1’s row position starts at the 2nd grid line named row-start and ends at the 3rd grid line named row-end; and its column position starts at the 1st grid line named col-start and ends at the 3rd grid line named col-start.

<!-- Slide 14 NAMING AND POSITIONING ITEMS BY GRID AREAS -->
Like grid line names, grid areas can also be named with the grid-template-areas property. Names can then be referenced to position grid items.

1.	Sets of names should be surrounded in single or double quotes, and each name separated by a whitespace.
Each set of names defines a row, and each name defines a column.
2.	Grid area names can be referenced by the same properties to position grid items: grid-row-start, grid-row-end, grid-column-start, and grid-column-end.
3.	The grid-row and grid-column shorthand properties can also reference grid area names.
4.	The grid-area shorthand property can also be used to reference grid area names.

<!-- Slide 15 Implicit Grid -->
An implicit grid is created when a grid needs to position items outside of the explicit grid because there isn’t enough space for items in the explicitly defined tracks or you decide to position something outside of the explicit grid. Those items are then auto-placed in the implicit grid.
The implicit grid can be defined using the grid-auto-rows, grid-auto-columns, and grid-auto-flow properties.

1.	In the first image we’ve only defined one row track, therefore grid items 1 and 2 are 70px tall.
A second row track was auto-created to make room for items 3 and 4. grid-auto-rows defines the row track sizes in the implicit grid, which is reflected by the the 140px heights of items 3 and 4.
2.	The default flow (direction) of a grid is row.
3.	A grid’s flow can be changed to column.
4.	In the last image, we’ve only defined the sizes of the first two column tracks—item 1 is 30px wide and item 2, 60px.
Column tracks are auto-created in the implicit grid to make room for items 3, 4 and 5; and track sizes are defined by grid-auto-columns

<!-- Slide 16 Implicitly Named Grid Areas -->
Grid lines can generally be named whatever you’d like, but assigning names ending in -start and -end comes with added benefits—they implicitly create named grid areas, which can be referenced for positioning.

In this example, both rows and columns have inner-start and inner-end lines, which implicitly assigns the grid area’s name as inner.
Grid items can then be positioned by the grid area name as opposed to line names.

<!-- Slide 17 Implicitly Named Grid Lines -->
Implicitly named grid lines work in reverse to implicitly named grid areas—naming grid areas implicitly assigns names to grid lines.

1.	Named grid areas will implicitly name the grid lines along the edges of the area. Those grid lines will be named based on the area name and suffixed with -start or -end.
2.	In the second image, the header was positioned using the implicit grid line names.

<!-- Slide 18 LAYERING GRID ITEMS -->
Grid items can be layered/stacked by properly positioning them and assigning z-index when necessary.

1.	In the first image, items 1 and 2 are positioned to start on row line 1 and set to span 2 columns.
Both items are positioned by grid line numbers. Item 1 is set to start at column line 1, and item 2 at column line 2, which results in both items overlapping in the center column track.
By default, item 2 would sit on top of item 1; however, we’ve created stacking context by assigning z-index: 1 to item 1, resulting it to sit on top of item 2.
2.	In the second image, a grid item is positioned and layered on top using implicit grid line names from the defined grid-template-areas.

<!-- Slide 18 LAYERING GRID ITEMS -->
CSS’s Box Alignment Module complements CSS Grid to allow items to be aligned along the row of column axis.
justify-items and justify-self align items along the row axis, and align-items and align-self align items along the column axis.
justify-items and align-items are applied to the grid container and support the following values:
•	auto
•	normal
•	start
•	end
•	center
•	stretch
•	baseline
•	first baseline
•	last baseline

On these slides you can see how each of the properties affects the position of the element.

<!-- Slide 19 INDIVIDUAL ITEMS (PROPERTIES) -->
Individual items can be self-aligned with the align-self and justify-self properties. These properties support the following valuse:
•	auto
•	normal
•	start
•	end
•	center
•	stretch
•	baseline
•	first baseline
•	last baseline

On these slides you can see how each of the properties affects the position of the element.

<!-- Slide 20 Aligning Grid Tracks -->
Grid tracks can be aligned relative to the grid container along the row and column axes.
align-content aligns tracks along the row axis and justify-content along the column axis. They support the following properties:
•	normal
•	start
•	end
•	center
•	stretch
•	space-around
•	space-between
•	space-evenly
•	baseline
•	first baseline
•	last baseline

On these slides you can see how each of the properties affects the position of the element.



In conclusion, I would like to say that the grid layout is an excellent method for placing and managing elements on the page, which opens up many possibilities. That's all I wanted to say. Thanks to all
