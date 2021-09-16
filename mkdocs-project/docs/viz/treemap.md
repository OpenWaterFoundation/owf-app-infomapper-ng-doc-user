# InfoMapper / Visualizations / Treemap #

## Introduction ##

The InfoMapper utilizes D3 to display the Treemap visualization. Treemaps recursively 
partition space into rectangles according to each data element's associated value. D3
supports multiple types of tiling methods and Treemaps. InfoMapper makes use of the
static Treemap with the squarify tiling method. This produces a Treemap that is not
non-interactive, and attempts to create a square of each data group.
The following examples show a simple and advanced Tidy Tree:

<p align="center"><b>Simple Treemap</b></p>
![Simple Tidy Tree](./images/simple-treemap.png)

<p align="center"><b>Advanced Treemap</b></p>
![Advanced Tidy Tree](./images/advanced-treemap.png)

## User Interface ##

**To be updated**

## Configuration ##

A JSON file is used to provide the InfoMapper with the necessary information to
be used by D3 when constructing a Treemap. Configuration file examples can be
found under [Data](#data). The following table describes the properties and
values that are utilized.

| Property Name | Description | Default |
| ---- | ---- | ---- |
| `chartType`<br><b>required</b> | Tells the InfoMapper and D3 what kind of visualization is to be constructed. `tidyTree` must be provided to create the Tidy Tree. | None - must be `treeMap`. |
| `dataPath` | The absolute path, or the path relative to the visualization configuration file for the D3 graph data file. | None - must be specified. |
| `name` | The property name to be used by D3 whose values will be displayed for each Treemap element. | `name` |
| `parent`<br><b>Used only with CSV data</b> | The property name to be used by D3 that describes each Treemap element's parent. | `parent` |
| `children`<br><b>Used only with JSON data</b> | The property name to be used by D3 whose nested elements will be used as the current Treemap element's descendants. | `children` |
| `value` | The property name to be used by D3 to  | `value` |
| `title` | The title to be displayed above the visualization. | None |
| `height` | The height of the visualization in pixels. | 500 |
| `width` | The width of the visualization in pixels. | 500 |

## Data ##

The InfoMapper supports both CSV and JSON data formats.

#### CSV ####

CSV data files can be created with only two columns: One for displaying on the visualization,
and another for telling D3 what the element's parent is. Each must be declared in
the configuration file using the properties `name` and `parent`.

An example CSV data file to create the simple Treemap above:

```csv
Basin,Parent Basin,Water
Colorado River Basins
Arkansas,Colorado River Basins
North Platte,Colorado River Basins
South Platte,Colorado River Basins
River A,Arkansas,3938
River B,Arkansas,3812
River C,Arkansas,6714
River D,Arkansas,743
River E,North Platte,3534
River F,North Platte,5731
River G,North Platte,7840
River H,North Platte,5914
River I,North Platte,3416
River J,South Platte,7074
```

Because Basin, Parent Basin, and Water is desired for the Tree's element name, parent,
and value respectively, the configuration would contain the following properties:

```json
{
  "name": "Basin",
  "parent": "Parent Basin",
  "value": "water"
}
```

#### JSON ####

**TODO - Need to talk to Steve about naming conventions**