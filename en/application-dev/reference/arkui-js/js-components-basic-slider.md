# slider

>  **NOTE**
>
>  This component is supported since API version 4. Updates will be marked with a superscript to indicate their earliest API version.

The **\<Slider>** component is used to quickly adjust settings, such as the volume and brightness.


## Child Components

Not supported


## Attributes

In addition to the [universal attributes](../arkui-js/js-components-common-attributes.md), the following attributes are supported.

| Name| Type| Default Value| Mandatory| Description|
| -------- | -------- | -------- | -------- | -------- |
| min | number | 0 | No| Minimum value of the slider.|
| max | number | 100 | No| Maximum value of the slider.|
| step | number | 1 | No| Step of each slide.|
| value | number | 0 | No| Initial value of the slider.|
| mode<sup>5+</sup> | string | outset | No| Slider style. Available values are as follows:<br>- **outset**: The slider is on the sliding bar.<br>- **inset**: The slider is inside the sliding bar.|
| showsteps<sup>5+</sup> | boolean | false | No| Whether to display slider scales.|
| showtips<sup>5+</sup> | boolean | false | No| Whether a tooltip is displayed to show the percentage value on the slider.|


## Styles

In addition to the [universal styles](../arkui-js/js-components-common-styles.md), the following styles are supported.

| Name| Type| Default Value| Mandatory| Description|
| -------- | -------- | -------- | -------- | -------- |
| color | &lt;color&gt; | #19000000 | No| Background color of the slider.|
| selected-color | &lt;color&gt; | #ff007dff | No| Selected color of the slider.|
| block-color | &lt;color&gt; | \#ffffff | No| Slider color.|


## Events

In addition to the [universal events](../arkui-js/js-components-common-events.md), the following events are supported.

| Name| Parameter| Description|
| -------- | -------- | -------- |
| change | ChangeEvent | Triggered when the value changes.|

**Table 1** ChangeEvent

| Attribute| Type| Description|
| -------- | -------- | -------- |
| value<sup>5+</sup> | number | Current value of the slider.|
| mode<sup>5+</sup> | string | Type of the change event. Available values are as follows:<br>- **start**: The **value** starts to change.<br>- **move**: The **value** is changing with users' dragging.<br>- **end**: The **value** stops changing.|


## Example

```html
<!-- xxx.hml -->
<div class="container">
  <text>slider start value is {{startValue}}</text>
  <text>slider current value is {{currentValue}}</text>
  <text>slider end value is {{endValue}}</text>
  <slider min="0" max="100" value="{{value}}" onchange="setvalue" ></slider>
</div>
```

```css
/* xxx.css */
.container {
  flex-direction: column;
  justify-content: center;
  align-items: center;
  
}
```

```js
// xxx.js
export default {
  data: {
    value: 0,
    startValue: 0,
    currentValue: 0,
    endValue: 0,
  },
  setvalue(e) {
    if (e.mode == "start") {
      this.value = e.value;
      this.startValue = e.value;
    } else if (e.mode == "move") {
      this.value = e.value;
      this.currentValue = e.value;
    } else if (e.mode == "end") {
      this.value = e.value;
      this.endValue = e.value;
    } else if (e.mode == "click) {
      this.value = e.value;
      this.currentValue = e.value;
    }
  }
}
```

![slider](figures/slider.png)
