# LongPressGesture

**LongPressGesture** is used to trigger a long press gesture, which requires one or more fingers with a minimum 500 ms hold-down time.

>  **NOTE**
>
>  This gesture is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.


## APIs

LongPressGesture(value?: { fingers?: number, repeat?: boolean, duration?: number })

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fingers | number | No| Minimum number of fingers to trigger a long press gesture. The value ranges from 1 to 10.<br>Default value: **1**|
| repeat | boolean | No| Whether to continuously trigger the event callback.<br>Default value: **false**|
| duration | number | No| Minimum hold-down time, in ms.<br>Default value: **500**|


## Events

| Name| Description|
| -------- | -------- |
| onAction(event:(event?: [GestureEvent](ts-gesture-settings.md)) =&gt; void) | Callback invoked when a long press gesture is recognized.|
| onActionEnd(event:(event?: [GestureEvent](ts-gesture-settings.md)) =&gt; void) | Callback invoked when the finger used for a long press gesture is lift.|
| onActionCancel(event: () =&gt; void) | Callback invoked when a tap cancellation event is received after a long press gesture is recognized.|


## Example

```ts
// xxx.ets
@Entry
@Component
struct LongPressGestureExample {
  @State count: number = 0

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.SpaceBetween }) {
      Text('LongPress onAction:' + this.count)
    }
    .height(200).width(300).padding(60).border({ width:1 }).margin(30)
    .gesture(
      LongPressGesture({ repeat: true })
        // Repeatedly triggered when the long press gesture exists.
        .onAction((event: GestureEvent) => {
          if (event.repeat) { this.count++ }
        })
        // Triggered when the long press gesture ends.
        .onActionEnd(() => {
          this.count = 0
        })
    )
  }
}
```

![en-us_image_0000001257058425](figures/en-us_image_0000001257058425.gif)
