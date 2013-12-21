# Simple plotting

A simple script for creating plots from the command line.  Behaves appropriately when either passed functions as arguments or lists of points from standard in.  This script requires the [NumPy][1] and [matplotlib][2] modules.

The graphs produced aren't intended to be of publication quality. The goal is to make readable graphs very quickly.

## Functions (Arguments)

For these, everything is given on the command line.

    simplot 'function(s)' minx maxx [miny maxy]

Three arguments are required: the function itself, which would normally be enclosed in quotes to avoid problems with shell interpretation; the minimum x value; and the maximum x value. The last two arguments, the minimum and maximum y values are optional—if they aren't given, the script will figure them out. A common reason to specify the y limits is if the function "blows up" between the x limits and the extreme y values make the rest of the graph look flat.

The function can include any Python expression or function, including those in the NumPy library. There's no need to use a `numpy` prefix. 

More than one function can be specified; separate them with a semicolon. Thus, something like

    simplot 'tan(x); x' pi 3*pi/2-.01 0 5

can be used to find the intersection of the two given functions. This example also shows that you can use expressions in the limits.

The result of `simplot` is an 800×600 PNG image titled `out.png` in the calling directory.  No controls for tick marks or grid spacing are provided—this is quick and dirty plotting.

<img src="http://farm8.staticflickr.com/7449/11444287224_fdf3652083.jpg" alt="Two-function plot" title="Two-function plot" />

## Points (Standard In)

The script that plots lists of points, `simplot`, gets its data from standard input. On the Mac, it would be common to pass data in from the clipboard this way:

    pbpaste | simplot

Each line of the input data represents one (x, y) point. The x and y values can be separated by tabs, spaces, or commas.

Normally, `simplot` plots the points only. If you want to connect the points with a line, use the `-l` option:

    pbpaste | simplot -l


[1]: http://www.numpy.org/
[2]: http://matplotlib.org/
