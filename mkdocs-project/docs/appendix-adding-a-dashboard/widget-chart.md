# InfoMapper / Dashboard / Chart Widget #

**This widget is currently under development.**

The Chart Widget is created as an object in the dashboard configuration file that
contains property names and its value.

## Creating a Chart Widget object ##

The following table describes every required/possible property that can be added
for displaying a Chart Widget on a dashboard.

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| type<br>**required** | The type of widget to create and display in the dashboard. The full list of available Chart Widget types are as follows:<br><ul><li>`chart` - Display a chart on the dashboard.</li></ul> | None - must be specified to be displayed. |
| dataPath<br>**required** |  | None - must be specified. |
| graphTemplatePath<br>**required** |  | None - must be specified. |
| name | A name for the widget. | None. |
| description | A description of what the widget will display on the dashboard. | None. |
| columns | The amount of columns the widget takes up. **NOTE:** The amount provided *must* be equal to or less than the number used for the **columns** property given in the main dashboard layout above, or else the dashboard will not create correctly. | `1` |
| rows | The amount of rows the widget takes up. | `1` |
| style | An object representing the styling of the widget. All available options are shown below in the **style** table. |  |

### style ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| backgroundColor | The background color of each widget. | `gray` |

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
  "dataPath": "",
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