# InfoMapper / Visualizations / Gapminder #

## Introduction ##

The InfoMapper is using Trendalyzer as a visualization for data. Gapminder, and
more specifically Hans Rosling, created the Trendalyzer statistic software, being
called Gapminder here. It was made for animating statistics on an interactive bubble
chart so that data visualization could be user friendly and easy to use.

## Configuration ##

A JSON file is used to provide the InfoMapper with the necessary details to create
and display the Gapminder visualization, any annotations for the data, and other
information. Please note that this is a work in progress, and some configuration
properties might change or become deprecated in future releases. The following table
describes the properties and values that are utilized.

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default** |
| ---- | ---- | ---- |
| `AnnotationsFileName` | The absolute or relative path from the `DataFileName` path to the file containing annotations for the visualization. | `None` |
| `DataFileName`<br><b>required</b> | The absolute path to the file containing the data to be displayed in the Gapminder visualization. | `None - must be specified` |
| `DocFilePath` | The absolute or relative path from the `DataFileName` path to the HTML, Markdown, or regular text file containing text to be displayed in a Documentation Dialog. Enables the `Documentation` Dialog button. | `None` |
|  | **Visualization Display** |  |
| `BottomXAxisTitleString` | The visualization X axis title. | `None` |
| `InputDateFormat` | Formats the date on the visualization. |  |
| `LeftYAxisTitleString` | The visualization Y axis title. | `None` |
| `MainTitleString` | The visualization main title. | `None` |
| `OutputDateFormat` | Formats the date on the visualization. For more information, visit the <a href="https://github.com/d3/d3-time-format" target="_blank">D3 Time Format</a> Github page.  |  |
| `SubTitleString` | The visualization sub title string, displayed under the main string. | `None` |
|  | **Visualization Setup** |  |
| `AnimationSpeed` | Sets the visualization animation speed from `1` - `100`, `1` being the slowest and `100` the fastest. | `75` |
| `TimeStep`<br><b>required</b> | The visualization time increment string. E.g. `1Year`, `6months`, `1day`. | `1Year` |
| `VariableNames`<br><b>required</b> | Holds each of the necessary fields for Gapminder creation and their supplied configuration header names. Has properties of its own, and can be found in the `VariableNames` table below. | See `VariableNames` table below. |
| `XAxisScale`<br><b>required</b> | The scale to display on the visualization X axis. Options are `log`, `linear`. | `None` |
| `YAxisScale`<br><b>required</b> | The scale to display on the visualization Y axis. Options are `log`, `linear`. | `None` |
| `YMax`<br><b>required</b> | The visualization Y axis max value. | `None - must be specified` |
|  | **Not yet implemented** |  |
| `AnnotationShapes` | Not currently in use. |  |
| `DatasetChoicesLabel` | Text to be displayed before the multiple dataset dropdown. | None - must be specified if `MultipleDatasets` is set to true. |
| `DatasetChoicesList` | A list of options to be displayed in the multiple dataset dropdown. | None - must be specified if `MultipleDatasets` is set to true. |
| `DefaultDatasetChoice` | The default dataset to display if multiple datasets are given. | None - must be specified if `MultipleDatasets` is set to true. |
| `DeveloperToolsEnabled` | Not currently in use. |  |
| `Interpolate` | Not currently in use. |  |
| `MultipleDatasets` | Boolean describing whether multiple datasets will be used in the visualization. | `false` |
| `TimeSeriesEnabled` | Not currently in use. |  |
| `TracerNames` | Not currently in use. |  |
| `RepositoryURL` | Not currently in use. |  |

<h3 align="center">VariableNames</h3>

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default** |
| ---- | ---- | ---- |
| `XAxis` | The header for X axis data. | `None - must be specified` |
| `YAxis` | The header for Y axis data. | `None - must be specified` |
| `Date` | The header that describes which date each datum takes place. | `None - must be specified` |
| `Sizing` | The header for sizing the 'dots' on the visualization. | `None - must be specified` |
| `Grouping` | The header name for how the data should be grouped and listed in the visualization legend. | `None - must be specified` |
| `Label` | The header for labelling each group. | `None - must be specified` |

#### Configuration File Example ####

```json
{
	"Properties": {
    "AnnotationsFileName": "../viz-data/annotations.json",
    "DocFilePath": "../../data-ts/gm-docs.html",
		"DataFileName": "assets/app/data-maps/data-viz/viz-data/sample-data.csv",
		"BottomXAxisTitleString": "Water-Use (acre-feet/year)",
    "InputDateFormat": "%Y",
    "LeftYAxisTitleString": "Water-Use Rate (GPCD)",
		"MainTitleString": "Water Providers in Colorado",
    "OutputDateFormat": "%Y",
		"SubTitleString": "Population(size), Basin(color), Water-Use(x), and Water-Use Rate(y).",
		"AnimationSpeed": 75,
		"TimeStep": "1Year",
    "VariableNames": {
			"XAxis": "WaterUse_AFY",
			"YAxis": "GPCD",
			"Date": "Year",
			"Sizing": "Population",
			"Grouping": "Basin",
			"Label": "County"
		},
		"XAxisScale": "log",
		"YAxisScale": "linear",
		"YMax": 525
	}
}
```