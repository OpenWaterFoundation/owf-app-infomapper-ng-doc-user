# InfoMapper / Getting Started

This page describes how to get started with using the InfoMapper.

## Introduction ##

Currently, the InfoMapper can only be installed by cloning the source repository.
An installer will be provided in the future.

Current development efforts by the Open Water Foundation are focusing
on the product design and staff requirements.
Although input from third parties is welcome, at this time,
priorities are focused on implementing features for OWF projects.

See other sections of this documentation for information about installing and configuring
the InfoMapper.

## The application configuration file ##

The `app-config.json` application configuration file is the crucial first step to
creating the InfoMapper, and any other application using the InfoMapper layout.
It is a basic JSON file that configures top level app properties and menu buttons.
The following tables describe each part of the file, with a simple example below.

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| homePage<br>**required** | A path to the home markdown file. The main landing Content Page to be displayed as the site home page. | None - file must be named `home.md`. |
| title | The application title to be displayed on the browser tab. | None - must be specified to be displayed. |
| favicon | A path to the favicon to be used in the browser tab. | The OWF logo. |
| dataUnitsPath | A path to a DATAUNIT file. Used for telling the application how to deal with rounding numbers for different types of units. | None |
| googleAnalyticsTrackingId | The unique Google Analytics Id to track website traffic. | None |
| version | The version of the application configuration file. | None |
| mainMenu | An array of MainMenu objects, to be displayed as buttons in the navbar of the site starting from the left. The mainMenu properties can be found in the following **mainMenu** table. | None |

### mainMenu ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| id<br>**required** | The unique Id of the page as a string that will be displayed on this menu click. Will be used in the page URL. | None - must be specified. |
| dashboardFile | **TODO** |  |
| mapProject | **TODO** |  |
| markdownFile | **TODO** |  |
| action<br>**required** | The action to be taken for this mainMenu button when clicked. Can be one of the following strings:<br><ul><li>`contentPage`</li><li>`dashboard`</li><li>`displayMap`</li></ul> | None - must be specified. |
| name | The string name to be displayed on the mainMenu button. | None - must be specified to be displayed. |
| enabled | A string or boolean representing if this mainMenu button can be clicked or not. Setting to "false" or false will gray out the menu. | `true` |
| visible | A string or boolean representing if this mainMenu button is created on the site navbar. | `true` |
| tooltip | A string to be displayed as a tooltip when a user hovers over the mainMenu button. |  |
| menus | An array of subMenu objects to be displayed as a dropdown when the mainMenu button is hovered over. SubMenu properties are listed below in the **menus** table. **Note:** Need to change to subMenu for consistency with the InfoMapper types and easier readability. |  |

### subMenu ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| id<br>**required** | The unique Id of the page as a string that will be displayed on this menu click. Will be used in the page URL. | None - must be specified. |
| mapProject | **TODO** |  |
| markdownFile | **TODO** |  |
| action<br>**required** | The action to be taken for this mainMenu button when clicked. Can be one of the following strings:<br><ul><li>`contentPage`</li><li>`displayMap`</li></ul> | None - must be specified. |
| name | The string name to be displayed on the mainMenu button. | None - must be specified to be displayed. |
| enabled | A string or boolean representing if this mainMenu button can be clicked or not. Setting to "false" or false will gray out the menu. | `true` |
| visible<br>**not currently working** | A string or boolean representing if this mainMenu button is created on the site navbar. | `true` |
| tooltip | A string to be displayed as a tooltip when a user hovers over the subMenu button. |  |
