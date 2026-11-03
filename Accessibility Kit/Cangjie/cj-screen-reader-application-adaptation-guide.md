# 应用开发指南

# [屏幕朗读应用适配指导](#%E5%B1%8F%E5%B9%95%E6%9C%97%E8%AF%BB%E5%BA%94%E7%94%A8%E9%80%82%E9%85%8D%E6%8C%87%E5%AF%BC)

## [概述](#%E6%A6%82%E8%BF%B0)

屏幕朗读软件（Screen Reader）主要帮助视障人士使用移动智能设备，通过语音输出，获取屏幕或界面中的信息。视障用户无法通过视觉直接感知和理解用户界面。他/她们需要在屏幕上使用手指探索或手势逐步在界面上进行导航，同时通过设备的朗读反馈来理解界面信息和潜在的交互功能。因此，让用户能够快速、准确地感知界面内容并进行正确交互是无障碍开发的关键。视障用户需要先通过手势使某个UI对象获得焦点，同时系统朗读出该对象的内容和功能，然后视障用户双击屏幕点击或选择该对象。

因此，进行开发时应遵循以下原则：

1. 确保视障用户可以通过手势快速、符合使用逻辑顺序地导航至页面内所有有效UI对象。
2. 确保用户在当前获焦的UI对象下接收到适当的语音朗读反馈，朗读内容应简洁清晰地告知用户当前所在UI对象内容、功能、以及可执行的操作。

同时，进行开发时，组件可以设置相应的[无障碍属性](../../API_Reference/source_zh_cn/arkui-cj/cj-universal-attribute-accessibility.html)和事件来更好地使用无障碍能力。

## [标注屏幕朗读内容的场景](#%E6%A0%87%E6%B3%A8%E5%B1%8F%E5%B9%95%E6%9C%97%E8%AF%BB%E5%86%85%E5%AE%B9%E7%9A%84%E5%9C%BA%E6%99%AF)

控件包含显示文本（text）、无障碍文本（accessibilityText）2个属性，其中，显示文本为用户界面上呈现的信息，无障碍文本为无障碍专有的朗读信息，不在界面上显示。屏幕朗读提取信息进行朗读时无障碍文本的优先级大于显示文本，即当无障碍文本不为空时，会朗读无障碍文本，否则朗读显示文本。

所以：

1. 对于文本类控件，尽量使用显示文本来表达信息，使视障用户和视力健全用户可以获取到相同的信息。
2. 对于文本类控件，如果除显示文本外，还额外提供了颜色等视觉效果为视力健全用户提供了更多信息的场景，可采用无障碍文本为视障用户提供更多的信息用于朗读。
3. 对于非文本类控件，可采用无障碍文本为视障用户提供朗读信息。

accessibilityText() 设置无障碍文本。聚焦button时朗读效果为："按钮, Accessibility text"。

```cangjie
import kit.UIKit.*

@Entry
@Component
class EntryView {
    var shortText: String = "Button"
    var longText: String = "Accessibility text"

    func build() {
        Navigation() {
            Column {
                Blank()
                Button(this.shortText).accessibilityText(this.longText).align(Alignment.Center).fontSize(20)
                Blank()
            }.width(100.percent).height(100.percent)
        }
    }
}
```

## [禁用屏幕朗读焦点的场景](#%E7%A6%81%E7%94%A8%E5%B1%8F%E5%B9%95%E6%9C%97%E8%AF%BB%E7%84%A6%E7%82%B9%E7%9A%84%E5%9C%BA%E6%99%AF)

装饰性的控件一般为分隔符、占位符和美化图标等，这类图形元素仅仅起到调整页面布局或装饰性效果，并不会向用户传达有效的信息或提供交互功能，删除后不影响指引用户体验。可以设置控件的无障碍是否可见的属性将其设置对无障碍不可见，这样在屏幕朗读模式下控件就不会获取焦点和朗读。

![图1](./figures/graph1.png)

accessibilityGroup(true) 用于多个组件的组合，组合内的默认没有焦点。

.accessibilityLevel("no")用于组件设置不可聚焦，不被无障碍感知。

例如：以下代码同时显示“Broadcast”和“No broadcast”消息，但当ScreenReader处于“打开”状态时，message可被聚焦，但message1将不被聚焦。

