# InfoMapper / Searching #

As of version `4.2.0`, global searching has been added to the InfoMapper. The following
list describes the currently supported items in an InfoMapper application that are
searchable.

| **Searchable item**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** |
| ---- | ---- |
| Content Pages | All provided markdown files that are given the `contentPage` **action** property in either a main menu or sub menu object in the `app-config.json` file. See the [Adding Content Pages](#adding-content-pages-to-the-search-index) to the search index section. |
| Maps | All provided JSON files that are given the `mapProject` **action** property in either a main menu menu or sub menu object in the `app-config.json` file that contains the top level **keywords** property in its map configuration file. See the [Adding Maps](#adding-maps-to-the-search-index) to the search index section. |

The following list contains items to be searchable in the future, and why they are
**not** currently supported.

| **Unsearchable item**&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; | **Description** |
| ---- | ---- |
| Markdown files in a map | All **docPath** properties in either a `geoMaps`, `geoLayerViewGroups`, or `geoLayerViews` **properties** object in map config files. The search results table displays the results with a link to the page that contains the user query. When searching through Content Pages or Maps with keywords, it is simple enough to route the user to that page without much hassle. Markdown files in a map, however, require much more handling.<br><br>First: Because these files are shown in a dialog, it cannot be simply routed to. Query parameters would need to be used to uniquely identify each dialog.<br><br>Second: Multiple dialogs open simultaneously would need to be supported. There is already a Window Manager in the Common package, so logic would need to be added to dynamically add and remove query parameters as they are opened & closed (on top of making sure a dialog can only be opened once).<br><br>Third: If query parameters are used, users could theoretically copy-paste a URL with a dialog open, paste it into another browser tab, and have a map shown with the open dialog based on the query parameter. This means there needs to be logic that checks the URL for query parameters when its loaded.<br><br>This is a generally high level description. For a more technical deep dive, see the <a href="https://github.com/OpenWaterFoundation/owf-app-infomapper-ng/issues/408" target="_blank">InfoMapper Search GitHub issue</a>. |

## Adding Content Pages to the search index ##

All InfoMapper Content Pages will be added to the search index by default, with one
caveat. The table that displays the search results will display each result with
a title. The title is parsed out from each markdown file, and *must* match the following:

```
# Some Title #
```

The title hash must be present before and after the title in order for the file to
be added to the index. If only one has is used, or the file begins with no title,
no error will occur, but a warning will be printed to DevTools saying that the file
will not be added to the index.

## Adding Maps to the search index ##

InfoMapper Map pages do not contain easy to search content like Content Pages, as
they are made up of configuration JSON and GeoJSON files. Specific words that describe
the map can be added to the map's top level configuration file object. This property
is called `keywords`, and is an array of strings. An example of the GeoMapProject
object can look something like the following (with other properties set to "..."
to more easily focus on the keywords):

```json
{
  "geoMapProjectId": "...",
  "name": "...",
  "description": "...",
  "projectType": "...",
  "properties": {
    "author": "...",
    "specificationFlavor": "...",
    "specificationVersion": "..."
  },
  "keywords": [
    "Ditch service areas",
    "Water districts raster",
    "Colorado municipal boundaries",
    "Polygon geometry map"
  ],
  "geoMaps": []
}
```

In this example, the names of all the map's layers are used, as well as name of GeoMap
itself. It is recommended to include `map` as a keyword somewhere. When searching,
any keywords found will have a higher impact score than words found in a markdown
file. This way, even though maps will possibly contain much fewer words than a markdown
file, any matching keywords found during a search query will be given more relevance,
and will be reflected in the results table.