# Button-annotated Scenarios

## Scenario Design

You must give annotations for any touchable button that is not a **Text** component, including the virtual button area in user-defined components. Otherwise, users may fail to implement corresponding functions. When annotating such components, ensure that the annotation text does not contain strings such as the component type and the prompt like "Open via one-finger double tap." Screen Reader automatically appends the annotation text based on the component type, component status, and enabled status of **Beginner's Guide**.

## Development Examples

In the following code, the annotation information of the **Image** component (actually the play/pause button) is provided by setting **accessibilityText**:

```typescript
const RESOURCE_STR_PLAY = $r('app.media.play')
const RESOURCE_STR_PAUSE = $r('app.media.pause')

@Entry
@Component
export struct Rule_2_1_5 {
  title: string = 'Rule 2.1.5'
  @State isPlaying: boolean = false
  play() {
    // play audio file
  }

  pause() {
    // pause playing of audio file
  }

  build() {
    NavDestination() {
      Column() {
        Flex({
          direction: FlexDirection.Column,
          alignItems: ItemAlign.Center,
          justifyContent: FlexAlign.Center,
        }) {
          Row() {
            Image(this.isPlaying ? RESOURCE_STR_PAUSE : RESOURCE_STR_PLAY)
              .width(50)
              .height(50)
              .onClick(() => {
                this.isPlaying = !this.isPlaying
                if (this.isPlaying) {
                  this.play()
                } else {
                  this.pause()
                }
              })
              .accessibilityRole(BUTTON_TYPE)
              .accessibilityText(this.isPlaying ? 'Pause' : 'Play') // Set the annotation information.
            Text('Good_morning.mp3')
              .margin({
                left: 10
              })
          }
        }
        .width('100%')
        .height('100%')
        .backgroundColor(Color.White)
      }
    }
    .title(this.title)
  }
}
```
