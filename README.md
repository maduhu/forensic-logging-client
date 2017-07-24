# forensic-logging-client
A client library used to connect to the forensic-logging-client

## Installation
You must have setup connection to the @leveloneproject npm repo on JFrog in order to install.
`npm install @leveloneproject/forensic-logging-sidecar`

## Usage
To use the forensic logging client, you only need to require it in the file you want to use the sidecar in, then call the relevant methods.:

```
'use strict'

const Client = require('@leveloneproject/forensic-logging-client')

const sidecar = createClient()

function createClient () {
  return Client.create({
    host: localhost,
    port: 5678,
    connectTimeout: 30000,
    reconnectInterval: 5000
  })
}

exports.connect = () => {
  return sidecar.connect()
}

exports.write = (msg) => {
  return sidecar.write(msg)
}
```

## API

### create(settings)
Creates a new sidecar client.

- `settings` {Object}
  - `host` {String} The hostname or IP address of the Sidecar Client server. Defaults to 'localhost'.
  - `port` {Number} The port for the Sidecar. Defaults to 5678.
  - `connectTimeout` {Number} The time, in milliseconds, to timeout a connection attempt to the Sidecar. Defaults to 30000.
  - `reconnectInterval` {Number} The time, in milliseconds, between connection attempts to the Sidecar. Defaults to 5000.
  
### sidecarClient.connect()
Connects to the sidecar.

This method will throw a `Unable to connect to sidecar within 30000ms` error if it can't connect to the sidecar.

### sidecarClient.write(message)
Writes a message to the sidecar.

- `message` {String} The message to send to the Sidecar.

This method will throw a `Sidecar is not connected` error if the sidecar has yet to be connected to.
