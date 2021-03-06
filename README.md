# Qavalry
Qavalry (Qavalry) is a framework combining Cucumber(.js), WebdriverIO and Selenium for setting up a quick and easy testing environment.

## Installation
You can install Qavalry using NPM:
```bash
npm install qavalry
```
Using a commandline tool you first need to setup the required output folders. You can simply do this by running the following command:
```bash
npx qavalry setup
```
After the setup is completed you can run Qavalry using the command below. 
```bash
npx qavalry run [--options options.js] [--config config.js]
```

## Publish changes

1. Create a new tag with `npm version x.x.x-beta.x`
2. Publish with `npm publish --tag beta` 

## Configuration
When running the qavalry run command it is mandatory to specify an options file. The following code shows an example of what your options.js could look like:
```js
// options.js
module.exports.config = {
    baseUrl: 'https://github.com',
    specs: ['./features/**/*.feature'],
    cucumberOpts: {
        tagExpression: '@tag1'
    }
}
```
Optionally you can also specify an config file, which will be used to override the default config file from WebdriverIO. The following code shows an example of what the config.js would look like if you wanted to run the tests in Firefox:
```js
// config.js
module.exports.config = {
    capabilities: [{
        browserName: 'firefox'
    }]
}
```
More about the WebdriverIO configuration can be found [here.](http://webdriver.io/guide/getstarted/configuration.html)
### Options.js
#### baseUrl
Base URL used for the tests being started.

Type: `String`<br>
Default: `null`<br>
Example: `https://github.com/`
#### specs
A list of path queries of the Cucumber tests which should be run.

Type: `String[]`<br>
Default: `[]`<br>
Example: `['./features/**/*.feature']`
#### logOutput
A list of path queries of the Cucumber tests which should be run.

Type: `String[]`<br>
Default: `[]`<br>
Example: `['./features/**/*.feature']`

# Local Development

## Build

Run the following command in the source repository:
```bash
npm link
```

`This flow is still not optimal.`
Go to an empty folder and run the following commands:
```bash
npx qavalry setup
npm install semver
npm install babel-preset-env
```
Lastly, copy the `<repo>\dist\jsonReport.js`  file to target folder `<qavalry setup folder>\node_modules\qavalry\dist\jsonReport.js`

## Publish

Run the following command in the source repository:
```bash
npm run build
npm run prepublish
npm login
npm publish
```
