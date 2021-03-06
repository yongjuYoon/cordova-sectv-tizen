[![Build Status](https://travis-ci.org/Samsung/cordova-sectv-tizen.svg?branch=master)](https://travis-ci.org/Samsung/cordova-sectv-tizen)

# cordova-sectv-tizen
`cordova-sectv-tizen` is an application library that allows for Cordova-based projects to be built for the 2015's Samsung Tizen TV Platform.
Cordova based applications are, at the core, applications written with web technology: HTML, CSS and JavaScript.

# Supported Platform
* 2015's Samsung Tizen TV

# Project Structure
```
    ./
     |-cordova-js-src/ .... cordova-js sectv-tizen platform implementation
     |  |-plugin/ ......... cordova plugin implementations
     |  |-exec.js ......... cordova/exec module
     |  `-platform.js ..... cordova/platform module having platform definition and bootstrap
     |-www/ ............... Project template for Tizen platform
     |-package.json ....... npm package configuration
     '-README.md .......... this file
```

# How to Build
This section describes the build process which creates `cordova.js` file for the `sectv-tizen` cordova platform.
Please see [Cordova-js](http://github.com/apache/cordova-js) for more detail of `compile` task.

1. Clone the [Cordova-js](http://github.com/apache/cordova-js) project as sibling of this project.
    ```sh
    $ git clone https://github.com/Samsung/cordova-sectv-tizen.git
    $ git clone https://github.com/apache/cordova-js.git
    ```
    
    Repositories will be created like below directory structure.
    ```
    ./
     |-cordova-js
     `-cordova-sectv-tizen
    ```

2. Add "sectv-tizen" as a target of "compile" task on `Gruntfile.js` in the cordova-js project.
    ```js
    ...
    grunt.initConfig({
        pkg: grunt.file.readJSON('package.json'),
        "compile": {
            ...,
            "sectv-tizen": {}
        },
        "compile-browserify": {
        ...
    });
    ```

3. Add "sectv-tizen" property to "cordova-platforms" object in the cordova-js project's `package.json` with path to this project's repository as its value.
    ```JSON
    "cordova-platforms": {
        ...,
        "cordova-sectv-tizen": "../cordova-sectv-tizen"
    }
    ```

4. In the `cordova-js` directory's root, run below command to create `cordova-js/pkg/cordova.sectv-tizen.js` file.
    ```sh
    $ grunt compile:sectv-tizen
    ```

5. We recommend to copy the created file to the `www` directory which is including Tizen Application project templates for further use. In the `cordova-js` directory:
    ```sh
    $ cp ./pkg/cordova.sectv-tizen.js ../cordova-sectv-tizen/www/cordova.js
    ```

# How to use
For creating application package for 2015's Tizen TV:

1. Create a Tizen project with Tizen IDE and copy the `www` directory's content to the Tizen project.
2. Copy the built `cordova-js/pkg/cordova.sectv-tizen.js` to your tizen project directory's root with name `cordova.js`.
3. Build the tizen project.

* We recommand to use the [grunt-cordova-sectv](http://github.com/Samsung/grunt-cordova-sectv) Grunt task to automate these process.

# Known Issues
Not yet

[![Analytics](https://ga-beacon.appspot.com/UA-70262254-1/cordova-sectv-tizen/README)](https://github.com/igrigorik/ga-beacon)
