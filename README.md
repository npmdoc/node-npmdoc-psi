# api documentation for  [psi (v3.0.0)](https://github.com/addyosmani/psi#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-psi.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-psi) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-psi.svg)](https://travis-ci.org/npmdoc/node-npmdoc-psi)
#### PageSpeed Insights with reporting

[![NPM](https://nodei.co/npm/psi.png?downloads=true)](https://www.npmjs.com/package/psi)

[![apidoc](https://npmdoc.github.io/node-npmdoc-psi/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-psi_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-psi/build..beta..travis-ci.org/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-psi/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-psi/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Addy Osmani",
        "email": "addyosmani@gmail.com",
        "url": "addyosmani.com"
    },
    "bin": {
        "psi": "cli.js"
    },
    "bugs": {
        "url": "https://github.com/addyosmani/psi/issues"
    },
    "dependencies": {
        "chalk": "^1.1.1",
        "download": "^4.4.1",
        "googleapis": "^16.1.0",
        "humanize-url": "^1.0.1",
        "lodash": "^4.5.1",
        "meow": "^3.5.0",
        "pify": "^2.3.0",
        "prepend-http": "^1.0.3",
        "pretty-bytes": "^4.0.2",
        "sort-on": "^1.2.2",
        "update-notifier": "^2.0.0"
    },
    "description": "PageSpeed Insights with reporting",
    "devDependencies": {
        "mocha": "^3.2.0",
        "xo": "^0.17.1"
    },
    "directories": {},
    "dist": {
        "shasum": "113c451ec094f9b16331db02eeb5295b8776a8be",
        "tarball": "https://registry.npmjs.org/psi/-/psi-3.0.0.tgz"
    },
    "engines": {
        "node": ">=4"
    },
    "files": [
        "cli.js",
        "index.js",
        "lib"
    ],
    "gitHead": "f69ff8857b43d81897970872849327c78cfdb1d0",
    "homepage": "https://github.com/addyosmani/psi#readme",
    "keywords": [
        "pagespeed",
        "insights",
        "speed",
        "page",
        "website",
        "measure",
        "optimize",
        "size"
    ],
    "license": "Apache-2.0",
    "maintainers": [
        {
            "name": "addyosmani",
            "email": "addyosmani@gmail.com"
        },
        {
            "name": "sindresorhus",
            "email": "sindresorhus@gmail.com"
        }
    ],
    "name": "psi",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git+https://github.com/addyosmani/psi.git"
    },
    "scripts": {
        "test": "xo && mocha"
    },
    "version": "3.0.0",
    "xo": {
        "space": true
    }
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module psi](#apidoc.module.psi)
1.  [function <span class="apidocSignatureSpan">psi.</span>output (url, opts)](#apidoc.element.psi.output)
1.  object <span class="apidocSignatureSpan">psi.</span>utils

#### [module psi.utils](#apidoc.module.psi.utils)
1.  [function <span class="apidocSignatureSpan">psi.utils.</span>buffer (msg, length)](#apidoc.element.psi.utils.buffer)
1.  [function <span class="apidocSignatureSpan">psi.utils.</span>labelize (label)](#apidoc.element.psi.utils.labelize)
1.  [function <span class="apidocSignatureSpan">psi.utils.</span>scoreColor {{signature}}](#apidoc.element.psi.utils.scoreColor)
1.  string <span class="apidocSignatureSpan">psi.utils.</span>divider



# <a name="apidoc.module.psi"></a>[module psi](#apidoc.module.psi)

#### <a name="apidoc.element.psi.output"></a>[function <span class="apidocSignatureSpan">psi.</span>output (url, opts)](#apidoc.element.psi.output)
- description and source-code
```javascript
(url, opts) => psi(url, opts).then(data => output(handleOpts(url, opts), data))
```
- example usage
```shell
...
// Get the PageSpeed Insights report
psi('theverge.com').then(data => {
console.log(data.ruleGroups.SPEED.score);
console.log(data.pageStats);
});

// Output a formatted report to the terminal
psi.output('theverge.com').then(() => {
console.log('done');
});

// Supply options to PSI and get back speed and usability scores
psi('theverge.com', {nokey: 'true', strategy: 'mobile'}).then(data => {
console.log('Speed score:', data.ruleGroups.SPEED.score);
console.log('Usability score:', data.ruleGroups.USABILITY.score);
...
```



# <a name="apidoc.module.psi.utils"></a>[module psi.utils](#apidoc.module.psi.utils)

#### <a name="apidoc.element.psi.utils.buffer"></a>[function <span class="apidocSignatureSpan">psi.utils.</span>buffer (msg, length)](#apidoc.element.psi.utils.buffer)
- description and source-code
```javascript
(msg, length) => {
  let ret = '';

  if (length === undefined) {
    length = 44;
  }

  length = length - msg.length - 1;

  if (length > 0) {
    ret = ' '.repeat(length);
  }

  return ret;
}
```
- example usage
```shell
...
  color = score < 21 ? chalk.red : color;
  color = score > 79 ? chalk.green : color;
  return color;
};

exports.labelize = str => {
  const label = humanizeTitleMap[str] || str;
  return label + exports.buffer(label) + chalk.grey('| ');
};
...
```

#### <a name="apidoc.element.psi.utils.labelize"></a>[function <span class="apidocSignatureSpan">psi.utils.</span>labelize (label)](#apidoc.element.psi.utils.labelize)
- description and source-code
```javascript
str => {
  const label = humanizeTitleMap[str] || str;
  return label + exports.buffer(label) + chalk.grey('| ');
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.psi.utils.scoreColor"></a>[function <span class="apidocSignatureSpan">psi.utils.</span>scoreColor {{signature}}](#apidoc.element.psi.utils.scoreColor)
- description and source-code
```javascript
score => {
  let color = chalk.yellow;
  color = score < 21 ? chalk.red : color;
  color = score > 79 ? chalk.green : color;
  return color;
}
```
- example usage
```shell
n/a
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
