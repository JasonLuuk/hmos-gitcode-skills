# Scenarios Involving Component Status Changes

## Development Examples

As shown in the following figure, the play/pause button has two states. The information annotated to the button should change along with the button state.

```typescript
import { PromptAction } from "@kit.ArkUI"

const RESOURCE_STR_PLAY = $r('app.media.play') // This is an image resource. Replace it with a local one.
const RESOURCE_STR_PAUSE = $r('app.media.pause') // This is an image resource. Replace it with a local one.

@Entry
@Component
export struct Rule_2_1_11 {
  title: string = 'Rule 2.1.8'
  @State isPlaying: boolean = true
  uiContext: UIContext = this.getUIContext();
  promptAction: PromptAction = this.uiContext.getPromptAction();
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
                this.promptAction.showToast({
                  message :this.isPlaying ? "Play" : "Pause"
                })
                this.isPlaying = !this.isPlaying
                if (this.isPlaying) {
                  this.play()
                } else {
                  this.pause()
                }
              })
              .accessibilityText(this.isPlaying ? 'Pause' : 'Play') // Set the annotation information of the accessibility framework.
          }
        }
        .width('100%')
        .height('100%')
        .backgroundColor(Color.White)
      }
    }.title(this.title)
  }
}
```
