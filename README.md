# JXA

Libraries, both native and runtime injectable, for macOS’ JavasScript for Automation ([JXA](https://developer.apple.com/library/archive/releasenotes/InterapplicationCommunication/RN-JavaScriptForAutomation/Articles/OSX10-11.html)) system.

## Contents

This repository contains two different kind of JXA libraries:

1. **Libraries:** these are native OSA libraries used with `Library()`. They are managed as JXA source code but need to  be compiled with `osacompile` before usage  (see below).
2. **Injections:** these are libraries extending the JXA object space. You will need the _JXA_ native library to inject them into the JXA runtime. These are used as is.

## Installing the libraries

OSA libraries need to go into a folder recognised by the  `Library()` command on your system (basically [here](https://developer.apple.com/library/archive/releasenotes/InterapplicationCommunication/RN-JavaScriptForAutomation/Articles/OSX10-10.html#//apple_ref/doc/uid/TP40014508-CH109-SW14) and, starting from macOS 10.11, [here](https://developer.apple.com/library/archive/releasenotes/InterapplicationCommunication/RN-JavaScriptForAutomation/Articles/OSX10-11.html#//apple_ref/doc/uid/TP40014508-CH110-SW10)). The recommended location is the _Script Libraries_ folder in you user _Library_.  

Note the script files in the **Libraries** tree need to be compiled to binary OSA script files before usage. You can either download the releases from Github, which contain the native libraries in  compiled format, or compile them yourself using  `osacompile` as follows:

```shell
osacompile -l JavaScript -o ~/Library/Script Libraries/<name>.scpt <name>.jxa
```

**Injections** should be copied to a recognised  location “as is”. The injection mechanism of the _JXA_ library expects plain text files, so do not compile these!

## Using the libraries

The **libraries**, once compiled and installed as described above, are directly available to the  `Library()` command in your scripts, i.e.

```js
const parser = Library('TextParser')
const addresses = parser.extractAddresses('Apple, One Apple Park Way, Cupertino, CA 95014.')
```

The **injection libraries** need a little two-step:

```js
const jxa = Library('JXA')
var _p = new Function(jxa.source('Path')); _p(); _p = null
```
This will inject the _Path_ extensions into the `Path` object.

### API

For the API of the individual libraries (either native or injected), see the [Wiki](https://github.com/kopischke/JXA/wiki#api-documentation).

### Compatibility

All scripts are written in ES6 conforming JavaScript. Because the JavaScript Core used in the first OS releases to support JXA, macOS 10.10 (*Yosemite*) and macOS 10.11 (*El Capitan)*, did not fully support the ES6 feature set, macOS 10.12 (*Sierra*) or better is required to use the libraries.
