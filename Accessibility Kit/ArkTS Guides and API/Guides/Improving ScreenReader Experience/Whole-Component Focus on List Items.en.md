# Whole-Component Focus on List Items

## Design Scenario

A list contains a series of list items with the same width. A list item may consist of display text combined with an interactive component. The display text generally serves as a functional description for the interactive component, similar to its label. Therefore, the display text and interactive component in a list item should be focused and announced as a whole. You can set [accessibilityGroup](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilitygroup) for a list item and use [accessibilityOptions](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-types#accessibilityoptions14) to specify the interactive component, bridging the accessibility status and accessibility tap event of the interactive component.

### accessibilityOptions Description

* [accessibilityPreferred](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-types#accessibilityoptions14): specifies whether to preferentially use the accessibility text for concatenation. If **accessibilityPreferred** is set to **true**, the system prioritizes the **accessibilityText** value of each child node during deep traversal. If the accessibility text is empty, the system uses the **Text** value. The concatenated result is then set for the parent node whose **accessibilityText** and **Text** are both empty. The default value is **false**, indicating that this feature is disabled.

* [stateControllerRoleType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-types#accessibilityoptions14): specifies a child component of a specific type to control the state announcement of the container component. After the container component with **accessibilityGroup** configured performs accessibility aggregation, the selected state and state announcement text of the child component of the specified type are used as the state and announcement text of the aggregated component. This eliminates the need to focus on the child component separately. If the aggregated component contains multiple child components of the same type, the first child component found under the aggregated component in the component tree is used as the control component. The default value is empty, indicating that no child component is specified.

* [stateControllerId](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-types#accessibilityoptions14): specifies a child component with a unique ID to control the state announcement of the container component. After the container component with **accessibilityGroup** configured performs accessibility aggregation, the selected state and state announcement text of the child component corresponding to the ID are used as the state and announcement text of the aggregated component. This eliminates the need to focus on the child component separately. If the aggregated component contains multiple child components with the same ID, the first child component found under the aggregated component in the component tree is used as the control component. If both **stateControllerRoleType** and **stateControllerId** are configured, the component with the same ID is preferentially matched. The default value is empty, indicating that no child component is specified.

* [actionControllerRoleType](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-types#accessibilityoptions14): specifies a child component of a specific type to control the operation execution of the container component. After the container component with **accessibilityGroup** configured performs accessibility aggregation, if an accessibility control operation is triggered, the operation is forwarded to the child component of the specified type. This eliminates the need to focus on the child component separately. Currently, only accessibility tap operations are supported. If the aggregated component contains multiple child components of the same type, the first child component found under the aggregated component in the component tree is used as the control component. The default value is empty, indicating that no child component is specified.

* [actionControllerId](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-types#accessibilityoptions14): specifies a child component with a unique ID to control the operation execution of the container component. After the container component with **accessibilityGroup** configured performs accessibility aggregation, if an accessibility control operation is triggered, the operation is forwarded to the child component corresponding to the ID. This eliminates the need to focus on the child component separately. Currently, only accessibility tap operations are supported. If the aggregated component contains multiple child components of the same type, the first child component found under the aggregated component in the component tree is used as the control component. If both this attribute and **actionControllerRoleType** are configured, the component with the same ID is preferentially matched. The default value is empty, indicating that no child component is specified.

## Development Process

The following example combines the switch, radio button, check box, and label text into a whole for focus and announcement:

```TypeScript
@Entry
@Component
export struct Rule_2_1_13 {
  title: string = 'Rule 2.1.13';
  scroller: Scroller = new Scroller();
  @State isToggleSwitch: boolean = false;
  @State isChecked: boolean = false;
  @State isSelected: boolean = false;

  build() {
    NavDestination() {
      Column() {
        Scroll(this.scroller) {
          Column({ space: 30 }) {
            Column() {
              Text("ID-based takeover of state and action for a toggle displayed as a switch")
              // Specify the toggle-type child component whose unique ID is toggletest1, set the style to switch, and bridge its accessibility state and accessibility tap event.
              Column() {
                Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
                  Text("Enable the feature")
                  Toggle({ type: ToggleType.Switch, isOn: true })
                    .selectedColor('#007DFF')
                    .switchPointColor('#FFFFFF')
                    .onChange((isOn: boolean) => {
                      console.info('Component status:' + isOn);
                    })
                    .id("toggletest1")
                }
              }.width('100%')
              .accessibilityGroup(true, {
                stateControllerId: "toggletest1",
                actionControllerId: "toggletest1"
              })
              .border({ color: Color.Black, width: 2 }).padding(10)
            }

            Column() {
              Text("ID-based takeover of state and action for a toggle displayed as a button")
              // Specify the toggle-type child component whose unique ID is toggletest1, set the style to button, and bridge its accessibility state and accessibility tap event.
              Column() {
                Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
                  Text("Change state")
                  Toggle({ type: ToggleType.Button, isOn: true }) {
                    Text('status button').fontColor('#182431').fontSize(12)
                  }.width(106)
                  .selectedColor('rgba(0,125,255,0.20)')
                  .onChange((isOn: boolean) => {
                    console.info('Component status:' + isOn);
                  })
                  .id("toggletest1")
                }
              }.width('100%')
              .accessibilityGroup(true, {
                stateControllerId: "toggletest1",
                actionControllerId: "toggletest1"
              })
              .border({ color: Color.Black, width: 2 }).padding(10)
            }

            Column() {
              Text("ID-based takeover of state and action for a toggle displayed as a radio button")
              // Specify the toggle-type child component whose unique ID is toggletest1, set the style to radio button, and bridge its accessibility state and accessibility tap event.
              Column() {
                Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
                  Text("Select the feature")
                  Toggle({ type: ToggleType.Checkbox, isOn: false })
                    .selectedColor('#007DFF')
                    .switchPointColor('#FFFFFF')
                    .onChange((isOn: boolean) => {
                      console.info('Component status:' + isOn);
                    })
                    .id("toggletest1")
                }
              }.width('100%')
              .accessibilityGroup(true, {
                stateControllerId: "toggletest1",
                actionControllerId: "toggletest1"
              })
              .border({ color: Color.Black, width: 2 }).padding(10)
            }

            Column() {
              Text("ID-based takeover of state and action for a radio button")
              // Specify the radio-type child component whose unique ID is radiotest1 and bridge its accessibility state and accessibility tap event.
              Column() {
                Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
                  Text("Change radio button selection")
                  Radio({
                    value: 'Radio2.1', group: 'radioGroup2',
                    indicatorType: RadioIndicatorType.TICK
                  })
                    .radioStyle({
                      checkedBackgroundColor: Color.Pink
                    })
                    .checked(false)
                    .height(20)
                    .width(20)
                    .onChange((isChecked: boolean) => {
                      console.info('Radio1 status is ' + isChecked);

                    })
                    .id("radiotest1")
                }
              }.width('100%')
              .accessibilityGroup(true, {
                stateControllerId: "radiotest1",
                actionControllerId: "radiotest1"
              })
              .border({ color: Color.Black, width: 2 }).padding(10)

              Radio({ value: 'Radio2.2', group: 'radioGroup2' })
                .checked(false)
                .radioStyle({
                  checkedBackgroundColor: Color.Pink
                })
                .height(20)
                .width(20)
                .onChange((isChecked: boolean) => {
                  console.info('Radio2 status is ' + isChecked);
                })
            }

            Column() {
              Text("ID-based takeover of state and action for a check box")
              // Specify the checkbox-type child component whose unique ID is checkboxtest1 and bridge its accessibility state and accessibility tap event.
              Column() {
                Flex({ justifyContent: FlexAlign.SpaceEvenly, alignItems: ItemAlign.Center }) {
                  Text("Change check box selection")
                  Checkbox({ name: 'checkbox2', group: 'checkboxGroup2' })
                    .select(true)
                    .selectedColor(0xed6f21)
                    .shape(CheckBoxShape.CIRCLE)
                    .onChange((value: boolean) => {
                      console.info('Checkbox2 change is' + value);
                    })
                    .id("checkboxtest1")
                }
              }.width('100%')
              .accessibilityGroup(true, {
                stateControllerId: "checkboxtest1",
                actionControllerId: "checkboxtest1"
              })
              .border({ color: Color.Black, width: 2 }).padding(10)
            }
          }
        }
        .scrollable(ScrollDirection.Vertical)
        .scrollBar(BarState.On)
        .friction(0.6)
        .edgeEffect(EdgeEffect.None)
        .width("100%")
      }
      .width("100%")
      .height("100%")
    }
    .title(this.title)
  }
}
```
