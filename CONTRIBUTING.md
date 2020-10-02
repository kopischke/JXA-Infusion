## How to contribute

The libraries and injections for JXA found in this repository originate in my personal automation needs. I have tried to keep them modular and generic enough to be useful outside the scenarios they were created for, but I don’t strive for “standard library“ levels of completeness. This means new features will probably only be added if you contribute code for them.

Extensions of, or entirely new, libraries and injections are welcome as long as their philosophy and API blends with the existing set, and as long as they follow the coding standards outlined below.

### API standards

APIs should be generic enough to be of use outside specialised situations. In  design and documentation, they should strive to feel at home besides [JS’ own](https://developer.mozilla.org/en-US/docs/Glossary/JavaScript) (for an example, see [`Array.prototype.findLast`](https://github.com/kopischke/JXA/wiki/Injections-API#findlast)). Where functionality  mimics JS core functionality, it should do so faithfully, even if that means more complexity (for an example, see [`String.prototype.toLocaleCapitalizedForm`](https://github.com/kopischke/JXA/wiki/Injections-API#tolocalecapitalizedform)).

### Coding standards

All code **must** be written in [_JavaScript Standard Style_](https://standardjs.com); functionality **must** be documented with  [_JSDoc_](https://jsdoc.app) tags. Please lint your code for both criteria before submitting, i.e. via [_ESLint_](https://eslint.org) (see below for configuration). 

#### Linting using ESLint

You will need [`eslint-config-standard`](https://github.com/standard/eslint-config-standard)  and [`eslint-plugin-jsdoc`](https://github.com/gajus/eslint-plugin-jsdoc) in your ESLint configuration. Typcially, these steps are needed:

```shell
# Install ESLint to your project development dependencies
npm install --save-dev eslint
# Install standard.js ESLint rules
npm install --save-dev eslint-config-standard eslint-plugin-standard eslint-plugin-promise eslint-plugin-import eslint-plugin-node
# Install JSDoc ESLint plugin
npm install --save-dev eslint-plugin-jsdoc
```

The repo contains an [`.eslintrc.json` configuration file](https://github.com/kopischke/JXA/blob/main/.eslintrc.json) with the needed settings to address the most common annoyances when linting JXA code.

#### Editor configuration

There is an [`.editorconfig` configuration file](https://github.com/kopischke/JXA/blob/main/.editorconfig) in the repo, which should help with the basic formatting and avoid manual editor configuration, if your editor supports [_EditorConfig_](https://editorconfig.org) (most seem to do, nowadays, or at least have a plugin that does).

### Testing

I am not aware of any JS testing framework supporting JXA, so there are no automated tests to write. However, you should extensively run any of your contributions and try out how edge cases perform manually in the Script Editor. 