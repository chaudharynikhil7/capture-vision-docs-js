---
layout: default-layout
title: class ImageManager - Dynamsoft Utility Module JS Edition API Reference
description: This page shows the JS edition of the class ImageManager in Dynamsoft Utility Module.
keywords: image manager, JS
needAutoGenerateSidebar: true
noTitleIndex: true
---

# ImageManager

The `ImageManager` class provides APIs for managing images. At present, it has only one API to save an image as a file.


| API Name                    | Description                          |
| --------------------------- | ------------------------------------ |
| [`saveToFile()`](#savetofile) | Saved the specified image as a file. |

### saveToFile

It is used to save images to files.

```typescript
saveToFile(image: Core.BasicStructures.DSImageData, name: string, download?: boolean): Promise<File>;
```

**Parameters**

`image`: An image of type `Core.BasicStructures.DSImageData`.
`name`: A string represents the saved image name.
`download`: An optional download boolean flag represents whether to download the file.

**Return Value**

Returns a Promise that resolves to a File object representing the saved image file.