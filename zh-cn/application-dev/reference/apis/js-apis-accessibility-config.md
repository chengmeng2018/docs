# 系统辅助功能配置

本模块提供系统辅助功能的配置，包括辅助扩展的启用与关闭、高对比度文字显示、鼠标键、无障碍字幕配置等。

> ![icon-note.gif](public_sys-resources/icon-note.gif) **说明：**
> 本模块首批接口从 API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口为系统接口。

## 导入模块

```typescript
import config from "@ohos.accessibility.config";
```

## 属性

**系统能力**：以下各项对应的系统能力均为SystemCapability.BarrierFree.Accessibility.Core

| 名称 | 参数类型 | 可读 | 可写 | 说明 | 
| -------- | -------- | -------- | -------- | -------- |
| highContrastText | [Config](#config)\<boolean>| 是 | 是 | 表示高对比度文字功能启用状态。 |
| invertColor | [Config](#config)\<boolean>| 是 | 是 | 表示颜色反转功能启用状态。 |
| daltonizationColorFilter | [Config](#config)&lt;[DaltonizationColorFilter](#daltonizationcolorfilter)&gt;| 是 | 是 | 表示颜色滤镜功能配置。 |
| contentTimeout | [Config](#config)\<number>| 是 | 是 | 表示内容显示建议时长配置。取值 0~5000，单位为毫秒。 |
| animationOff | [Config](#config)\<boolean>| 是 | 是 | 表示关闭动画功能启用状态。 |
| brightnessDiscount | [Config](#config)\<number>| 是 | 是 | 表示亮度折扣系统配置。取值 0~1.0。 |
| mouseKey | [Config](#config)\<boolean>| 是 | 是 | 表示鼠标键功能启用状态。 |
| mouseAutoClick | [Config](#config)\<number>| 是 | 是 | 表示鼠标自动点击功能启用状态。取值 0~5000，单位为毫秒。 |
| shortkey | [Config](#config)\<boolean>| 是 | 是 | 表示辅助扩展快捷键功能启用状态。 |
| shortkeyTarget | [Config](#config)\<string>| 是 | 是 | 表示辅助扩展快捷键的目标配置。取值为辅助应用的名称，格式为："bundleName/abilityName"。 |
| captions | [Config](#config)\<boolean>| 是 | 是 | 表示辅助字幕功能启用状态。 |
| captionsStyle | [Config](#config)\<[accessibility.CaptionsStyle](./js-apis-accessibility.md#captionsstyle8)>| 是 | 是 | 表示辅助字幕的配置。 |

## enableAbility

enableAbility(name: string, capability: Array&lt;[accessibility.Capability](./js-apis-accessibility.md#capability)&gt;): Promise&lt;void&gt;;

启用辅助扩展。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | name | string | 是 | 辅助应用的名称，格式为："bundleName/abilityName"。 |
  | capability | Array&lt;[accessibility.Capability](./js-apis-accessibility.md#capability)&gt;) | 是 | 辅助应用的能力属性。 |

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise实例，用于返回方法执行结果。 |

**示例：**

  ```typescript
  config.enableAbility("com.ohos.example/axExtension", ['retrieve'])
      .then(() => {
        console.info('enable succeed');
      }).catch((error) => {
        console.error('enable failed');
      });
  ```

## enableAbility

enableAbility(name: string, capability: Array&lt;[accessibility.Capability](./js-apis-accessibility.md#capability)&gt;, callback: AsyncCallback&lt;void&gt;): void;

启用辅助扩展。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | name | string | 是 | 辅助应用的名称，格式为："bundleName/abilityName"。 |
  | capability | Array&lt;[accessibility.Capability](./js-apis-accessibility.md#capability)&gt; | 是 | 辅助应用的能力属性。 |
  | callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，返回方法执行结果。 |

**示例：**

  ```typescript
  config.enableAbility("com.ohos.example/axExtension", ['retrieve'], (err, data) => {
      if (err) {
          console.error('enable failed');
          return;
      }
      console.info('enable succeed');
    })
  ```

## disableAbility

disableAbility(name: string): Promise&lt;void&gt;;

关闭辅助扩展。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | name | string | 是 | 辅助应用的名称，格式为："bundleName/abilityName"。 |

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise实例，用于返回方法执行结果。 |

**示例：**

  ```typescript
  config.disableAbility("com.ohos.example/axExtension")
      .then(() => {
        console.info('disable succeed');
      }).catch((error) => {
        console.error('disable failed');
      });
  ```

## disableAbility

disableAbility(name: string, callback: AsyncCallback&lt;void&gt;): void;

关闭辅助扩展。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | name | string | 是 | 辅助应用的名称，格式为："bundleName/abilityName"。 |
  | callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，返回方法执行结果。 |

**示例：**

  ```typescript
  config.disableAbility("com.ohos.example/axExtension", (err, data) => {
      if (err) {
          console.error('disable failed');
          return;
      }
      console.info('disable succeed');
    })
  ```

## on('enableAbilityListsStateChanged')

on(type: 'enableAbilityListsStateChanged', callback: Callback&lt;void&gt;): void;

添加启用的辅助扩展的列表变化监听。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | type | string | 是 | 参数固定为enableAbilityListsStateChanged，监听启用的辅助扩展的列表变化。 |
  | callback | Callback&lt;void&gt; | 是 | 回调函数，在启用的辅助扩展的列表变化时通过此函数进行通知。 |

**示例：**

  ```typescript
  config.on('enableAbilityListsStateChanged',() => {
      console.info('ax extension ability enable list changed');
  });
  ```

## off('enableAbilityListsStateChanged')

off(type: 'enableAbilityListsStateChanged', callback?: Callback&lt;void&gt;): void;

取消启用的辅助扩展的列表变化监听。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | type |  string | 否 | 参数固定为enableAbilityListsStateChanged，监听启用的辅助扩展的列表变化。 |
  | callback | Callback&lt;void&gt; | 否 | 要取消的监听回调函数。 |

**示例：**

  ```typescript
  config.off('enableAbilityListsStateChanged');
  ```

## Config

用于属性的设置、获取与监听。

### set

set(value: T): Promise&lt;void&gt;;

设置属性。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | value | T | 是 | 设置的属性值。 |

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;void&gt; | Promise实例，用于返回方法执行结果。 |

**示例：**

  ```typescript
  config.highContrastText.set(true)
      .then(() => {
        console.info('highContrastText set succeed');
      }).catch((error) => {
        console.error('highContrastText set failed');
      });
  ```

### set

set(value: T, callback: AsyncCallback&lt;void&gt;): void;

设置属性。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | value | T | 是 | 设置的属性值。 |
  | callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，返回方法执行结果。 |

**示例：**

  ```typescript
  config.highContrastText.set(true, (err, data) => {
      if (err) {
          console.error('highContrastText set failed');
          return;
      }
      console.info('highContrastText set succeed');
    })
  ```

### get

get(): Promise&lt;T&gt;;

获取属性。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**返回值：**

  | 类型 | 说明 |
  | -------- | -------- |
  | Promise&lt;T&gt; | Promise实例，用于返回属性值。 |

**示例：**

  ```typescript
  config.highContrastText.get()
      .then((value) => {
        console.info('highContrastText get succeed');
      }).catch((error) => {
        console.error('highContrastText get failed');
      });
  ```

### get

get(callback: AsyncCallback&lt;T&gt;): void;

获取属性。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callback | AsyncCallback&lt;void&gt; | 是 | 回调函数，返回属性值。 |

**示例：**

  ```typescript
  config.highContrastText.get((err, data) => {
      if (err) {
          console.error('highContrastText get failed');
          return;
      }
      console.info('highContrastText get succeed');
    })
  ```

### on

on(callback: Callback&lt;T&gt;): void;

添加属性变化监听。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callback | Callback&lt;T&gt; | 是 | 回调函数，在属性变化时通过此函数进行通知。 |

**示例：**

  ```typescript
  config.highContrastText.on(() => {
      console.info('highContrastText changed');
  });
  ```

### off

off(callback?: Callback&lt;T&gt;): void;

取消属性变化监听。

**系统能力**：SystemCapability.BarrierFree.Accessibility.Core

**参数：**

  | 参数名 | 参数类型 | 必填 | 说明 |
  | -------- | -------- | -------- | -------- |
  | callback | Callback&lt;T&gt; | 否 | 要取消的监听回调函数。 |

**示例：**

  ```typescript
  config.highContrastText.off();
  ```

## DaltonizationColorFilter

用于不同弱视类型的校正颜色滤镜。

**系统能力**：以下各项对应的系统能力均为 SystemCapability.BarrierFree.Accessibility.Core

| 名称 | 描述 |
| -------- | -------- |
| Normal | 表示正常类型。 |
| Protanomaly | 表示红色弱视类型。 |
| Deuteranomaly | 表示绿色弱视类型。 |
| Tritanomaly  | 表示蓝色弱视类型。 |