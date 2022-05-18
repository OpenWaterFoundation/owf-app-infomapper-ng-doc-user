# InfoMapper / Dashboard / Title Widget #

The Title widget is created as an object in the dashboard configuration file that
contains property names and its value.

## Creating a Title Widget object ##

The following table describes every required/possible property that can be added
for displaying a Title Widget on a dashboard.

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default** |
| ---- | ---- | ---- |
| `type`<br>**required** | The type of widget to create and display in the dashboard. To display a title widget, the type must be the following (case insensitive):<br><ul><li>`title` - Display a title on the dashboard.</li></ul> | None - must be specified to be displayed. |
| `text`<br>**required** | A string representing what will be shown as the title in the widget. | None - must be specified. |
| `name`<br>**required** | A unique name for the widget used for identification. | None - must be specified. |
| `columns` | The amount of columns the widget takes up. **NOTE:** The amount provided *must* be equal to or less than the number used for the **columns** property given in the [Dashboard layout](./add-dashboard.md#layout), or the dashboard will not create correctly. | `1` |
| `description` | A description of what the widget will display on the dashboard. | None. |
| `rows` | The amount of rows the widget takes up. | `1` |
| `style` | An object representing the styling of the widget. All available options are shown below in the **style** table. |  |

### style ###

All available style properties are passed right into an HTML DOM Style object using
CSS. Because of this, all values given for the following properties can use the
[CSS Property](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Properties_Reference)
nomenclature. This means normal strings like `black`, more granular strings such as
`DodgerBlue`, hex values like `#d5d6d5`, etc. can be provided.

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; |
| ---- | ---- | ---- |
| `backgroundColor` | The background color of the widget. | `gray` |
| `fontFamily` | The type of font to use for the text in the widget. | `Roboto, "Helvetica Neue", sans-serif` |
| `fontSize` | The size of all font in the widget. | `16px` |
| `fontStyle` | The ability to italicize the title. | `normal` |
| `fontWeight` | The ability to use bold on the title. | `normal` |
| `textColor` | The color of all non-link text in the widget. | `black` |
| `textDecoration` | The ability to underline the title. | `''` |

----

## Title Widget object ##

The following is an example of a simple Title widget in the dashboard configuration
file, and what it looks like on a dashboard. This object would be added to the
dashboard configuration's **widgets** array.

```json
{
  "type": "title",
  "name": "Simple title widget",
  "title": "My Dashboard Title Widget",
  "description": "A simple title widget for testing.",
  "columns": 4,
  "rows": 1,
  "style": {
    "backgroundColor": "white",
    "textColor": "black",
    "fontSize": "36px",
    "fontStyle": "italic",
    "fontWeight": "bold",
    "textDecoration": "underline"
  }
}
```

![Simple Title Widget](../images/simple-title.png)

**<p style="text-align: center;">
Simple Title Widget Example (<a href="../images/simple-title.png">see full-size image</a>)
</p>**