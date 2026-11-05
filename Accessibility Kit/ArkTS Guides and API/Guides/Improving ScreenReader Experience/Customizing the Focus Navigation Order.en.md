# Customizing the Focus Navigation Order

## Design Scenario

Since API version 18, users can swipe left or right with one finger to switch between focused elements after enabling ScreenReader. By default, the focus moves in the sequence of the node tree. If the default focus navigation order does not meet your requirements, you need to customize the next focus to redefine the focus navigation order.

The [accessibilityNextFocusId](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilitynextfocusid18) attribute specifies the ID of the next component to receive focus during focus navigation. It is recommended that you set the focus navigation order to follow the screen's top-to-bottom and left-to-right sequence.

In API version 26.0.0 and later versions, the **nextFocusParams** parameter is added to specify whether the focus search considers focusable nodes in the descendants of the target element.

## Parameter Description

**Table 1** [Description of input parameters](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilitynextfocusid18)

| Property | Type | Description |
| --- | --- | --- |
| nextId | string | ID of the next component to receive focus. |
| nextFocusParams | AccessibilityNextFocusParams | Detailed parameters. |

**Table 2** [AccessibilityNextFocusParams](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilitynextfocusid18) description

| Property | Type | Description |
| --- | --- | --- |
| isConsiderDescendants | boolean | Indicates whether the focus search considers focusable nodes in the descendants of the target element (default value: **false**). |

## Development Process

The visual focus navigation order of the components in this instance is A->B->C->D->E. After the [accessibilityNextFocusId](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilitynextfocusid18) parameter is set, the final focus navigation order is A->C->D->E.

```TypeScript
@Entry
@Component
export struct NextFocusIdBasic {
  title: string = 'NextFocusIdBasic';

  build() {
    NavDestination() {
      Column({ space: 10 }) {
        Button('Button A; the next focus target is column')
          .onClick(() => {
          }).fontSize(20).width('80%')
          .accessibilityNextFocusId('next_column')

        Button('Button B')
          .onClick(() => {
          }).fontSize(20).width('80%')

        Column() {
          Button('Button C')
            .onClick(() => {
            }).fontSize(20).width('80%')

          Button('Button D')
            .onClick(() => {
            }).fontSize(20).width('80%')
        }
        .id('next_column')
        .backgroundColor(Color.Green)

        Button('Button E')
          .id('btn_e')
          .onClick(() => {
          }).fontSize(20).width('80%')
      }
      .width('100%')
      .height('100%')
    }
    .title(this.title)
  }
}
```
