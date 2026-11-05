# @ohos.application.AccessibilityExtensionAbility (AccessibilityExtensionAbility)

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

The **AccessibilityExtensionAbility** module provides accessibility extension capabilities based on the ExtensionAbility framework.

> NOTE
>
> * The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

> phone | 2in1 | tablet | wearable

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';
```

## AccessibilityExtensionAbility

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

The **AccessibilityExtensionAbility** module provides accessibility extension capabilities based on the ExtensionAbility framework.

### Properties

> phone | 2in1 | tablet | wearable

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| context | [AccessibilityExtensionContext](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext) | No | No | Context of the accessibility extension ability. |

## AccessibilityEvent

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Defines an accessibility event.

### Properties

> phone | 2in1 | tablet | wearable

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| eventType | [accessibility.EventType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-accessibility#eventtype) \| [accessibility.WindowUpdateType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-accessibility#windowupdatetype) \| [TouchGuideType](#touchguidetype) \| [GestureType](#gesturetype) \| [PageUpdateType](#pageupdatetype) | No | No | Event type. **EventType**: accessibility event type. **WindowUpdateType**: window update type. **TouchGuideType**: touch guide type. **GestureType**: gesture type. **PageUpdateType**: page update type. |
| target | [AccessibilityElement](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#accessibilityelement) | No | Yes | Target component where the event occurs. |
| timeStamp | number | No | Yes | Timestamp of the event, in milliseconds. The default value is **0**. |
| elementId^12+^ | number | No | Yes | Component ID for auto-focusing. The default value is **0**. |
| textAnnouncedForAccessibility^12+^ | string | No | Yes | Content for auto-broadcasting. Set the broadcast content based on the actual scenario. No special restrictions. |
| extraInfo^20+^ | string | No | Yes | Added or deleted text content carried by the **TextArea**, **TextInput**, **SearchField**, or **RichEdit** component. Set this parameter based on site requirements. No special restrictions. |

## AccessibilityElement^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type AccessibilityElement = _AccessibilityElement

Indicates an accessibility element. For details, see [AccessibilityElement](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#accessibilityelement).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _AccessibilityElement | Indicates an accessibility element. For details, see [AccessibilityElement](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#accessibilityelement). |

**Example**

```ts
import { AccessibilityElement } from '@kit.AccessibilityKit';

let accessibilityElement: AccessibilityElement;
```

## ElementAttributeValues^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type ElementAttributeValues = _ElementAttributeValues

Provides attribute names and value types of a node element. For details, see [ElementAttributeValues](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#elementattributevalues).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _ElementAttributeValues | Attribute names and value types of a node element. For details, see [ElementAttributeValues](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#elementattributevalues). |

**Example**

```ts
import { ElementAttributeValues } from '@kit.AccessibilityKit';

let elementAttributeValues: ElementAttributeValues;
```

## FocusDirection^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type FocusDirection = _FocusDirection

Enumerates the focus directions. For details, see [FocusDirection](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#focusdirection).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _FocusDirection | Focus directions. For details, see [FocusDirection](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#focusdirection). |

**Example**

```ts
import { FocusDirection } from '@kit.AccessibilityKit';

let focusDirection: FocusDirection;
```

## ElementAttributeKeys^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type ElementAttributeKeys = keyof ElementAttributeValues

Describes the attribute name of [ElementAttributeValues](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#elementattributevalues).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| keyof [ElementAttributeValues](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#elementattributevalues) | Union type of all attribute names in [ElementAttributeValues](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#elementattributevalues). |

**Example**

```ts
import { ElementAttributeKeys } from '@kit.AccessibilityKit';

let elementAttributeKeys: ElementAttributeKeys;
```

## FocusType^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type FocusType = _FocusType

Enumerates the focus types. For details, see [FocusType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#focustype).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _FocusType | Focus types. For details, see [FocusType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#focustype). |

**Example**

```ts
import { FocusType } from '@kit.AccessibilityKit';

let focusType: FocusType;
```

## WindowType ^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type WindowType = _WindowType

Enumerates the window types. For details, see [WindowType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#windowtype).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _WindowType | Window types. For details, see [WindowType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#windowtype). |

**Example**

```ts
import { WindowType } from '@kit.AccessibilityKit';

