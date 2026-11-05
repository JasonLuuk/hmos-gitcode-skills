# Automatic Centering of Cards

## Design Scenario

In a horizontal scrolling container, center-aligned scroll-snapping highlights detailed information and operation options for the center card. To ensure the accessibility of a focused card when ScreenReader is enabled, the container automatically scrolls a focused card to the center so that its importance is visually emphasized. To achieve this, the application needs to obtain the card index through [ForEach](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-rendering-control-foreach) or [LazyForEach](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-rendering-control-lazyforeach), register the accessibility focus callback [onAccessibilityFocus](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-accessibility-event#onaccessibilityfocus) on the focusable card control, and call the [scrollToIndex](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-container-scroll#scrolltoindex) API of the scrolling container and specify the card index in the callback to center the focused card.

## Development Process

The following example implements a focused card that is automatically centered in the horizontal scrolling container.

```TypeScript
class ListDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
export struct Rule_2_1_18 {
  title: string = 'Rule 2.1.18';
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
  private scrollerForList: Scroller = new Scroller();

  build() {
    NavDestination() {
      Column() {
        List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
          LazyForEach(this.arr, (index: number) => {
            ListItem() {
              Text('' + index)
                .width('100%')
                .height(100)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
            .width('60%') // Configure a wide-format item.
            .onClick( () => {
              // Configure the tap event so that the component can be focused in accessibility mode.
            })
            // Configure the accessibility focus callback.
            .onAccessibilityFocus((isFocus: boolean) => {
              if (isFocus) {
                // If the item is focused, scroll the list to center the current list item.
                this.scrollerForList.scrollToIndex(index, false, ScrollAlign.CENTER)
              }
            })
          }, (item: string) => item)
        }
        .width('90%')
        .scrollBar(BarState.Off)
        .scrollSnapAlign(ScrollSnapAlign.CENTER) // Set center-aligned scroll snapping.
        .listDirection(Axis.Horizontal) // Set the horizontal list.
      }
      .width('100%')
      .height('100%')
      .backgroundColor(0xDCDCDC)
      .padding({ top: 5 })
    }
    .title(this.title)
  }
}
```
