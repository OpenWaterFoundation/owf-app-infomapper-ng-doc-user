# InfoMapper / Story / Adding a Story

Stories can be used in applications by combining text, interactive maps, and other
multimedia content to tell an immersive narrative.

## Adding a story to `app-config.json` ##

Adding a story to an application can be done by first adding it as a navigation
bar button in the main `app-config.json` file. This can be a MainMenu or SubMenu,
which can look similar to the following:

```json
{
  "id": "test-story",
  "storyFile": "stories/test-story/test-story.json",
  "name": "Test Story",
  "action": "story"
}
```

More information on the application configuration file can be found in the
[Install and Config appendix](../appendix-install/app-config.md).

## Configuration file ##

**NOTE: This is a work in progress and will likely change until this message
is removed.**

The following tables describe each story configuration mandatory and optional
properties, with a simple example at the end. Each section describes the "object"
in the file.

### StoryConf ###

As of now the StoryConf object only takes a StoryMain object. More properties
might be added later.

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| story<br>**required** | A StoryMain object. | None - must be provided. |

### StoryMain ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| name | The name of the Story. | None. |
| chapters<br>**required** | An array of StoryChapter objects. | None - must be provided. |

### StoryChapters ###

| **Property** | **Description** | **Default** |
| ---- | ---- | ---- |
| name | The name of the Chapter. | None. |
| tooltip | A tooltip for this chapter to be displayed on a story side navigation list hover.  | None. |
| pages<br>**required** | A array of [Dashboard configuration objects](../appendix-adding-a-dashboard/add-dashboard.md#configuration-file). This is so each page can take advantage of the layout provided by a dashboard.  | None - must be provided. |

### Story configuration file example ###

The following is a simple configuration file example with the resulting Story
displayed after.

```json
{
  "story": {
    "name": "Poudre Basin Example Story",
    "chapters": [
      {
        "name":"Text & Map Examples",
        "tooltip": "Text & Map page",
        "pages": [
          {
            "metadata": {
              "author": "Josh Keahey",
              "title": "Text & Map",
              "id": "text-map-example-1",
              "version": "1.0.0"
            },
            "layout": {
              "columns": 4,
              "backgroundColor": "black",
              "gutterSize": 5
            },
            "widgets": [
              {
                "type": "text",
                "name": "Simple Markdown Text Widget",
                "description": "A widget that displays dashboard text and other useful information.",
                "textPath": "/data-ts/line-maps-group-doc.md",
                "contentType": "Markdown",
                "columns": 1,
                "rows": 1,
                "style": {
                  "backgroundColor": "#212121",
                  "textColor": "white"
                }
              },
              {
                "type": "map",
                "mapConfigPath": "data-maps/map-configuration-files/line-geometry-map.json",
                "name": "Simple Map widget for page 1",
                "columns": 3,
                "rows": 1
              }
            ]
          },
          {
            "metadata": {
              "author": "Josh Keahey",
              "title": "Test Story Page 2",
              "id": "text-map-example-2",
              "version": "1.0.0"
            },
            "layout": {
              "columns": 4,
              "backgroundColor": "black",
              "gutterSize": 5
            },
            "widgets": [
              {
                "type": "text",
                "name": "Simple Markdown Text Widget",
                "description": "A widget that displays dashboard text and other useful information.",
                "textPath": "/data-ts/snodas.md",
                "contentType": "Markdown",
                "columns": 1,
                "rows": 1,
                "style": {
                  "backgroundColor": "#212121",
                  "textColor": "white"
                }
              },
              {
                "type": "map",
                "mapConfigPath": "data-maps/map-configuration-files/point-geometry-map.json",
                "name": "Simple Map widget for page 2",
                "columns": 3,
                "rows": 1
              }
            ]
          }
        ]
      },
      {
        "name":"All Text Examples",
        "pages": [
          {
            "metadata": {
              "author": "Josh Keahey",
              "title": "Text",
              "id": "text-example-1",
              "version": "1.0.0"
            },
            "layout": {
              "columns": 4,
              "backgroundColor": "black",
              "gutterSize": 5
            },
            "widgets": [
              {
                "type": "text",
                "name": "Simple Markdown Text Widget",
                "description": "A widget that displays dashboard text and other useful information.",
                "textPath": "/data-ts/map-doc.md",
                "contentType": "Markdown",
                "columns": 4,
                "rows": 1,
                "style": {
                  "backgroundColor": "#212121",
                  "textColor": "white"
                }
              }
            ]
          }
        ]
      }
    ]
  }
}
```

### Resulting story ###

