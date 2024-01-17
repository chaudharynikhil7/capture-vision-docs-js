---
layout: default-layout
title: CaptureVisionRouter Single Process - Dynamsoft Capture Vision JavaScript Edition API
description: This page introduces APIs related to Single Process with Dynamsoft Capture Vision JavaScript Edition.
keywords: capture vision, caputre, image processing, api reference, javascript, js
needAutoGenerateSidebar: true
needGenerateH3Content: false
noTitleIndex: true
breadcrumbText: CVR JavaScript CaptureVisionRouter
---

# CaptureVisionRouter Single Image Processing

| API Name              | Description                                               |
| --------------------- | --------------------------------------------------------- |
| [capture()](#capture) | Process an image or file to derive important information. |

## capture

Process an image or file to derive important information.

**Syntax**

```typescript
capture(imageOrFile: Blob | ArrayBuffer | Uint8Array | Uint8ClampedArray | HTMLImageElement | HTMLCanvasElement | HTMLVideoElement | Core.DSImageData | string, templateName?: string): Promise<Array<Core.CapturedResult>>;
```

**Parameters**

`imageOrFile`: specifies the image or file to be processed. It can accept various types of data representing images: `Blob`,`ArrayBuffer`,`Uint8Array`,`Uint8ClampedArray`,`HTMLImageElement`,`HTMLCanvasElement`,`HTMLVideoElement`,`Core.DSImageData`,`string`.

`templateName`: specifies a "CaptureVisionTemplate" to use. If not specified, "Default" is used. There are two types of CaptureVisionTemplates: the [built-in ones](./built-in-templates.md) which come with the SDK and the custom ones that get initialized when the user calls [initSettings](./settings.md#initsettings). Please be aware that the [built-in CaptureVisionTemplates](./built-in-templates.md) will be overwritten should the user calls [initSettings](./settings.md#initsettings) and pass his own settings.

**Return value**

A promise that resolves to an array of [CapturedResult]({{ site.dcv_js_api }}core/basic-structures/captured-result.html) objects which are the derived information from each image processed.

**Code snippet**

```javascript
let router = await Dynamsoft.CVR.CaptureVisionRouter.createInstance();
let results = await router.capture("blob:https://demo.dynamsoft.com/afb84bd2-e8cb-4b96-92b6-36dc89783692", "ReadSingleBarcode");
let count = results.items.length;
for(let i = 0; i < count; i++) {
    //...
}
```