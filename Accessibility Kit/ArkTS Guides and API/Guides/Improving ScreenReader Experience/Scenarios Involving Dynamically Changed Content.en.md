# Scenarios Involving Dynamically Changed Content

## Scenario Design

After the important content on the UI changes dynamically, the changed content needs to be read aloud in real time. Specifically, when the content on the UI changes dynamically and it has a necessary prompt/notification/guidance function for the user, the changed content needs to be broadcasted using the proactive broadcast API provided by the Accessibility Kit.

Parameters of the proactive broadcast API are described as follows.

**Table1** EventInfo

| Property | Type | Description | Example |
| --- | --- | --- | --- |
| type | EventType | Type of the proactive broadcast event | announceForAccessibility |
| bundleName | string | Target bundle name | Bundle name of the current application |
| triggerAction | Action | Action that triggers an event | Click or other operations have no impact. |
| textAnnouncedForAccessibility | string | Text for proactive broadcast | test123 text |

## Development Examples

```typescript
import accessibility from '@ohos.accessibility';

@Entry
@Component
export struct Rule_2_1_7 {
  title: string = 'Rule 2.1.7';
  shortText: string = 'Button';
  longText: string = 'sendAccessibilityEvent';
  eventInfo: accessibility.EventInfo = ({
    type: 'announceForAccessibility',
    bundleName: 'com.example.pagesrouter',
    triggerAction: 'common',
    textAnnouncedForAccessibility: 'test123 text'
  });

  build() {
    NavDestination() {
      Column() {
        Blank()
        Button(this.shortText)
          .accessibilityText(this.longText)
          .align(Alignment.Center)
          .fontSize(20)
          .onClick(() => {
            accessibility.sendAccessibilityEvent(this.eventInfo).then(() => {
              console.info(`test123 Succeeded in send event, eventInfo is ${JSON.stringify(this.eventInfo)}`);
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
