# InfoMapper / Installation and Configuration #

This documentation describes how to install and configure the InfoMapper.

* [Install InfoMapper](#install-infomapper)
* [File Organization Strategies](#file-organization-strategies)
	+ [Map-centric File Organization](#map-centric-file-organization)
	+ [Shared Files by Type](#shared-files-by-type)
	+ [Hybrid File Organization](#hybrid-file-organization)
* [Configure InfoMapper](#configure-infomapper)
	+ [`app-config.json`](#app-configjson)
	+ [Map Configuration File](#map-configuration-file)
	+ [Map Event Configuration File](#map-event-configuration-file)
	+ [Time Series Configuration File](#time-series-configuration-file)

----------------------

## Install InfoMapper ##

Currently, installation of the InfoMapper requires cloning the GitHub repository.
See the [owf-app-infomapper-ng](https://github.com/OpenWaterFoundation/owf-app-infomapper-ng)
repository README for instructions.

The InfoMapper is typically installed parallel to a "workflow" repository that
contains processing workflow to create information products.
See the [owf-app-poudre-dashboard-workflow](https://github.com/OpenWaterFoundation/owf-app-poudre-dashboard-workflow)
repository for an example that provides a specific configuration and data files to the InfoMapper.
See also the deployed
[Poudre Basin Information](http://poudre.openwaterfoundation.org/latest/) website.

## File Organization Strategies ##

The InfoMapper provides flexibility in organizing files by supporting
absolute and relative paths (see
[`app-config.json` Path Specification](app-config.md#path-specification)).
The following sections explain options for organizing application files,
based on experience gained during InfoMapper development and implementation.

Configuration files and documentation are typically created with a text editor
and are saved in a repository.
TSTool, GeoProcessor, R, and other workflow files are typically run to
create content and are copied to the data folders.

### Map-centric File Organization ###

InfoMapper implementations are map-centric by design,
with applications configured with menus that correspond to maps.
Although it is possible to share map layers (such as streamflow),
disk and cloud storage are cheap and experience has shown that
it is easier in many cases just to copy layer files into each map folder.
Data layers that are large might need to be shared but such layers might
be provided as web services (so minimal local file management),
and large layers are typically only shown one one or a few maps in an application,
so the need for copies can be minimized.
If necessary, some files can be shared using a hybrid of map-centric file organization
and shared files, with appropriate paths being used in configuration files.

The following is a typical InfoMapper organization using map-centric organization,
using an example from the
[Poudre Basin Information](http://poudre.openwaterfoundation.org/latest/) implementation.
In this case, the majority of map data and configuration files are in folders for
the map, with only a few map-related files such as map marker images
being located in the global `img/` folder.

```
assets/
  app/
    app-config.json                    Main application configuration file.
    content-pages/                     Top-level general content pages, markdown.
      home.md                          Main landing page.
      *.md                             Other content pages, markdown.
    data-maps/                         Main folder for all map data and configuration files.
      TopMenu/                         Folders that match top-level menus.
        SubMenu/                       Folders that match sub-menus.
          map1-config-map.json         The map configuration file.
          map1-config-map.md           Documentation for map, markdown.
          downloads/                   Original data files that are distributed.
          graphs/                      Graph configuration files for popups.
            xxx-graph-config.json      TSTool graph template as JSON.
          layers/                      Spatial data layers and related files used by map.
            xxx.geojson                GeoJSON file for map layer.
            xxx.tif                    GeoTIFF file for map layer.
            xxx.md                     Documentation for layer, markdown.
            xxx-classify-yyy.csv       Classification file for layer xxx and attribute yyy.
            xxx-event-config.json      Map event handler configuration for layer.
          ts/                          Time series needed for graphs accessed from map,
                                       for example produced by TSTool.
            *.csv                      CSV time series files.
            *.dv                       TSTool DateValue format time series files.
    img/
      default-image1.png               Images that are shared in application,
                                       including map marker icons.
      DATAUNIT                         Dataunits file for units checks/conversions.
                                       Other files (may move to main 'app' folder).
```

### Shared Files by Type ###

In some cases it may be helpful to organize InfoMapper files to allow sharing
between maps, with files typically organized by file type.
The following file organization illustrates this approach,
which is used in the InfoMapper development files.
This approach is helpful when files are being reused.

```
assets/
  app/
    app-config.json                    Main application configuration file.
    content-pages/                     Top-level general content pages, markdown.
      home.md                          Main landing page.
      *.md                             Other content pages, markdown.
    data-maps/                         Data and configurations for maps.
      map-classification-files/        Map classification files, for symbols.
        xxx-classify-yyy.csv           Classification file for layer xxx and attribute yyy.
      map-configuration-files/         Map configuration files.
        xxx-config-map.json            The map configuration file.
      map-layers/                      Map layer files.
        xxx.geojson                    GeoJSON file for map layer.
        xxx.tif                        GeoTIFF file for map layer.
      graph-templates/                 Graph configuration files.
        xxx-graph-config.json          TSTool graph template as JSON.
    data-ts/                           Time series needed for graphs accessed from map,
                                       for example produced by TSTool.
      *.csv                            CSV time series files.
      *.dv                             TSTool DateValue format time series files.
```

### Hybrid File Organization ###

It may make sense to organize files using a hybrid approach that uses
aspects of each of the previously-described approaches.
For example:

1. Use a map-centric approach for most files and use a top-level `data-ts/` folder for
time series to allow time series to be accessed from multiple graphs.
This makes sense because time series are typically stored in separate files and
copying many files wastes storage space and can lead to data inconsistencies.
2. Use a map-centric approach for most files but store shared layers in a folder that
is accessed by multiple maps.  This makes sense when the map layer is used in many
maps and/or is large and would waste storage space.

In a hybrid approach, map and other configuration files must specify file locations
using absolute path (from application configuration folder) or
`../../` relative paths (from map configuration file folder).

## Configure InfoMapper ##

The InfoMapper is an Angular application.
Therefore, application configuration relies on files in the `src/assets/` folder.
An `app/` folder is used in `assets` to isolate specific implementations
of the InfoMapper from the core software configuration.
The contents of `app/` can vary between implementations.
Guidelines for file organization are being developed.

### `app-config.json` ###

The main application configuration file `app-config.json` is used to provide overall application configuration information
such as menus, sub-menus, and associated website content.

* See the [`app-config.json`](app-config.md) specification

### Map Configuration File ###

Map configuration files are created by the GeoProcessor software.
This ensures that the JSON map configuration files are properly formatted.
For example, see:

* [Poudre Basin Information GeoProcessor command files](https://github.com/OpenWaterFoundation/owf-infomapper-poudre/blob/master/workflow/BasinEntities/Political-Counties/03-create-counties-map.gp)
* [InfoMapper test data GeoProcessor command files](https://github.com/OpenWaterFoundation/owf-app-infomapper-ng/tree/master/data-prep)

### Map Event Configuration File ###

Map event configuration files are used to configure actions that occur
when interacting with maps, such as clicking on a map feature to display a graph.

* See the [Map Event Configuration File](map-event-config-file.md) specification.

### Time Series Configuration File ###

Time series configuration files are used to configure time series visualizations
including graphs.

* See the [Time Series Configuration File](time-series-config-file.md) specification.