```cangjie
import kit.UIKit.*

@Entry
@Component
class EntryView {
    @State
    var message: String = "Broadcast"
    @State
    var message1: String = "No broadcast"

    func build() {
        Navigation() {
            Column {
                Row() {
                    Text(this.message).fontSize(40).fontWeight(FontWeight.Bold).fontColor(Color.BLUE).margin(left: 40)
                }.width(100.percent).height(50.percent)

                Row() {
                    Text(this.message1).fontSize(40).fontWeight(FontWeight.Bold).fontColor(Color.BLUE).margin(left: 40).
                        accessibilityLevel("no") // use for component
                }
                    // .accessibilityGroup(true)
                    //.accessibilityLevel("no-hide-descendants") // use for container
                    // 可以使用这两行代替上面的accessibilityLevel("no")
                    .width(100.percent).height(50.percent)
            }.height(100.percent)
        }
    }
}
```

## [多维嵌套场景](#%E5%A4%9A%E7%BB%B4%E5%B5%8C%E5%A5%97%E5%9C%BA%E6%99%AF)

如果应用展示的是多维信息，还可能出现“嵌套组”的情况。在嵌套组中，应避免两个可获焦对象的功能或朗读内容产生重复。比如下图的天气卡片，时间和地点信息获取到焦点时，都是朗读的时间信息；不同焦点的重复朗读会额外增减用户的操作步骤，焦点控制杂乱，这些对同一个信息结构的完整描述应该统一标注在这几个子控件的父控件上。

![图2](./figures/graph2.png)

```cangjie
import kit.UIKit.*

@Entry
@Component
class EntryView {
    func build() {
        Navigation() {
            Column {
                Text('Incorrect behavior:') // 播报 "Time Group 12:05 Beijing" + "12:05" + "Beijing".
                    //继续下滑焦点可聚焦至子控件文本重复了两次。这是不正确的。
                    .width(100.percent).fontSize(12).fontColor(Color.BLACK).margin(bottom: 12)

                Row() {
                    Text("12:05") // time information
                        .fontSize(32).fontColor(Color.RED).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center).margin(right: 20)
                    Text("Beijing") // location information
                        .fontSize(20).fontColor(Color.GREEN).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center)
                }.accessibilityText("Time Group") // 时间信息、位置信息和此可访问性文本在获得焦点时被朗读。
                    // 带有时间信息的文本组件可聚焦并朗读
                    // 具有位置信息的文本组件可聚焦并朗读
                    .height(50).margin(bottom: 150)

                Text('Correct behavior:') // 只朗读 "07:05 Moscow" ，不重复文本。是正确的。
                    .width(100.percent).fontSize(12).fontColor(Color.BLACK).margin(bottom: 12)

                Row() {
                    Text("07:05") // time information
                        .fontSize(32).fontColor(Color.RED).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center).margin(right: 20)
                    Text("Moscow") // location information
                        .fontSize(20).fontColor(Color.GREEN).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center)
                }.height(50).accessibilityGroup(true) // 获取焦点时朗读时间和位置信息。
            // 带有时间信息的文本组件无法聚焦和朗读
            //具有位置信息的文本组件无法获得焦点并朗读
            }.alignItems(HorizontalAlign.Start).padding(10)
        }
    }
}
```

## [组合场景](#%E7%BB%84%E5%90%88%E5%9C%BA%E6%99%AF)

在一些场景中，一个功能上完整的UI对象可能是由若干个更小的UI组件组合而成的。若每一个小的UI组件都可以获焦并朗读，则会造成信息冗余和效率降低。同时由于可聚焦的组件过多过细，也会影响触摸浏览时走焦的性能体验。在这种情况下，将它们在功能或语义上聚合成一个自然组并作为一个独立可获焦的UI元素来向视障用户表达内容更加合理，且更加高效。

总体原则是：对于表示同一个对象信息的多个组件，需要进行组合标注，对外只暴露一个无障碍焦点。

![图3](./figures/graph3.png)

如下，可以将多个控件设置为一个组，通过对组设置朗读标签，达到整组播报的效果，组内的子控件设置不可获取焦点。