let windowType: WindowType;
```

## Rect^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type Rect = _Rect

Defines a rectangle. For details, see [Rect](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#rect).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _Rect | Rectangle. For details, see [Rect](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext#rect). |

**Example**

```ts
import { Rect } from '@kit.AccessibilityKit';

let rect: Rect;
```

## AccessibilityExtensionContext^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type AccessibilityExtensionContext = _AccessibilityExtensionContext.default

Defines the context of the accessibility extension. For details, see [AccessibilityExtensionContext](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext).

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| _AccessibilityExtensionContext.default | Context of the accessibility extension. For details, see [AccessibilityExtensionContext](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-inner-application-accessibilityextensioncontext). |

**Example**

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class EntryAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    let axContext = this.context;
  }
}
```

## GestureType

> phone | 2in1 | tablet | wearable

type GestureType = 'left' | 'leftThenRight' | 'leftThenUp' | 'leftThenDown' | 'right' | 'rightThenLeft' | 'rightThenUp' | 'rightThenDown' | 'up' | 'upThenLeft' | 'upThenRight' | 'upThenDown' | 'down' | 'downThenLeft' | 'downThenRight' | 'downThenUp' | 'twoFingerSingleTap' | 'twoFingerDoubleTap' | 'twoFingerDoubleTapAndHold' | 'twoFingerTripleTap' | 'twoFingerTripleTapAndHold' | 'threeFingerSingleTap' | 'threeFingerDoubleTap' | 'threeFingerDoubleTapAndHold' | 'threeFingerTripleTap' | 'threeFingerTripleTapAndHold' | 'fourFingerSingleTap' | 'fourFingerDoubleTap' | 'fourFingerDoubleTapAndHold' | 'fourFingerTripleTap' | 'fourFingerTripleTapAndHold' | 'threeFingerSwipeUp' | 'threeFingerSwipeDown' | 'threeFingerSwipeLeft' | 'threeFingerSwipeRight' | 'fourFingerSwipeUp' | 'fourFingerSwipeDown' | 'fourFingerSwipeLeft' | 'fourFingerSwipeRight'

Enumerates gesture types.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'left' | Left gesture. |
| 'leftThenRight' | Left-then-right gesture. |
| 'leftThenUp' | Left-then-up gesture. |
| 'leftThenDown' | Left-then-down gesture. |
| 'right' | Right gesture. |
| 'rightThenLeft' | Right-then-left gesture. |
| 'rightThenUp' | Right-then-up gesture. |
| 'rightThenDown' | Right-then-down gesture. |
| 'up' | Up gesture. |
| 'upThenLeft' | Up-then-left gesture. |
| 'upThenRight' | Up-then-right gesture. |
| 'upThenDown' | Up-then-down gesture. |
| 'down' | Down gesture. |
| 'downThenLeft' | Down-then-left gesture. |
| 'downThenRight' | Down-then-right gesture. |
| 'downThenUp' | Down-then-up gesture. |
| 'twoFingerSingleTap'^11+^ | Two-finger single-tap gesture. |
| 'twoFingerDoubleTap'^11+^ | Two-finger double-tap gesture. |
| 'twoFingerDoubleTapAndHold'^11+^ | Two-finger double-tap-and-hold gesture. |
| 'twoFingerTripleTap'^11+^ | Two-finger triple-tap gesture. |
| 'twoFingerTripleTapAndHold'^11+^ | Two-finger triple-tap-and-hold gesture. |
| 'threeFingerSingleTap'^11+^ | Three-finger single-tap gesture. |
| 'threeFingerDoubleTap'^11+^ | Three-finger double-tap gesture. |
| 'threeFingerDoubleTapAndHold'^11+^ | Three-finger double-tap-and-hold gesture. |
| 'threeFingerTripleTap'^11+^ | Three-finger triple-tap gesture. |
| 'threeFingerTripleTapAndHold'^11+^ | Three-finger triple-tap-and-hold gesture. |
| 'fourFingerSingleTap'^11+^ | Four-finger single-tap gesture. |
| 'fourFingerDoubleTap'^11+^ | Four-finger double-tap gesture. |
| 'fourFingerDoubleTapAndHold'^11+^ | Four-finger double-tap-and-hold gesture. |
| 'fourFingerTripleTap'^11+^ | Four-finger triple-tap gesture. |
| 'fourFingerTripleTapAndHold'^11+^ | Four-finger triple-tap-and-hold gesture. |
| 'threeFingerSwipeUp'^11+^ | Three-finger swipe-up gesture. |
| 'threeFingerSwipeDown'^11+^ | Three-finger swipe-down gesture. |
| 'threeFingerSwipeLeft'^11+^ | Three-finger swipe-left gesture. |
| 'threeFingerSwipeRight'^11+^ | Three-finger swipe-right gesture. |
| 'fourFingerSwipeUp'^11+^ | Four-finger swipe-up gesture. |
| 'fourFingerSwipeDown'^11+^ | Four-finger swipe-down gesture. |
| 'fourFingerSwipeLeft'^11+^ | Four-finger swipe-left gesture. |
| 'fourFingerSwipeRight'^11+^ | Four-finger swipe-right gesture. |

