---
layout: default
title: Create a Basic Project
categories: Overview
---

### Overview

We will create a basic project from scratch.

#### Requirements

Follow the [SPFx Development](https://docs.microsoft.com/en-us/sharepoint/dev/spfx/set-up-your-development-environment) overview for guidance on how to setup a development environment.

- [NodeJS](https://nodejs.org/)
- [VS Code](https://code.visualstudio.com/)

### Create Directory

We will create a directory and create the project file.

```
mkdir my-project
cd my-project
npm init --y
```

![create project](/images/create-project.png)

This will create a `package.json` file giving an overview of the project and external libraries it consumes.

### Configure Project

Next, we will include our external libraries for building and packaging the solution.

#### Development Libraries

These libraries will be used to build and package the solution.

**Babel**

Babel is used to ensure the JavaScript will run in legacy and current browsers.

* [@babel/core](https://babeljs.io)
    * [@babel/preset-env](https://babeljs.io/docs/en/babel-preset-env)

**Webpack**

Webpack is used to bundle the files into a single output.

* [webpack](https://webpack.js.org/)
* [webpack-cli](https://webpack.js.org/api/cli/)
* Compile TypeScript to JavaScript
    * [babel-loader](https://www.npmjs.com/package/babel-loader)
    * [ts-loader](https://www.npmjs.com/package/ts-loader)
* Compile SASS/CSS
    * [css-loader](https://www.npmjs.com/package/css-loader)
    * [html-loader](https://www.npmjs.com/package/html-loader)
    * [node-sass](https://www.npmjs.com/package/node-sass)
    * [sass-loader](https://www.npmjs.com/package/sass-loader)
    * [style-loader](https://www.npmjs.com/package/style-loader)
* SASS/CSS Image References
    * [url-loader](https://www.npmjs.com/package/url-loader)

```
npm i --save-dev webpack webpack-cli @babel/core @babel/preset-env babel-loader css-loader html-loader node-sass sass-loader style-loader ts-loader url-loader
```
_The '--save-dev' will update the package.json file's "devDependencies" property._

#### Project Libraries

These libraries will be used by your project code and included in the output bundled file.

##### Basic SharePoint Project

A basic project with only the SharePoint REST library required.

* [gd-sprest](https://github.com/gunjandatta/sprest)

```
npm i --save gd-sprest
```
_The '--save' will update the package.json file's "dependencies" property._

##### Basic SharePoint Project w/ Bootstrap Components

A basic project with the SharePoint REST and Bootstrap component libraries.

* [gd-sprest-bs](https://github.com/gunjandatta/sprest-bs)

```
npm i --save gd-sprest-bs
```
_The '--save' will update the package.json file's "dependencies" property._

##### Basic Dashboard Project

A basic dashboard solution using the [dattatable library](/dattatable). A [step-by-step](https://github.com/gunjandatta/sp-dashboard/wiki) walkthrough is available.

* [dattatable](https://github.com/datta-framework/dattatable)
    * [gd-sprest-bs](https://gunjandatta.github.io/extras/bs)
    * [moment](https://momentjs.com/)
* [datatables.net](https://datatables.net/)
    * [datatables.net-bs5](https://datatables.net/examples/styling/bootstrap5.html)
    * [jquery](https://jquery.com/)

```
npm i --save dattatable gd-sprest-bs moment datatables.net datatables.net-bs5 jquery
```
_The '--save' will update the package.json file's "dependencies" property._

#### Project Configuration (./package.json)

Update the `main` source property to the project's entry point. Update the `scripts` property to run build and compile the solution.

```
"main": "src/index.ts",
"scripts": {
    "all": "npm run build && npm run prod",
    "build": "webpack --mode=development",
    "prod": "webpack --mode=production"
}
```

#### TypeScript Configuration (./tsconfig.json)

Since we are using [TypeScript](https://www.typescriptlang.org/) to code the solution, we will need to specify theenvironment and source files to include.

```json
{
    "compilerOptions": {
        "target": "es5",
        "lib": [
            "dom",
            "es2015"
        ]
    },
    "include": [
        "src/**/*"
    ]
}
```

#### WebPack Configuration (./webpack.config.js)

```js
var project = require("./package.json");
var path = require("path");

// Return the configuration
module.exports = (env, argv) => {
    var isDev = argv.mode !== "production";
    return {
        // Set the main source as the entry point
        entry: [
            path.resolve(__dirname, project.main)
        ],

        // Output location
        output: {
            path: path.resolve(__dirname, "dist"),
            filename: project.name + (isDev ? "" : ".min") + ".js"
        },

        // Resolve the file names
        resolve: {
            extensions: [".js", ".css", ".scss", ".ts"]
        },

        // Dev Server
        devServer: {
            inline: true,
            hot: true,
            open: true,
            publicPath: "/dist/"
        },

        // Loaders
        module: {
            rules: [
                // SASS to JavaScript
                {
                    // Target the sass and css files
                    test: /\.s?css$/,
                    // Define the compiler to use
                    use: [
                        // Create style nodes from the CommonJS code
                        { loader: "style-loader" },
                        // Translate css to CommonJS
                        { loader: "css-loader" },
                        // Compile sass to css
                        { loader: "sass-loader" }
                    ]
                },
                // Handle Image Files
                {
                    test: /\.(jpe?g|png|gif|svg|eot|woff|ttf)$/,
                    loader: "url-loader"
                },
                // JavaScript
                {
                    // Target JavaScript files
                    test: /\.jsx?$/,
                    use: [
                        // JavaScript (ES5) -> JavaScript (Current)
                        {
                            loader: "babel-loader",
                            options: { presets: ["@babel/preset-env"] }
                        }
                    ]
                },
                // TypeScript to JavaScript
                {
                    // Target TypeScript files
                    test: /\.tsx?$/,
                    use: [
                        // JavaScript (ES5) -> JavaScript (Current)
                        {
                            loader: "babel-loader",
                            options: { presets: ["@babel/preset-env"] }
                        },
                        // TypeScript -> JavaScript (ES5)
                        { loader: "ts-loader" }
                    ]
                }
            ]
        }
    };
}
```

### Start Coding

Create your src/index.ts file and start coding.

#### Build Solution

Run `npm run build` or `npm run prod` to create the `dist/my-project.js` or `dist/my-project.min.js` output files. Running `npm run all` will create both.