```cangjie
import kit.UIKit.*

@Entry
@Component
class EntryView {
    func build() {
        Navigation() {
            Column {
                Row() {
                    //默认只有子组件才能获取焦点
                    //日期、天气、温度等信息在每个组件独立获取焦点时分别朗读
                    //在组合式组件规范里是不正确的。
                    Text("23 Dec 2023") // 日期信息。组件可独立对焦和朗读
                        .fontSize(32).fontColor(Color.RED).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center).margin(right: 20)
                    Column() // 天气信息。组件可独立对焦和朗读
                        .backgroundColor(Color.BLUE).width(50).height(50).accessibilityText("Snow") // 当该组件被屏幕阅读器选中时，该组件不包含文本信息，因此将读取此文本
                        .margin(
                        right: 20)
                    Text("-1") // 温度信息。组件可独立对焦和朗读
                        .fontSize(20).fontColor(Color.GREEN).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center)
                }.height(50).margin(bottom: 20)

                Row() {
                    //因为accessibilityGroup属性设置为true，子组件无法获取焦点。
                    //获取焦点时，日期、天气、温度信息一起朗读
                    //此时只有Row可以获取焦点，这是符合组合式组件规范的。
                    Text("24 Dec 2023") //日期信息。组件无法聚焦，无法朗读，因为父组件的accessibilityGroup属性设置为true
                        .fontSize(32).fontColor(Color.RED).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center).margin(right: 20)

                    Column() //天气信息组件无法聚焦，无法朗读，因为父组件的accessibilityGroup为true
                        .backgroundColor(Color.YELLOW).width(50).height(50).accessibilityText("Sunny") // 组件不包含文本信息，当组件被屏幕阅读器选中时，因此将读取此文本
                        .margin(
                        right: 20)
                    Text("-7") // //温度信息。组件无法聚焦，无法朗读因为父组件的accessibilityGroup为true
                        .fontSize(20).fontColor(Color.GREEN).fontWeight(FontWeight.Bold).textAlign(
                        TextAlign.Center)
                }.height(50).margin(bottom: 20).accessibilityGroup(true) // 将accessibilityGroup属性设置为true，默认拼接所有子组件text，不会拼接accessibilityText
                    .accessibilityText("24 Dec 2023 Sunny -7") //如果默认的子组件拼接的text不符合预期，需要在设置accessibilityGroup为true的节点设置accessibilityText，复写文本
            }.alignItems(HorizontalAlign.Start).padding(10)
        }
    }
}
```

## [按钮标注场景](#%E6%8C%89%E9%92%AE%E6%A0%87%E6%B3%A8%E5%9C%BA%E6%99%AF)

对于用户可点击等操作的任何按钮，如果不是文本类控件，则须通过给出标注信息，包括用户自定义的控件中的虚拟按钮区域，否则可能会导致屏幕朗读用户无法完成对应的功能。

此类控件在进行标注时，标注文本不要包含控件类型、“单指双击即可打开”之类的字符串，此部分指引由屏幕朗读根据控件类型、控件状态，并结合用户是否开启了“新手指引”自动追加朗读。

![图4](./figures/graph4.png)

在下面的代码片段中，您可以看到Image组件（它实际上是一个播放/暂停按钮），通过设置accessibilityText属性提供标注信息：

```cangjie
import kit.UIKit.*

const RESOURCE_STR_PLAY = 'app.media.play'
const RESOURCE_STR_PAUSE = 'app.media.pause'

@Entry
@Component
class EntryView {
    @State
    var isPlaying: Bool = false

    func play() {
        // play audio file
    }

    func pause() {
        // pause playing of audio file
    }

    func build() {
        NavDestination() {
            Column() {
                Flex(
                    FlexParams(
                        direction: FlexDirection.Column,
                        alignItems: ItemAlign.Center,
                        justifyContent: FlexAlign.Center
                    )
                ) {
                    Row() {
                        Image(if (this.isPlaying) {
                            RESOURCE_STR_PAUSE
                        } else {
                            RESOURCE_STR_PLAY
                        }).width(50).height(50).onClick {
                            evt =>
                            this.isPlaying = !this.isPlaying
                            if (this.isPlaying) {
                                this.play()
                            } else {
                                this.pause()
                            }
                        }
                    }.accessibilityText(if (this.isPlaying) {
                        'Pause'
                    } else {
                        'Play'
                    }) // 设置可访问性框架的注释信息
                    Text('Good_morning.mp3').margin(left: 10)
                }.width(100.percent).height(100.percent).backgroundColor(Color.WHITE)
            }
        }
    }
}
```

