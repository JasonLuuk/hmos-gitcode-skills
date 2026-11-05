# Customizing the Control Status Announcement

## Use Cases

A control supporting switchable states can be in the selected or unselected status. ScreenReader can derive the default status description label from the semantic attributes of the control. In certain cases, the derived default status description label may not fully fit your service scenario. In such cases, you can use [accessibilityStateDescription](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilitystatedescription23) to specify the status description label. When ScreenReader is enabled, if the status description label of a tappable control is specified, ScreenReader will announce the specified status description label when the user focuses on the control or performs a double-tap operation.

## accessibilityStateDescription Description

* accessibilityStateDescription

  : status description label of a component. The value can be of the string or Resource type. The default value is empty.

## Development Process

The following example implements a favorite button, for which the specified status description labels are announced when the button is tapped.

```TypeScript
@Entry
@Component
export struct Rule_2_1_14 {
  title: string = 'Rule 2.1.14';
  // Favorite button status, indicating whether the button is selected.
  @State private isSelected: boolean = false;

  build() {
    NavDestination() {
      Column() {
        Button() {
          // Display different icons based on the status.
          Image(this.isSelected ? $r('app.media.favorIcon') : $r('app.media.unfavorIcon'))
            .width(30)
            .height(30)
        }
        // Specify the status description label of the button, which can be "Favorited" or "Not favorited".
        .accessibilityStateDescription(this.isSelected ? "Favorited" : "Not favorited")
        // Set the selected status of the button.
        .accessibilitySelected(this.isSelected)
        // Handle the button tap event to switch the status between selected and unselected.
        .onClick(() => {
          this.isSelected = !this.isSelected;
        })
      }
      .width('100%')
      .height('100%')
    }
    .title(this.title)
  }
}
```
