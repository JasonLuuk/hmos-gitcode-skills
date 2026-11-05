# API 参考

# [ohos.accessibility（辅助功能）](#ohosaccessibility%E8%BE%85%E5%8A%A9%E5%8A%9F%E8%83%BD)

本模块提供辅助功能查询能力，包括获取辅助应用列表、辅助应用启用状态、无障碍字幕配置、发送无障碍事件等。

## [导入模块](#%E5%AF%BC%E5%85%A5%E6%A8%A1%E5%9D%97)

```cangjie
import kit.AccessibilityKit.*
```

## [使用说明](#%E4%BD%BF%E7%94%A8%E8%AF%B4%E6%98%8E)

API示例代码使用说明：

- 若示例代码首行有“// index.cj”注释，表示该示例可在仓颉模板工程的“index.cj”文件中编译运行。
- 若示例需获取[Context](../AbilityKit/cj-apis-ability.html#class-context)应用上下文，需在仓颉模板工程中的“main\_ability.cj”文件中进行配置。

上述示例工程及配置模板详见[仓颉示例代码说明](../../cj-development-intro.html#%E4%BB%93%E9%A2%89%E7%A4%BA%E4%BE%8B%E4%BB%A3%E7%A0%81%E8%AF%B4%E6%98%8E)。

## [func getAccessibilityExtensionList(AbilityType, AbilityState)](#func-getaccessibilityextensionlistabilitytype-abilitystate)

```cangjie
public func getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState): Array<AccessibilityAbilityInfo>
```

**功能：** 查询辅助应用列表。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名         | 类型                                 | 必填 | 默认值 | 说明       |
|-------------|------------------------------------|----|-----|----------|
| abilityType | [AbilityType](#enum-abilitytype)   | 是  | \-  | 辅助应用的类型。 |
| stateType   | [AbilityState](#enum-abilitystate) | 是  | \-  | 辅助应用的状态。 |

**返回值：**

| 类型                                                                       | 说明          |
|--------------------------------------------------------------------------|-------------|
| Array&lt;[AccessibilityAbilityInfo](#class-accessibilityabilityinfo)&gt; | 返回辅助应用信息列表。 |

**示例：**

```cangjie
// index.cj

import kit.AccessibilityKit.*
import ohos.base.*

try {
    let arrAccessibilityAbilityInfo = getAccessibilityExtensionList(
        AbilityType.ABILITYTYPE_AUDIBLE, AbilityState.ABILITYSTATE_ENABLE)
    AppLog.info("isOpenAccessibility: ${arrAccessibilityAbilityInfo.size}")
} catch (e: Exception) {
    AppLog.error("isOpenAccessibility: ${e.toString()}")
}
```

## [func isOpenAccessibility()](#func-isopenaccessibility)

```cangjie
public func isOpenAccessibility(): Bool
```

**功能：** 是否启用了辅助功能。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型   | 说明                      |
|------|-------------------------|
| Bool | 启用辅助功能返回true，否则返回false。 |

**示例：**

```cangjie
// index.cj

import kit.AccessibilityKit.*
import ohos.base.*

try {
    let isOpen: Bool = isOpenAccessibility()
    AppLog.info("isOpenAccessibility: ${isOpen}")
} catch (e: Exception) {
    AppLog.error("isOpenAccessibility: ${e.toString()}")
}
```

## [func isOpenTouchGuide()](#func-isopentouchguide)

```cangjie
public func isOpenTouchGuide(): Bool
```

**功能：** 是否开启了触摸浏览模式。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Vision

**起始版本：** 19

**返回值：**

| 类型   | 说明                      |
|------|-------------------------|
| Bool | 启用辅助功能返回true，否则返回false。 |

**示例：**

```cangjie
// index.cj

import kit.AccessibilityKit.*
import ohos.base.*

try {
    let isOpen: Bool = isOpenTouchGuide()
    AppLog.info("isOpenTouchGuide: ${isOpen}")
} catch (e: Exception) {
    AppLog.error("isOpenTouchGuide: ${e.toString()}")
}
```

## [func isScreenReaderOpen()](#func-isscreenreaderopen)

```cangjie
public func isScreenReaderOpen(): Bool
```

**功能：** 是否开启了屏幕朗读模式。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型   | 说明                      |
|------|-------------------------|
| Bool | 启用屏幕朗读返回true，否则返回false。 |

**示例：**

```cangjie
// index.cj

import kit.AccessibilityKit.*
import ohos.base.*

try {
    let isOpen: Bool = isScreenReaderOpen()
    AppLog.info("isScreenReaderOpen: ${isOpen}")
} catch (e: Exception) {
    AppLog.error("isScreenReaderOpen: ${e.toString()}")
}
```

## [func off(AccCallBackType)](#func-offacccallbacktype)

```cangjie
public func off(`type`: AccCallBackType): Unit
```

**功能：** 取消监听辅助应用或触摸浏览功能启用状态变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名      | 类型                                       | 必填 | 默认值 | 说明        |
|----------|------------------------------------------|----|-----|-----------|
| \`type\` | [AccCallBackType](#enum-acccallbacktype) | 是  | \-  | 取消监听的事件名。 |

**异常：**

- [BusinessException](../BasicServicesKit/cj-apis-base.html#class-businessexception)：对应错误码的详细介绍请参见[通用错误码](../../errorcodes/cj-errorcode-universal.html)。
  
  错误码ID错误信息
  
  401Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  
  2\. Incorrect parameter types;  
  3\. Parameter verification failed.

## [func on(AccCallBackType, Callback1Argument&lt;Bool&gt;)](#func-onacccallbacktype-callback1argumentbool)

```cangjie
public func on(`type`: AccCallBackType, callback: Callback1Argument<Bool>): Unit
```

**功能：** 监听辅助应用或触摸浏览功能启用状态变化事件，使用callback异步回调。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名      | 类型                                                                                             | 必填 | 默认值 | 说明                   |
|----------|------------------------------------------------------------------------------------------------|----|-----|----------------------|
| \`type\` | [AccCallBackType](#enum-acccallbacktype)                                                       | 是  | \-  | 监听的事件名。              |
| callback | [Callback1Argument](../BasicServicesKit/cj-apis-base.html#class-callback1argument)&lt;Bool&gt; | 是  | \-  | 回调函数，此状态为全局辅助应用启用状态。 |

**异常：**

- [BusinessException](../BasicServicesKit/cj-apis-base.html#class-businessexception)：对应错误码的详细介绍请参见[通用错误码](../../errorcodes/cj-errorcode-universal.html)。
  
  错误码ID错误信息
  
  401Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  
  2\. Incorrect parameter types;  
  3\. Parameter verification failed.

**示例：**

```cangjie
// index.cj

import kit.AccessibilityKit.*
import ohos.base.*

// 此处代码可添加在依赖项定义中
class AccCallback <: Callback1Argument<Bool> {
    public func invoke(arg: Bool) {
        AppLog.info("callback: ${arg}")
    }
}

try {
    let cb = AccCallback()
    on(AccCallBackType.ACCCALLBACKTYPE_ACCESSIBILITYSTATECHANGE, cb)
    AppLog.info("on accessibilityStateChange")
    off(AccCallBackType.ACCCALLBACKTYPE_ACCESSIBILITYSTATECHANGE)
    AppLog.info("off accessibilityStateChange")
} catch (e: Exception) {
    AppLog.error("on/off accessibilityStateChange: ${e.toString()}")
}
```

## [func sendAccessibilityEvent(EventInfo)](#func-sendaccessibilityeventeventinfo)

```cangjie
public func sendAccessibilityEvent(event: EventInfo): Unit
```

**功能：** 发送无障碍事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                            | 必填 | 默认值 | 说明       |
|-------|-------------------------------|----|-----|----------|
| event | [EventInfo](#class-eventinfo) | 是  | \-  | 无障碍事件对象。 |

**异常：**

- [BusinessException](../BasicServicesKit/cj-apis-base.html#class-businessexception)：对应错误码的详细介绍请参见[通用错误码](../../errorcodes/cj-errorcode-universal.html)。
  
  错误码ID错误信息
  
  401Input parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  
  2\. Incorrect parameter types;  
  3\. Parameter verification failed.

**示例：**

```cangjie
// index.cj

import kit.AccessibilityKit.*
import ohos.base.*

try {
    let act: Action = Action.ACTION_FOCUS
    let evenInfo: EventInfo = EventInfo(`type`: EventType.EVENTTYPE_ACCESSIBILITYFOCUS, bundleName: "testDemo", triggerAction: act)
    sendAccessibilityEvent(evenInfo)
    AppLog.info("sendAccessibilityEvent")
} catch (e: Exception) {
    AppLog.error("sendAccessibilityEvent: ${e.toString()}")
}
```

## [class AccessibilityAbilityInfo](#class-accessibilityabilityinfo)

```cangjie
public class AccessibilityAbilityInfo {}
```

**功能：** 辅助应用信息。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [prop abilityTypes](#prop-abilitytypes)

```cangjie
public prop abilityTypes: Array<AbilityType>
```

**功能：** 辅助应用类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** Array&lt;[AbilityType](#enum-abilitytype)&gt;

**读写能力：** 只读

**起始版本：** 19

### [prop bundleName](#prop-bundlename)

```cangjie
public prop bundleName: String
```

**功能：** Bundle名称。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** String

**读写能力：** 只读

**起始版本：** 19

### [prop capabilities](#prop-capabilities)

```cangjie
public prop capabilities: Array<Capability>
```

**功能：** 辅助应用能力列表。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** Array&lt;[Capability](#enum-capability)&gt;

**读写能力：** 只读

**起始版本：** 19

### [prop description](#prop-description)

```cangjie
public prop description: String
```

**功能：** 辅助应用描述。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** String

**读写能力：** 只读

**起始版本：** 19

### [prop eventTypes](#prop-eventtypes)

```cangjie
public prop eventTypes: Array<EventType>
```

**功能：** 辅助应用关注的无障碍事件列表。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** Array&lt;[EventType](#enum-eventtype)&gt;

**读写能力：** 只读

**起始版本：** 19

### [prop id](#prop-id)

```cangjie
public prop id: String
```

**功能：** ability id。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** String

**读写能力：** 只读

**起始版本：** 19

### [prop label](#prop-label)

```cangjie
public prop label: String
```

**功能：** 扩展应用在扩展服务列表中的名称。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** String

**读写能力：** 只读

**起始版本：** 19

### [prop name](#prop-name)

```cangjie
public prop name: String
```

**功能：** ability名。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** String

**读写能力：** 只读

**起始版本：** 19

### [prop needHide](#prop-needhide)

```cangjie
public prop needHide: Bool
```

**功能：** 辅助应用是否在已安装的扩展服务列表中被隐藏，true表示隐藏服务，false表示显示服务。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** Bool

**读写能力：** 只读

**起始版本：** 19

### [prop targetBundleNames](#prop-targetbundlenames)

```cangjie
public prop targetBundleNames: Array<String>
```

**功能：** 关注的目标Bundle名称。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** Array&lt;String&gt;

**读写能力：** 只读

**起始版本：** 19

## [class CaptionsStyle](#class-captionsstyle)

```cangjie
public class CaptionsStyle {
    public CaptionsStyle(
        public var fontFamily: CaptionsFontFamily,
        public var fontScale: Int32,
        public var fontColor: UInt32,
        public var fontEdgeType: CaptionsFontEdgeType,
        public var backgroundColor: UInt32,
        public var windowColor: UInt32
    )
}
```

**功能：** 字幕风格。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**起始版本：** 19

### [var backgroundColor](#var-backgroundcolor)

```cangjie
public var backgroundColor: UInt32
```

**功能：** 描述字幕背景颜色，例如red对应#FF0000。

**类型：** UInt32

**读写能力：** 可读写

**起始版本：** 19

### [var fontColor](#var-fontcolor)

```cangjie
public var fontColor: UInt32
```

**功能：** 描述字幕字体颜色，例如red对应#FF0000。

**类型：** UInt32

**读写能力：** 可读写

**起始版本：** 19

### [var fontEdgeType](#var-fontedgetype)

```cangjie
public var fontEdgeType: CaptionsFontEdgeType
```

**功能：** 描述字幕字体边缘。

**类型：** [CaptionsFontEdgeType](#enum-captionsfontedgetype)

**读写能力：** 可读写

**起始版本：** 19

### [var fontFamily](#var-fontfamily)

```cangjie
public var fontFamily: CaptionsFontFamily
```

**功能：** 描述字幕字体。

**类型：** [CaptionsFontFamily](#enum-captionsfontfamily)

**读写能力：** 可读写

**起始版本：** 19

### [var fontScale](#var-fontscale)

```cangjie
public var fontScale: Int32
```

**功能：** 描述字幕字体缩放系数，单位%，参数范围1\~200。

**类型：** Int32

**读写能力：** 可读写

**起始版本：** 19

### [var windowColor](#var-windowcolor)

```cangjie
public var windowColor: UInt32
```

**功能：** 描述字幕窗口颜色，例如red对应#FF0000。

**类型：** UInt32

**读写能力：** 可读写

**起始版本：** 19

### [CaptionsStyle(CaptionsFontFamily, Int32, UInt32, CaptionsFontEdgeType, UInt32, UInt32)](#captionsstylecaptionsfontfamily-int32-uint32-captionsfontedgetype-uint32-uint32)

```cangjie
public CaptionsStyle(
    public var fontFamily: CaptionsFontFamily,
    public var fontScale: Int32,
    public var fontColor: UInt32,
    public var fontEdgeType: CaptionsFontEdgeType,
    public var backgroundColor: UInt32,
    public var windowColor: UInt32
)
```

**功能：** CaptionsStyle的构造函数。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**起始版本：** 19

**参数：**

| 参数名             | 类型                                                 | 必填 | 默认值 | 说明                         |
|-----------------|----------------------------------------------------|----|-----|----------------------------|
| fontFamily      | [CaptionsFontFamily](#enum-captionsfontfamily)     | 是  | \-  | 描述字幕字体。                    |
| fontScale       | Int32                                              | 是  | \-  | 描述字幕字体缩放系数，单位%，参数范围1\~200。 |
| fontColor       | UInt32                                             | 是  | \-  | 描述字幕字体颜色，例如red对应#FF0000。   |
| fontEdgeType    | [CaptionsFontEdgeType](#enum-captionsfontedgetype) | 是  | \-  | 描述字幕字体边缘。                  |
| backgroundColor | UInt32                                             | 是  | \-  | 描述字幕背景颜色，例如red对应#FF0000。   |
| windowColor     | UInt32                                             | 是  | \-  | 描述字幕窗口颜色，例如red对应#FF0000。   |

## [class EventInfo](#class-eventinfo)

```cangjie
public class EventInfo {
    public var `type`: EventType
    public var windowUpdateType: ?WindowUpdateType
    public var bundleName: String
    public var componentType: ?String
    public var pageId: ?Int32
    public var description: ?String
    public var triggerAction: Action
    public var textMoveUnit: ?TextMoveUnit
    public var contents: ?Array<String>
    public var lastContent: ?String
    public var beginIndex: ?Int32
    public var currentIndex: ?Int32
    public var endIndex: ?Int32
    public var itemCount: ?Int32
    public var elementId: ?Int64
    public var textAnnouncedForAccessibility: ?String
    public var customId: ?String
    public init(`type`!: EventType, bundleName!: String, triggerAction!: Action)
}
```

**功能：** 界面变更事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [var \`type\`](#var-type)

```cangjie
public var `type`: EventType
```

**功能：** 无障碍事件类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** [EventType](#enum-eventtype)

**读写能力：** 可读写

**起始版本：** 19

### [var beginIndex](#var-beginindex)

```cangjie
public var beginIndex: ?Int32
```

**功能：** 画面显示条目的开始序号。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Int32

**读写能力：** 可读写

**起始版本：** 19

### [var bundleName](#var-bundlename)

```cangjie
public var bundleName: String
```

**功能：** 目标应用名。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** String

**读写能力：** 可读写

**起始版本：** 19

### [var componentType](#var-componenttype)

```cangjie
public var componentType: ?String
```

**功能：** 事件源组件类型，如按钮、图表。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?String

**读写能力：** 可读写

**起始版本：** 19

### [var contents](#var-contents)

```cangjie
public var contents: ?Array<String>
```

**功能：** 内容列表。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Array&lt;String&gt;

**读写能力：** 可读写

**起始版本：** 19

### [var currentIndex](#var-currentindex)

```cangjie
public var currentIndex: ?Int32
```

**功能：** 当前条目序号。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Int32

**读写能力：** 可读写

**起始版本：** 19

### [var customId](#var-customid)

```cangjie
public var customId: ?String
```

**功能：** 主动聚焦的组件ID。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?String

**读写能力：** 可读写

**起始版本：** 19

### [var description](#var-description)

```cangjie
public var description: ?String
```

**功能：** 事件描述。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?String

**读写能力：** 可读写

**起始版本：** 19

### [var elementId](#var-elementid)

```cangjie
public var elementId: ?Int64
```

**功能：** 组件elementId。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Int64

**读写能力：** 可读写

**起始版本：** 19

### [var endIndex](#var-endindex)

```cangjie
public var endIndex: ?Int32
```

**功能：** 画面显示条目的结束序号。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Int32

**读写能力：** 可读写

**起始版本：** 19

### [var itemCount](#var-itemcount)

```cangjie
public var itemCount: ?Int32
```

**功能：** 条目总数。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Int32

**读写能力：** 可读写

**起始版本：** 19

### [var lastContent](#var-lastcontent)

```cangjie
public var lastContent: ?String
```

**功能：** 最新内容。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?String

**读写能力：** 可读写

**起始版本：** 19

### [var pageId](#var-pageid)

```cangjie
public var pageId: ?Int32
```

**功能：** 事件源的页面ID。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?Int32

**读写能力：** 可读写

**起始版本：** 19

### [var textAnnouncedForAccessibility](#var-textannouncedforaccessibility)

```cangjie
public var textAnnouncedForAccessibility: ?String
```

**功能：** 主动播报的内容。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?String

**读写能力：** 可读写

**起始版本：** 19

### [var textMoveUnit](#var-textmoveunit)

```cangjie
public var textMoveUnit: ?TextMoveUnit
```

**功能：** 文本移动粒度。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?[TextMoveUnit](#enum-textmoveunit)

**读写能力：** 可读写

**起始版本：** 19

### [var triggerAction](#var-triggeraction)

```cangjie
public var triggerAction: Action
```

**功能：** 触发事件的Action。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** [Action](#enum-action)

**读写能力：** 可读写

**起始版本：** 19

### [var windowUpdateType](#var-windowupdatetype)

```cangjie
public var windowUpdateType: ?WindowUpdateType
```

**功能：** 窗口变化类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**类型：** ?[WindowUpdateType](#enum-windowupdatetype)

**读写能力：** 可读写

**起始版本：** 19

### [init(EventType, String, Action)](#initeventtype-string-action)

```cangjie
public init(`type`!: EventType, bundleName!: String, triggerAction!: Action)
```

**功能：** EventInfo的构造函数。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名           | 类型                           | 必填 | 默认值 | 说明                     |
|---------------|------------------------------|----|-----|------------------------|
| \`type\`      | [EventType](#enum-eventtype) | 是  | \-  | **命名参数。** 无障碍事件类型。     |
| bundleName    | String                       | 是  | \-  | **命名参数。** 目标应用名。       |
| triggerAction | [Action](#enum-action)       | 是  | \-  | **命名参数。** 触发事件的Action。 |

## [class GesturePath](#class-gesturepath)

```cangjie
public class GesturePath {}
```

**功能：** 表示手势路径信息。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

## [class GesturePoint](#class-gesturepoint)

```cangjie
public class GesturePoint {}
```

**功能：** 表示手势触摸点。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

## [enum AbilityState](#enum-abilitystate)

```cangjie
public enum AbilityState <: Equatable<AbilityState> & ToString {
    | ABILITYSTATE_ENABLE
    | ABILITYSTATE_DISABLE
    | ABILITYSTATE_INSTALL
    | ...
}
```

**功能：** 辅助应用状态类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[AbilityState](#enum-abilitystate)&gt;
- ToString

### [ABILITYSTATE\_DISABLE](#abilitystate_disable)

```cangjie
ABILITYSTATE_DISABLE
```

**功能：** 表示辅助应用已禁用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYSTATE\_ENABLE](#abilitystate_enable)

```cangjie
ABILITYSTATE_ENABLE
```

**功能：** 表示辅助应用已启用。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYSTATE\_INSTALL](#abilitystate_install)

```cangjie
ABILITYSTATE_INSTALL
```

**功能：** 表示辅助应用已安装。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(AbilityState)](#func-abilitystate)

```cangjie
public operator func !=(other: AbilityState): Bool
```

**功能：** 对应用状态类型进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                 | 必填 | 默认值 | 说明    |
|-------|------------------------------------|----|-----|-------|
| other | [AbilityState](#enum-abilitystate) | 是  | \-  | 应用状态。 |

**返回值：**

| 类型   | 说明                           |
|------|------------------------------|
| Bool | 如果应用状态类型不同，返回true，否则返回false。 |

### [func ==(AbilityState)](#func-abilitystate-1)

```cangjie
public operator func ==(other: AbilityState): Bool
```

**功能：** 对应用状态类型进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                 | 必填 | 默认值 | 说明    |
|-------|------------------------------------|----|-----|-------|
| other | [AbilityState](#enum-abilitystate) | 是  | \-  | 应用状态。 |

**返回值：**

| 类型   | 说明                           |
|------|------------------------------|
| Bool | 如果应用状态类型相同，返回true，否则返回false。 |

### [func toString()](#func-tostring)

```cangjie
public func toString(): String
```

**功能：** 将应用状态转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明          |
|--------|-------------|
| String | 应用状态的字符串表示。 |

## [enum AbilityType](#enum-abilitytype)

```cangjie
public enum AbilityType <: Equatable<AbilityType> & ToString {
    | ABILITYTYPE_AUDIBLE
    | ABILITYTYPE_GENERIC
    | ABILITYTYPE_HAPTIC
    | ABILITYTYPE_SPOKEN
    | ABILITYTYPE_VISUAL
    | ABILITYTYPE_ALL
    | ...
}
```

**功能：** 无障碍辅助应用类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[AbilityType](#enum-abilitytype)&gt;
- ToString

### [ABILITYTYPE\_ALL](#abilitytype_all)

```cangjie
ABILITYTYPE_ALL
```

**功能：** 表示以上所有类别。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYTYPE\_AUDIBLE](#abilitytype_audible)

```cangjie
ABILITYTYPE_AUDIBLE
```

**功能：** 表示具有听觉反馈。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYTYPE\_GENERIC](#abilitytype_generic)

```cangjie
ABILITYTYPE_GENERIC
```

**功能：** 表示具有通用反馈。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYTYPE\_HAPTIC](#abilitytype_haptic)

```cangjie
ABILITYTYPE_HAPTIC
```

**功能：** 表示具有触觉反馈。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYTYPE\_SPOKEN](#abilitytype_spoken)

```cangjie
ABILITYTYPE_SPOKEN
```

**功能：** 表示具有语音反馈。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ABILITYTYPE\_VISUAL](#abilitytype_visual)

```cangjie
ABILITYTYPE_VISUAL
```

**功能：** 表示具有视觉反馈。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(AbilityType)](#func-abilitytype)

```cangjie
public operator func !=(other: AbilityType): Bool
```

**功能：** 对应用类型进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                               | 必填 | 默认值 | 说明    |
|-------|----------------------------------|----|-----|-------|
| other | [AbilityType](#enum-abilitytype) | 是  | \-  | 应用类型。 |

**返回值：**

| 类型   | 说明                        |
|------|---------------------------|
| Bool | 若应用类型不同，返回true，否则返回false。 |

### [func ==(AbilityType)](#func-abilitytype-1)

```cangjie
public operator func ==(other: AbilityType): Bool
```

**功能：** 对应用类型进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                               | 必填 | 默认值 | 说明    |
|-------|----------------------------------|----|-----|-------|
| other | [AbilityType](#enum-abilitytype) | 是  | \-  | 应用类型。 |

**返回值：**

| 类型   | 说明                        |
|------|---------------------------|
| Bool | 若应用类型相同，返回true，否则返回false。 |

### [func toString()](#func-tostring-1)

```cangjie
public func toString(): String
```

**功能：** 将应用类型转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明          |
|--------|-------------|
| String | 应用类型的字符串表示。 |

## [enum AccCallBackType](#enum-acccallbacktype)

```cangjie
public enum AccCallBackType <: Equatable<AccCallBackType> & Hashable & ToString {
    | ACCCALLBACKTYPE_ACCESSIBILITYSTATECHANGE
    | ACCCALLBACKTYPE_TOUCHGUIDESTATECHANGE
    | ...
}
```

**功能：** 监听的事件名。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[AccCallBackType](#enum-acccallbacktype)&gt;
- Hashable
- ToString

### [ACCCALLBACKTYPE\_ACCESSIBILITYSTATECHANGE](#acccallbacktype_accessibilitystatechange)

```cangjie
ACCCALLBACKTYPE_ACCESSIBILITYSTATECHANGE
```

**功能：** 'accessibilityStateChange'，即辅助应用启用状态变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACCCALLBACKTYPE\_TOUCHGUIDESTATECHANGE](#acccallbacktype_touchguidestatechange)

```cangjie
ACCCALLBACKTYPE_TOUCHGUIDESTATECHANGE
```

**功能：** 'touchGuideStateChange'，即触摸浏览启用状态变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(AccCallBackType)](#func-acccallbacktype)

```cangjie
public operator func !=(other: AccCallBackType): Bool
```

**功能：** 对监听的事件名进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                       | 必填 | 默认值 | 说明     |
|-------|------------------------------------------|----|-----|--------|
| other | [AccCallBackType](#enum-acccallbacktype) | 是  | \-  | 监听事件名。 |

**返回值：**

| 类型   | 说明                          |
|------|-----------------------------|
| Bool | 若监听的事件名不同，返回true，否则返回false。 |

### [func ==(AccCallBackType)](#func-acccallbacktype-1)

```cangjie
public operator func ==(other: AccCallBackType): Bool
```

**功能：** 对监听事件名进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                       | 必填 | 默认值 | 说明      |
|-------|------------------------------------------|----|-----|---------|
| other | [AccCallBackType](#enum-acccallbacktype) | 是  | \-  | 监听的事件名。 |

**返回值：**

| 类型   | 说明                          |
|------|-----------------------------|
| Bool | 若监听的事件名相同，返回true，否则返回false。 |

### [func hashCode()](#func-hashcode)

```cangjie
public func hashCode(): Int64
```

**功能：** 获取监听事件名的哈希值。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型    | 说明         |
|-------|------------|
| Int64 | 监听事件名的哈希值。 |

### [func toString()](#func-tostring-2)

```cangjie
public func toString(): String
```

**功能：** 将监听事件名转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明           |
|--------|--------------|
| String | 监听事件名的字符串表示。 |

## [enum Action](#enum-action)

```cangjie
public enum Action <: Equatable<Action> & ToString {
    | ACTION_ACCESSIBILITYFOCUS
    | ACTION_CLEARACCESSIBILITYFOCUS
    | ACTION_FOCUS
    | ACTION_CLEARFOCUS
    | ACTION_CLEARSELECTION
    | ACTION_CLICK
    | ACTION_LONGCLICK
    | ACTION_CUT
    | ACTION_COPY
    | ACTION_PASTE
    | ACTION_SELECT
    | ACTION_SETTEXT
    | ACTION_DELETE
    | ACTION_SCROLLFORWARD
    | ACTION_SCROLLBACKWARD
    | ACTION_SETSELECTION
    | ACTION_SETCURSORPOSITION
    | ACTION_HOME
    | ACTION_BACK
    | ACTION_RECENTTASK
    | ACTION_NOTIFICATIONCENTER
    | ACTION_CONTROLCENTER
    | ACTION_COMMON
    | ...
}
```

**功能：** 应用所支持的目标动作，需要配置参数的目标动作已在描述中标明。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[Action](#enum-action)&gt;
- ToString

### [ACTION\_ACCESSIBILITYFOCUS](#action_accessibilityfocus)

```cangjie
ACTION_ACCESSIBILITYFOCUS
```

**功能：** 表示获得无障碍焦点操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_BACK](#action_back)

```cangjie
ACTION_BACK
```

**功能：** 表示返回上一级操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_CLEARACCESSIBILITYFOCUS](#action_clearaccessibilityfocus)

```cangjie
ACTION_CLEARACCESSIBILITYFOCUS
```

**功能：** 表示清除无障碍焦点操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_CLEARFOCUS](#action_clearfocus)

```cangjie
ACTION_CLEARFOCUS
```

**功能：** 表示清除焦点操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_CLEARSELECTION](#action_clearselection)

```cangjie
ACTION_CLEARSELECTION
```

**功能：** 表示清除选择操作。当前版本暂不支持。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_CLICK](#action_click)

```cangjie
ACTION_CLICK
```

**功能：** 表示点击操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_COMMON](#action_common)

```cangjie
ACTION_COMMON
```

**功能：** 表示没有特定操作，用于主动聚焦、主动播报等场景。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_CONTROLCENTER](#action_controlcenter)

```cangjie
ACTION_CONTROLCENTER
```

**功能：** 表示打开控制中心操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_COPY](#action_copy)

```cangjie
ACTION_COPY
```

**功能：** 表示复制操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_CUT](#action_cut)

```cangjie
ACTION_CUT
```

**功能：** 表示剪切操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_DELETE](#action_delete)

```cangjie
ACTION_DELETE
```

**功能：** 表示删除操作。当前版本暂不支持。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_FOCUS](#action_focus)

```cangjie
ACTION_FOCUS
```

**功能：** 表示获得焦点操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_HOME](#action_home)

```cangjie
ACTION_HOME
```

**功能：** 表示返回桌面操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_LONGCLICK](#action_longclick)

```cangjie
ACTION_LONGCLICK
```

**功能：** 表示长按操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_NOTIFICATIONCENTER](#action_notificationcenter)

```cangjie
ACTION_NOTIFICATIONCENTER
```

**功能：** 表示打开通知栏操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_PASTE](#action_paste)

```cangjie
ACTION_PASTE
```

**功能：** 表示粘贴操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_RECENTTASK](#action_recenttask)

```cangjie
ACTION_RECENTTASK
```

**功能：** 表示打开最近任务操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_SCROLLBACKWARD](#action_scrollbackward)

```cangjie
ACTION_SCROLLBACKWARD
```

**功能：** 表示向后滚动操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_SCROLLFORWARD](#action_scrollforward)

```cangjie
ACTION_SCROLLFORWARD
```

**功能：** 表示向前滚动操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_SELECT](#action_select)

```cangjie
ACTION_SELECT
```

**功能：** 表示选择操作。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_SETCURSORPOSITION](#action_setcursorposition)

```cangjie
ACTION_SETCURSORPOSITION
```

**功能：** 表示设置光标位置操作，需配置参数offset。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_SETSELECTION](#action_setselection)

```cangjie
ACTION_SETSELECTION
```

**功能：** 表示选择操作，需配置参数selectTextBegin、selectTextEnd、selectTextInForWard。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [ACTION\_SETTEXT](#action_settext)

```cangjie
ACTION_SETTEXT
```

**功能：** 表示设置文本操作，需配置参数setText。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(Action)](#func-action)

```cangjie
public operator func !=(other: Action): Bool
```

**功能：** 对目标动作进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                     | 必填 | 默认值 | 说明    |
|-------|------------------------|----|-----|-------|
| other | [Action](#enum-action) | 是  | \-  | 目标动作。 |

**返回值：**

| 类型   | 说明                        |
|------|---------------------------|
| Bool | 若目标动作不同，返回true，否则返回false。 |

### [func ==(Action)](#func-action-1)

```cangjie
public operator func ==(other: Action): Bool
```

**功能：** 对目标动作进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                     | 必填 | 默认值 | 说明    |
|-------|------------------------|----|-----|-------|
| other | [Action](#enum-action) | 是  | \-  | 目标动作。 |

**返回值：**

| 类型   | 说明                        |
|------|---------------------------|
| Bool | 若目标动作相同，返回true，否则返回false。 |

### [func toString()](#func-tostring-3)

```cangjie
public func toString(): String
```

**功能：** 将目标动作转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明          |
|--------|-------------|
| String | 目标动作的字符串表示。 |

## [enum Capability](#enum-capability)

```cangjie
public enum Capability <: Equatable<Capability> & ToString {
    | CAPABILITY_RETRIEVE
    | CAPABILITY_TOUCHGUIDE
    | CAPABILITY_KEYEVENTOBSERVER
    | CAPABILITY_ZOOM
    | CAPABILITY_GESTURE
    | ...
}
```

**功能：** 辅助应用能力类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[Capability](#enum-capability)&gt;
- ToString

### [CAPABILITY\_GESTURE](#capability_gesture)

```cangjie
CAPABILITY_GESTURE
```

**功能：** 表示具有执行手势动作的能力。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPABILITY\_KEYEVENTOBSERVER](#capability_keyeventobserver)

```cangjie
CAPABILITY_KEYEVENTOBSERVER
```

**功能：** 表示具有过滤按键事件的能力。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPABILITY\_RETRIEVE](#capability_retrieve)

```cangjie
CAPABILITY_RETRIEVE
```

**功能：** 表示具有检索窗口内容的能力。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPABILITY\_TOUCHGUIDE](#capability_touchguide)

```cangjie
CAPABILITY_TOUCHGUIDE
```

**功能：** 表示具有触摸探索模式的能力。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPABILITY\_ZOOM](#capability_zoom)

```cangjie
CAPABILITY_ZOOM
```

**功能：** 表示具有控制显示放大的能力。当前版本暂不支持。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(Capability)](#func-capability)

```cangjie
public operator func !=(other: Capability): Bool
```

**功能：** 对应用能力进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                             | 必填 | 默认值 | 说明    |
|-------|--------------------------------|----|-----|-------|
| other | [Capability](#enum-capability) | 是  | \-  | 应用能力。 |

**返回值：**

| 类型   | 说明                        |
|------|---------------------------|
| Bool | 若应用能力不同，返回true，否则返回false。 |

### [func ==(Capability)](#func-capability-1)

```cangjie
public operator func ==(other: Capability): Bool
```

**功能：** 对应用能力进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                             | 必填 | 默认值 | 说明    |
|-------|--------------------------------|----|-----|-------|
| other | [Capability](#enum-capability) | 是  | \-  | 应用能力。 |

**返回值：**

| 类型   | 说明                        |
|------|---------------------------|
| Bool | 若应用能力相同，返回true，否则返回false。 |

### [func toString()](#func-tostring-4)

```cangjie
public func toString(): String
```

**功能：** 将应用能力转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明          |
|--------|-------------|
| String | 应用能力的字符串表示。 |

## [enum CaptionsFontEdgeType](#enum-captionsfontedgetype)

```cangjie
public enum CaptionsFontEdgeType {
    | CAPTIONSFONTEDGETYPE_NONE
    | CAPTIONSFONTEDGETYPE_RAISED
    | CAPTIONSFONTEDGETYPE_DEPRESSED
    | CAPTIONSFONTEDGETYPE_UNIFORM
    | CAPTIONSFONTEDGETYPE_DROPSHADOW
    | ...
}
```

**功能：** 字幕字体边缘类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**起始版本：** 19

### [CAPTIONSFONTEDGETYPE\_DEPRESSED](#captionsfontedgetype_depressed)

```cangjie
CAPTIONSFONTEDGETYPE_DEPRESSED
```

**功能：** 表示凹陷效果。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTEDGETYPE\_DROPSHADOW](#captionsfontedgetype_dropshadow)

```cangjie
CAPTIONSFONTEDGETYPE_DROPSHADOW
```

**功能：** 表示阴影效果。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTEDGETYPE\_NONE](#captionsfontedgetype_none)

```cangjie
CAPTIONSFONTEDGETYPE_NONE
```

**功能：** 表示无效果。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTEDGETYPE\_RAISED](#captionsfontedgetype_raised)

```cangjie
CAPTIONSFONTEDGETYPE_RAISED
```

**功能：** 表示凸起效果。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTEDGETYPE\_UNIFORM](#captionsfontedgetype_uniform)

```cangjie
CAPTIONSFONTEDGETYPE_UNIFORM
```

**功能：** 表示轮廓效果。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

## [enum CaptionsFontFamily](#enum-captionsfontfamily)

```cangjie
public enum CaptionsFontFamily {
    | CAPTIONSFONTFAMILY_DEFAULT
    | CAPTIONSFONTFAMILY_MONOSPACEDSERIF
    | CAPTIONSFONTFAMILY_SERIF
    | CAPTIONSFONTFAMILY_MONOSPACEDSANSSERIF
    | CAPTIONSFONTFAMILY_SANSSERIF
    | CAPTIONSFONTFAMILY_CASUAL
    | CAPTIONSFONTFAMILY_CURSIVE
    | CAPTIONSFONTFAMILY_SMALLCAPITALS
    | ...
}
```

**功能：** 字幕字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Hearing

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_CASUAL](#captionsfontfamily_casual)

```cangjie
CAPTIONSFONTFAMILY_CASUAL
```

**功能：** 表示非正式字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_CURSIVE](#captionsfontfamily_cursive)

```cangjie
CAPTIONSFONTFAMILY_CURSIVE
```

**功能：** 表示手写字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_DEFAULT](#captionsfontfamily_default)

```cangjie
CAPTIONSFONTFAMILY_DEFAULT
```

**功能：** 表示默认字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_MONOSPACEDSANSSERIF](#captionsfontfamily_monospacedsansserif)

```cangjie
CAPTIONSFONTFAMILY_MONOSPACEDSANSSERIF
```

**功能：** 表示等宽Sans Serif字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_MONOSPACEDSERIF](#captionsfontfamily_monospacedserif)

```cangjie
CAPTIONSFONTFAMILY_MONOSPACEDSERIF
```

**功能：** 表示等宽Serif字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_SANSSERIF](#captionsfontfamily_sansserif)

```cangjie
CAPTIONSFONTFAMILY_SANSSERIF
```

**功能：** 表示Sans Serif字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_SERIF](#captionsfontfamily_serif)

```cangjie
CAPTIONSFONTFAMILY_SERIF
```

**功能：** 表示Serif字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [CAPTIONSFONTFAMILY\_SMALLCAPITALS](#captionsfontfamily_smallcapitals)

```cangjie
CAPTIONSFONTFAMILY_SMALLCAPITALS
```

**功能：** 表示小型大写字母字体。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

## [enum EventType](#enum-eventtype)

```cangjie
public enum EventType {
    | EVENTTYPE_ACCESSIBILITYFOCUS
    | EVENTTYPE_ACCESSIBILITYFOCUSCLEAR
    | EVENTTYPE_CLICK
    | EVENTTYPE_LONGCLICK
    | EVENTTYPE_FOCUS
    | EVENTTYPE_SELECT
    | EVENTTYPE_HOVERENTER
    | EVENTTYPE_HOVEREXIT
    | EVENTTYPE_TEXTUPDATE
    | EVENTTYPE_TEXTSELECTIONUPDATE
    | EVENTTYPE_SCROLL
    | EVENTTYPE_REQUESTFOCUSFORACCESSIBILITY
    | EVENTTYPE_ANNOUNCEFORACCESSIBILITY
    | EVENTTYPE_UNKNOWN
    | ...
}
```

**功能：** 无障碍事件类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_ACCESSIBILITYFOCUS](#eventtype_accessibilityfocus)

```cangjie
EVENTTYPE_ACCESSIBILITYFOCUS
```

**功能：** 表示获得无障碍焦点的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_ACCESSIBILITYFOCUSCLEAR](#eventtype_accessibilityfocusclear)

```cangjie
EVENTTYPE_ACCESSIBILITYFOCUSCLEAR
```

**功能：** 表示清除无障碍焦点的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_ANNOUNCEFORACCESSIBILITY](#eventtype_announceforaccessibility)

```cangjie
EVENTTYPE_ANNOUNCEFORACCESSIBILITY
```

**功能：** 表示主动播报的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_CLICK](#eventtype_click)

```cangjie
EVENTTYPE_CLICK
```

**功能：** 表示点击组件的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_FOCUS](#eventtype_focus)

```cangjie
EVENTTYPE_FOCUS
```

**功能：** 表示组件获得焦点的事件。当前版本暂不支持。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_HOVERENTER](#eventtype_hoverenter)

```cangjie
EVENTTYPE_HOVERENTER
```

**功能：** 表示悬停进入组件的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_HOVEREXIT](#eventtype_hoverexit)

```cangjie
EVENTTYPE_HOVEREXIT
```

**功能：** 表示悬停离开组件的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_LONGCLICK](#eventtype_longclick)

```cangjie
EVENTTYPE_LONGCLICK
```

**功能：** 表示长按组件的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_REQUESTFOCUSFORACCESSIBILITY](#eventtype_requestfocusforaccessibility)

```cangjie
EVENTTYPE_REQUESTFOCUSFORACCESSIBILITY
```

**功能：** 表示主动聚焦的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_SCROLL](#eventtype_scroll)

```cangjie
EVENTTYPE_SCROLL
```

**功能：** 表示滚动视图的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_SELECT](#eventtype_select)

```cangjie
EVENTTYPE_SELECT
```

**功能：** 表示选择组件的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_TEXTSELECTIONUPDATE](#eventtype_textselectionupdate)

```cangjie
EVENTTYPE_TEXTSELECTIONUPDATE
```

**功能：** 表示选定文本已更改的事件。当前版本暂不支持。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_TEXTUPDATE](#eventtype_textupdate)

```cangjie
EVENTTYPE_TEXTUPDATE
```

**功能：** 表示组件文本已更改的事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [EVENTTYPE\_UNKNOWN](#eventtype_unknown)

```cangjie
EVENTTYPE_UNKNOWN
```

**功能：** 表示未知的无障碍事件类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

## [enum TextMoveUnit](#enum-textmoveunit)

```cangjie
public enum TextMoveUnit <: Equatable<TextMoveUnit> & ToString {
    | TEXTMOVEUNIT_CHAR
    | TEXTMOVEUNIT_WORD
    | TEXTMOVEUNIT_LINE
    | TEXTMOVEUNIT_PAGE
    | TEXTMOVEUNIT_PARAGRAPH
    | ...
}
```

**功能：** 文本无障碍导航移动粒度。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[TextMoveUnit](#enum-textmoveunit)&gt;
- ToString

### [TEXTMOVEUNIT\_CHAR](#textmoveunit_char)

```cangjie
TEXTMOVEUNIT_CHAR
```

**功能：** 表示以字符为移动粒度遍历节点文本。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [TEXTMOVEUNIT\_LINE](#textmoveunit_line)

```cangjie
TEXTMOVEUNIT_LINE
```

**功能：** 表示以行为移动粒度遍历节点文本。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [TEXTMOVEUNIT\_PAGE](#textmoveunit_page)

```cangjie
TEXTMOVEUNIT_PAGE
```

**功能：** 表示以页为移动粒度遍历节点文本。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [TEXTMOVEUNIT\_PARAGRAPH](#textmoveunit_paragraph)

```cangjie
TEXTMOVEUNIT_PARAGRAPH
```

**功能：** 表示以段落为移动粒度遍历节点文本。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [TEXTMOVEUNIT\_WORD](#textmoveunit_word)

```cangjie
TEXTMOVEUNIT_WORD
```

**功能：** 表示以词为移动粒度遍历节点文本。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(TextMoveUnit)](#func-textmoveunit)

```cangjie
public operator func !=(other: TextMoveUnit): Bool
```

**功能：** 对文本移动粒度进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                 | 必填 | 默认值 | 说明      |
|-------|------------------------------------|----|-----|---------|
| other | [TextMoveUnit](#enum-textmoveunit) | 是  | \-  | 文本移动粒度。 |

**返回值：**

| 类型   | 说明                           |
|------|------------------------------|
| Bool | 若对文本移动粒度不同，返回true，否则返回false。 |

### [func ==(TextMoveUnit)](#func-textmoveunit-1)

```cangjie
public operator func ==(other: TextMoveUnit): Bool
```

**功能：** 对文本移动粒度进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                 | 必填 | 默认值 | 说明      |
|-------|------------------------------------|----|-----|---------|
| other | [TextMoveUnit](#enum-textmoveunit) | 是  | \-  | 文本移动粒度。 |

**返回值：**

| 类型   | 说明                           |
|------|------------------------------|
| Bool | 若对文本移动粒度相同，返回true，否则返回false。 |

### [func toString()](#func-tostring-5)

```cangjie
public func toString(): String
```

**功能：** 将文本移动粒度转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明            |
|--------|---------------|
| String | 文本移动粒度的字符串表示。 |

## [enum WindowUpdateType](#enum-windowupdatetype)

```cangjie
public enum WindowUpdateType <: Equatable<WindowUpdateType> & ToString {
    | WINDOWUPDATETYPE_ADD
    | WINDOWUPDATETYPE_REMOVE
    | WINDOWUPDATETYPE_BOUNDS
    | WINDOWUPDATETYPE_ACTIVE
    | WINDOWUPDATETYPE_FOCUS
    | ...
}
```

**功能：** 窗口变化类型。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**父类型：**

- Equatable&lt;[WindowUpdateType](#enum-windowupdatetype)&gt;
- ToString

### [WINDOWUPDATETYPE\_ACTIVE](#windowupdatetype_active)

```cangjie
WINDOWUPDATETYPE_ACTIVE
```

**功能：** 表示窗口变为活动或不活动的窗口变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [WINDOWUPDATETYPE\_ADD](#windowupdatetype_add)

```cangjie
WINDOWUPDATETYPE_ADD
```

**功能：** 表示添加窗口的窗口变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [WINDOWUPDATETYPE\_BOUNDS](#windowupdatetype_bounds)

```cangjie
WINDOWUPDATETYPE_BOUNDS
```

**功能：** 表示窗口边界已更改的窗口变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [WINDOWUPDATETYPE\_FOCUS](#windowupdatetype_focus)

```cangjie
WINDOWUPDATETYPE_FOCUS
```

**功能：** 表示窗口焦点发生变化的窗口变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [WINDOWUPDATETYPE\_REMOVE](#windowupdatetype_remove)

```cangjie
WINDOWUPDATETYPE_REMOVE
```

**功能：** 表示一个窗口被删除的窗口变化事件。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

### [func !=(WindowUpdateType)](#func-windowupdatetype)

```cangjie
public operator func !=(other: WindowUpdateType): Bool
```

**功能：** 对窗口变化类型进行判不等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                         | 必填 | 默认值 | 说明      |
|-------|--------------------------------------------|----|-----|---------|
| other | [WindowUpdateType](#enum-windowupdatetype) | 是  | \-  | 窗口变化类型。 |

**返回值：**

| 类型   | 说明                          |
|------|-----------------------------|
| Bool | 若窗口变化类型不同，返回true，否则返回false。 |

### [func ==(WindowUpdateType)](#func-windowupdatetype-1)

```cangjie
public operator func ==(other: WindowUpdateType): Bool
```

**功能：** 对窗口变化类型进行判等。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**参数：**

| 参数名   | 类型                                         | 必填 | 默认值 | 说明      |
|-------|--------------------------------------------|----|-----|---------|
| other | [WindowUpdateType](#enum-windowupdatetype) | 是  | \-  | 窗口变化类型。 |

**返回值：**

| 类型   | 说明                          |
|------|-----------------------------|
| Bool | 若窗口变化类型相同，返回true，否则返回false。 |

### [func toString()](#func-tostring-6)

```cangjie
public func toString(): String
```

**功能：** 将窗口变化类型转换为字符串。

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**起始版本：** 19

**返回值：**

| 类型     | 说明            |
|--------|---------------|
| String | 窗口变化类型的字符串表示。 |