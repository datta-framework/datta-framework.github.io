---
layout: default
title:  ""
categories: Solutions
---
![Demo](https://dev.azure.com/gudatta/0b5a858a-1b86-4230-93a6-b7aea3f76bbb/_apis/git/repositories/15f13730-9bab-4b25-9b9d-f18db8c4b233/items?path=%2Fdemo.png)

### Overview

Displays a banner at the top of modern or classic pages.

[Click Here](https://github.com/datta-framework/outages) to access the repository.

#### Deployment Guide

Follow the [deployment steps](/jump-start-projects/overview/deployment) based on the target environment.

##### Additional Steps

###### Classic Pages

To target classic pages, a user custom action must be added to the site collection or web.

1. Access the page containing the solution
2. Access the developer tool's console
   a) Press F-12 or Ctrl+Shift+I
   b) Select the console tab
3. Add/Remove the banner
   a) `Outages.Configuration.CustomAction.install()`
   b) `Outages.Configuration.CustomAction.uninstall()`

#### Extending the Solution

The solution can be forked and extended for further client customizations.