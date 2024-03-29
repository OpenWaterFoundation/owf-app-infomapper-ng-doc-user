# InfoMapper / Dashboard / Text Widget #

The Text Widget is created as an object in the dashboard configuration file that
contains property names and its value.

## Creating a Text Widget object ##

The following table describes every required/possible property that can be added
for displaying a Text Widget on a dashboard.

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** | **Default** |
| ---- | ---- | ---- |
| `type`<br>**required** | The type of widget to create and display in the dashboard. The full list of available Text Widget types are as follows:<br><ul><li>`textHTML` - Display text from a HTML file.</li><li>`textMarkdown` - Display text from a markdown file.</li></ul> | None - must be specified to be displayed. |
| `textPath`<br>**required** | The path to the text data file being used by this widget. Can either be an absolute path that assumes the project's `src/assets/app/` is the default home directory, or a relative path from the dashboard configuration file. | None - must be specified. |
| `contentType`<br>**required** | The type of data that will be read from the `textPath` property. The following are all currently supported Text widget content types: <ul><li>`HTML`</li><li>`Markdown`</li></ul> |  |
| `name`<br>**required** | A unique name for the widget used for identification. | None - must be specified. |
| `columns` | The amount of columns the widget takes up. **NOTE:** The amount provided *must* be equal to or less than the number used for the **columns** property given in the [Dashboard layout](./add-dashboard.md#layout), or the dashboard will not create correctly. | `1` |
| `description` | A description of what the widget will display on the dashboard. | None. |
| `rows` | The amount of rows the widget takes up. | `1` |
| `style` | An object representing the styling of the widget. All available options are shown below in the **style** table. |  |

### style ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| `backgroundColor` | The background color of each widget. | `gray` |
| `textColor` | The color of all non-link text in the file. | `black` |

----

## Text Widget object ##

The following is an example of a simple text widget in the dashboard configuration
file, and what it looks like on a dashboard. This object would be added to the
dashboard configuration's **widgets** array.

```json
{
  "type": "text",
  "name": "About the Project",
  "description": "Displays text about a project from a markdown file.",
  "textPath": "/content-pages/about-the-project.md",
  "contentType": "Markdown",
  "columns": 3,
  "rows": 2,
  "style": {
    "backgroundColor": "#ffffff",
    "textColor": "black"
  }
}
```

![Simple Text Widget](./images/simple-text-markdown.png)

**<p style="text-align: center;">
Simple Text Widget Example (<a href="../images/simple-text-markdown.png">see full-size image</a>)
</p>**