# SQLite3 for offline environments - sqlite3-offline-next
[![BSD-3 licensed](https://img.shields.io/github/license/nicolaiort/sqlite3-offline-next?style=for-the-badge)](https://raw.githubusercontent.com/nicolaiort/sqlite3-offline-next/master/LICENSE)
[![npm](https://img.shields.io/npm/v/sqlite3-offline-next?style=for-the-badge)](https://www.npmjs.com/package/sqlite3-offline-next)
[![npm bundle size](https://img.shields.io/bundlephobia/min/sqlite3-offline-next?style=for-the-badge)](https://www.npmjs.com/package/sqlite3-offline-next)
[![npm](https://img.shields.io/npm/dw/sqlite3-offline-next?style=for-the-badge)](https://www.npmjs.com/package/sqlite3-offline-next)
![node-current](https://img.shields.io/node/v/sqlite3-offline-next?style=for-the-badge)
![forthebadge](https://img.shields.io/badge/fuck%20it-ship%20it-ff69b4?style=for-the-badge)
![security](https://img.shields.io/badge/security%20by-offline-lightgray?style=for-the-badge)

> Bundled library for [SQLite3](https://github.com/mapbox/node-sqlite3) for offline deployments.
> Zero dependencies, zero external HTTP downloads.

Based on the awesome work of [DenisCarriere](https://github.com/DenisCarriere) and [Howe Huang](https://github.com/shihuihzh) and just forked + published to by [me](https://github.com/nicolaiort).

After version upgrade to v5.0.0, Offical [SQLite3](https://github.com/mapbox/node-sqlite3) use Node-API to build native addons so that we can use one prebuild native library support across versions of Node.js. But Unfortunately, some old Node release and Electron version has been end of support.

## Install 🛠

```bash
# Install as normal package
npm install --save sqlite3-offline-next
yarn sqlite3-offline-next

# Install as sqlite3 alias
npm install --save sqlite3@npm:sqlite3-offline-next
yarn add sqlite3@npm:sqlite3-offline-next
```

## Quickstart 🚀

```javascript
const sqlite3 = require('sqlite3-offline-next').verbose()
var db = new sqlite3.Database('./dev.db')

db.serialize(function() {
  db.run("CREATE TABLE lorem (info TEXT)")

  var stmt = db.prepare("INSERT INTO lorem VALUES (?)")
  for (var i = 0; i < 10; i++) {
    stmt.run("Ipsum " + i)
  }
  stmt.finalize()

  db.each("SELECT rowid AS id, info FROM lorem", function(err, row) {
    console.log(row.id + ": " + row.info)
  })
})

db.close()
```


## Supported Platforms

- Windows x64 & ia32
- MacOSX x64
- Linux x64

### Untested
> These plattforms should work but I haven't tested them yet...

- Electron (Version below v5.0.0)
  - v1.5
  - v1.6
  - v1.7
  - v8.2
- Electron (Version after v5.0.0)
  - v6.0
  - v6.1
  - v7.0
  - v6.1
  - v8.0
  - v8.1
  - v8.2

## Supported NodeJS Releases

### Tested (only for v5.0.0 and up)

- Node.js v16
- Node.js v15
- Node.js v14

### Untested
> These releases should work but I haven't tested them yet...

Version v5.0.0 and up
- Node.js v13
- Node.js v12
- Node.js v11

Versions below v5.0.0
- Node.js v13
- Node.js v12
- Node.js v11
- Node.js v10
- Node.js v9
- Node.js v8
- Node.js v7
- Node.js v6
- Node.js v5
- Node.js v4

## License

BSD © [Mapbox](https://github.com/mapbox/node-sqlite3)
