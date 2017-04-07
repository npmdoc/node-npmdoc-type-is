# api documentation for  [type-is (v1.6.15)](https://github.com/jshttp/type-is#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-type-is.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-type-is) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-type-is.svg)](https://travis-ci.org/npmdoc/node-npmdoc-type-is)
#### Infer the content-type of a request.

[![NPM](https://nodei.co/npm/type-is.png?downloads=true)](https://www.npmjs.com/package/type-is)

[![apidoc](https://npmdoc.github.io/node-npmdoc-type-is/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-type-is_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-type-is/build/apidoc.html)

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
            "name": "Douglas Christopher Wilson",
            "email": "doug@somethingdoug.com"
        },
        {
            "name": "Jonathan Ong",
            "email": "me@jongleberry.com",
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
            "name": "dougwilson",
            "email": "doug@somethingdoug.com"
        },
        {
            "name": "jongleberry",
            "email": "jonathanrichardong@gmail.com"
        }
    ],
    "name": "type-is",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
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
    "version": "1.6.15"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module type-is](#apidoc.module.type-is)
1.  [function <span class="apidocSignatureSpan">type-is.</span>hasBody (req)](#apidoc.element.type-is.hasBody)
1.  [function <span class="apidocSignatureSpan">type-is.</span>is (value, types_)](#apidoc.element.type-is.is)
1.  [function <span class="apidocSignatureSpan">type-is.</span>match (expected, actual)](#apidoc.element.type-is.match)
1.  [function <span class="apidocSignatureSpan">type-is.</span>normalize (type)](#apidoc.element.type-is.normalize)



# <a name="apidoc.module.type-is"></a>[module type-is](#apidoc.module.type-is)

#### <a name="apidoc.element.type-is.hasBody"></a>[function <span class="apidocSignatureSpan">type-is.</span>hasBody (req)](#apidoc.element.type-is.hasBody)
- description and source-code
```javascript
function hasbody(req) {
  return req.headers['transfer-encoding'] !== undefined ||
    !isNaN(req.headers['content-length'])
}
```
- example usage
```shell
...
typeis(req, ['html', 'json'])     // 'json'
typeis(req, ['application/*'])    // 'application/json'
typeis(req, ['application/json']) // 'application/json'

typeis(req, ['html']) // false
'''

### typeis.hasBody(request)

Returns a Boolean if the given 'request' has a body, regardless of the
'Content-Type' header.

Having a body has no relation to how large the body is (it may be 0 bytes).
This is similar to how file existence works. If a body does exist, then this
indicates that there is data to read from the Node.js request stream.
...
```

#### <a name="apidoc.element.type-is.is"></a>[function <span class="apidocSignatureSpan">type-is.</span>is (value, types_)](#apidoc.element.type-is.is)
- description and source-code
```javascript
function typeis(value, types_) {
  var i
  var types = types_

  // remove parameters and normalize
  var val = tryNormalizeType(value)

  // no type or invalid
  if (!val) {
    return false
  }

  // support flattened arguments
  if (types && !Array.isArray(types)) {
    types = new Array(arguments.length - 1)
    for (i = 0; i < types.length; i++) {
      types[i] = arguments[i + 1]
    }
  }

  // no types, return the content type
  if (!types || !types.length) {
    return val
  }

  var type
  for (i = 0; i < types.length; i++) {
    if (mimeMatch(normalize(type = types[i]), val)) {
      return type[0] === '+' || type.indexOf('*') !== -1
        ? val
        : type
    }
  }

  // no matches
  return false
}
```
- example usage
```shell
...

  req.on('data', function (chunk) {
    // ...
  })
}
'''

### type = typeis.is(mediaType, types)

'mediaType' is the [media type](https://tools.ietf.org/html/rfc6838) string. 'types' is an array of types.

<!-- eslint-disable no-undef -->

'''js
var mediaType = 'application/json'
...
```

#### <a name="apidoc.element.type-is.match"></a>[function <span class="apidocSignatureSpan">type-is.</span>match (expected, actual)](#apidoc.element.type-is.match)
- description and source-code
```javascript
function mimeMatch(expected, actual) {
  // invalid type
  if (expected === false) {
    return false
  }

  // split types
  var actualParts = actual.split('/')
  var expectedParts = expected.split('/')

  // invalid format
  if (actualParts.length !== 2 || expectedParts.length !== 2) {
    return false
  }

  // validate type
  if (expectedParts[0] !== '*' && expectedParts[0] !== actualParts[0]) {
    return false
  }

  // validate suffix wildcard
  if (expectedParts[1].substr(0, 2) === '*+') {
    return expectedParts[1].length <= actualParts[1].length + 1 &&
      expectedParts[1].substr(1) === actualParts[1].substr(1 - expectedParts[1].length)
  }

  // validate subtype
  if (expectedParts[1] !== '*' && expectedParts[1] !== actualParts[1]) {
    return false
  }

  return true
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.type-is.normalize"></a>[function <span class="apidocSignatureSpan">type-is.</span>normalize (type)](#apidoc.element.type-is.normalize)
- description and source-code
```javascript
function normalize(type) {
  if (typeof type !== 'string') {
    // invalid type
    return false
  }

  switch (type) {
    case 'urlencoded':
      return 'application/x-www-form-urlencoded'
    case 'multipart':
      return 'multipart/*'
  }

  if (type[0] === '+') {
    // "+json" -> "*/*+json" expando
    return '*/*' + type
  }

  return type.indexOf('/') === -1
    ? mime.lookup(type)
    : type
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
