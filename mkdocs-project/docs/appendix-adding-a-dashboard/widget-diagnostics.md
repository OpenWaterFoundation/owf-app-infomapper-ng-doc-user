# InfoMapper / Dashboard / Diagnostics Widget #

The Diagnostics Widget is created as an object in the dashboard configuration file that
contains property names and its value.

## Creating a Diagnostics Widget object ##

The following table describes every required/possible property that can be added
for displaying a Diagnostics Widget on a dashboard.

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default** |
| ---- | ---- | ---- |
| `type`<br>**required** | The type of widget to create and display in the dashboard. The full list of available Chart Widget types are as follows:<br><ul><li>`chart` - Display diagnostics on the dashboard.</li></ul> | None - must be specified to be displayed. |
| `name`<br>**required** | A unique name for the widget used for identification. | None. |
| `description` | A description of what the widget will display on the dashboard. | None. |
| `columns` | The amount of columns the widget takes up. **NOTE:** The amount provided *must* be equal to or less than the number used for the **columns** property given in the [Dashboard layout](./add-dashboard.md#layout), or the dashboard will not create correctly. | `1` |
| `rows` | The amount of rows the widget takes up. | `1` |
| `style` | An object representing the styling of the widget. All available options are shown below in the **style** table. |  |

### style ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| `backgroundColor` | The background color of each widget. | `gray` |

----

## Diagnostics Widget object ##

The following is an example of a simple Diagnostics widget in the dashboard
configuration file, and what it looks like on a dashboard. 

```json
{
  "type": "diagnostics",
  "name": "Diagnostics test widget",
  "description": "A simple Diagnostics widget on a dashboard.",
  "columns": 1,
  "rows": 1,
  "style": {
    "backgroundColor": "lightgrey"
  }
}
```

![Simple Diagnostics Widget](./images/simple-diagnostics.png)

**<p style="text-align: center;">
Simple Diagnostics Widget Example (<a href="../images/simple-diagnostics.png">see full-size image</a>)
</p>**