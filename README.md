# api documentation for  [dist (v0.1.2)](https://github.com/jgallen23/dist)  [![npm package](https://img.shields.io/npm/v/npmdoc-dist.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-dist) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-dist.svg)](https://travis-ci.org/npmdoc/node-npmdoc-dist)
#### a cli tool and library to create development and production versions for the browser

[![NPM](https://nodei.co/npm/dist.png?downloads=true&downloadRank=true&stars=true)](https://www.npmjs.com/package/dist)

[![apidoc](https://npmdoc.github.io/node-npmdoc-dist/build/screenCapture.buildCi.browser.apidoc.html.png)](https://npmdoc.github.io/node-npmdoc-dist/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-dist/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-dist/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Greg Allen",
        "url": "http://jga.me"
    },
    "bin": {
        "dist": "./bin/dist.js"
    },
    "bugs": {
        "url": "https://github.com/jgallen23/dist/issues"
    },
    "dependencies": {
        "filesize": "~1.6.6",
        "optimist": "~0.3.5",
        "uglify-js": "~1.3.4"
    },
    "description": "a cli tool and library to create development and production versions for the browser",
    "devDependencies": {
        "mocha": "*"
    },
    "directories": {},
    "dist": {
        "shasum": "8898629cc251297e36d1354a9a9598619aba5b1a",
        "tarball": "https://registry.npmjs.org/dist/-/dist-0.1.2.tgz"
    },
    "homepage": "https://github.com/jgallen23/dist",
    "main": "./lib/dist.js",
    "maintainers": [
        {
            "name": "jga"
        }
    ],
    "name": "dist",
    "optionalDependencies": {},
    "repository": {
        "type": "git",
        "url": "git+https://github.com/jgallen23/dist.git"
    },
    "scripts": {
        "test": "mocha"
    },
    "version": "0.1.2"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module dist](#apidoc.module.dist)
1.  [function <span class="apidocSignatureSpan"></span>dist (options)](#apidoc.element.dist.dist)
1.  [function <span class="apidocSignatureSpan">dist.</span>toString ()](#apidoc.element.dist.toString)



# <a name="apidoc.module.dist"></a>[module dist](#apidoc.module.dist)

#### <a name="apidoc.element.dist.dist"></a>[function <span class="apidocSignatureSpan"></span>dist (options)](#apidoc.element.dist.dist)
- description and source-code
```javascript
dist = function (options) {


  if (options.input) {
    options.source = fs.readFileSync(options.input, 'utf8');
  } else {
    if (!options.filename && options.complete) {
      return options.complete(new Error('filename is required when using source'));
    }
  }

  options.copyright = (options.copyright) ? fs.readFileSync(options.copyright, 'utf8') + '\n' : '';

  var devFile = (options.input) ? path.basename(options.input) : options.filename;
  var devSource = options.copyright + options.source;

  var prodFile = getProdFilename(devFile);
  var prodSource = generateProd(options.source, options.copyright);

  var dev = {
    filename: devFile,
    source: devSource,
    size: size(devSource)
  }

  var prod = {
    filename: prodFile,
    source: prodSource,
    size: size(prodSource)
  }

  if (options.out) {
    dev.filename = path.join(options.out, dev.filename);
    prod.filename = path.join(options.out, prod.filename);

    fs.writeFileSync(dev.filename, dev.source);
    fs.writeFileSync(prod.filename, prod.source);

  }


  if (options.complete) {
    options.complete(null, dev, prod)
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.dist.toString"></a>[function <span class="apidocSignatureSpan">dist.</span>toString ()](#apidoc.element.dist.toString)
- description and source-code
```javascript
toString = function () {
    return toString;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
