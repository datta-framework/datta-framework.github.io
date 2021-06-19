---
layout: default
title:  ""
categories: Solutions
---
![Demo](https://dev.azure.com/gudatta/0b5a858a-1b86-4230-93a6-b7aea3f76bbb/_apis/git/repositories/aabe30ef-6318-4318-a08f-85cbe1817d95/items?path=%2Fdemo.png)

### Overview

Helps manage user license requests from an organization. The solution is designed for SharePoint 2013/Online environments.

[Click Here](https://github.com/datta-framework/lmt) to access the repository.

#### Deployment Guide

Follow the [deployment steps](/jump-start-projects/overview/deployment) based on the target environment.

##### Additional Steps

###### Create the Security Groups

1. Access the page containing the solution
2. Access the developer tool's console
   a) Press F-12 or Ctrl+Shift+I
   b) Select the console tab
3. Create the security groups
   `LicenseManagementTool.Configuration.createSecurityGroups()`

#### Extending the Solution

The solution can be forked and extended for further client customizations.