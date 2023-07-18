# Flutter_doc_CokBK_Des_Update_UI_based_orientation
 https://docs.flutter.dev/cookbook/design/orientation
Update the UI based on orientation
==================================

1.  [Cookbook](https://docs.flutter.dev/cookbook)
2.  [Design](https://docs.flutter.dev/cookbook/design)
3.  [Update the UI based on orientation](https://docs.flutter.dev/cookbook/design/orientation)

In some situations, you want to update the display of an app when the user rotates the screen from portrait mode to landscape mode. For example, the app might show one item after the next in portrait mode, yet put those same items side-by-side in landscape mode.

In Flutter, you can build different layouts depending on a given [`Orientation`](https://api.flutter.dev/flutter/widgets/Orientation.html). In this example, build a list that displays two columns in portrait mode and three columns in landscape mode using the following steps:

1.  Build a `GridView` with two columns.
2.  Use an `OrientationBuilder` to change the number of columns.

[](https://docs.flutter.dev/cookbook/design/orientation#1-build-a-gridview-with-two-columns)1\. Build a `GridView` with two columns
-----------------------------------------------------------------------------------------------------------------------------------

First, create a list of items to work with. Rather than using a normal list, create a list that displays items in a grid. For now, create a grid with two columns.

content_copy

```
return GridView.count(
  // A list with 2 columns
  crossAxisCount: 2,
  // ...
);
```

To learn more about working with `GridViews`, see the [Creating a grid list](https://docs.flutter.dev/cookbook/lists/grid-lists) recipe.

[](https://docs.flutter.dev/cookbook/design/orientation#2-use-an-orientationbuilder-to-change-the-number-of-columns)2\. Use an `OrientationBuilder` to change the number of columns
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

To determine the app's current `Orientation`, use the [`OrientationBuilder`](https://api.flutter.dev/flutter/widgets/OrientationBuilder-class.html) widget. The `OrientationBuilder` calculates the current `Orientation` by comparing the width and height available to the parent widget, and rebuilds when the size of the parent changes.

Using the `Orientation`, build a list that displays two columns in portrait mode, or three columns in landscape mode.

content_copy

```
body: OrientationBuilder(
  builder: (context, orientation) {
    return GridView.count(
      // Create a grid with 2 columns in portrait mode,
      // or 3 columns in landscape mode.
      crossAxisCount: orientation == Orientation.portrait ? 2 : 3,
    );
  },
),
```
