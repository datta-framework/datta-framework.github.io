---
layout: default
title:  "Code Overview"
categories: Overview
---
An overview of the source code for each solution.

### `assets` Folder

Files, excluding the bundled output JavaScript file, associated with the solution that are required to be uploaded to SharePoint.

#### index.html

The `index.html` file is file referenced by the content editor WebPart. It contains the following:

* target element to render the application to
* script element referencing the solution
* style element for CSS customizations related to classic pages only

### `dist` Folder

Contains the output bundled/packaged solution files.

* [project].js
  * The bundled development file
* [project].min.js
  * The bundled production file
* [project].sppkg
  * The SPFx package file

### `spfx` Folder

Contains the SPFx source code for building the SPFx package file. Reference the [SPFx Solutions](/jump-start-projects/overview/spfx.md) page for an overview of adding a modern WebPart.

### `src` Folder

The main folder containing the solution source code.

### Configuration Files

* `clean.js`
  * Deletes the SPFx package file from the `dist` folder
* `package.json`
  * The solution source code configuration
* `tsconfig.json`
  * The typescript configuration _[TypeScript Web Site](https://www.typescriptlang.org/)_
* `webpack.config.js`
  * The webpack configuration _[WebPack Web Site](https://webpack.js.org/)_
