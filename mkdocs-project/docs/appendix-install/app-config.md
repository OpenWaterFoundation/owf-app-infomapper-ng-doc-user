# InfoMapper / `app-config.json` Configuration File

The `app-config-json` file should exist in the `assets/app/` folder.
It is the main configuration file for the application and describes application content and behavior.
Other configuration files are provided for maps.

* [Introduction](#introduction)
* [Application Properties](#application-properties)
* [Main Menu Properties](#main-menu-properties)
* [Menu Properties](#menu-properties)
* [Path Specification](#path-specification)
* [InfoMapper Application URL Mapping](#infomapper-application-url-mapping)

----

## Introduction ##

The following is an example of an `app-config.json` configuration file:

```
{
  "title": "Poudre Basin Information",
  "homePage": "/content-pages/home.md",
  "version": "0.2.0.dev (2020-05-05)",
  "favicon": "/img/owf-logo-favicon-32x32.ico",
  "mainMenu": [
    {
      "id": "BasinEntities",
      "name": "Basin Entities",
      "align": "left",
      "menus": [
        {
          "id" : "water-districts",
          "name": "Division 1 Water Districts",
          "action": "displayMap",
          "mapProject" : "data-maps/BasinEntities/WaterDistricts/div1-water-districts.json"
        },
        {
          "id" : "ditches",
          "name":  "Agriculture - Ditches",
          "action": "displayMap",
          "enabled": false,
          "mapProject" : "data-maps/BasinEntities/Agriculture-Ditches/ditches.json"
        }
      ]
    },
    {
      "id": "about-the-project",
      "name": "About the Project",
      "action": "contentPage",
      "align": "right",
      "markdownFile": "/content-pages/about-the-project.md"
    }
  ]
}
```

## Application Properties ##

Top-level application properties are described in the following table.

**<p style="text-align: center;">
`app-config.json` Application Properties
</p>**

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Type** | **Description** | **Default** |
| -- | -- | -- | -- |
| `title`<br>**required** | string | Title for the application, shown on the left side of the menu bar and is also used as the web page title shown in web browser tabs. | None - must be specified. |
| `homePage` | file path | Path to the home page, which is shown when the application starts.  This is typically `/content-pages/home.md`.  Markdown will be converted to html.  See the [Path Specification](#path-specification) section. | Blank page. |
| `version`<br>**required** | string |  Version of the application configuration in format `0.2.0.dev (2020-05-05)`.  This is **not** the InfoMapper software version.  | None - must be specified. |
| `favicon` | file path | Path to a favicon image file to use for website, which is shown in the browser tab. | Open Water Foundation favicon. |
| `mainMenu`<br>**required** | array | Main menu definition - see the next section. | None - must be specified. |
| ========== | ========= | Proposed properties | ============= |
| `googlenAnalytics`<br>`TrackingId` | string | Google Analytics tracking identifier. | Analytics are not used. |

## Main Menu Properties ##

The top-level `mainMenu` element has the following properties.
Either the `menus` or `action` property should be specified.

**<p style="text-align: center;">
`app-config.json` Main Menu Properties
</p>**

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Type** | **Description** | **Default** |
| -- | -- | -- | -- |
| `id`<br>**required** | string | Internal identifier for the main menu, will be used in the URL.  See the [InfoMapper Application URL Mapping](#infomapper-application-url-mapping) section. | None - must be specified. |
| `name`<br>**required** | string | The text displayed for the menu. | None - must be specified. |
| `align` | string | The menu alignment:  `left` or ?. | Required? |
| `enabled` | boolean | Whether or not the menu is enabled, `false` or `true`. Disabled menus will be shown in grey and will not respond to user actions. | `true` |
| `action` | string | Indicates that selecting the main menu item will cause an action:<ul><li>`contentPage` - display a content page.  Specify the name of the content file using the `markdownFile` property.</li></ul> | |
| =========== | ====== | Properties for sub-menus. | ============ |
| `menus` | array | Array of sub-menus. See the next section. | |
| =========== | ====== | Properties for `action=contentPage`. | ============ |
| `markdownFile` | file path | Used with `action` that is a `contentPage`.  Path to a Markdown file to display on a content page.  See [Path Specification](#path-specification) section. | |

## Menu Properties ##

Menu properties define actions that will occur when a menu item is selected.
Define each menu as an item in the `menus` array (see previous section).

**<p style="text-align: center;">
`app-config.json` Sub-menu Properties
</p>**

| **Property**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Type** | **Description** | **Default** |
| -- | -- | -- | -- |
| `name`<br>**required** | string | The text displayed for the menu item. | None - must be specified. |
| `enabled` | boolean | Whether or not the menu is enabled, `false` or `true`. Disabled menus will be shown in grey and will not respond to user actions. | `true` |
| `action`<br>**required** | string | The action to take when the menu item is clicked.<ul><li>`contentPage` - display a content page containing text, images, links, etc, using an internal HTML viewer</li><li>`externalLink` - link to another web page</li><li>`mapProject` - display a map</li></ul><br>See below for properties based on the action. | None - must be specified. |
| =========== | ====== | Properties if `action=contentPage`. | ============ |
| `markdownFile` | file path | Used with `action` that is a `contentPage`.  Path to a Markdown file to display on a content page.  See [Path Specification](#path-specification) section. | |
| =========== | ====== | Properties if `action=externalLink`. | ============ |
| `url` | URL | URL of page to link to.  A new web browser tab will be opened so that the current state of the InfoMapper is not lost.  See [Path Specification](#path-specification) section.| |
| =========== | ====== | Properties if `action=mapProject`. | ============ |
| `mapProject` | file path | Path to a [GeoMapProject JSON file](http://software.openwaterfoundation.org/geoprocessor/latest/doc-user/appendix-geomapproject/geomapproject/) to display.  Currently, only GeoMapProject with `projectType=SingleMap` (one map in the project) is supported.  See the [Path Specification](#path-specification) section. | |

## Path Specification ##

The InfoMapper configuration file,  GeoMapProject configuration files,
and other data use paths to indicate the location of files.
Each configuration property that is a file path adheres to the following behavior.

* the folder for each configuration file is used as the folder for relative paths:
	+ the application configuration file exists in the root folder of the application (`assets/app`),
	which is considered the top-level (root) for absolute paths,
	and relative paths in the application configuration file will be appended to the application folder
	+ map configuration files exist in a map data folder folder (e.g., `assets/app/data-maps/some-folder`),
	and relative paths in the map configuration file will be appended to the map folder
* each file path encountered in a configuration file supports the following:
	+ `filename` - full path will be the path to the **configuration file** appended with `/filename`
	+ `/filename` - full path will be the path to the **application folder** appended with `/filename`
	+ `URL` - URL to file using `http` or `https` protocol,
	which allows retrieving the file from a remote server

URLs are most often used when retrieving a data layer from a remote machine,
perhaps with attributes that are updated on a regular frequency.
It may be possible to provide the application configuration or other data files via URLs.
Combinations of higher-level file path
specified as a URL and lower-level file path specified as a non-URL may be supported in the future,
in order to support a URL+relative path data model.
Currently each URL must be specified with full path.
The use of URLs in GeoMapProject configuration files must be coordinated with
GeoProcessor command files that create map configuration files.

### Path Example for Local Files ###

For example, consider the following InfoMapper data files organization,
where maps are organized consistent with InfoMapper menus:


```
assets/
  app/
    app-config.json
    content-pages/
      home.md
    data-maps/
      TopMenu/
        SubMenu/
          map1-config.json
    img/
      default-image1.png
```

The path the `map1-config.json` map configuration file can be
specified in the application configuration file (`app-config.json`)
in either of the following ways because the application configuration
file folder is the same as the application root folder:

* `/data-maps/TopMenu/SubMenu/map1-config.json`
* `data-maps/TopMenu/SubMenu/map1-config.json`

If in a map configuration file, the path to a default image for map marker
(`default-image1.png`) can be specified as:

* `/img/defult-image.json`
* `../../../img/default-image.json`

The latter notation is typically only useful when traversing a small number of parent folders.

### Path Example for Remote Files ###

Need to add an example with URLs to specify data file location.

## InfoMapper Application URL Mapping ##

The InfoMapper uses internal "routing" to map URLs shown in the browser with content shown in the application.
The content defined in the application and map configuration files must be
aligned with the URLs used in the application.
The following examples illustrate how URLs are mapped to internal application data.

The hash character (`#`) in the URL is an indicator to the InfoMapper that he following
part of the URL should be interpreted internally.

**<p style="text-align: center;">
InfoMapper Application URL Mapping
</p>**

| **InfoMapper URL**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Descripton** |
| -- | -- |
| `http://someserver/someapp/` | Load the application and display the home page. |
| `http://someserver/someapp/#/` | Load the application and display the home page. |
| `http://someserver/someapp/#/`<br>`map/current-streamflow` | Display a map with menu `id` property value `current-streamflow`.  All menu items with `action` of `displayMap` are listed under `map/` in the InfoMapper URL. |
| `http://someserver/someapp/#/`<br>`map/current-streamflow?`<br>`parameters` | Same as above, with additional parameters to configure the map display. |
| `http://someserver/someapp/#/`<br>`content-page/home` | Display a content page for application property `homePage`. |
| `http://someserver/someapp/#/`<br>`content-page/about` | Display a content page with menu `id` property value `about`.  All menu items with `action` of `contentPage` are listed under `content-page/` in the InfoMapper URL. 
