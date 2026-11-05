# Scenarios Where a New Focus Position Is Set

## Scenario Design

If the component with the current focus disappears or is hidden, the focus needs to be set to a new position. Generally, the new focus should be on the next component located in the position of the original component, instead of the component located in front of the original component. The application can call the proactive focus API to focus on the specified component.

The following table lists the parameters of the proactive focus API.

**Table1** **EventInfo**

| Property | Type | Description | Example |
| --- | --- | --- | --- |
| type | EventType | Type of the proactive focus event | requestFocusForAccessibility |
| bundleName | string | Target bundle name | Bundle name of the current application |
| triggerAction | Action | Action that triggers an event | Click or other operations have no impact. |
| customId | string | Component ID | abc345 |

## Development Examples

```typescript
import accessibility from '@ohos.accessibility';

@Entry
@Component
export struct Rule_2_1_12 {
  title: string = 'Rule 2.1.12';
  eventInfo: accessibility.EventInfo = ({
    type: 'requestFocusForAccessibility',
    bundleName: 'com.example.pagesrouter',
    triggerAction: 'common',
    customId: 'button1'
  });

  build() {
    NavDestination() {
      Column() {
        Blank()
        Button('button1')
          .accessibilityText('Click to focus on button2')
          .align(Alignment.Center)
          .fontSize(20)
          .id('button1')
          .onClick(() => {
            this.eventInfo.customId = 'button2';
            accessibility.sendAccessibilityEvent(this.eventInfo).then(() => {
              console.info(`Succeeded in send event, eventInfo is ${JSON.stringify(this.eventInfo)}`);
            });
          })
        Blank().height('10px')
        Button('button2')
          .accessibilityText('Click to focus on button1')
          .align(Alignment.Center)
          .fontSize(20)
          .id('button2')
          .onClick(() => {
            this.eventInfo.customId = 'button1';
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
