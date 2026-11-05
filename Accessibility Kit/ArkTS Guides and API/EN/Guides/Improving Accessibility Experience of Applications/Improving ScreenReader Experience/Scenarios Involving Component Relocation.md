# Scenarios Involving Component Relocation

## Scenario Design

To ensure that the information heard by visually impaired users is the same as that seen by other users, the component location to be moved must be broadcast in real time during component relocation. The broadcast of the new location will interrupt the broadcast of the old location. After the component is moved to a determined place, the information about the location is broadcast.

## Development Examples

When a user moves up a web page bookmark, the system broadcasts this operation and will announce a specific location where the bookmark is to be placed during the movement. The application can call the proactive broadcast API to automatically broadcast the information.

![](images/en-us_image_0000002779664568.png)

```typescript
import accessibility from '@ohos.accessibility';

@Entry
@Component
export struct Rule_2_1_11 {
  title: string = 'Rule 2.1.11';
  eventInfo: accessibility.EventInfo = ({
    type: 'announceForAccessibility',
    bundleName: 'com.example.pagesrouter',
    triggerAction: 'common',
    textAnnouncedForAccessibility: 'Move to the top of the Huawei official website bookmark'
  });

  build() {
    NavDestination() {
      Column() {
        Blank()
        Button('button')
          .accessibilityText('Proactively broadcast')
          .align(Alignment.Center)
          .fontSize(20)
          .id('button1')
          .onClick(() => {
            accessibility.sendAccessibilityEvent(this.eventInfo).then(() => {
              console.info(`Succeeded in send event, eventInfo is ${JSON.stringify(this.eventInfo)}`);
            });
          })
        Blank()
      }
      .width('100%')
      .height('100%')
    }
    .title(this.title)
  }
}
```
