---
layout: post
title:  "SPFx Solutions"
categories: Overview
---
These steps will give an overview of creating a modern SPFx WebPart to an existing solution.

1. Access the solution using the command prompt or powershell
2. Access the `spfx` folder
3. Run `yo @microsoft/sharepoint` _(You must run this within the `spfx` folder)_
   a) Select the `WebPart` for the `type`
   b) Set the name
   c) Set the description
   d) Select `No JavaScript framework`
4. After the files are created run `npm i` or `pnpm i` to install the libraries
5. Access the `spfx/config/package-solution.json` and update the following properties
   a) name
   b) developer name and website url properties
   c) Update the zippedPackage to have the following value
      `../../dist/project.sppkg`
6. Access the `spfx/src/webparts/project/name.ts` webpart file
7. Append the import statement
```ts
import "../../../../dist/project.min.js";
declare var GlobalVariableName;
```
8. Replace the render method with the following code
```ts
public render(): void {
  // Render the application
  GlobalVariableName.render(this.domElement, this.context.pageContext);
}
```
9. Run `npm run all` from the root project folder to build the solution files and SPfx package
