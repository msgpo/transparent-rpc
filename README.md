# Transparent RPC

[![Build Status](https://travis-ci.com/stanford-oval/transparent-rpc.svg?branch=master)](https://travis-ci.com/stanford-oval/transparent-rpc) [![Coverage Status](https://coveralls.io/repos/github/stanford-oval/transparent-rpc/badge.svg?branch=master)](https://coveralls.io/github/stanford-oval/transparent-rpc?branch=master) [![Dependency Status](https://david-dm.org/stanford-oval/transparent-rpc/status.svg)](https://david-dm.org/stanford-oval/transparent-rpc) [![Greenkeeper badge](https://badges.greenkeeper.io/stanford-oval/transparent-rpc.svg)](https://greenkeeper.io/) [![Language grade: JavaScript](https://img.shields.io/lgtm/grade/javascript/g/stanford-oval/transparent-rpc.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/stanford-oval/transparent-rpc/context:javascript)

Automatic Proxy-based RPC for Node.js

## How to use:

- Add `$rpcMethods` property to the prototype of the classes you want to export
- Create `rpc.Socket` object wrapping the transport layer (an object-mode stream supporting arbitrary objects)

  ````
  const rpc = require('transparent-rpc');
  let socket = new rpc.Socket(...);
  ````

- Publish the first stub object:

  ```
  let id = socket.addStub(mystub);
  ```

- Transmit the ID of the stub out of band
- Handle methods on the stub
- Objects received by the stub will be proxies
- Invoking a method on a proxy returns a promise for the execution of that method
- To publish more objects, return them from the stub's methods, or pass them them to remote proxy methods
