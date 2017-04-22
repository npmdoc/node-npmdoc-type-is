# npmdoc-type-is

#### api documentation for  [type-is (v1.6.15)](https://github.com/jshttp/type-is#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-type-is.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-type-is) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-type-is.svg)](https://travis-ci.org/npmdoc/node-npmdoc-type-is)

#### Infer the content-type of a request.

[![NPM](https://nodei.co/npm/type-is.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/type-is)

- [https://npmdoc.github.io/node-npmdoc-type-is/build/apidoc.html](https://npmdoc.github.io/node-npmdoc-type-is/build/apidoc.html)

[![apidoc](https://npmdoc.github.io/node-npmdoc-type-is/build/screenCapture.buildCi.browser.%252Ftmp%252Fbuild%252Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-type-is/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-type-is/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-type-is/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/jshttp/type-is/issues"
    },
    "contributors": [
        {
            "name": "Douglas Christopher Wilson"
        },
        {
            "name": "Jonathan Ong",
            "url": "http://jongleberry.com"
        }
    ],
    "dependencies": {
        "media-typer": "0.3.0",
        "mime-types": "~2.1.15"
    },
    "description": "Infer the content-type of a request.",
    "devDependencies": {
        "eslint": "3.19.0",
        "eslint-config-standard": "7.1.0",
        "eslint-plugin-markdown": "1.0.0-beta.4",
        "eslint-plugin-promise": "3.5.0",
        "eslint-plugin-standard": "2.1.1",
        "istanbul": "0.4.5",
        "mocha": "1.21.5"
    },
    "directories": {},
    "dist": {
        "shasum": "cab10fb4909e441c82842eafe1ad646c81804410",
        "tarball": "https://registry.npmjs.org/type-is/-/type-is-1.6.15.tgz"
    },
    "engines": {
        "node": ">= 0.6"
    },
    "files": [
        "LICENSE",
        "HISTORY.md",
        "index.js"
    ],
    "gitHead": "9e88be851cc628364ad8842433dce32437ea4e73",
    "homepage": "https://github.com/jshttp/type-is#readme",
    "keywords": [
        "content",
        "type",
        "checking"
    ],
    "license": "MIT",
    "maintainers": [
        {
            "name": "dougwilson"
        },
        {
            "name": "jongleberry"
        }
    ],
    "name": "type-is",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jshttp/type-is.git"
    },
    "scripts": {
        "lint": "eslint --plugin markdown --ext js,md .",
        "test": "mocha --reporter spec --check-leaks --bail test/",
        "test-cov": "istanbul cover node_modules/mocha/bin/_mocha -- --reporter dot --check-leaks test/",
        "test-travis": "istanbul cover node_modules/mocha/bin/_mocha --report lcovonly -- --reporter spec --check-leaks test/"
    },
    "version": "1.6.15",
    "bin": {}
}
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
