# InfoMapper / `app-config.json` Configuration File

The `app-config-json` file should exist in the `assets/app/` folder.
It is the main configuration for the application and describes application content and behavior.

* [Introduction](#introduction)
* [Application Properties](#application-properties)
* [Main Menu Properties](#main-menu-properties)
* [Menu Properties](#menu-properties)

----

## Introduction ##

The following is an example of an `app-config.json` configuration file:

```
{
  "title": "Poudre Basin Information",
  "version": "0.2.0.dev (2020-05-05)",
  "mainMenu": [
    {
      "id": "BasinEntities",
      "name": "Basin Entities",
      "align": "left",
      "enabled": "true",
      "menus": [
        {
          "name": "Division 1 Water Districts",
          "enabled": "true",
          "action": "displayMap",
          "mapProject" : "div1-water-districts.json"
        },
        {
          "name":  "Agriculture - Ditches",
          "enabled": "true",
          "action": "displayMap",
          "mapProject" : "theNameOfTheMapProjectFile"
        }
      ]
    },
    {
      "id": "Tab",
      "name": "About the Project",
      "action": "genericPage",
      "align": "right",
      "enabled": "true",
      "markdownFile": "about-the-project"
    }
  ]
}
```

## Application Properties ##

Top-level application properties are described in the following table.

**<p style="text-align: center;">
`app-config.json` Application Properties
</p>**

| **Property** | **Type** | **Description** | **Default** |
| -- | -- | -- | -- |
| `title`<br>**required** | string | Title for the application, shown on the left side of the menu bar. | None - must be specified. |
| `version`<br>**required** | string |  Version of the application configuration in format `0.2.0.dev (2020-05-05)`.  This is **not** the InfoMapper software version.  | None - must be specified. |
| `mainMenu`<br>**required** | array | Main menu definition - see the next section. | None - must be specified. |

## Main Menu Properties ##

The top-level `mainMenu` element has the following properties.
Either the `menus` or `action` property should be specified.

**<p style="text-align: center;">
`app-config.json` Main Menu Properties
</p>**

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Type** | **Description** | **Default** |
| -- | -- | -- | -- |
| `id`<br>**required** | string | Internal identifier for the main menu. | None - must be specified. |
| `name`<br>**required** | string | The text displayed for the menu. | None - must be specified. |
| `align` | string | The menu alignment:  `left` or ?. | Required? |
| `enabled` | boolean | Whether or not the menu is enabled, `false` or `true`. Disabled menus will be shown in grey and will not respond to user actions. | `true` |
| =========== | ====== | Properties for sub-menus. | ============ |
| `menus` | array | Array of sub-menus. See the next section. | |
| =========== | ====== | Properties for action. | ============ |
| `action` | string | Indicates that selecting the main menu item will cause an action:<ul><li>`contentPage` - display a content page.  Specify the name of the page using the `markdownFile` property.</li></ul> | |
| `markdownFile` | string | Name of the Markdown file to display on a content page (must specify `action=contentPage`).  The name should be relative to ? | |

## Menu Properties ##

Menu properties define actions that will occur when a menu item is selected.

**<p style="text-align: center;">
`app-config.json` Sub-menu Properties
</p>**

| **Property** | **Type** | **Description** | **Default** |
| -- | -- | -- | -- |
| `name`<br>**required** | string | The text displayed for the menu item. | None - must be specified. |
| `enabled` | boolean | Whether or not the menu is enabled, `false` or `true`. Disabled menus will be shown in grey and will not respond to user actions. | `true` |
| `action`<br>**required** | string | The action to take when the menu item is clicked. | None - must be specified. |
| =========== | ====== | Properties if `action=externalLink`. | ============ |
| `url` | string | URL of page to link to.  A new web browser tab will be opened so that the current state of the InfoMapper is not lost. | |
| =========== | ====== | Properties if `action=mapProject`. | ============ |
| `mapProject` | string | Name of the [GeoMapProject JSON file](http://software.openwaterfoundation.org/geoprocessor/latest/doc-user/appendix-geomapproject/geomapproject/) to display.  **Need to describe what the path to the map project is relative to.  Currently, only GeoMapProject with `projectType=SingleMap` are recognized (**is this true?**).** | |
