# forensic-logging-client
Client to connect to the forensic-logging-sidecar

## Usage
To use the forensic logging client, you only need to require it in the file you want to use the sidecar in:

```
const Client = require('@leveloneproject/forensic-logging-client')
```

To initialize the sidecar client simplay call the `create` method with the relevant values.

```
const client = Client.create({
        host: thehost,
        port: 5678,
        connectTimeout: 3000,
        reconnectInterval: 5000
  })
  ```

Once the client has been created, you need to make a call to `connect` to it.

```
client.connect()
```

After the client has been connected, you can `write` to it at will.

```
client.write('the message')
```
