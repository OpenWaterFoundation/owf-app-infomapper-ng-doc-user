# InfoMapper / Installation and Configuration #

This documentation describes how to install and configure the InfoMapper.

* [Install InfoMapper](#install-infomapper)
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

## Configure InfoMapper ##

The InfoMapper is an Angular application.
Therefore, application configuration relies on files in the `src/assets/` folder.
An `app/` folder is used in `assets` to isolate specific implementations of the InfoMapper from the core software configuration.
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
