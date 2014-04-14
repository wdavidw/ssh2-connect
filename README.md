[![Build Status](https://secure.travis-ci.org/wdavidw/node-ssh2-connect.png)][travis]

Node.js ssh2-connect
====================

The Node.js ssh2-connect package extends the [`ssh2`][ssh2] module to provide 
a simplified callback-back approach to initiate a new SSH connection.

Installation
------------

This is OSS and licensed under the [new BSD license][license].

```bash
npm install ssh2-connect
```

Examples
--------

The example is using both the "ssh2-connect" and "ssh2-fs" modules.

```js
connect = require('ssh2-connect');
fs = require('ssh2-fs');
connect({host: 'localhost'}, function(err, ssh){
  fs.mkdir(ssh, '/tmp/a_dir', (err, stdout, stderr){
    console.log(stdout);
  });
});
```

Compare this to the more verbose alternative using the original ssh2 module.

```js
ssh2 = require('ssh2');
fs = require('ssh2-fs');
connection = new ssh2();
connection.on('error', function(err){
  connection.end()
});
connection.on('ready', function(){
  fs.mkdir(connection, '/tmp/a_dir', (err, stdout, stderr){
    console.log(stdout);
  });
});
connection.connect({host: 'localhost'});
```

Development
-----------

Tests are executed with mocha. To install it, simple run `npm install`, it will install
mocha and its dependencies in your project "node_modules" directory.

To run the tests:
```bash
npm test
```

The tests run against the CoffeeScript source files.

To generate the JavaScript files:
```bash
make build
```

The test suite is run online with [Travis][travis] against Node.js version 0.9, 
0.10 and 0.11.

Contributors
------------

*   David Worms: <https://github.com/wdavidw>

[travis]: http://travis-ci.org/wdavidw/node-ssh2-connect
[ssh2]: https://github.com/mscdex/ssh2
[license]: https://github.com/wdavidw/node-ssh2-connect/blob/master/LICENSE.md

