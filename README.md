# bootstrap-treeview-node

> - list directory-tree (recursively) based on [directory-tree](https://www.npmjs.com/package/directory-tree),
> - working nicely with [bootstrap-treeview](https://github.com/jonmiles/bootstrap-treeview).

Creates an javascript object representing a directory tree.

## Install
```js
npm i -S bootstrap-treeview-node

```


##Usage

```js
var dirTree = require('bootstrap-treeview-node');
var tree = dirTree('/some/path');
```

And you can also filter by extensions (with Array), or by name patterns (with RegExp):

```js
var dirTree = require('bootstrap-treeview-node');
var filteredTree = dirTree('/some/path', ['.jpg', '.png']);
```

This will take a directory tree:

```
photos
├── summer
│   └── june
│       └── windsurf.jpg
└── winter
    └── january
        ├── ski.png
        └── snowboard.jpg
```

And return a js object:

```json
{
  "href": "photos",
  "text": "photos",
  "size": 600,
  "nodes": [
    {
      "href": "photos/summer",
      "text": "summer",
      "size": 400,
      "nodes": [
        {
          "href": "photos/summer/june",
          "text": "june",
          "size": 400,
          "nodes": [
            {
              "href": "photos/summer/june/windsurf.jpg",
              "size": 400,
              "text": "windsurf.jpg",
            }
          ]
        }
      ]
    },
    {
      "href": "photos/winter",
      "text": "winter",
      "size": 200,
      "nodes": [
        {
          "href": "photos/winter/january",
          "text": "january",
          "size": 200,
          "nodes": [
            {
              "href": "photos/winter/january/ski.png",
              "text": "ski.png",
              "size": 100,
            },
            {
              "href": "photos/winter/january/snowboard.jpg",
              "text": "snowboard.jpg",
              "size": 100,
            }
          ]
        }
      ]
    }
  ]
}
```

## API

#### dirTree(path [, includes, excludes])

- `path` {String}:   is the relative or absolute path to the base directory e.g. '.' for cwd.
- `includes` {RegExp|Array}: optional, Array tests the file extension, RegExp tests the filename.
- `excludes` {RegExp|Array}: optional, Array tests the file extension, RegExp tests the filename.

## Examples

```js
var tree
tree = dirTree('.', ['.jpg', '.png']) // list only files with .jpg or .png file extensions
tree = dirTree('/home/pi', /^[A-z]/) // list only files/directories that start with letters
tree = dirTree('../', null, /^\./) // ignore only files/directories that start with a dot like .git
```


## Dev

To run tests go the package root in your CLI and run,

```bash
$ npm test
```

Make sure you have the dev dependcies installed (e.g. `npm install .`)


## Credit

- based on [directory-tree](https://www.npmjs.com/package/directory-tree),
- mainly only useful together with [bootstrap-treeview](https://github.com/jonmiles/bootstrap-treeview)

