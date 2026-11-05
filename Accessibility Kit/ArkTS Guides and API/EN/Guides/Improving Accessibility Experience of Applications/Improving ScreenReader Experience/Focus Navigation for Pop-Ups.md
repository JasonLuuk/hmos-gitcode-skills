# Focus Navigation for Pop-Ups

## Design Scenario

Pop-ups can be classified into modal and non-modal pop-ups based on user interaction scenarios. The difference lies in whether users are required to respond to them.

* Modal pop-up: This type of pop-ups is a strong interaction element. It interrupts a user's current task and requires a response before the user can proceed with other actions. It is typically used when important information needs to be conveyed to the user. In ScreenReader mode, when a modal pop-up is displayed, the focus automatically moves to the modal pop-up. Before the pop-up is closed, the focus cannot move to nodes outside the pop-up.

* Non-modal pop-up: This is a weaker form of interaction and does not interfere with the user's current task. The user is not required to respond to the pop-up, which usually has a time limit and disappears automatically after a set period. It is generally used to convey information to the user and guide them to perform specific operations. In ScreenReader mode, when a non-modal pup-up is displayed, the focus is automatically placed on the non-modal pop-up by default. Before the pop-up is closed, the focus can be moved to nodes outside the pop-up. In particular, if the pop-up is displayed as a child window, the focus can only be moved to a node outside the pop-up by continuous touch and drag without lifting your finger or by touching the node, but cannot be moved to the node by lift-up flick-swipe.

The pop-up components for which the model type can be set include [Popup](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ohos-arkui-advanced-popup), [Menu](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-basic-components-menu), [Dialog](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ohos-arkui-advanced-dialog), and [bindSheet](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/ts-universal-attributes-sheet-transition#bindsheet).

## Development Process

The following example implements a modal pop-up and a non-modal pop-up, which can be opened by tapping different buttons:

```TypeScript
@Entry
@Component
export struct Rule_2_1_17 {
  title: string = 'Rule 2.1.17';
  // Controller of a modal pop-up.
  private modelDialogController: CustomDialogController = this.createDialogController(true);
  // Controller of a non-modal pop-up.
  private nonModelDialogController: CustomDialogController = this.createDialogController(false);

  /**
   * Creates a pop-up controller.
   * @param isModal Indicates whether the pop-up is a modal pop-up.
   * @returns Returns the created pop-up controller.
   */
  private createDialogController(isModal: boolean): CustomDialogController {
    return new CustomDialogController({
      builder: CustomDialogExample({
        controller: isModal ? this.modelDialogController : this.nonModelDialogController,
        isModal: isModal,
        cancel: () => {
          if (isModal) {
            this.modelDialogController.close();
          } else {
            this.nonModelDialogController.close();
          }
        }
      }),
      autoCancel: true,
      isModal: isModal,
      onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
        if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
          dismissDialogAction.dismiss();
        }
        if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
          dismissDialogAction.dismiss();
        }
      },
      showInSubWindow: true,
      alignment: DialogAlignment.Center,
      width: 300,
      height: 250,
    })
  }

  build() {
    NavDestination() {
      Scroll() {
        Column() {
          // Button of a modal pop-up.
          Button('Modal dialog')
            .margin({ bottom: 5 })
            .onClick(() => {
              this.modelDialogController.open();
            })

          // Button of a non-modal pop-up.
          Button('Non-modal dialog')
            .onClick(() => {
              this.nonModelDialogController.open();
            })
        }.margin({ bottom: 5 })
      }
    }.title(this.title)
  }
}

@CustomDialog
struct CustomDialogExample {
  // Indicates whether the pop-up is a modal pop-up.
  isModal?: boolean;
  // Pop-up controller.
  controller?: CustomDialogController;
  // Callback for closing the pop-up.
  cancel: () => void = () => {};

  build() {
    Column() {
      // Title of the pop-up.
      Text(this.isModal ? 'Modal pop-up' : 'Non-modal pop-up')
        .fontSize(30)
        .height(100)
      Text('Test node 1')
      Text('Test node 2')
      Text('Test node 3')
      // Button for closing the pop-up.
      Button('Close')
        .onClick(() => {
          this.cancel?.();
        })
        .margin(20)
    }
  }
}
```
