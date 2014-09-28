# nconf-validator

Validation plugin for [nconf][0]


## Installation

### Installing npm (node package manager)
``` bash
  $ curl http://npmjs.org/install.sh | sh
```

### Installing nconf
``` bash
  $ [sudo] npm install nconf
```

### Installing nconf-validator
``` bash
  $ [sudo] npm install nconf-validator
```


## Usage
Following is a basic usage of the plugin. See `usage.1.js` and `usage.2.js` files for more usage examples.

### Require
Since `nconf-validator` is a `nconf` plugin, `nconf` must be loadded prior to `nconf-validator` and its reference must be passed as a required argument. So to use `nconf-validator`, the code looks something like this:
```js
var nconf = require('nconf');
var nval = require('nconf-validator')(nconf);
```

### Add rules
To add validation rules, `addRule` method can be used as follows:
```js
nval.addRule("app_ip", "ip");
nval.addRule("app_port", "port");
```
The above lines setup nconf-validator to perform following checks:
1. `app_ip`: a valid IP address
2. `app_port`: a valid port number

### Validate
Finally run validation on `nval`
```js
nval.validate();
```
Note that `validate` method is never called automatically. It must be called manually when one or more config values change and needs to be validated.


## End Matter

### Afterword

In simple scenarios, we may use a simple `config.json` file which stores all configuration of the app (essentially set by the app developer). So there's little or no need for validating that data. But as things get more complex, such as taking configuration values from command line and environment, we may start using a library like `nconf` to manage our configuration with ease. And in that exct situation, there's definitely a need for validating those values. 
While comparing `nconf` with [`convict`][2], I felt both of these awesome libraries were lacking some essential features that was available in the other. `nconf` was very easy to extend, so I made this little `nconf` plugin to add validation which was available in the other library.

### Author

[Mihir Gokani][1]


[0]: https://github.com/indexzero/nconf
[1]: https://github.com/mihirgokani007
[2]: https://github.com/mozilla/node-convict

