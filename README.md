#CSS Media Query Cheat Sheet and Live Demo

First, visit the [Live Demo](http://andrelion.github.io/mediaquery/livedemo.html) page.

##Media features

Most media features can be prefixed with "min-" or "max-" to express "greater or equal to" or "less than or equal to" constraints.  This avoids using the "<" and ">" symbols, which would conflict with HTML and XML.  If you use a media feature without specifying a value, the expression resolves to true if the feature's value is non-zero.

>Note: If a media feature doesn't apply to the device on which the browser is running, expressions involving that media feature are always false.  For example, querying the aspect ratio of an aural device always results in false.

###color
* **Value**: *color*
* **Media**: visual
* **Accepts min/max prefixes**: yes

Indicates the number of bits per color component of the output device.  If the device is not a color device, this value is zero.

>Note: If the color components have different numbers of bits per color component, the smallest number is used.  For example, if a display uses 5 bits for blue and red and 6 bits for green, then the device is considered to use 5 bits per color component.  If the device uses indexed colors, the minimum number of bits per color component in the color table is used.

Examples

To apply a style sheet to all color devices:

```
@media all and (color) { ... }
```

To apply a style sheet to devices with at least 4 bits per color component:

```
@media all and (min-color: 4) { ... }
```

###color-index

* **Value**: *integer*
* **Media**: visual
* **Accepts min/max prefixes**: yes

Indicates the number of entries in the color look-up table for the output device.

Examples

To indicate that a style sheet should apply to all devices using indexed color, you can do:

```
@media all and (color-index) { ... }
```

To apply a style sheet to indexed color devices with at least 256 colors:

```
<link rel="stylesheet" media="all and (min-color-index: 256)" href="http://foo.bar.com/stylesheet.css" />
```

###aspect-ratio

* **Value**: *ratio*
* **Media**: visual, tactile
* **Accepts min/max prefixes**: yes

Describes the aspect ratio of the targeted display area of the output device.  This value consists of two positive integers separated by a slash ("/") character.  This represents the ratio of horizontal pixels (first term) to vertical pixels (second term).

Example

The following selects a special style sheet to use for when the display area is at least as wide as it is high.

```
@media screen and (min-aspect-ratio: 1/1) { ... }
```

This selects the style when the aspect ratio is either 1:1 or greater. In other words, these styles will only be applied when the viewing area is square or landscape.

###device-aspect-ratio

* **Value**: *ratio*
* **Media**: visual, tactile
* **Accepts min/max prefixes**: yes

Describes the aspect ratio of the output device.  This value consists of two positive integers separated by a slash ("/") character.  This represents the ratio of horizontal pixels (first term) to vertical pixels (second term).

Example

The following selects a special style sheet to use for widescreen displays.

```
@media screen and (device-aspect-ratio: 16/9), screen and (device-aspect-ratio: 16/10) { ... }
```

This selects the style when the aspect ratio is either 16:9 or 16:10.

###device-height

* **Value**: *length*
* **Media**: visual, tactile
* **Accepts min/max prefixes**: yes

Describes the height of the output device (meaning the entire screen or page, rather than just the rendering area, such as the document window).

Example

To apply a style sheet to a document when displayed on a screen that is less than 800 pixels wide, you can use this:

```
<link rel="stylesheet" media="screen and (max-device-width: 799px)" />
```

###device-width

* **Value**: *length*
* **Media**: visual, tactile
* **Accepts min/max prefixes**: yes

Describes the width of the output device (meaning the entire screen or page, rather than just the rendering area, such as the document window).

###grid

* **Value**: *integer*
* **Media**: all
* **Accepts min/max prefixes**: no

Determines whether the output device is a grid device or a bitmap device.  If the device is grid-based (such as a TTY terminal or a phone display with only one font), the value is 1.  Otherwise it is zero.

Example

To apply a style to handheld devices with a 15-character or narrower display:

```
@media handheld and (grid) and (max-width: 15em) { ... }
```

>Note: The "em" unit has a special meaning for grid devices; since the exact width of an "em" can't be determined, 1em is assumed to be the width of one grid cell horizontally, and the height of one cell vertically.

###height

* **Value**: *length*
* **Media**: visual, tactile
* **Accepts min/max prefixes**: yes

The height media feature describes the height of the output device's rendering surface (such as the height of the viewport or of the page box on a printer).

>Note: As the user resizes the window, Firefox switches style sheets as appropriate based on media queries using the width and height media features.

###monochrome

* **Value**: *integer*
* **Media**: visual
* **Accepts min/max prefixes**: yes

Indicates the number of bits per pixel on a monochrome (greyscale) device.  If the device isn't monochrome, the device's value is 0.

Examples

To apply a style sheet to all monochrome devices:

```
@media all and (monochrome) { ... }
```

To apply a style sheet to monochrome devices with at least 8 bits per pixel:

```
@media all and (min-monochrome: 8) { ... }
```

###orientation

* **Value**: landscape | portrait
* **Media**: visual
* **Accepts min/max prefixes**: no

Indicates whether the device is in landscape (the display is wider than it is tall) or portrait (the display is taller than it is wide) mode.

Example

To apply a style sheet only in portrait orientation:

```
@media all and (orientation: portrait) { ... }
```

###resolution

* **Value**: *resolution*
* **Media**: bitmap
* **Accepts min/max prefixes**: yes

Indicates the resolution (pixel density) of the output device.  The resolution may be specified in either dots per inch (dpi) or dots per centimeter (dpcm).

Example

To apply a style sheet to devices with at least 300 dots per inch of resolution:

```
@media print and (min-resolution: 300dpi) { ... }
```

###scan

* **Value**: progressive | interlace
* **Media**: tv
* **Accepts min/max prefixes**: no

Describes the scanning process of television output devices.

Example

To apply a style sheet only to progressive scanning televisions:

```
@media tv and (scan: progressive) { ... }
```

###width

* **Value**: *length*
* **Media**: visual, tactile
* **Accepts min/max prefixes**: yes

The width media feature describes the width of the rendering surface of the output device (such as the width of the document window, or the width of the page box on a printer).

>Note: As the user resizes the window, Firefox switches style sheets as appropriate based on media queries using the width and height media features.

Examples

If you want to specify a style sheet for handheld devices, or screen devices with a width greater than 20em, you can use this query:

```
@media handheld and (min-width: 20em), screen and (min-width: 20em) { ... }
```

This media query specifies a style sheet that applies to printed media wider than 8.5 inches:

```
<link rel="stylesheet" media="print and (min-width: 8.5in) href="http://foo.com/mystyle.css" />
```

This query specifies a style sheet that is usable when the viewport is between 500 and 800 pixels wide:

```
@media screen and (min-width: 500px) and (max-width: 800px) { ... }
```
