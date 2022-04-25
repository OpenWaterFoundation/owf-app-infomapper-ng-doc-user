# InfoMapper / Dashboard / Chart Widget #

The Chart Widget is created as an object in the dashboard configuration file that
contains property names and its value.

## Creating a Chart Widget object ##

The following table describes every required/possible property that can be added
for displaying a Chart Widget on a dashboard.

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default** |
| ---- | ---- | ---- |
| `type`<br>**required** | The type of widget to create and display in the dashboard. The full list of available Chart Widget types are as follows:<br><ul><li>`chart` - Display a chart on the dashboard.</li></ul> | None - must be specified to be displayed. |
| `chartFeaturePath`<br>**required** | The path or URL to a simple JSON file that contains the features and their values for the chart. | None - must be specified. |
| `graphTemplatePath`<br>**required** | The path or URL to a TSTool created graph template file. More information can be found at the [TSTool Time Series Viewing Tools User Documentation](https://opencdss.state.co.us/tstool/latest/doc-user/appendix-tsview/tsview/#time-series-product-file-json-format). | None - must be specified. |
| `name` | A name for the widget. | None. |
| `description` | A description of what the widget will display on the dashboard. | None. |
| `columns` | The amount of columns the widget takes up. **NOTE:** The amount provided *must* be equal to or less than the number used for the **columns** property given in the [Dashboard layout](./add-dashboard.md#layout), or the dashboard will not create correctly. | `1` |
| `rows` | The amount of rows the widget takes up. | `1` |
| `style` | An object representing the styling of the widget. All available options are shown below in the **style** table. |  |

### style ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| `backgroundColor` | The background color of each widget. | `gray` |

----

## Simple Chart Widget object ##

The following is an example of a simple Chart widget in the dashboard
configuration file, and what it looks like on a dashboard. 

```json
{
  "type": "chart",
  "name": "Chart test widget",
  "description": "A simple Chart widget on a dashboard.",
  "columns": 1,
  "rows": 1,
  "chartFeaturePath": "/data-ts/diversions.json",
  "graphTemplatePath": "",
  "style": {
    "backgroundColor": "lightgrey"
  }
}
```

![Simple Chart Widget](./images/simple-chart.png)

**<p style="text-align: center;">
Simple Chart Widget Example (<a href="../images/simple-chart.png">see full-size image</a>)
</p>**