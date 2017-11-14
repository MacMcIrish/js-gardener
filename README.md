# Gardener [![gardener](https://github.com/simlu/grunt-gardener/blob/master/assets/badge-large.svg)](https://github.com/simlu/grunt-gardener)

[![Build Status](https://img.shields.io/travis/simlu/grunt-gardener/master.svg)](https://travis-ci.org/simlu/grunt-gardener)
[![Test Coverage](https://img.shields.io/coveralls/simlu/grunt-gardener/master.svg)](https://coveralls.io/github/simlu/grunt-gardener?branch=master)
[![Greenkeeper badge](https://badges.greenkeeper.io/simlu/grunt-gardener.svg)](https://greenkeeper.io/)
[![NPM](https://img.shields.io/npm/v/grunt-gardener.svg)](https://www.npmjs.com/package/grunt-gardener)
[![Downloads](https://img.shields.io/npm/dt/grunt-gardener.svg)](https://www.npmjs.com/package/grunt-gardener)
[![Semantic-Release](https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg)](https://github.com/semantic-release/semantic-release)
[![Gardener](https://github.com/simlu/grunt-gardener/blob/master/assets/badge.svg)](https://github.com/simlu/grunt-gardener)
[![Gitter](https://img.shields.io/gitter/room/simlu/grunt-gardener.svg)](https://gitter.im/simlu/grunt-gardener)

Minimizes package setup and maintenance complexity, so you can focus on writing code. Highly recommended if you are getting started with a new package and extremely useful if you are maintaining multiple packages.

Gardener enforces many best code style practises using [ESLint](https://eslint.org/) and [YAMLlint](https://github.com/nodeca/js-yaml), semi-automates config generation, provides various integrity tests (e.g. checks for un-used dependencies), enforces 100% test coverage using [Istanbul](https://istanbul.js.org/) and helps you set up [CI](https://en.wikipedia.org/wiki/Continuous_integration) using [TravisCI](https://travis-ci.org/), [CD](https://en.wikipedia.org/wiki/Continuous_delivery) using [Semantic-Release](https://github.com/semantic-release/semantic-release) ([NPM](https://www.npmjs.com/), [GitHub](https://github.com/)) and semi-automatic dependency updates using [Greenkeeper](https://greenkeeper.io/).

# Getting Started

### Preparation

- Create New Project
- Create Empty Repository
- Run `git init`, `git remote add origin URL`, `git checkout -b master`
- Run `npm init` and fill in details

### Install Gardener

    $ npm install --save-dev grunt-gardener

### Run Basic Setup

Create `gruntfile.js` in the root folder with the following contents

```javascript
module.exports = (grunt) => {
  grunt.initConfig({
    pkg: grunt.file.readJSON('package.json'),
    gardener: {
      this: {
        options: {}
      }
    }
  });

  grunt.loadNpmTasks('grunt-gardener');
};
```

Then run

    $ grunt gardener

This will generate some files and alter your existing package.json file.

# Folder Structure

Write your tests in the `test` and your code in the `lib` folder.

# Badges

When completed, verify each badge by clicking on it.

If you username is different between github and other services, you will need to adjust the badge urls.

### Travis

Create TravisCI account, preferably with the same username that you use for github. Then enable TravisCI access to your repo.

### Coveralls

Create Coveralls account, preferably with the same username that you use for github. Then enable Coveralls access to your repo.

### Greenkeeper

Create Greenkeeper account, preferably with the same username that you use for github. Then enable Greenkeeper access to your repo.

### NPM and Downloads

Create NPM account, preferably with the same username that you use for github.

### Semantic-Release

Install Semantic-Release globally with

    $ npm install -g semantic-release-cli

then run

    $ semantic-release-cli setup

and follow instructions.

### Gardener

You've already enabled this by following the first steps of the Readme.

### Gitter

Log into Gitter and create a room with your project name on github.

# Options

### skip

Type: `array`<br>
Default: `[]`

Array of tasks to skip. Should not be necessary to use unless you really need to. Available tasks are:
- `mkdir`: Auto create folders
- `copy`: Copy template files
- `gardener_configure`: Alter configuration files, insert badges
- `projectUpdate`: Install dependencies exactly as specified in package.json
- `eslint`: Ensure code is according to best eslint practises
- `yamllint`: Ensure yaml files are passing lint
- `depcheck`: Ensure all installed dependencies are used
- `checkDependencies`: Ensure dependencies are installed as specified in package.json
- `mocha_istanbul`: Run tests in `test` folder and force 100% coverage

### root

Type: `string`<br>
Default: `process.cwd()`

Specify the directory to run the tests against. Useful if you have multiple packages that you manage centralized from a parent folder.

# Ignore Files

### .coverignore

Define files which should be excluded from coverage. Always excluded files can be found [here](lib/conf/.coverignore).

### .eslintignore

Define files which should be excluded for eslint. Always excluded files can be found [here](lib/conf/.eslintignore).

### .depunusedignore

Define packages that should be excluded from usage check. Useful when a false negative is detected, e.g. for plugins where usage is defined in configuration. Always excluded packages can be found [here](lib/conf/.depunusedignore).

# Sample Project

While this project utilizes itself for testing (how cool is that?), a cleaner example can be found [here](test/mock).

All [my npm packages](https://www.npmjs.com/~simlu) also utilize Gardener.

# How to Contribute

When you contribute to any Gardener repositories, always run `npm test` locally before you open a PR.