## [插画/视频/动画的播报场景](#%E6%8F%92%E7%94%BB%E8%A7%86%E9%A2%91%E5%8A%A8%E7%94%BB%E7%9A%84%E6%92%AD%E6%8A%A5%E5%9C%BA%E6%99%AF)

如下图，插画信息有一定提示作用，插画和对应的功能介绍应该组合在一起，当焦点落到插画或者包含插画的符合控件时，需要朗读出对应的功能描述。建议插画和功能介绍作为一个组合使用一个焦点朗读。它可以借助“accessibilityGroup(true)”属性来实现。

![图5](./figures/graph5.png)

```cangjie
import kit.UIKit.*
import ohos.resource_manager.__GenerateResource__

@Entry
@Component
class EntryView {
    let description: String = 'gesture swipe left then up'
    func build() {
        NavDestination() {
            Column() {
                Flex(
                    FlexParams(
                        direction: FlexDirection.Column,
                        alignItems: ItemAlign.Center,
                        justifyContent: FlexAlign.Center
                    )
                ) {
                    Column() {
                        Image(@r(app.media.gesture_swipe_left_then_up)).width(220).height(220)
                        Text(this.description).fontSize(22).fontColor(Color.RED).fontWeight(FontWeight.Bold).textAlign(
                            TextAlign.Center)
                    }.accessibilityGroup(true).justifyContent(FlexAlign.Center) // 将图像和文本合并为一个辅助功能对象
                }.width(100.percent).height(100.percent).backgroundColor(Color.WHITE)
            }
        }
    }
}
```

以下List的每个Item，应该进行组合标注，从而给用户一个完整的提示信息：

- 对于列表/网格控件，控件中的每个项目默认需要一起标记。
- 列表/网格控件，每个item应提供item包含的元素的所有信息。
- 建议朗读列表每一项的所有嵌套元素的组合信息。

![图6](./figures/graph6.png)

它可以借助“accessibilityGroup(true)”属性来实现：

```cangjie
import kit.UIKit.*
import ohos.resource_manager.__GenerateResource__

@Entry
@Component
class EntryView {
    func build() {
        NavDestination() {
            Flex(
                FlexParams(
                    direction: FlexDirection.Column,
                    alignItems: ItemAlign.Center,
                    justifyContent: FlexAlign.Center
                )
            ) {
                Column() {
                    Item_2_1_9(
                        title: "Video card",
                        subtitle: "provided with options",
                        time: "1:23 hrs",
                        color: Color(0xffdee5ff)
                    )
                    Item_2_1_9(
                        title: "Music card",
                        subtitle: "sound feedback available",
                        time: "2:75 min",
                        color: Color(0x92e1ffd8)
                    )
                    Item_2_1_9(
                        title: "Live card",
                        subtitle: "health support on request",
                        time: "10:55",
                        color: Color(0xfff3deff)
                    )
                    Item_2_1_9(
                        title: "Play card",
                        subtitle: "play station tournament",
                        time: "5:12 hrs",
                        color: Color(0x92e1ffd8)
                    )
                    Item_2_1_9(
                        title: "Theater card",
                        subtitle: "ticket on concert",
                        time: "2:75 min",
                        color: Color(0xffdee5ff)
                    )
                }
            }
        }
    }
}

@Component
class Item_2_1_9 {
    var title: String = "Video card"
    var subtitle: String = "provided with additional options"
    var time: String = "1:23 hr"
    var color: Color = Color(0x80FAFAFA)

    func build() {
        Flex(
            FlexParams(
                direction: FlexDirection.Column,
                alignItems: ItemAlign.Center,
                justifyContent: FlexAlign.Center
            )
        ) {
            Column() {
                Text(this.title).fontSize(22).fontWeight(FontWeight.Bold).textAlign(TextAlign.Center).padding(left: 20,
                    right: 0)
                Text(this.subtitle).fontSize(14).fontColor(Color.GRAY).fontWeight(FontWeight.Normal).textAlign(
                    TextAlign.Center).padding(left: 20, right: 0)
            }

            Column() {
                Text(this.time).fontSize(20).fontWeight(FontWeight.Normal).textAlign(TextAlign.Center).padding(left: 10,
                    right: 10)
            }

            Column() {
                Image(@r(app.media.ic_arrow)).width(28).height(28).fillColor(Color.GRAY)
            }.align(Alignment.End)
        }.width(90.percent).height(75).border(
            width: 1.px,
            color: Color(0xFFC0C0C0),
            radius: 8,
            style: BorderStyle.Solid
        ).backgroundColor(this.color).accessibilityGroup(true) // combines text and image into single object
            .margin(top: 10)
    }
}
```

