# Setup

### As CLI {#setup-as-command-line-tool}

Run this to install **Nesu** as a global package:

```bash
$ npm install -g @rappopo/nesu
```

Go to your project folder, and invoke:

```bash
$ nesu
```

The first time **Nesu** starts, it’ll create an empty `config.json` configuration file, `transformer` and `last_seq` __folder in your project folder. Quit **Nesu** by pressing `Ctrl-c` and start customizing its configurations \(please see details below\).

### As Library {#setup-as-a-library}

Go to your node.js application project folder, and type:

```bash
$ npm install --save @rappopo/nesu
```

Create an empty new js file, e.g.: **nesu.js**, and enter the following code:

```javascript
var nesu = require('@rappopo/nesu')
nesu()
```

Also create the `config.json` configuration file in the same folder as **nesu.js** file above like this example below:

```javascript
{
  "db": {
    "mydb1": {
      "idleTimeout": 0
    },
    "mydb2": {
      "cdb": {
        "url": "http://couchdb:5984",
        "name": "mycouchdb1"
      },
      "es": {
        "url": "http://elasticsearch:9200",
        "name": "myesindex1"
      },
      "bulkLimit": 500,
      "idleTimeout": 10
    }
  },
  "default": {
    "bulkLimit": 5000
  }
}
```

And finaly:

```bash
$ node nesu.js
```

But most likely you’ll want to use a process manager like **pm2**.

Program will automatically create an empty `config.js` file if missing. Two empty folders `transformer` and `last_seq` will also be created.

You might also want to change the configuration object above dynamically within your script, like this:

```javascript
...
nesu({ config: <config> })
...
```

The value of `<config>` will simply be merged with the above configuration file.

