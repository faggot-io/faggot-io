faggot-io - Real-time log monitoring in your browser [![Build Status](https://travis-ci.org/muchweb/faggot-io.svg?branch=master)](https://travis-ci.org/muchweb/faggot-io) [![Dependency Status](https://gemnasium.com/muchweb/faggot-io.svg)](https://gemnasium.com/muchweb/faggot-io)
=================================================

Powered by [node.js](http://nodejs.org) + [socket.io](http://socket.io)

## How does it work?

*Harvesters* watch log files for changes, send new log messages to the *server* via TCP, which broadcasts to *web clients* via socket.io.

Log streams are defined by mapping file paths to a stream name in harvester configuration.

Users browse streams and nodes in the web UI, and activate (stream, node) pairs to view and search log messages in screen widgets.

## Install Server & Harvester

### Docker
Check our [Docker faggot-io server image](https://registry.hub.docker.com/u/muchweb/faggot-io-arch/).

### NPM

> Please note that you will require `coffee-script` installed
> ```
> npm install -g coffee-script
> ```

---

> Please also note that on GNU operation system, you will require `node-gyp` dependencies:
>
> - `python2`
> - `make`
> - `gcc`
>
> These can be installed via your package manager

---

1. Install via NPM

    ```bash
    npm install -g faggot-io --user "ubuntu"
    ```

2. Run server

    ```bash
    faggot-io-server
    ```

3. Configure harvester

    ```bash
    nano ~/.faggot-io/harvester.conf
    ```

4. Run harvester

    ```bash
    faggot-io-harvester
    ```

5. Browse to [http://localhost:28778](http://localhost:28778) to see live logs

## Server TCP Interface

Harvesters connect to the server via TCP, and write properly formatted strings to the socket.  Third party harvesters can send messages to the server using the following commands:

Send a log message

    +log|my_stream|my_node|info|this is log message\r\n

Register a new node

    +node|my_node\r\n

Register a new node, with stream associations

    +node|my_node|my_stream1,my_stream2\r\n

Remove a node

    -node|my_node\r\n


## Building

Global NPM dependencies: `coffee-script`, `mocha`, `less` and `browserify`

    npm install
    cake build

### Building documentation

Global NPM dependency: `yuidocjs`

    cake docs

Then navigate to `docs/index.html`

Theme was based on [yuidoc-bootstrap-theme](https://www.npmjs.org/package/yuidoc-bootstrap-theme).

## Testing

Global NPM dependencies: `nodeunit`

    npm test

## Credits

Based on [NarrativeScience/Log.io](https://github.com/NarrativeScience/Log.io).

- Mike Smatherzs &lt;msmathers@narrativescience.com&gt; ([msmathers](http://github.com/msmathers))
- Narrative Science http://narrativescience.com ([NarrativeScience](http://github.com/NarrativeScience))
- muchweb ([muchweb](http://github.com/muchweb))

## Acknowledgements

- Jeremy Ashkenas ([jashkenas](https://github.com/jashkenas))
- Guillermo Rauch &lt;guillermo@learnboost.com&gt; ([Guille](http://github.com/guille))
- Ryan Dahl &lt;ry at tiny clouds dot org&gt; ([ry](https://github.com/ry)) + Joyent http://www.joyent.com/ ([joyent](https://github.com/joyent/))
- [turtlebender](http://github.com/turtlebender)
- [jdrake](http://github.com/jdrake)

## License

Copyright 2013 Narrative Science &lt;contrib@narrativescience.com&gt;

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
