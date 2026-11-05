# @ohos.accessibility.GesturePath (Gesture Path)

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

The **GesturePath** module provides APIs for creating gesture path information required for an accessibility application to inject gestures.

> NOTE
>
> * The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

> phone | 2in1 | tablet | wearable

```ts
import { GesturePath } from '@kit.AccessibilityKit';
```

## GesturePath

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Defines a gesture path.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

### Properties

> phone | 2in1 | tablet | wearable

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| points | Array<[GesturePoint](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-accessibility-gesturepoint#gesturepoint)> | No | No | Gesture touch point. |
| durationTime | number | No | No | Total gesture duration, in milliseconds. |

### constructor^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

constructor(durationTime: number);

Defines a constructor used to create a **GesturePath** instance.

> NOTE
>
> This API is supported since API version 9 and deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| durationTime | number | Yes | Total gesture duration, in milliseconds. |

**Example**

```ts
import { GesturePath } from '@kit.AccessibilityKit';

let gesturePath = new GesturePath(20);
```
