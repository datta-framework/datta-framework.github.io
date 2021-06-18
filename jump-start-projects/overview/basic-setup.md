Follow these steps to create a solution from a Jump Start project.

#### Fork the Solution

Find the target jump start project repository and select the ellipsis to view other options. Select the `Fork` command to clone the solution to your own project.

##### Download the Code

Use `git clone _url to repository_` to download the solution to your development machine.

#### Update the Configuration

Edit the `package.json` file and update the following properties:

* name
* description
* scripts
  * _(Optional) Update the `all` command to exclude the `spfx` option if you are not building an SPFx solution_
* repository
  * Clear or update the url property
* author

#### Install the Libraries

Run `pnpm i` or `npm i` to install the libraries.

##### Install Additional Libraries

If you need to install additional libaries, do so now using the `pnpm i --save [library]` or `npm i --save [library]` command. You can find the available libraries at [NPM](https://www.npmjs.com/).

#### Update the Global Strings

Edit the `src/strings.ts` file and update the following properties:

* AppElementId
* GlobalVariable
* ProjectDescription
* ProjectName
* Lists
  * Define all list names used in this project
* SolutionUrl
  * Replace `core-sp` with the `name` property in the `package.json` file
* WebSourceUrl
 * Replace `core-sp` with the `name` property in the `package.json` file
 * Replace `core-sp.min.js` with the `name` property in the `package.json` file

#### Update the Assets File

The `assets/index.html` file is referenced by the content editor webpart for classic solutions. Update the following properties:

* Replace the id `datta-core` property with the `AppElementId` property in the `src/strings.ts` file
* Replace the src `core-sp.min.js` property with the `name`.min.js property in the `package.json` file
