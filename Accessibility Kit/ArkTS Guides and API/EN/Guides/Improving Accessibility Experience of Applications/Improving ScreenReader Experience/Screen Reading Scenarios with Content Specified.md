# Screen Reading Scenarios with Content Specified

## Scenario Design

When the screen reading function is enabled, the information of **accessibilityText** is extracted for reading. If **accessibilityText** is empty, the information of **text** is read aloud. Comply with the following principles during development:

* For the **Text** component, use **text** to provide information so that visually impaired users can obtain the same information as other users.

* If a visual effect, such as color, is configured for the **Text** component for visually sound users to obtain more information, you can also use **accessibilityText** to provide more information for visually impaired users.

* For non-text components, use **accessibilityText** to provide information for visually impaired users through screen reading.

## Development Examples

The following uses **accessibilityText()** as an example to describe how to set **accessibilityText**. When the button is focused, the reading effect is "Accessibility text, button."

```typescript
@Entry
@Component
export struct Rule_2_1_1 {
  title: string = 'Rule 2.1.1';
  shortText: string = 'Button';
  longText: string = 'Accessibility text';

  build() {
    NavDestination() {
      Column() {
        Blank()
        Button(this.shortText)
          .accessibilityText(this.longText)
          .align(Alignment.Center)
          .fontSize(20)
        Blank()
      }
      .width('100%')
      .height('100%')
    }
    .title(this.title)
  }
}
```
