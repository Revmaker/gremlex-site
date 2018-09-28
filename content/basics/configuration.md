---
title: "Configuration"
date: 2018-09-28T13:52:35-07:00
weight: 2
---

## Configuration
You can configure Gremlex by adding the following to your `config.exs`:
```js
config :gremlex,
  host: "127.0.0.1",
  port: 8182,
  path: "/gremlin",
  pool_size: 10,
  secure: false
```

Gremlex uses [confex](https://github.com/Nebo15/confex), so that you can easily define
your configuration to use environment variables when it comes time to deploying. To do so,
simply have the parameters that need to be dynamically read at run time set to `{:SYSTEM, "ENV_VAR_NAME"}`.

### Parameters
* `host`: Gremlin host to connect to (defaults to "127.0.0.1")
* `port`: Port Gremlin is listening to on host (defaults to 8182)
* `path`: Websocket path to Gremlin (defaults to "/gremlin")
* `pool_size`: The number of connections to keep open in the pool (defaults to 10)
* `secure`: Set to `true` to connect to a server with SSL enabled