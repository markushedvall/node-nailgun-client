# node-nailgun-client

A Node.js [Nailgun](http://martiansoftware.com/nailgun/) client API.

The Nailgun client API lets you run java code in Nailgun directly from your javascript in a Node.js environment.

# Install

```
npm install node-nailgun-client
```

# Example

Executing a command on a Nailgun server is very simple:
```javascript
var nailgunClient = require('node-nailgun-client');

var nail = nailgunClient.exec('ng-stats');

nail.stdout.pipe(process.stdout);
```

The Nailgun server address and port can be specfied using options:
```javascript
var nailgunClient = require('node-nailgun-client');

var options {
  address: 'localhost',
  port: 2113,
}

var args = ['your', 'args'];

var nail = nailgunClient.exec('yourpackage.YourClass', args, options);

nail.stdout.pipe(process.stdout);
nail.stderr.pipe(process.stderr);

process.stdin.pipe(nail.stdin);

nail.on('exit', function(code) {
  process.exit(code);
});
```

# License
Apache License 2.0
