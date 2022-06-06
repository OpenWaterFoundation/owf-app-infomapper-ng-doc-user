# InfoMapper / Classification File #

Classification files are CSV files that are used to help style and display
different elements in an InfoMapper application by conditionally checking
data values.

* [Introduction](#introduction)

## Introduction ##

Classification files can be used in multiple places in an InfoMapper app:

* Categorized or graduated Map layers.
* [Status Indicator widget](../appendix-adding-a-dashboard/widget-status-indicator.md)

The following is an example of a classification file with headers:

```csv
# The value from attribute is compared as follows to determine symbol:
#  value > valueMin
#  value <= valueMax
valueMin,valueMax,color,opacity,fillColor,fillOpacity,weight,label,level
-Infinity,<-4.2,#ffffff,0.0,#fffffff,1.00,1,Unknown,black
>=-4.2,<-3.0,#fd0017,0.0,#fd0017,0.35,1,Extremely Dry,red
>=-3.0,<-2.0,#fda824,0.0,#fda824,0.35,1,Moderately Dry,yellow
>=-2.0,<-1.0,#fed283,0.0,#fed283,0.35,1,Slightly Dry,yellow
>=-1.0,<1.0,#ffffc0,0.0,#ffffc0,0.35,1,Near Average,green
>=1.0,<2.0,#d2e8fe,0.0,#d2e8fe,0.35,1,Slightly Wet,green
>=2.0,<3.0,#f8e1fe,0.0,#f8e1fe,0.35,1,Moderately Wet,green
>=3.0,Infinity,#1471fc,0.0,#1471fc,0.35,1,Extremely Wet,green
```

Classification files have been created in an agnostic way so that one classification
file can be used by multiple elements (e.g. a graduated map layer in a map and two
status indicator widgets from a few dashboards). Each will use the rows and columns
they care about and ignore the rest. This way the amount of files used can be decreased.

## Map Layer example ##

**To be finished.**

## Status Indicator widget ##

To use the classification file with a Status Indicator widget, add the path to the
classification file in the `classificationFile` widget property in a dashboard configuration
file. More information can be found in the [Status Indicator Widget](../appendix-adding-a-dashboard/widget-status-indicator.md) documentation.

The only three columns used by the Status Indicator are `valueMin`, `valueMax`, and
`level`. Any other column name, including those from the example above can exist; they
will simply be ignored. The values are used to determine where a data point falls
between, and the level is the color to be displayed for the data point. The supported
value for each are as follows:

### `valueMin` & `valueMax` ###

* `-Infinity` - Used for any number less than the smallest provided number.
* Any real number
* `Infinity` - Used for any number greater than the largest provided number.

### `level` ###

* `black` - No data.
* `red` - Failing.
* `yellow` - Warning.
* `green` - Passing.