## [内容动态变化场景](#%E5%86%85%E5%AE%B9%E5%8A%A8%E6%80%81%E5%8F%98%E5%8C%96%E5%9C%BA%E6%99%AF)

1. 适用场景：界面上重要内容在动态变化后，需要实时发送变化后的朗读内容
2. 说明：如果界面上内容发生动态变化且其内容对用户具有必要的提示/告知/指导作用，则其发生变化后需对其变化内容进行朗读，可调用无障碍提供的主动朗读接口进行播报。

![图7](./figures/graph7.png)

```cangjie
import kit.AccessibilityKit.*

var eventInfo: EventInfo = EventInfo(
    `type`: EventType.EVENTTYPE_ANNOUNCEFORACCESSIBILITY,
    bundleName: 'com.example.pagesrouter',
    triggerAction: Action.ACTION_COMMON
)

eventInfo.textAnnouncedForAccessibility = 'test123 text'
sendAccessibilityEvent(eventInfo)
AppLog.info("test123 Succeeded in send event")
```

**表1** EventInfo 说明

| 属性                            | 类型        | 说明          | 例                        |
|-------------------------------|-----------|-------------|--------------------------|
| `type`                        | EventType | 主动播报事件类型    | announceForAccessibility |
| bundleName                    | String    | 目标应用名       | 当前应用包名                   |
| triggerAction                 | Action    | 触发事件的Action | click或其他都不会有任何影响         |
| textAnnouncedForAccessibility | String    | 主动播报的内容     | test123 text             |

## [控件状态变化场景](#%E6%8E%A7%E4%BB%B6%E7%8A%B6%E6%80%81%E5%8F%98%E5%8C%96%E5%9C%BA%E6%99%AF)

例如下图，播放暂停按钮对应着两种状态，在状态切换时需要实时变化对应的标注信息。

![图8](./figures/graph8.png)

```cangjie
import ohos.component.*
import ohos.resource_manager.__GenerateResource__
import ohos.prompt_action.PromptAction
import ohos.base.Color

@Entry
@Component
class EntryView {
    @State
    var isPlaying = true
    func play() {
        // play audio file
    }
    func pause() {
        // pause playing of audio file
    }
    func build() {
        NavDestination() {
            Column() {
                Flex(
                    FlexParams(
                        direction: FlexDirection.Column,
                        alignItems: ItemAlign.Center,
                        justifyContent: FlexAlign.Center
                    )
                ) {
                    Row() {
                        Image(if (this.isPlaying) {
                            @r(app.media.play)
                        } else {
                            @r(app.media.pause)
                        }).width(50).height(50).onClick {
                            evt =>
                            PromptAction.showToast(message: if (this.isPlaying) {
                                "Play"
                            } else {
                                "Pause"
                            })
                            this.isPlaying = !this.isPlaying
                            if (this.isPlaying) {
                                this.play()
                            } else {
                                this.pause()
                            }
                        }.accessibilityText(if (this.isPlaying) {
                            "Play"
                        } else {
                            "Pause"
                        }) // 设置可访问性框架的注释信息
                    }
                }.width(100.percent).height(100.percent).backgroundColor(Color.WHITE)
            }
        }
    }
}
```

## [操作错误场景](#%E6%93%8D%E4%BD%9C%E9%94%99%E8%AF%AF%E5%9C%BA%E6%99%AF)

比如网络连接错误，或者其他警告信息，不能仅仅以颜色区分，需要实时告诉用户错误提示和改进方法。

![](./figures/graph9.png)

如下是一个将连接中断播报出来的例子。

