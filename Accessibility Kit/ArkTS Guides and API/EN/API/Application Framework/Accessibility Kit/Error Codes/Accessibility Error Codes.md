# Accessibility Error Codes

> phone | 2in1 | tablet | wearable

> NOTE
>
> This topic describes only module-specific error codes. For details about universal error codes, see [Universal Error Codes](https://developer.huawei.com/consumer/en/doc/doccenter-references/api/errorcode-universal).

## 9300000 Accessibility Service Abnormal

> phone | 2in1 | tablet | wearable

**Error Message**

System abnormality.

**Description**

This error code is reported when the system service is abnormal.

**Possible Causes**

This error code indicates that the accessibility system service is abnormal. The possible causes are as follows:

1. The accessibility service is not started properly.
2. The internal IPC of the system is abnormal.
3. The internal functions of the accessibility service are abnormal.

**Solution**

System service error. Try again later or restart the device and retry.

## 9300003 No Accessibility Permission to Perform the Operation

> phone | 2in1 | tablet | wearable

**Error Message**

No accessibility permission to perform the operation.

**Description**

This error code is reported when an application performs an accessibility operation for which the related permission has not been granted.

**Possible Causes**

The permission for performing the accessibility operation is not granted when the accessibility application is enabled.

**Solution**

1. Request from the user the permission for performing the accessibility operation, stating the reason for the request.
2. Have the accessibility application re-enabled and the required accessibility operation enabled.

## 9300004 Property Not Found

> phone | 2in1 | tablet | wearable

**Error Message**

This property does not exist.

**Description**

This error code is reported when the entered property of the accessibility node element does not exist.

**Possible Causes**

The property does not exist in the accessibility node element.

**Solution**

Make sure the accessibility node element has the target property.

## 9300005 Action Not Supported

> phone | 2in1 | tablet | wearable

**Error Message**

This action is not supported.

**Description**

This error code is reported when the application performs an action that is not supported by the accessibility node element.

**Possible Causes**

An action that is not supported by the accessibility node element is performed.

**Solution**

Make sure the action to perform is included in the list of actions supported by the accessibility node element.
