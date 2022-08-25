# InfoMapper / Dashboard / Data Formatting #

# Introduction #



## Data Formats ##

The Selector widget can read in different types of data. This section describes
what needs to be done for the selector to correctly retrieve the data for displaying
not just in this widget, but for consumption in others.

### CSV ###

Here are the main points to keep in mind when attempting to read CSV data into
the Selector widget.

#### Comments ####

Comments are allowed in CSV files and is determined to be a `#` at the beginning
of a line. This might be configurable later so other comment characters can be used.

#### Headers ####

The Selector widget assumes the data will have headers, which can be used as ${}
properties elsewhere in the configuration widget object.

#### Multiple headers & metadata ####

Some web services (e.g. CDSS) return CSV data with two header rows: one for metadata
and one for the main data. This confuses the CSV reader in the Selector widget,
and will incorrectly assign the metadata headers as the main headers.

In cases like this, some lines of actual, non-commented data need to be skipped.
This is when the Selector widget's `skipDataLines` property comes in. Setting it
to `x` will skip the first x lines of data, resolving this issue.

### geoJSON ###

Any correctly made geoJSON ([RFC 7946](https://datatracker.ietf.org/doc/html/rfc7946))
following the right hand rule can be used by the Selector widget. For more information
on the right hand rule and for fixing any old geoJSON files, visit
[Mapster's geoJSON fixer](https://mapster.me/right-hand-rule-geojson-fixer/).

### JSON ###

For now, the Selector widget only reads one type of JSON data: A named array JSON
object. A simple example would look like the following:

```json
{
  "propertyName": "value",
  "desiredResults": [
    {
      "propertyName": "value"
    }
  ]
}
```

The `JSONArrayName` property must be used if reading JSON data, but will most likely
change in updated versions. It should be given the name of the array in the JSON
object, so for the above example, `namedArray`.