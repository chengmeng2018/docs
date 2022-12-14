# Path

The **<Path\>** component is used to define a closed shape.

> **NOTE**
>
> This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

Not supported

## APIs

Path(value?: { width?: number | string; height?: number | string; commands?: string })

**Parameters**

| Name  | Type        | Mandatory| Description                           |
| -------- | ---------------- | ---- | ----------------------------------- |
| width    | number \| string | No  | Width of the rectangle where the path is located.<br>Default value: **0**   |
| height   | number \| string | No  | Height of the rectangle where the path is located.<br>Default value: **0**   |
| commands | string           | No  | Command for drawing the path.<br>Default value: **''**|

## Attributes

In addition to the [universal attributes](ts-universal-attributes-size.md), the following attributes are supported.

| Name    | Type                               | Default Value | Description                                    |
| -------- | ----------------------------------- | ---- | ---------------------------------------- |
| commands | string                              | ''   | Command for drawing the path. The unit is px. For details about how to convert pixel units, see [Pixel Units](ts-pixel-units.md).|
| fill | [ResourceColor](ts-types.md) | Color.Black | Color of the fill area.|
| fillOpacity | number \| string \| [Resource](ts-types.md#resource)| 1 | Opacity of the fill area.|
| stroke | [ResourceColor](ts-types.md) | - | Stroke color.|
| strokeDashArray | Array&lt;Length&gt; | [] | Stroke dashes.|
| strokeDashOffset | number \| string | 0 | Offset of the start point for drawing the stroke.|
| strokeLineCap | [LineCapStyle](ts-appendix-enums.md#linecapstyle) | LineCapStyle.Butt | Cap style of the stroke.|
| strokeLineJoin | [LineJoinStyle](ts-appendix-enums.md#linejoinstyle) | LineJoinStyle.Miter | Join style of the stroke.|
| strokeMiterLimit | number \| string | 4 | Limit value when the sharp angle is drawn as a miter.|
| strokeOpacity | number \| string \| [Resource](ts-types.md#resource)| 1 | Opacity of the stroke.<br>**NOTE**<br>The value range is [0.0, 1.0]. If the set value is less than 0.0, **0.0** will be used. If the set value is greater than 1.0, **1.0** will be used.|
| strokeWidth | Length | 1 | Width of the stroke.|
| antiAlias | boolean | true | Whether anti-aliasing is enabled.|

The supported commands are as follows:

| Command  | Name                              | Parameter                                      | Description                                      |
| ---- | -------------------------------- | ---------------------------------------- | ---------------------------------------- |
| M    | moveto                           | (x y)                                   | Starts a new subpath at the point specified by the given (x, y) coordinates. For example, `M 0 0` starts a new subpath at point (0, 0).|
| L    | lineto                           | (x y)                                   | Draws a line from the current point to the point specified by the given (x, y) coordinates. The specified point becomes the start point of the new subpath. For example, `L 50 50` draws a line from the current point to point (50, 50), which is the start point of the new subpath.|
| H    | horizontal lineto                | x                                        | Draws a horizontal line from the current point. This command is equivalent to the **L** command where the y-coordinate is 0. For example, `H 50 ` draws a line from the current point to point (50, 0), which is the start point of the new subpath.|
| V    | vertical lineto                  | y                                        | Draws a vertical line from the current point. This command is equivalent to the **L** command where the x-coordinate is 0. For example, `V 50 ` draws a line from the current point to point (0, 50), which is the start point of the new subpath.|
| C    | curveto                          | (x1 y1 x2 y2 x y)                        | Draws a cubic Bezier curve from the current point to the point specified by the given (x, y) coordinates, with (x1, y1) as the control point of the curve start point and (x2, y2) as the control point of the curve end point. For example, `C100 100 250 100 250 200 ` draws a cubic Bezier curve from the current point to point (250, 200), which is the start point of the new subpath.|
| S    | smooth curveto                   | (x2 y2 x y)                              | Draws a cubic Bezier curve from the current point to the point specified by the given (x, y) coordinates, with (x2, y2) as the control point of the curve end point. If the previous command is **C** or **S**, the control point of the curve start point is the mapping of the control point of the curve end point in the previous command relative to the start point. For example, in `C100 100 250 100 250 200 S400 300 400 200`, the second segment of the cubic Bezier curve uses point (250, 300) as the control point of the curve start point. If there is no previous command or the previous command is not **C** or **S**, the control point of the curve start point coincides with the current point.|
| Q    | quadratic Belzier curve          | (x1 y1 x y)                              | Draws a quadratic Bezier curve from the current point to the point specified by the given (x, y) coordinates, with (x1, y1) as the control point. For example, `Q400 50 600 300` draws a quadratic Bezier curve from the current point to point (600, 300), which is the start point of the new subpath.|
| T    | smooth quadratic Belzier curveto | (x y)                                    | Draws a quadratic Bezier curve from the current point to the point specified by the given (x, y) coordinates. If the previous command is **Q** or **T**, the control point is the mapping of the control point of the curve end point in the previous command relative to the start point. For example, in `Q400 50 600 300 T1000 300`, the second segment of the quadratic Bezier curve uses point (800, 350) as the control point. If there is no previous command or the previous command is not **Q** or **T**, the control point of the curve start point coincides with the current point.|
| A    | elliptical Arc                   | (rx ry x-axis-rotation large-arc-flag sweep-flag x y) | Draws an elliptical arc from the current point to the point specified by the given (x, y) coordinates. **(rx, ry)** and **x-axis-rotation** define the size and direction of the arc, indicating how the arc rotates relative to the current coordinate system (in degrees). **large-arc-flag** and **sweep-flag** define how the arc is drawn.|
| Z    | closepath                        | none                                     | Closes the current subpath by connecting the current path back to the initial point of the current subpath.            |

For example, **commands('M0 20 L50 50 L50 100 Z')** defines a triangle that starts from position (0, 20), by drawing a line from point (0, 20) to point (50, 50), then a line from point (50, 50) to point (50, 100), and finally a line from point (50, 100) to point (0, 20).

## Example

```ts
// xxx.ets
@Entry
@Component
struct PathExample {
  build() {
    Column({ space: 10 }) {
      Text('Straight line')
        .fontSize(11)
        .fontColor(0xCCCCCC)
        .width('90%')
      // Draw a straight line whose length is 900 px and width is 3 vp.
      Path()
        .width(300)
        .height(10)
        .commands('M0 0 L900 0')
        .stroke(Color.Black)
        .strokeWidth(3)

      Text('Straight line graph')
        .fontSize(11)
        .fontColor(0xCCCCCC)
        .width('90%')
      // Draw a straight line.
      Row({ space: 20 }) {
        Path()
          .width(100)
          .height(100)
          .commands('M150 0 L300 300 L0 300 Z')
          .fillOpacity(0)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width(100)
          .height(100)
          .commands('M0 0 H300 V300 H0 Z')
          .fillOpacity(0)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width(100)
          .height(100)
          .commands('M150 0 L0 150 L60 300 L240 300 L300 150 Z')
          .fillOpacity(0)
          .stroke(Color.Black)
          .strokeWidth(3)
      }.width('100%')

      Text('Curve graphics').fontSize(11).fontColor(0xCCCCCC).width('90%')
      // Draw an arc.
      Row({ space: 20 }) {
        Path()
          .width(100)
          .height(100)
          .commands("M0 300 S150 0 300 300 Z")
          .fillOpacity(0)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width(100)
          .height(100)
          .commands('M0 150 C0 150 150 0 300 150 L150 300 Z')
          .fillOpacity(0)
          .stroke(Color.Black)
          .strokeWidth(3)
        Path()
          .width(100)
          .height(100)
          .commands('M0 200 A30 20 20 0 0 250 200 Z')
          .fillOpacity(0)
          .stroke(Color.Black)
          .strokeWidth(3)
      }
    }.width('100%')
    .margin({ top: 5 })
  }
}
```

![en-us_image_0000001219744193](figures/en-us_image_0000001219744193.png)
