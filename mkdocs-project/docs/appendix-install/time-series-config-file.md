# Time Series Configuration File #

* [Introduction](#introduction)
* [Examples](#examples)
	+ [Poudre Basin Information - County Population](#poudre-basin-information-county-population)

----------

## Introduction ##

A time series configuration file, also called "time series graph configuration" and "time series product" file,
is created by TSTool by running the
[`ProcessTSProduct(OutputProductFile="somefile.json")`](https://opencdss.state.co.us/tstool/latest/doc-user/command-ref/ProcessTSProduct/ProcessTSProduct/)
command.
This file provides a verbose representation of a time series product, such as a graph,
and allows the InfoMapper to create a corresponding graph using a charting package (by default plotly).
The benefit of this approach is that a visualization can be prototyped in TSTool and saved for use with the InfoMapper.
It is typical that a specific graph configuration will be prototyped and then generalized into a template that can be
used with multiple map features, for example to show a graph for streamflow stations.

## Examples ##

The following examples illustrate the use of graph configurations.

### Poudre Basin Information - County Population ###

The [Poudre Basin Information website](https://poudre.openwaterfoundation.org/latest/#/map/entities-counties) 
implements a graph configuration to display graphs of county
population time series (click on a county to display population time series).
The following illustrate the steps necessary to configure a time series graph.

1. A TSTool command file is used to query and process time series.  See the
[`02b-create-population-graph-config.tstool`](https://github.com/OpenWaterFoundation/owf-infomapper-poudre/blob/master/workflow/BasinEntities/Political-Counties/02b-create-population-graph-config.tstool)
command file, near the bottom.
This command file creates time series data files that can be accessed as locations are selected on the map,
and graph configuration templates that describe the graph so that it can be created by InfoMapper charting tools.
2. Time series results are graphed and are edited to create a time series product:
	1. Initially, time series of interest in the results are selected and a graph is created.
	The graph will display using default properties.
	2. Right-click on the graph and use the ***Properties*** editor to customize the graph.
	3. Save the graph as a time series product (`*.tsp`) file, in this case
	[`county-population-graph-config.tsp`](https://github.com/OpenWaterFoundation/owf-infomapper-poudre/blob/master/workflow/BasinEntities/Political-Counties/graphs/county-population-graph-config.tsp).
	The example is for Larimer county.
	4. Automate processing the graph using the 
	[`ProcessTSProduct(OutputProductFile="somefile.json")`](https://opencdss.state.co.us/tstool/latest/doc-user/command-ref/ProcessTSProduct/ProcessTSProduct/)
	command.  This saves a "prototype" graph as JSON, using the specific time series identifiers,
	in this case
	[`county-population-graph-config-prototype.json`](https://github.com/OpenWaterFoundation/owf-infomapper-poudre/blob/master/workflow/BasinEntities/Political-Counties/graphs/county-population-graph-config-prototype.json).
	Unlike the `*.tsp` file, which contains only minimal configuration that is different from internal defaults,
	the `*.json` file is verbose and contains all properties.
	This ensures that the product can be completely defined in InfoMapper.
3. Convert the JSON time series product into a template.
	1. Use the
	[`TextEdit`](https://opencdss.state.co.us/tstool/latest/doc-user/command-ref/TextEdit/TextEdit/)
	command to replace the specific time series location identifier `Larimer` with a property
	using notation `${featureAttribute:county}`, which causes InfoMapper to insert the value of the `county` attribute for the
	county layer when processing the graph.
	Use this technique for all occurances of strings that need to be modified in order to
	create a working visualization.
	2. As necessary, use [property modifiers](app-config.md#property-modifiers) to modify layer attribute value to
	match time series identifiers.
	This is necessary because some counties have names like `RIO GRANDE`, which must be reformatted.
4. Use the time series graph configuration file in
	[event handler configuration](map-event-config-file.md),
	as the `resourcePath` that will be processed when a map feature is clicked and popup action executed.