## PageUpdateType

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate'

Enumerates the page update types.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'pageContentUpdate' | Update of the page content. |
| 'pageStateUpdate' | Update of the page status. |

## TouchGuideType

> phone | 2in1 | tablet | wearable

type TouchGuideType = 'touchBegin' | 'touchEnd'

Enumerates the touch guide event types.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'touchBegin' | Start of touch. |
| 'touchEnd' | End of touch. |

## AccessibilityExtensionAbility.onConnect^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

onConnect(): void;

Called when the **AccessibilityExtensionAbility** is enabled and connected to the system service. In this API, you can have the service logic initialized. This API can be overridden as required.

> NOTE
>
> This API is supported since API version 9 and deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Example**

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onConnect(): void {
    console.info('AxExtensionAbility onConnect');
  }
}
```

## AccessibilityExtensionAbility.onDisconnect^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

onDisconnect(): void;

Called when the **AccessibilityExtensionAbility** is disabled and disconnected from the system service. In this API, you can implement the service logic of resource release and exit. This API can be overridden as required.

> NOTE
>
> This API is supported since API version 9 and deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Example**

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onDisconnect(): void {
    console.info('AxExtensionAbility onDisconnect');
  }
}
```

## AccessibilityExtensionAbility.onAccessibilityEvent^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

onAccessibilityEvent(event: AccessibilityEvent): void;

Called when an event that matches the specified bundle and event type occurs. In this API, you can implement event-specific service logic. Generally, this API needs to be overridden.

> NOTE
>
> This API is supported since API version 9 and deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [AccessibilityEvent](#accessibilityevent) | Yes | Accessibility event. No return value. |

**Example**

```ts
import { AccessibilityExtensionAbility, AccessibilityEvent } from '@kit.AccessibilityKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onAccessibilityEvent(event: AccessibilityEvent): void {
    console.info('AxExtensionAbility onAccessibilityEvent');
    if (event.eventType === 'click') {
      console.info('AxExtensionAbility onAccessibilityEvent: click');
    }
  }
}
```

## AccessibilityExtensionAbility.onKeyEvent^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

onKeyEvent(keyEvent: KeyEvent): boolean;

Called when a physical key is pressed. In this API, you can determine whether to consume the event based on the service.

> NOTE
>
> This API is supported since API version 9 and deprecated since API version 12. Related capabilities are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyEvent | [KeyEvent](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-keyevent#keyevent) | Yes | Key event. If **true** is returned, the key is consumed. |

**Return value**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the event is consumed and will not be transferred; returns **false** if the event is not consumed and will be transferred. |

**Example**

```ts
import { AccessibilityExtensionAbility } from '@kit.AccessibilityKit';
import { KeyEvent } from '@kit.InputKit';

class MyAccessibilityExtensionAbility extends AccessibilityExtensionAbility {
  onKeyEvent(keyEvent: KeyEvent): boolean {
    console.info('AxExtensionAbility onKeyEvent');
    if (keyEvent.key.code === 16) {
      console.info('AxExtensionAbility onKeyEvent: intercept 16');
      return true;
    }
    return false;
  }
}
```
