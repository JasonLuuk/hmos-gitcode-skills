# Customizing Scroll Steps for Accessibility Operations

## Design Scenario

The adjustable slider supports long press and drag operations, and the adjustment step can be less than 1% of the value range. This is applicable to fine-grained control scenarios such as video playback progress adjustment. However, the long press and drag operation is not user-friendly for visually impaired users. Therefore, when the ScreenReader feature is enabled, the system additionally supports the adjustment of the focused slider by swiping up or down. After each adjustment, the current status value (in percentage by default) is automatically announced. To avoid redundant announcements of identical values during successive adjustments, you need to use [accessibilityActionOptions](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-accessibility#accessibilityactionoptions23) to configure the slider's scroll steps for accessibility operations, ensuring that the adjustment increment is greater than or equal to 1% of the value range.

## **accessibilityActionOptions** Description

* scrollStep

  : specifies the accessibility scroll steps triggered by an accessibility gesture. In ScreenReader mode, when the focus is on the

  Slider

  component, the actual step size is

  scrollStep

  ×

  step

  when a user swipes up or down to adjust the slider. It takes effect only for the

  Slider

  component. The value range is [1, (

  max

  -

  min

  )/

  step

  ]. The default value is

  1

  . If the value is out of the range, the default value

  1

  is used. If the value is a non-integer within the range, the value is rounded down.

## Development Process

The following example implements an adjustable slider and specifies the steps for accessibility operations:

```TypeScript
@Entry
@Component
export struct Rule_2_1_15 {
  title: string = 'Rule 2.1.15';
  @State scrollStep: number = 3;

  build() {
    NavDestination() {
      Column() {
        // Create a slider with the minimum value of 0, maximum value of 100, current value of 10, and step of 10.
        Slider({
          min: 0,
          max: 100,
          value: 10,
          step: 10,
          style: SliderStyle.OutSet
        })
          // In ScreenReader mode, after the slider is focused, swipe up or down to adjust the slider by 3 steps.
          .accessibilityActionOptions({ scrollStep: this.scrollStep })
          .onChange((value: number, mode: SliderChangeMode) => {
            console.info('value:' + value + 'mode:' + mode.toString());
          })
      }
      .width('100%')
      .height('100%')
    }
    .title(this.title)
  }
}
```
