---
layout: default-layout
title: CaptureVisionRouter Consecutive Process - Dynamsoft Capture Vision JavaScript Edition API
description: This page introduces APIs related to Consecutive Process of Dynamsoft Capture Vision JavaScript Edition.
keywords: capture vision, Consecutive Process, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
breadcrumbText: CVR JavaScript CaptureVisionRouter
---

# CaptureVisionRouter Multiple Image Processing

| API Name                                                            | Description                                                                                  |
| ------------------------------------------------------------------- | -------------------------------------------------------------------------------------------- |
| [setInput()](#setinput)                                             | Sets up an image source to provide images for continuous processing.                         |
| [getInput()](#getinput)                                             | Returns the image source object.                                                             |
| [addImageSourceStateListener()](#addimagesourcestatelistener)       | Adds an `ImageSourceStateListener` object that listens to state changes of the image source. |
| [removeImageSourceStateListener()](#removeimagesourcestatelistener) | Removes the specified `ImageSourceStateListener` object.                                     |
| [addResultReceiver()](#addresultreceiver)                           | Adds a `CapturedResultReceiver` object as the receiver of captured results.                  |
| [removeResultReceiver()](#removeresultreceiver)                     | Removes the specified `CapturedResultReceiver` object.                                       |
| [addResultFilter()](#addresultfilter)                               | Adds a `CapturedResultFilter` object to filter non-essential results.                        |
| [removeResultFilter()](#removeresultfilter)                         | Removes the specified `CapturedResultFilter` object.                                         |
| [startCapturing()](#startcapturing)                                 | Starts to process images consecutively.                                                      |
| [stopCapturing()](#stopcapturing)                                   | Stops the consecutive process.                                                               |

<!-- 
| [addCaptureStateListener()](#addcapturestatelistener)               | Adds a CaptureStateListener object to listen to the state changes of the capture process.  |
| [removeCaptureStateListener()](#removecapturestatelistener)         | Removes the specified CaptureStateListener object.                                         | -->

## setInput

Sets up an image source to provide images for continuous processing.

**Syntax**

```typescript
setInput(imageSource: Core.ImageSourceAdapter): void;
```

**parameter**

`imageSource`: The image source adapter object representing the input image source.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let view = await Dynamsoft.DCE.CameraView.createInstance();
cameraEnhancer = await Dynamsoft.DCE.CameraEnhancer.createInstance(view);
router.setInput(dce);
```

## getInput

Returns the image source object.

**Syntax**

```typescript
getInput(): Core.ImageSourceAdapter;
```

**parameter**

None.

**Return Value**

Returns the current image source adapter object representing the input image source.

**Code snippet**

```javascript
const imageSource = CaptureVisionRouter.getInput();
```
<!--
## addCaptureStateListener

Adds an object that listens to the state changes of the capture process.

**Syntax**

```typescript
addCaptureStateListener(listener: CaptureStateListener): void;
```

**parameter**

`listener`: The capture state listener object to be added.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let csl = {
            onCaptureStateChanged(state) {
                console.log("run CaptureStateListener", state);
            }
        }
router.addCaptureStateListener(csl);
```

## removeCaptureStateListener

Removes an object which listens to the state changes of the capture process.

**Syntax**

```typescript
removeCaptureStateListener(listener: CaptureStateListener): void;
```

**parameter**

`listener`: The capture state listener object to be added.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let csl = {
            onCaptureStateChanged(state) {
                console.log("run CaptureStateListener", state);
            }
        }
router.removeCaptureStateListener(csl);
```
-->

## addImageSourceStateListener

Adds an `ImageSourceStateListener` object that listens to state changes of the image source.

**Syntax**

```typescript
addImageSourceStateListener(listener: ImageSourceStateListener): void;
```

**parameter**

`listener`: The image source state listener object to be added.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let listener = {
    onImageSourceStateListener(state) {
        console.log("run ImageSourceAdapterStatusListener", state);
    }
}
router.addImageSourceStateListener(listener);
```

## removeImageSourceStateListener

Removes the specified `ImageSourceStateListener` object.

**Syntax**

```typescript
removeImageSourceStateListener(listener: ImageSourceStateListener): void;
```

**parameter**

`listener`: The image source state listener object to be added.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let listener = {
    onImageSourceStateListener(state) {
        console.log("run ImageSourceAdapterStatusListener", state);
    }
}
router.removeImageSourceStateListener(listener);
```

## addResultReceiver

Adds a `CapturedResultReceiver` object as the receiver of captured results.

**Syntax**

```typescript
addResultReceiver(receiver: Core.CapturedResultReceiver): void;
```

**parameter**

`receiver`: The result receiver object to be added.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDetectedQuadsReceived(result) {
    //* Do something with the result */
};
router.addResultReceiver(resultReceiver);
```

## removeResultReceiver

Removes the specified `CapturedResultReceiver` object.

**Syntax**

```typescript
removeResultReceiver(receiver: Core.CapturedResultReceiver): void;
```

**parameter**

`receiver`: The result receiver object to be added.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
const resultReceiver = new Dynamsoft.CVR.CapturedResultReceiver();
resultReceiver.onDetectedQuadsReceived(result) {
    //* Do something with the result */
};
router.addResultReceiver(resultReceiver);
router.removeResultReceiver(resultReceiver);
```

## addResultFilter

Adds a `CapturedResultFilter` object to filter non-essential results.

**Syntax**

```typescript
addResultFilter(filter: Core.CapturedResultFilter): Promise<void>;
```

**parameter**

`filter`: The result filter object to be added.

**Return Value**

Returns a promise that resolves when the result filter have been successfully added.

**Code snippet**

```javascript
filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
router.addResultReceiver(filter);
```

> In the provided code snippet, the default filter implementation is utilized. This filter can offer cross-validation and de-duplication functionalities. To utilize this filter, it's necessary to include the corresponding package `dynamsoft-utility`.

**See also**

[MultiFrameResultCrossFilter](https://www.dynamsoft.com/capture-vision/docs/web/programming/javascript/api-reference/utility/multi-frame-result-cross-filter.html?product=ddn&repoType=web)

## removeResultFilter

Removes the specified `CapturedResultFilter` object.

**Syntax**

```typescript
removeResultFilter(filter: Core.CapturedResultFilter): void;
```

**parameter**

`filter`: The result filter object to be removed.

**Return Value**

None.

**Code snippet**

```javascript
filter = new Dynamsoft.Utility.MultiFrameResultCrossFilter();
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
router.addResultReceiver(filter);
router.removeResultFilter(filter);
```

## startCapturing

Starts to process images consecutively.

**Syntax**

```typescript
startCapturing(templateName?: string): Promise<void>;
```

**parameter**

`templateName`: specifies a "CaptureVisionTemplate" to use. If not specified, "Default" is used. There are two types of CaptureVisionTemplates: the [built-in ones](./built-in-templates.md) which come with the SDK and the custom ones that get initialized when the user calls [initSettings](./settings.md#initsettings). Please be aware that the [built-in CaptureVisionTemplates](./built-in-templates.md) will be overwritten should the user calls [initSettings](./settings.md#initsettings) and pass his own settings.

**Return Value**

Returns a promise that resolves to void.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
await router.startCapturing();
```

## stopCapturing

Stops the consecutive process.

**Syntax**

```typescript
stopCapturing(): void;
```

**parameter**

None.

**Return Value**

None.

**Code snippet**

```javascript
router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
router.stopCapturing();
```