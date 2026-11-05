# Scenarios Where the Screen Reading Focus Is Disabled

## Scenario Design

Decorative components, which are usually separators, placeholders, and beautification icons, are used only to adjust the UI layout or decorative effect. They do not convey effective information to users or provide interaction functions. Deleting them does not affect the use of functions. You can set the **accessibilityGroup**, **accessibilityLevel**, and **visibility** attributes of a component to make the component non-focusable. In this way, the component does not obtain the focus or will not be read aloud in screen reader mode.

You can use the following accessibility attributes to change the focusable attribute of a component:

* **accessibilityGroup(true)** is used to combine all the texts of the child components and set them to the accessibility group node. Unless **accessibilityLevel** is set to **yes**, the child components are not focusable by default.

* **accessibilityLevel("no")** is used to set a component to be unfocusable and ignore its text and click attributes of the current component.

* **accessibilityLevel("no-hide-descendants")** is used to set a component and all its child components to be unfocusable and ignore their text and click attributes.

## Development Examples

The following takes **Broadcast** and **No broadcast** as an example. When Screen Reader is enabled, **message** can be focused, but **message1** cannot.

```typescript
@Entry
@Component
export struct Rule_2_1_2 {
  title: string = 'Rule 2.1.2'
  @State message: string = 'Broadcast';
  @State message1: string = 'No broadcast';

  build() {
    NavDestination() {
      Column() {
        Row() {
          Text(this.message)
            .fontSize(40)
            .fontWeight(FontWeight.Bold)
            .fontColor(Color.Blue)
            .margin({
              left: 40
            })
        }
        .width('100%')
        .height('50%')
        Row() {
          Text(this.message1)
            .fontSize(40)
            .fontWeight(FontWeight.Bold)
            .fontColor(Color.Grey)
            .margin({
              left: 40
            }).accessibilityLevel("no") // use for component
        }
        //.accessibilityGroup(true)
        //.accessibilityLevel("no-hide-descendants") // use for container
        // The above two lines can be used to replace accessibilityLevel("no") in line 28.
        .width('100%')
        .height('50%')
      }
      .height('100%')
    }
    .title(this.title)
  }
}
```
