# Multi-dimensional Nesting Scenarios

## Scenario Design

If multi-dimensional information is displayed in an application, nested groups may be used. If a nested group contains multiple focusable objects, repeated reading of the functions or content of these objects should be avoided. For example, in the weather widget shown below, when both time and location are focused, the time is read aloud. To prevent repeated reading of different focuses from complicating the operation steps and disordering the focus control, the complete description of the same information structure should be marked on the parent component of these child components.

![](images/en-us_image_0000002808984209.png)

## Development Examples

```typescript
@Entry
@Component
export struct Rule_2_1_3 {
  title: string = 'Rule 2.1.3'

  build() {
    NavDestination() {
      Column() {
        Text('Incorrect behavior:') // Read the following aloud: "Time Group 12:05 Beijing" + "12:05" + "Beijing".
          // When users continue to swipe down, the child component Text is focused and read again. This processing is incorrect.
          .width('100%')
          .fontSize(12)
          .fontColor(Color.Black)
          .margin({bottom: 12})
        Row(){
          Text("12:05") // time information
            .fontSize(32)
            .fontColor(Color.Red)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
            .margin({right: 20})

          Text("Beijing") // location information
            .fontSize(20)
            .fontColor(Color.Green)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
        }
        .accessibilityText("Time Group") // The time information, location information, and the accessibility text are read aloud when it is focused.
        // The Text component with time information can be focused and read aloud.
        // The Text component with location information can be focused and read aloud.
        .height(50)
        .margin({bottom: 150})

        Text('Correct behavior:') // Read only "07:05 Moscow". No repeated reading. This processing is correct.
          .width('100%')
          .fontSize(12)
          .fontColor(Color.Black)
          .margin({bottom: 12})
        Row(){
          Text("07:05") // time information
            .fontSize(32)
            .fontColor(Color.Red)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
            .margin({right: 20})

          Text("Moscow") // location information
            .fontSize(20)
            .fontColor(Color.Green)
            .fontWeight(FontWeight.Bold)
            .textAlign(TextAlign.Center)
        }
        .height(50)
        .accessibilityGroup(true) // Read the time and location information when it is focused.
        // The Text component with time information cannot be focused and read.
        // The Text component with location information cannot be focused and read.
      }
      .alignItems(HorizontalAlign.Start)
      .padding(10)
    }
    .title(this.title)
  }
}
```
