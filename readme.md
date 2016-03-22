# folder-walker

A recursive stream of the files and directories in a given folder. Can take multiple folders.

[![build status](http://img.shields.io/travis/karissa/folder-walker.svg?style=flat)](http://travis-ci.org/karissa/folder-walker)
![dat](http://img.shields.io/badge/Development%20sponsored%20by-dat-green.svg?style=flat)

## Install

```
npm install folder-walker
```

## Examples

### Multiple folders

```js
var walker = require('folder-walker')
var stream = walker(['/path/to/folder', '/another/folder/here'])
stream.on('data', function (data) {
  console.log(data)
})
```

Example item in the stream:

```js
{
  basename: 'index.js',
  relname: 'test/index.js',
  root: '/Users/karissa/dev/node_modules/folder-walker',
  filepath: '/Users/karissa/dev/node_modules/folder-walker/test/index.js',
  stat: [fs.Stat Object],
  type: 'file' // or 'directory'
}
```

### Ignores

```js
var stream = walker('/path/to/folder', { ignore: ['.git', '.dat'] })
```