# @ohos.accessibility (Accessibility)

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

The **Accessibility** module implements the accessibility features, including obtaining the accessibility application list, accessibility application enabling state, and captions configuration.

> NOTE
>
> * The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

> phone | 2in1 | tablet | wearable

```ts
import { accessibility } from '@kit.AccessibilityKit';
```

## AbilityState

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type AbilityState = 'enable' | 'disable' | 'install'

Enumerates the states of an accessibility application.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'enable' | The accessibility application is enabled. |
| 'disable' | The accessibility application is disabled. |
| 'install' | The accessibility application has been installed. |

## AbilityType

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type AbilityType = 'audible' | 'generic' | 'haptic' | 'spoken' | 'visual' | 'all'

Enumerates the types of accessibility applications.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'audible' | The accessibility application provides audible feedback. |
| 'generic' | The accessibility application provides generic feedback. |
| 'haptic' | The accessibility application provides haptic feedback. |
| 'spoken' | The accessibility application provides spoken feedback. |
| 'visual' | The accessibility application provides visual feedback. |
| 'all'^9+^ | All the preceding types. |

## AccessibilityAbilityInfo

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Provides information about an accessibility application.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

### Properties

> phone | 2in1 | tablet | wearable

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| id | string | Yes | No | Ability ID. |
| name | string | Yes | No | Ability name. |
| bundleName | string | Yes | No | Bundle name. |
| targetBundleNames^9+^ | Array<string> | Yes | No | Name of the target bundle. |
| abilityTypes | Array<[AbilityType](#abilitytype)> | Yes | No | Accessibility application type. |
| capabilities | Array<[Capability](#capability)> | Yes | No | Capabilities list of the accessibility application. |
| description | string | Yes | No | Description of the accessibility application. |
| eventTypes | Array<[EventType](#eventtype)> | Yes | No | List of events that the accessibility application focuses on. |
| needHide^12+^ | boolean | Yes | No | Whether the auxiliary application is hidden in the list of installed extended services. The value **true** means the auxiliary application is hidden, and the value **false** means the opposite. |
| label^12+^ | string | Yes | No | Name of the application in the extended service list. |

## Action

> phone | 2in1 | tablet | wearable

type Action = 'accessibilityFocus' | 'clearAccessibilityFocus' | 'focus' | 'clearFocus' | 'clearSelection' |

'click' | 'longClick' | 'cut' | 'copy' | 'paste' | 'select' | 'setText' | 'delete' |

'scrollForward' | 'scrollBackward' | 'setSelection' | 'setCursorPosition' | 'home' |

'back' | 'recentTask' | 'notificationCenter' | 'controlCenter' | 'common' | 'injectAction'

Target actions supported by the application. The target actions for which parameters need to be set have been specified in the description of the following table.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'click' | Click. |
| 'longClick' | Long press. |
| 'scrollForward' | Scroll forward. |
| 'scrollBackward' | Scroll backward. |
| 'focus' | Obtain a focus. |
| 'clearFocus' | Clear a focus. |
| 'clearSelection' | Clear selection. Not supported yet. |
| 'accessibilityFocus' | Obtain an accessibility focus. |
| 'clearAccessibilityFocus' | Clear an accessibility focus. |
| 'cut' | Cut. |
| 'copy' | Copy. |
| 'paste' | Paste. |
| 'select' | Select. |
| 'setText' | Set text. You need to set the **setText** parameter. |
| 'delete' | Delete. Not supported yet. |
| 'setSelection' | Select. You need to set the **selectTextBegin**, **selectTextEnd** and **selectTextInForWard** parameters. |
| 'common' | Common actions used in auto-focusing and auto-broadcasting. |
| 'home' | Return to the home screen. |
| 'back' | Return to the previous screen. |
| 'recentTask' | Open a recent task. |
| 'notificationCenter' | Open the notification bar. |
| 'controlCenter' | Open the control center. |
| 'setCursorPosition' | Set cursor location. You need to set the **offset** parameter. |
| 'injectAction' | Injection action. The **injectActionType** parameter must be set. **Since**: 26.0.0 **Model restriction**: This API can be used only in the stage model. |

## Capability

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type Capability = 'retrieve' | 'touchGuide' | 'keyEventObserver' | 'zoom' | 'gesture'

Enumerates the capabilities of an accessibility application.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'retrieve' | Capability to retrieve the window content. |
| 'touchGuide' | Capability of touch guide mode. |
| 'keyEventObserver' | Capability to filter key events. |
| 'zoom' | Capability to control the display zoom level. Not supported currently. |
| 'gesture' | Capability to perform gesture actions. |

## CaptionsFontEdgeType^8+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type CaptionsFontEdgeType = 'none' | 'raised' | 'depressed' | 'uniform' | 'dropShadow'

Enumerates the font edge types of captions.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

| Type | Description |
| --- | --- |
| 'none' | No effect. |
| 'raised' | Raised effect. |
| 'depressed' | Depressed effect. |
| 'uniform' | Uniform effect. |
| 'dropShadow' | Drop shadow effect. |

## CaptionsFontFamily^8+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type CaptionsFontFamily = 'default' | 'monospacedSerif' | 'serif' | 'monospacedSansSerif' |

'sansSerif' | 'casual' | 'cursive' | 'smallCapitals'

Enumerates the font families of captions.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

| Type | Description |
| --- | --- |
| 'default' | Default font family. |
| 'monospacedSerif' | Monospaced Serif fonts, which use the same width for each character. |
| 'serif' | Serif fonts. |
| 'monospacedSansSerif' | Monospaced Sans Serif fonts, which use the same width for each character. |
| 'sansSerif' | Sans Serif fonts. |
| 'casual' | Casual fonts. |
| 'cursive' | Cursive fonts. |
| 'smallCapitals' | Small caps fonts. |

## CaptionsStyle^8+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Describes the style of captions.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| fontFamily | [CaptionsFontFamily](#captionsfontfamily8) | No | No | Font family of captions. |
| fontScale | number | No | No | Font scale factor of captions, in percentage. The value ranges from 1 to 200. |
| fontColor | number \| string | No | No | Font color of captions. **number**: HEX format, used to represent colors defined in either the RGB or ARGB color models. **string**: #rrggbb, #rrggbbaa, #rgb, or #rgba format. Example: opaque red; number: 0xffff0000; string: '#ff0000', '#ff0000ff', '#f00', or '#f00f' |
| fontEdgeType | [CaptionsFontEdgeType](#captionsfontedgetype8) | No | No | Font edge type of captions. |
| backgroundColor | number \| string | No | No | Background color of captions. **number**: HEX format, used to represent colors defined in either the RGB or ARGB color models. **string**: #rrggbb, #rrggbbaa, #rgb, or #rgba format. Example: opaque red; number: 0xffff0000; string: '#ff0000', '#ff0000ff', '#f00', or '#f00f' |
| windowColor | number \| string | No | No | Window color of captions. **number**: HEX format, used to represent colors defined in either the RGB or ARGB color models. **string**: #rrggbb, #rrggbbaa, #rgb, or #rgba format. Example: opaque red; number: 0xffff0000; string: '#ff0000', '#ff0000ff', '#f00', or '#f00f' |

## CaptionsManager^8+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Implements configuration management for captions. Before calling any API of **CaptionsManager**, you must use the [accessibility.getCaptionsManager()](#accessibilitygetcaptionsmanagerdeprecated) API to obtain a **CaptionsManager** instance.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

### Properties

> phone | 2in1 | tablet | wearable

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| enabled | boolean | No | No | Whether to enable captions configuration. The value **true** indicates that the caption configuration is enabled, and **false** indicates the opposite. |
| style | [CaptionsStyle](#captionsstyle8) | No | No | Style of captions. |

### on('enableChange')^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

on(type: 'enableChange', callback: Callback<boolean>): void;

Subscribes to the state changes of captions configuration. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   off('enableChange')
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.
> * This API is supported since API version 8 and deprecated since API version 12. Related features are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'enableChange'** in this API. |
| callback | Callback<boolean> | Yes | Callback invoked when the enabled status of captions configuration changes. The value **true** indicates that the subtitle configuration is enabled, and the value **false** indicates that the subtitle configuration is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

### on('styleChange')^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

on(type: 'styleChange', callback: Callback<CaptionsStyle>): void;

Subscribes to captions style changes. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   off('styleChange')
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.
> * This API is supported since API version 8 and deprecated since API version 12. Related features are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'styleChange'** in this API. |
| callback | Callback<[CaptionsStyle](#captionsstyle8)> | Yes | Callback invoked when the style of captions changes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

### off('enableChange')^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

off(type: 'enableChange', callback?: Callback<boolean>): void;

Unsubscribes from the state changes of captions configuration. This API uses an asynchronous callback to return the result.

> NOTE
>
> This API is supported since API version 8 and deprecated since API version 12. Related features are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'enableChange'** in this API. |
| callback | Callback<boolean> | No | Callback used to unregister. It must be consistent with the callback used in [on('enableChange')](#onenablechangedeprecated). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

### off('styleChange')^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

off(type: 'styleChange', callback?: Callback<CaptionsStyle>): void;

Unsubscribes from the captions style changes. This API uses an asynchronous callback to return the result.

> NOTE
>
> This API is supported since API version 8 and deprecated since API version 12. Related features are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'styleChange'** in this API. |
| callback | Callback<[CaptionsStyle](#captionsstyle8)> | No | Callback used to unregister. It must be consistent with the callback used in [on('styleChange')](#onstylechangedeprecated). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## EventInfo

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

Describes a GUI change event.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

### Properties

> phone | 2in1 | tablet | wearable

| Name | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| type | [EventType](#eventtype) | No | No | Accessibility event type (mandatory). |
| windowUpdateType | [WindowUpdateType](#windowupdatetype) | No | Yes | Window update type. |
| bundleName | string | No | No | Name of the target application (mandatory). |
| componentType | string | No | Yes | It should correspond to the event source component type, and the default value is empty. Example: - Button type - > 'Button' - Image type - > 'Image' |
| pageId | number | No | Yes | ID of the page where the event occurs. The default value is **0**. |
| description | string | No | Yes | Event description, which is set according to the actual scenario with no special restrictions, and the default value is empty. |
| triggerAction | [Action](#action) | No | No | Action that triggers the event (mandatory). |
| textMoveUnit | [TextMoveUnit](#textmoveunit) | No | Yes | Text moving granularity. The default value is char. |
| contents | Array<string> | No | Yes | Content list, which is set according to the actual scenario with no special restrictions. The default value is empty. |
| lastContent | string | No | Yes | Latest content, which is set according to the actual scenario with no special restrictions. The default value is empty. |
| beginIndex | number | No | Yes | Start index. The default value is **0**. |
| currentIndex | number | No | Yes | Current index. The default value is **0**. |
| endIndex | number | No | Yes | End index. The default value is **0**. |
| itemCount | number | No | Yes | Total number of items. The default value is **0**. |
| elementId^12+^ | number | No | Yes | Element ID of the component. The default value is **0**. |
| textAnnouncedForAccessibility^12+^ | string | No | Yes | Content for auto-broadcasting. When the application needs to proactively broadcast, set the broadcast content according to the actual scenario with no special restrictions, and the default value is empty. |
| textResourceAnnouncedForAccessibility^18+^ | Resource | No | Yes | Content for auto-broadcasting. The value is a string of the **Resource** type. |
| customId^12+^ | string | No | Yes | Component ID for active focusing, and the default value is empty. |

### constructor

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

constructor(jsonObject: Object)

Constructor, which is used to construct an EventInfo instance using a JSON object.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| jsonObject | Object | Yes | JSON object that contains the **type**, **bundleName**, and **triggerAction** fields. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});
```

### constructor^11+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

constructor(type: EventType, bundleName: string, triggerAction: Action)

Constructor, which is used to construct an EventInfo instance using independent parameters.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [EventType](#eventtype) | Yes | Accessibility event types. |
| bundleName | string | Yes | Target application name. |
| triggerAction | [Action](#action) | Yes | Action that triggers the event. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo = new accessibility.EventInfo('click', 'com.example.MyApplication', 'click');
```

## EventType

> phone | 2in1 | tablet | wearable

type EventType = 'accessibilityFocus' | 'accessibilityFocusClear' |

'click' | 'longClick' | 'focus' | 'select' | 'hoverEnter' | 'hoverExit' |

'textUpdate' | 'textSelectionUpdate' | 'scroll' | 'requestFocusForAccessibility' |

'announceForAccessibility' | 'requestFocusForAccessibilityNotInterrupt' |

'announceForAccessibilityNotInterrupt' | 'scrolling' | 'pageActive' | 'notificationUpdate'

Accessibility event types.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'accessibilityFocus' | Event indicating that the accessibility focus is obtained. |
| 'accessibilityFocusClear' | Event indicating that the accessibility focus is cleared. |
| 'click' | Event of clicking a component. |
| 'longClick' | Event indicating that the component is long pressed. |
| 'select' | Event of selecting a component. |
| 'hoverEnter' | Event indicating that the hover enters a component. |
| 'hoverExit' | Event indicating that the hover exits a component. |
| 'focus' | Event indicating that the component obtains the focus. Not supported currently. |
| 'textUpdate' | Event indicating that the component text has been updated. |
| 'textSelectionUpdate' | Event indicating that the selected text has been updated. Not supported currently. |
| 'scroll' | Event of the scroll view. |
| 'requestFocusForAccessibility' | Event of the auto-focusing. |
| 'announceForAccessibility' | Event of the auto-broadcasting. |
| 'requestFocusForAccessibilityNotInterrupt'^18+^ | Event of the auto-focusing without interruption. |
| 'announceForAccessibilityNotInterrupt'^18+^ | Event of the auto-broadcasting without interruption. |
| 'scrolling'^18+^ | Event indicating that an item is scrolled out of the screen in the scrolling view. |
| 'pageActive'^23+^ | Event indicating that a page changes. The value is fixed at **'pageActive'**. |
| 'notificationUpdate' | Event indicating that a notification changes. The value is fixed at **'notificationUpdate'**. **Since**: 26.0.0 |

## TextMoveUnit

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type TextMoveUnit = 'char' | 'word' | 'line' | 'page' | 'paragraph'

Enumerates the movement units for traversing the node text.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'char' | The movement unit for traversing the node text is by character. |
| 'word' | The movement unit for traversing the node text is by word. |
| 'line' | The movement unit for traversing the node text is by line. |
| 'page' | The movement unit for traversing the node text is by page. |
| 'paragraph' | The movement unit for traversing the node text is by paragraph. |

## WindowUpdateType

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

type WindowUpdateType = 'add' | 'remove' | 'bounds' | 'active' | 'focus'

Window update type.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'add' | Window adding. |
| 'remove' | Window deletion. |
| 'bounds' | Window boundary change. |
| 'active' | Window activity change. |
| 'focus' | Window focus change. |

## accessibility.getAbilityLists^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>

Obtains the accessibility application list. This API uses a promise to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](#abilitytype) | Yes | Accessibility application type. |
| stateType | [AbilityState](#abilitystate) | Yes | Accessibility application status. |

**Return value**

| Type | Description |
| --- | --- |
| Promise<Array<[AccessibilityAbilityInfo](#accessibilityabilityinfo)>> | Promise used to return the accessibility application list. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get accessibility extension list because ${JSON.stringify(err)}`);
});
```

## accessibility.getAbilityLists^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

getAbilityLists(abilityType: AbilityType, stateType: AbilityState,callback: AsyncCallback<Array<AccessibilityAbilityInfo>>): void

Obtains the accessibility application list. This API uses an asynchronous callback to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9-1) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](#abilitytype) | Yes | Accessibility application type. |
| stateType | [AbilityState](#abilitystate) | Yes | Accessibility application status. |
| callback | AsyncCallback<Array<[AccessibilityAbilityInfo](#accessibilityabilityinfo)>> | Yes | Callback used to return the accessibility application list. If the operation is successful, **err** is **undefined** and **data** is the accessibility application list. Otherwise, it is an error object. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list because ${JSON.stringify(err)}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
})
```

## accessibility.getAccessibilityExtensionList^9+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState): Promise<Array<AccessibilityAbilityInfo>>

Obtains the accessibility application list. This API uses a promise to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](#abilitytype) | Yes | Accessibility application type. |
| stateType | [AbilityState](#abilitystate) | Yes | Accessibility application status. |

**Return value**

| Type | Description |
| --- | --- |
| Promise<Array<[AccessibilityAbilityInfo](#accessibilityabilityinfo)>> | Promise used to return the accessibility application list. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Parameter example**

| Accessibility Application Type/State | enable | disable | install |
| --- | --- | --- | --- |
| **audible** | Queries enabled accessibility applications with audible feedback. | Queries disabled accessibility applications with audible feedback. | Queries installed accessibility applications with audible feedback. |
| **generic** | Queries enabled accessibility applications with generic feedback. | Queries disabled accessibility applications with generic feedback. | Queries installed accessibility applications with generic feedback. |
| **haptic** | Queries enabled accessibility applications with haptic feedback. | Queries disabled accessibility applications with haptic feedback. | Queries installed accessibility applications with haptic feedback. |
| **spoken** | Queries enabled accessibility applications with spoken feedback. | Queries disabled accessibility applications with spoken feedback. | Queries installed accessibility applications with spoken feedback. |
| **visual** | Queries enabled accessibility applications with visual feedback. | Queries disabled accessibility applications with visual feedback. | Queries installed accessibility applications with visual feedback. |
| **all** | Queries all enabled accessibility applications. | Queries all disabled accessibility applications. | Queries all installed accessibility applications. |

**Example of querying all installed accessibility applications**:

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'all'; // Set the accessibility application type to 'all'.
let abilityState: accessibility.AbilityState = 'install'; // Set the accessibility application state to 'install'.

accessibility.getAccessibilityExtensionList(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
});

// For example, install an accessibility application whose bundle name is com.example.myaccessibilityapp in the system.
// The log output is as follows:
// [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
// "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
// "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
// "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
// "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
// "announceForAccessibility","announceForAccessibilityNotInterrupt",
// "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
```

**Example of querying all enabled accessibility applications with voice feedback**:

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken'; // Set the accessibility application type to 'spoken'.
let abilityState: accessibility.AbilityState = 'enable'; // Set the accessibility application state to 'enable'.

accessibility.getAccessibilityExtensionList(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.getAccessibilityExtensionList^9+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState, callback: AsyncCallback<Array<AccessibilityAbilityInfo>>): void

Obtains the accessibility application list. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](#abilitytype) | Yes | Accessibility application type. |
| stateType | [AbilityState](#abilitystate) | Yes | Accessibility application status. |
| callback | AsyncCallback<Array<[AccessibilityAbilityInfo](#accessibilityabilityinfo)>> | Yes | Callback used to return the accessibility application list. If the operation is successful, **err** is **undefined** and **data** is the accessibility application list. Otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Parameter example**

| Accessibility Application Type/State | enable | disable | install |
| --- | --- | --- | --- |
| **audible** | Queries enabled accessibility applications with audible feedback. | Queries disabled accessibility applications with audible feedback. | Queries installed accessibility applications with audible feedback. |
| **generic** | Queries enabled accessibility applications with generic feedback. | Queries disabled accessibility applications with generic feedback. | Queries installed accessibility applications with generic feedback. |
| **haptic** | Queries enabled accessibility applications with haptic feedback. | Queries disabled accessibility applications with haptic feedback. | Queries installed accessibility applications with haptic feedback. |
| **spoken** | Queries enabled accessibility applications with spoken feedback. | Queries disabled accessibility applications with spoken feedback. | Queries installed accessibility applications with spoken feedback. |
| **visual** | Queries enabled accessibility applications with visual feedback. | Queries disabled accessibility applications with visual feedback. | Queries installed accessibility applications with visual feedback. |
| **all** | Queries all enabled accessibility applications. | Queries all disabled accessibility applications. | Queries all installed accessibility applications. |

**Example of querying all installed accessibility applications**:

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'all'; // Set the accessibility application type to 'all'.
let abilityState: accessibility.AbilityState = 'install'; // Set the accessibility application state to 'install'.

accessibility.getAccessibilityExtensionList(abilityType, abilityState,(err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});

// For example, install an accessibility application whose bundle name is com.example.myaccessibilityapp in the system.
// The log output is as follows:
// [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
// "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
// "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
// "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
// "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
// "announceForAccessibility","announceForAccessibilityNotInterrupt",
// "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
```

**Example of querying all enabled accessibility applications with voice feedback**:

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken'; // Set the accessibility application type to 'spoken'.
let abilityState: accessibility.AbilityState = 'enable'; // Set the accessibility application state to 'enable'.

accessibility.getAccessibilityExtensionList(abilityType, abilityState,(err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`failed to get accessibility extension list, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```

## accessibility.getAccessibilityExtensionListSync^12+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

getAccessibilityExtensionListSync(abilityType: AbilityType, stateType: AbilityState): Array<AccessibilityAbilityInfo>

Query the list of accessibility applications in the current system, which can be queried by criteria.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| abilityType | [AbilityType](#abilitytype) | Yes | Accessibility application type. |
| stateType | [AbilityState](#abilitystate) | Yes | Accessibility application status. |

**Return value**

| Type | Description |
| --- | --- |
| Array<[AccessibilityAbilityInfo](#accessibilityabilityinfo)> | Promise used to return the accessibility application list. |

**Parameter example**

| Accessibility Application Type/State | enable | disable | install |
| --- | --- | --- | --- |
| **audible** | Queries enabled accessibility applications with audible feedback. | Queries disabled accessibility applications with audible feedback. | Queries installed accessibility applications with audible feedback. |
| **generic** | Queries enabled accessibility applications with generic feedback. | Queries disabled accessibility applications with generic feedback. | Queries installed accessibility applications with generic feedback. |
| **haptic** | Queries enabled accessibility applications with haptic feedback. | Queries disabled accessibility applications with haptic feedback. | Queries installed accessibility applications with haptic feedback. |
| **spoken** | Queries enabled accessibility applications with spoken feedback. | Queries disabled accessibility applications with spoken feedback. | Queries installed accessibility applications with spoken feedback. |
| **visual** | Queries enabled accessibility applications with visual feedback. | Queries disabled accessibility applications with visual feedback. | Queries installed accessibility applications with visual feedback. |
| **all** | Queries all enabled accessibility applications. | Queries all disabled accessibility applications. | Queries all installed accessibility applications. |

**Example of querying all installed accessibility applications**:

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'all'; // Set the accessibility application type to 'all'.
let abilityState: accessibility.AbilityState = 'install'; // Set the accessibility application state to 'install'.
let data: accessibility.AccessibilityAbilityInfo[];

try {
  data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
} catch (error) {
  let err = error as BusinessError;
  console.error(`failed to get accessibility extension list because ${JSON.stringify(err)}`);
}

// For example, install an accessibility application whose bundle name is com.example.myaccessibilityapp in the system.
// The log output is as follows:
// [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
// "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
// "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
// "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
// "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
// "announceForAccessibility","announceForAccessibilityNotInterrupt",
// "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
```

**Example of querying all enabled accessibility applications with voice feedback**:

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken'; // Set the accessibility application type to 'spoken'.
let abilityState: accessibility.AbilityState = 'enable'; // Set the accessibility application state to 'enable'.
let data: accessibility.AccessibilityAbilityInfo[];

try {
  data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
} catch (error) {
  let err = error as BusinessError;
  console.error(`failed to get accessibility extension list because ${JSON.stringify(err)}`);
}
```

## accessibility.getCaptionsManager^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

getCaptionsManager(): CaptionsManager

Obtains a **CaptionsManager** instance.

> NOTE
>
> This API is supported since API version 8 and deprecated since API version 12. Related features are no longer available in the system.

**System capability**: SystemCapability.BarrierFree.Accessibility.Hearing

**Return value**

| Type | Description |
| --- | --- |
| [CaptionsManager](#captionsmanager8) | Captions configuration. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let captionsManager = accessibility.getCaptionsManager();
```

## accessibility.on('accessibilityStateChange')

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

on(type: 'accessibilityStateChange', callback: Callback<boolean>): void

Subscribes to the state changes of the accessibility application. This API uses an asynchronous callback to return the result. To obtain information about accessibility applications in the system, use [accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12).

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.off('accessibilityStateChange')
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'accessibilityStateChange'** in this API. |
| callback | Callback<boolean> | Yes | Callback invoked when the enabled status of accessibility application changes. The returned result indicates the global enabled status of the accessibility application. The value **true** indicates that the accessibility application is enabled, and **false** indicates that the accessibility application is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// When one or more accessibility applications have been installed in the system:
// 1. After the first application is enabled, the callback returns true.
// 2. If one or more applications have been enabled and the last enabled one is disabled, the callback returns false.
accessibility.on('accessibilityStateChange', (data: boolean) => {
  console.info(`subscribe accessibility state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.on('touchGuideStateChange')

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

on(type: 'touchGuideStateChange', callback: Callback<boolean>): void

Subscribes to the state changes in touch guide mode. This API uses an asynchronous callback to return the result. To obtain information about accessibility applications in the system, use [accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12).

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.off('touchGuideStateChange')
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Vision

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'touchGuideStateChange'** in this API. |
| callback | Callback<boolean> | Yes | Callback invoked when the enabling state of touch guide mode changes. The value **true** indicates that the touch guide mode is enabled, and the value **false** indicates that the touch guide mode is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// When one or more accessibility applications with touch guide mode (touchGuide is set in Capability) have been installed in the system:
// 1. After the first application is enabled, the callback returns true.
// 2. If one or more applications have been enabled and the last enabled one is disabled, the callback returns false.
accessibility.on('touchGuideStateChange', (data: boolean) => {
  console.info(`subscribe touch guide state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.on('screenReaderStateChange')^18+^

> phone 18+ | 2in1 18+ | tablet 18+ | wearable 18+

on(type: 'screenReaderStateChange', callback: Callback<boolean>): void

Subscribes to the state changes of the screen reader. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.off('screenReaderStateChange')
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'screenReaderStateChange'** in this API. |
| callback | Callback<boolean> | Yes | Callback invoked when the enabling state of screen reader changes. The value **true** indicates that the screen reader is enabled, and the value **false** indicates that the screen reader is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.on('screenReaderStateChange', (data: boolean) => {
  console.info(`subscribe screen reader state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.on('touchModeChange')^20+^

> phone 20+ | 2in1 20+ | tablet 20+ | wearable 20+

on(type: 'touchModeChange', callback: Callback<string>): void

Subscribes to the single- or double-touch event changes in touch guide mode. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.off('touchModeChange')
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'touchModeChange'** in this API. |
| callback | Callback<string> | Yes | Callback to be invoked when the single- or double-touch event changes. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onAnimationReduceStateChange^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

onAnimationReduceStateChange(callback: Callback<boolean>): void

Subscribes to the state changes in animation reduction mode. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.offAnimationReduceStateChange
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | Yes | Callback function. Returns **true** if animation reduction mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onFlashReminderStateChange^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

onFlashReminderStateChange(callback: Callback<boolean>): void

Subscribes to the state changes in flash alerts mode. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.offFlashReminderStateChange
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | Yes | Callback function. Returns **true** if flash alerts mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe flashReminder state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onFlashReminderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onAudioMonoStateChange^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

onAudioMonoStateChange(callback: Callback<boolean>): void

Subscribes to the state changes in mono audio mode. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.offAudioMonoStateChange
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | Yes | Callback function. Returns **true** if mono audio mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onSeniorModeStateChange

> phone 26.0.0+ | 2in1 26.0.0+ | tablet 26.0.0+ | wearable 26.0.0+

onSeniorModeStateChange(callback: Callback<boolean>): void

Listens for enabling status changes of the senior mode. This API uses an asynchronous callback to return the result.

> NOTE
>
> * The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> * After calling this method, you must use
>   accessibility.offSeniorModeStateChange
>   to cancel the listener before the object's lifecycle ends. Otherwise, a crash may occur.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | Yes | Callback function. The value **true** indicates that the senior mode is enabled, and the value **false** indicates that the senior mode is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('accessibilityStateChange')

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

off(type: 'accessibilityStateChange', callback?: Callback<boolean>): void

Unsubscribes from the state changes of the accessibility application. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'accessibilityStateChange'** in this API. |
| callback | Callback<boolean> | No | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('accessibilityStateChange')](#accessibilityonaccessibilitystatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.off('accessibilityStateChange', (data: boolean) => {
  console.info(`Unsubscribe accessibility state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.off('touchGuideStateChange')

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

off(type: 'touchGuideStateChange', callback?: Callback<boolean>): void

Unsubscribes from the state changes in touch guide mode. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'touchGuideStateChange'** in this API. |
| callback | Callback<boolean> | No | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('touchGuideStateChange')](#accessibilityontouchguidestatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.off('touchGuideStateChange', (data: boolean) => {
  console.info(`Unsubscribe touch guide state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.off('screenReaderStateChange')^18+^

> phone 18+ | 2in1 18+ | tablet 18+ | wearable 18+

off(type: 'screenReaderStateChange', callback?: Callback<boolean>): void

Unsubscribes from the state changes of the screen reader. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'screenReaderStateChange'** in this API. |
| callback | Callback<boolean> | No | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('screenReaderStateChange')](#accessibilityonscreenreaderstatechange18). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

accessibility.off('screenReaderStateChange', (data: boolean) => {
  console.info(`Unsubscribe screen reader state change, result: ${JSON.stringify(data)}`);
});
```

## accessibility.off('touchModeChange')^20+^

> phone 20+ | 2in1 20+ | tablet 20+ | wearable 20+

off(type: 'touchModeChange', callback?: Callback<string>): void

Unsubscribes from the single- or double-touch event changes in touch guide mode. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Event type, which is set to **'touchModeChange'** in this API. |
| callback | Callback<string> | No | Callback used to unregister. The value must be the same as the value of callback in [accessibility.on('touchModeChange')](#accessibilityontouchmodechange20). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchModeChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offAnimationReduceStateChange^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

offAnimationReduceStateChange(callback?: Callback<boolean>): void

Unsubscribes from the state changes in animation reduction mode. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | No | Callback function. Cancels the event response of a specified callback object. The value must be the same as the value of callback in [accessibility.onAnimationReduceStateChange](#accessibilityonanimationreducestatechange23). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offFlashReminderStateChange^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

offFlashReminderStateChange(callback?: Callback<boolean>): void

Unsubscribes from the state changes in flash alerts mode. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | No | Callback function. Cancels the event response of a specified callback object. The value must be the same as the value of callback in [accessibility.onFlashReminderStateChange](#accessibilityonflashreminderstatechange23). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe flashReminder state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onFlashReminderStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offFlashReminderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offAudioMonoStateChange^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

offAudioMonoStateChange(callback?: Callback<boolean>): void

Unsubscribes from the state changes in mono audio mode. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | No | Callback function. Cancels the event response of a specified callback object. The value must be the same as the value of callback in [accessibility.onAudioMonoStateChange](#accessibilityonaudiomonostatechange23). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offSeniorModeStateChange

> phone 26.0.0+ | 2in1 26.0.0+ | tablet 26.0.0+ | wearable 26.0.0+

offSeniorModeStateChange(callback?: Callback<boolean>): void

Cancels listening for the senior mode change event. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback<boolean> | No | Callback function. The value **true** indicates that the senior mode is enabled, and the value **false** indicates that the senior mode is disabled. Cancels the event response of a specified callback object. It must be consistent with the callback used in [accessibility.onSeniorModeStateChange](#accessibilityonseniormodestatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isOpenAccessibility^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

isOpenAccessibility(): Promise<boolean>

Checks whether an accessibility application is enabled. This API uses a promise to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenAccessibilitySync](#accessibilityisopenaccessibilitysync10) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| Promise<boolean> | Promise used to return the result. Returns **true** if the accessibility application is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility().then((data: boolean) => {
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`)
}).catch((err: BusinessError) => {
  console.error(`failed to  isOpenAccessibility, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.isOpenAccessibility^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

isOpenAccessibility(callback: AsyncCallback<boolean>): void

Checks whether an accessibility application is enabled. This API uses an asynchronous callback to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenAccessibilitySync](#accessibilityisopenaccessibilitysync10) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | AsyncCallback<boolean> | Yes | Callback used to return the result. Returns **true** if the accessibility application is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to isOpenAccessibility, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
});
```

## accessibility.isOpenAccessibilitySync^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

isOpenAccessibilitySync(): boolean

Checks whether any accessibility application has been enabled in the system. To obtain information about accessibility applications in the system, use [accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12).

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| boolean | Whether any accessibility application has been enabled in the system. Returns **true** if one or more accessibility applications are enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 1. If no accessibility application is enabled, the system returns false.
// 2. If any accessibility application is enabled, the system returns true.
let status: boolean = accessibility.isOpenAccessibilitySync();
```

## accessibility.isOpenTouchGuide^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

isOpenTouchGuide(): Promise<boolean>

Checks whether touch guide mode is enabled. This API uses a promise to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenTouchGuideSync](#accessibilityisopentouchguidesync10) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Vision

**Return value**

| Type | Description |
| --- | --- |
| Promise<boolean> | Promise used to return the result. Returns **true** if touch guide mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide().then((data: boolean) => {
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`failed to  isOpenTouchGuide, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.isOpenTouchGuide^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

isOpenTouchGuide(callback: AsyncCallback<boolean>): void

Checks whether touch guide mode is enabled. This API uses an asynchronous callback to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenTouchGuideSync](#accessibilityisopentouchguidesync10) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Vision

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | AsyncCallback<boolean> | Yes | Callback used to return the result. Returns **true** if touch guide mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`failed to isOpenTouchGuide, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
});
```

## accessibility.isOpenTouchGuideSync^10+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

isOpenTouchGuideSync(): boolean

Checks whether touch guide mode is enabled.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.BarrierFree.Accessibility.Vision

**Return value**

| Type | Description |
| --- | --- |
| boolean | Whether touch guide mode is enabled. Returns **true** if touch guide mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isOpenTouchGuideSync();
```

## accessibility.isScreenReaderOpenSync^18+^

> phone 18+ | 2in1 18+ | tablet 18+ | wearable 18+

isScreenReaderOpenSync(): boolean

Checks whether screen reader mode is enabled.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Vision

**Return value**

| Type | Description |
| --- | --- |
| boolean | Whether the screen reader is enabled. Returns **true** if the screen reader is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isScreenReaderOpenSync();
```

## accessibility.isAnimationReduceEnabled^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

isAnimationReduceEnabled(): Promise<boolean>

Checks whether animation reduction mode is enabled. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| Promise<boolean> | Promise used to return the result. Returns **true** if animation reduction mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAnimationReduceEnabled().then((data: boolean) => {
      console.info(`success data:isAnimationReduceEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isAnimationReduceEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAnimationReduceEnabledSync^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

isAnimationReduceEnabledSync(): boolean

Checks whether animation reduction mode is enabled with a synchronous method.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| boolean | Whether animation reduction mode is enabled. Returns **true** if animation reduction mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAnimationReduceEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isFlashReminderEnabled^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

isFlashReminderEnabled(): Promise<boolean>

Checks whether flash alerts mode is enabled. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| Promise<boolean> | Promise used to return the result. Returns **true** if flash alerts mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isFlashReminderEnabled().then((data: boolean) => {
      console.info(`success data:isFlashReminderEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isFlashReminderEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isFlashReminderEnabledSync^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

isFlashReminderEnabledSync(): boolean

Checks whether flash alerts mode is enabled with a synchronous method.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| boolean | Whether flash alerts mode is enabled. Returns **true** if flash alerts mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isFlashReminderEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAudioMonoEnabled^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

isAudioMonoEnabled(): Promise<boolean>

Checks whether mono audio mode is enabled. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| Promise<boolean> | Promise used to return the result. Returns **true** if mono audio mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAudioMonoEnabled().then((data: boolean) => {
      console.info(`success data:isAudioMonoEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to isAudioMonoEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAudioMonoEnabledSync^23+^

> phone 23+ | 2in1 23+ | tablet 23+ | wearable 23+

isAudioMonoEnabledSync(): boolean

Checks whether mono audio mode is enabled with a synchronous mode.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| boolean | Whether mono audio mode is enabled. Returns **true** if mono audio mode is enabled; returns **false** otherwise. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAudioMonoEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isSeniorModeEnabled

> phone 26.0.0+ | 2in1 26.0.0+ | tablet 26.0.0+ | wearable 26.0.0+

isSeniorModeEnabled(): Promise<boolean>

Checks whether the senior mode is enabled. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| Promise<boolean> | Promise used to return the result. The value **true** indicates that the senior mode is enabled, and the value **false** indicates that the senior mode is disabled. |

**Error codes**

For details about the error codes, see [Accessibility Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-accessibility).

| ID | Error Message |
| --- | --- |
| 9300000 | System abnormality. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isSeniorModeEnabled().then((data: boolean) => {
      console.info(`success data:isSeniorModeEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`failed to call isSeniorModeEnabled, Code is ${err.code}, message is ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.sendEvent^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

sendEvent(event: EventInfo): Promise<void>

Sends an accessibility event. This API uses a promise to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.sendAccessibilityEvent](#accessibilitysendaccessibilityevent9) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EventInfo](#eventinfo) | Yes | Accessibility event. |

**Return value**

| Type | Description |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`failed to sendEvent, Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.sendEvent^(deprecated)^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

sendEvent(event: EventInfo, callback: AsyncCallback<void>): void

Sends an accessibility event. This API uses an asynchronous callback to return the result.

> NOTE
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.sendAccessibilityEvent](#accessibilitysendaccessibilityevent9-1) instead.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EventInfo](#eventinfo) | Yes | Accessibility event. |
| callback | AsyncCallback<void> | Yes | Callback used to return the result. If the operation fails, **err** that contains data is returned. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to sendEvent, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

## accessibility.sendAccessibilityEvent^9+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

sendAccessibilityEvent(event: EventInfo): Promise<void>

Sends an accessibility event. This API uses a promise to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EventInfo](#eventinfo) | Yes | Accessibility event. |

**Return value**

| Type | Description |
| --- | --- |
| Promise<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`failed to send event , Code is ${err.code}, message is ${err.message}`);
});
```

## accessibility.sendAccessibilityEvent^9+^

> phone 12+ | 2in1 13+ | tablet 12+ | wearable 18+

sendAccessibilityEvent(event: EventInfo, callback: AsyncCallback<void>): void

Sends an accessibility event. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [EventInfo](#eventinfo) | Yes | Accessibility event. |
| callback | AsyncCallback<void> | Yes | Callback used to return the result. If the operation fails, **err** that contains data is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

| ID | Error Message |
| --- | --- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

**Example of auto-focusing:**

```ts
@Entry
@Component
struct Index {

  build() {
    Column() {
      // Add the ID attribute to the component to be focused. The uniqueness of the ID is ensured by the user.
      Button('Component to be focused').id('click')
    }
  }
}
```

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'requestFocusForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  customId: 'click' // ID attribute value of the component to be focused.
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

**Example of resource-supported auto-broadcasting^18+^:**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'announceForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  textResourceAnnouncedForAccessibility: $r('app.string.ResourceName'),
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`failed to send event, Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

## accessibility.getTouchModeSync^20+^

> phone 20+ | 2in1 20+ | tablet 20+ | wearable 20+

getTouchModeSync(): string

Queries single- or double-touch mode.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability**: SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type | Description |
| --- | --- |
| string | Touch mode. - **singleTouchMode**: Single-touch mode. - **doubleTouchMode**: Double-touch mode. - **none**: Touch guide mode is disabled. |

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let touchMode: string = accessibility.getTouchModeSync();
    console.info(`current touch mode: ${JSON.stringify(touchMode)}`);
  }

  build() {
    Column() {
    }
  }
}
```
