---
layout: default
title:  "Deployment"
categories: Overview
---
### Building the Solution

`npm run [command]`
The following commands are available
*  all
  * Runs all scripts
* build
  * Creates the `dist/[project].js` solution file
* prod
  * Creates the `dist/[project].min.js` solution file
* spfx
  * Creates the `dist/[project].sppkg` solution file

### Classic Solution

1. Access the target web to deploy the solution to
2. Access the `Site Assets` library
3. Create a folder to match the `project` name
4. Upload the following files to the folder
   * `assets/index.html`
   * `dist/[project].min.js`
5. Access the `Site Pages` library
6. Select `New` and click the `Web Part Page` option
   * Set the name
   * Select `Full Page` template
   * Select `Site Assets` for the target location
7. Move the page to the target solution folder
8. Edit the page
9. Click the target zone to add the WebPart to
10. Select `Content Editor` from the `Media and More` group
11. Set the relative url to the index.html file
12. Set the border to `none`
13. Save the page

### Modern Solution

1. Access the tenant or site collection app catalog
2. Upload the `dist/[project].sppkg` file to the app catalog
   * _Check-In the file if necessary_
3. Deploy the solution
4. Access the target web to deploy the solution to
5. Access the `Site Contents`
6. Click `Add -> App`
7. Select the `[Solution]` app
8. Create or access a modern page
9. Edit the page
10. Add the webpart to the target location
11. Save and publish the page

### SharePoint Assets _(Optional)_

#### Creating the Assets

1. Access the page containing the solution
2. Access the developer tool's console
   a) Press F-12 or Ctrl+Shift+I
   b) Select the console tab
3. Install the Solution
   `GlobalVariableName.Configuration.install()`

#### Removing the Assets

1. Access the page containing the solution
2. Access the developer tool's console
   a) Press F-12 or Ctrl+Shift+I
   b) Select the console tab
3. Install the Solution
   `GlobalVariableName.Configuration.uninstall()`