```cangjie
import kit.UIKit.*

@Entry
@Component
class EntryView {
    func build() {
        NavDestination() {
            Column() {
                Flex(
                    FlexParams(
                        direction: FlexDirection.Column,
                        alignItems: ItemAlign.Center,
                        justifyContent: FlexAlign.Center
                    )
                ) {
                    Row() {
                        Text('Connection state').fontSize(30)
                    }
                    Row() {
                        Radio(value: 'Radio1', group: 'radioGroup').checked(true).radioStyle(
                            checkedBackgroundColor: Color.RED).height(50).width(50).onChange(
                            {
                            isChecked: Bool => AppLog.info('Radio1 status is ${isChecked}')
                        })
                        Text('Connection interrupted').fontColor(Color.RED)
                    }.width(80.percent).accessibilityGroup(true) //将单选和文本合并到单个对象中
                }.width(100.percent).height(100.percent).backgroundColor(Color.WHITE)
            }
        }
    }
}
```

## [多语种场景](#%E5%A4%9A%E8%AF%AD%E7%A7%8D%E5%9C%BA%E6%99%AF)

当对朗读内容进行标注时，须对标注字符串进行多语种翻译，具体支持的语种和应用本身界面支持的语种保持一致。若采用多个字符串进行朗读内容的拼接，需考虑多语种的情况，避免拼接后朗读错误，例如阿拉伯语从右到左。

```cangjie
import kit.UIKit.*

@Entry
@Component
class EntryView {
    private var multilingual: String = 'It is convenient: 屏幕朗读已开启 and use'
    func build() {
        NavDestination() {
            Column() {
                Flex(
                    FlexParams(
                        direction: FlexDirection.Column,
                        alignItems: ItemAlign.Center,
                        justifyContent: FlexAlign.Center
                    )
                ) {
                    Row() {
                        Text(this.multilingual).fontSize(30).fontColor(Color.BLUE)
                    }.width(80.percent)
                }.width(100.percent).height(100.percent).backgroundColor(Color.WHITE)
            }
        }
    }
}
```

## [控件位置调整场景](#%E6%8E%A7%E4%BB%B6%E4%BD%8D%E7%BD%AE%E8%B0%83%E6%95%B4%E5%9C%BA%E6%99%AF)

移动过程中需要实时播报即将移动到的位置，新位置的播报会打断老位置的播报，放置到确定位置后，需要再播报已经放置的位置信息，尽量保证视障用户耳朵听到的信息和我们通过眼睛看到的信息是一致的。例如，网页书签被托起时，会播报已托起，移动的过程中，根据即将放置的位置播报“移至第几行，第几列”，放置后播报“已放至第几行，第几列”。应用可调用主动播报的接口来进行主动播报。

![图10](./figures/graph10.png)

## [重新设置新焦点位置的场景](#%E9%87%8D%E6%96%B0%E8%AE%BE%E7%BD%AE%E6%96%B0%E7%84%A6%E7%82%B9%E4%BD%8D%E7%BD%AE%E7%9A%84%E5%9C%BA%E6%99%AF)

1. 适用场景：当前焦点所在的控件消失或者隐藏后，需要重新设置新的焦点位置
2. 说明：一般情况下，新焦点应该在原控件位置的下一个控件上，不应该跳变到前面的控件。应用可以调用主动聚焦的接口对想要聚焦的组件进行主动聚焦。
3. 示例代码：

```cangjie
func build() {
    Column() {
        Button(`待聚焦组件`).id("abc345")
    }
}
```

```cangjie
import kit.AccessibilityKit.*
import ohos.base.AppLog

var eventInfo: EventInfo = EventInfo(
    `type`: EventType.EVENTTYPE_REQUESTFOCUSFORACCESSIBILITY,
    bundleName: "com.example.pagesrouter", triggerAction: Action.ACTION_COMMON)
eventInfo.customId = "abc345"
sendAccessibilityEvent(eventInfo)
AppLog.info("sendAccessibilityEvent")
```

**表2** EventInfo 说明

| 属性            | 类型        | 说明          | 例                        |
|---------------|-----------|-------------|--------------------------|
| `type`        | EventType | 主动播报事件类型    | announceForAccessibility |
| bundleName    | String    | 目标应用名       | 当前应用包名                   |
| triggerAction | Action    | 触发事件的Action | click或其他都不会有任何影响         |
| customId      | String    | 组件id        | abc345                   |