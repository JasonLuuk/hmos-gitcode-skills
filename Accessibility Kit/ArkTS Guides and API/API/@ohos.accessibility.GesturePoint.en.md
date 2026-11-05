# @ohos.accessibility.GesturePoint (Gesture Point)

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

The **GesturePoint** module provides APIs for creating gesture touch point information required for an accessibility application to inject gestures.

> NOTE
>
> * The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

> phone | 2in1 | tablet | wearable

```ts
import { GesturePoint } from '@kit.AccessibilityKit';
```

## GesturePoint

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Defines a gesture touch point.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

### Attributes

> phone | 2in1 | tablet | wearable

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| positionX | number | No | No | X coordinate of the touch point, in pixels (px). |
| positionY | number | No | No | Y coordinate of the touch point, in pixels (px). |

### constructor^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

constructor(positionX: number, positionY: number);

Defines a constructor used to create a **GesturePoint** instance.

> NOTE
>
> This API is supported since API version 9 and deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| positionX | number | Yes | X coordinate of the touch point, in pixels (px). |
| positionY | number | Yes | Y coordinate of the touch point, in pixels (px). |

**Example**

```ts
import { GesturePoint } from '@kit.AccessibilityKit';

let gesturePoint = new GesturePoint(1, 2);
```
