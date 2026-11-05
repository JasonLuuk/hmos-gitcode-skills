# Multilingual Scenarios

## Scenario Design

In multilingual scenarios, a string to read must be translated into multiple languages. The supported target languages are the same as those supported by the application UI. Pay special attention in the case of concatenated strings to avoid reading errors. For example, Arabic is read from right to left.

## Development Examples

```typescript
@Entry
@Component
export struct Rule_2_1_10 {
  title: string = 'Rule 2.1.10'
  private multilingual: string = 'It is convenient: Screen Reader is enabled and in use'

  build() {
    NavDestination() {
      Column() {
        Flex({
          direction: FlexDirection.Column,
          alignItems: ItemAlign.Center,
          justifyContent: FlexAlign.Center,
        }) {
          Row() {
            Text(this.multilingual)
              .fontSize(30)
              .fontColor(Color.Blue)
          }
          .width('80%')
        }
        .width('100%')
        .height('100%')
        .backgroundColor(Color.White)
      }
    }.title(this.title)
  }
}
```
