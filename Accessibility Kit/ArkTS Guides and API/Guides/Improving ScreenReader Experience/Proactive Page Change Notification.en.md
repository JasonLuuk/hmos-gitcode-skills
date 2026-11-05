# Proactive Page Change Notification

## Design Scenario

Applications can overlay custom pages on top of the original page to achieve page switching effects. However, the system cannot automatically detect this scenario, which may lead to lost focus. In this case, your application can call the API for proactively notifying page changes to instruct ScreenReader to search for a node to focus on the new page. This API allows you to specify the root node of the new page. If a valid root node is specified, ScreenReader searches for the first focus starting from this root node. If no root node is specified, it searches for the first focus starting from the root node of the current window by default.

## Parameters Related to the API for Proactive Page Change Notification

**Table 1** [EventInfo](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/js-apis-accessibility#eventinfo) description

| Property | Type | Description | Example |
| --- | --- | --- | --- |
| type | EventType | Type of the proactive page change notification event. | pageActive |
| bundleName | string | Target application name. | 'com.example.accessibilityinfo' |
| triggerAction | Action | Action that triggers the event. | common |
| customId | string | Root node ID of the custom page. | 'abc345' |

## Development Process

The following example implements custom page switching by changing the Z-order of the child components within [Stack](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-container-stack):

```TypeScript
import { accessibility } from '@kit.AccessibilityKit'

@Entry
@Component
export struct Rule_2_1_16 {
  title: string = 'Rule 2.1.16';
  // Define a state variable to control the number of layers displayed at the top.
  @State topLayer: number = 0;

  // Define a custom page.
  @Builder
  Layer(text: string, index: number) {
    Column() {
      Column() {
        Text(text)
          .fontSize(24)
          .fontWeight(FontWeight.Bold)
          .margin({ bottom: 20 })
        Text(`${text} Test node 1`)
        Text(`${text} Test node 2`)
        Text(`${text} Test node 3`)
        // Create a button to switch pages.
        Button(`Switch to page ${index}`)
          .onClick(() => {
            // Determine the current top layer and switch between 0 and 1.
            if (this.topLayer === 0) {
              this.topLayer = 1;
            } else {
              this.topLayer = 0;
            }
            // Define the event information. The event type is pageActive, and the ID of the root node on the page is `Layer_${this.topLayer}`.
            const eventInfo: accessibility.EventInfo = ({
              type: 'pageActive',
              bundleName: 'com.samples.uiextensionandaccessibility',
              triggerAction: 'common',
              customId: `Layer_${this.topLayer}`
            });
            // Send an event to proactively notify the page change.
            accessibility.sendAccessibilityEvent(eventInfo).then(() => {
              console.info(`pageActive event send Successed, customId=Layer_${this.topLayer}.`); // Log indicating that the event is sent successfully.
            });
          })
      }
      // Specify the custom node ID, which is used to identify the root node of the page.
      .id('Layer_' + index)
    }
    .height('100%')
    .width('100%')
    .backgroundColor(index === 0 ? Color.Red : Color.Green)
    .justifyContent(FlexAlign.Center)
    .alignItems(HorizontalAlign.Center)
    .borderRadius(16)
    .padding(20)
    // Modify the Z-order of the page to implement the page switching effect.
    .zIndex(this.topLayer === index ? 1 : 0)
    // Specify whether the custom page node is recognizable by accessibility services based on whether the current page is displayed on the top layer. If not, set it to be unrecognizable.
    .accessibilityLevel(this.topLayer === index ? 'no' : 'no-hide-descendants')
  }

  build() {
    NavDestination() {
      Column() {
        Stack() {
          this.Layer('Page 0', 0)
          this.Layer('Page 1', 1)
        }
      }
    }
  }
}
```
