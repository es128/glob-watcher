# glob-watcher [![NPM version][npm-image]][npm-url] [![Build Status][travis-image]][travis-url] [![Coveralls Status][coveralls-image]][coveralls-url] [![Dependency Status][david-image]][david-url]

## Information

<table>
<tr>
<td>Package</td><td>glob-watcher</td>
</tr>
<tr>
<td>Description</td>
<td>Watch globs</td>
</tr>
<tr>
<td>Node Version</td>
<td>>= 0.10</td>
</tr>
</table>

## Usage

```javascript
var watch = require('glob-watcher');

// callback interface
watch(['./*.js', '!./something.js'], function(){
  // this function will be called each time a globbed
  // file is changed

  // if you need access to the `evt` object, listen
  // for the `change` event (see below)
});

// EE interface
var watcher = watch(['./*.js', '!./something.js']);
watcher.on('change', function(evt) {
  // evt has what file changed and all that jazz
});

// add files after it has been created
watcher.add('./somefolder/somefile.js');

// stop watching certain files
watcher.remove('./somefolder/dontcare.*');

// stop watching entirely
watcher.close();

// options can be passed to the underlying watch lib (chokidar) as a second arg
watcher = watch('./*.js', {usePolling: true});
```

[Chokidar options reference](https://github.com/paulmillr/chokidar#api)

*Note:* glob-watcher overrides chokidar's default `ignoreInitial` setting to
`true` if you do not set it explicitly. 


[npm-url]: https://npmjs.org/package/glob-watcher
[npm-image]: https://badge.fury.io/js/glob-watcher.png

[travis-url]: https://travis-ci.org/wearefractal/glob-watcher
[travis-image]: https://travis-ci.org/wearefractal/glob-watcher.png?branch=master

[coveralls-url]: https://coveralls.io/r/wearefractal/glob-watcher
[coveralls-image]: https://coveralls.io/repos/wearefractal/glob-watcher/badge.png

[depstat-url]: https://david-dm.org/wearefractal/glob-watcher
[depstat-image]: https://david-dm.org/wearefractal/glob-watcher.png

[david-url]: https://david-dm.org/wearefractal/glob-watcher
[david-image]: https://david-dm.org/wearefractal/glob-watcher.png?theme=shields.io
