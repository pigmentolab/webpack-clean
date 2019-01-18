[![GitHub stars](https://img.shields.io/github/stars/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/network)
[![GitHub issues](https://img.shields.io/github/issues/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/issues)
[![GitHub issues closed](https://img.shields.io/github/issues-closed/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/issues?q=is%3Aissue+is%3Aclosed)

[![Github release date](https://img.shields.io/github/release-date/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/releases)
[![Github release version](https://img.shields.io/github/release/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/releases)
[![npm release version](https://img.shields.io/npm/v/webpack-glob-clean.svg?style=flat-square)](https://nodei.co/npm/webpack-glob-clean)
[![Github commits since last release](https://img.shields.io/github/commits-since/pigmentolab/webpack-clean/latest.svg?style=flat-square)](https://www.npmjs.com/package/webpack-glob-clean)

[![npm](https://nodei.co/npm/webpack-glob-clean.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/webpack-glob-clean)

[![npm monthly downloads](https://img.shields.io/npm/dm/webpack-glob-clean.svg?style=flat-square)](https://www.npmjs.com/package/webpack-glob-clean)
[![npm yearly downloads](https://img.shields.io/npm/dy/webpack-glob-clean.svg?style=flat-square)](https://www.npmjs.com/package/webpack-glob-clean)

[![license](https://img.shields.io/github/license/pigmentolab/webpack-clean.svg?style=flat-square)](https://github.com/pigmentolab/webpack-clean/blob/master/LICENSE)

## Webpack Glob Clean

A webpack plugin to clean specified files after build

### Getting started

Install the plugin:

```
npm install webpack-glob-clean --save-dev
yarn add webpack-glob-clean --dev
```


### API
```javascript
new WebpackCleanPlugin(files: array|string, [ { [basePath: string], [removeMaps: boolean] } ])
```

* `files` - array of files or string for a single file relative to the `basePath` or to the `context` of your config (if the `basePath` param is not specified),
* `basePath` (optional) - string - directory to be resolved to
* `verbose` (optional) - boolean - enable verbose logging. Disabled by default.
* `forceDelete` (optional) - boolean - specify if the files should be force deleted in case of compile errors. If `forceDelete` is not enabled, the compile errors will be logged to `stdout` but the deletion of the files will not take place. Disabled by default.

### Usage

```javascript
var WebpackCleanPlugin = require('webpack-glob-clean');

module.exports = {
    context: path.join(__dirname, './'),
    entry: './src/index.js',
    output: {
        filename: 'bundle.js',
        path: path.resolve(__dirname, 'dist')
    },
    plugins: [
        new WebpackCleanPlugin([
            'dist/test1.js',
            'dist/test2.js'
        ])
    ]
};

module.exports = {
    plugins: [
        new WebpackCleanPlugin(
            'dist/fileA.js',
            {basePath: path.join(__dirname, './')}
        )
    ]
};

module.exports = {
    plugins: [
        new WebpackCleanPlugin(
            'dist/**/fileA.js',
            {basePath: path.join(__dirname, './')}
        )
    ]
};

module.exports = {
    plugins: [
        new WebpackCleanPlugin([
            'fileA.js',
            'folder/**/*.map',
            'dist/*.js'
        ], {basePath: path.join(__dirname, 'dist')})
    ]
};

module.exports = {
    plugins: [
        new WebpackCleanPlugin([
            'fileA.js',
            'fileB.js'
        ], {basePath: path.join(__dirname, 'dist'), verbose: true})
    ]
};

module.exports = {
    plugins: [
        new WebpackCleanPlugin([
            'fileA.js',
            'fileB.js'
        ], {basePath: path.join(__dirname, 'dist'), forceDelete: true})
    ]
};
```
