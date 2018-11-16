# multines&nbsp;&nbsp;[![Build Status](https://travis-ci.org/mcollina/multines.svg)](https://travis-ci.org/mcollina/multines)

Multi-process [nes][nes] backend, turn [nes][nes] into a fully scalable solution.

**multines** connect multiple instances of [Hapi][hapi] and [nes][nes]
through an external pub/sub broker, currently only [redis][redis] and
[mongodb][mongodb] are supported.

**multines** is powered by [MQEmitter][mqemitter],
[MQEmitterRedis][mqredis] and [MQEmitterMongodb][mqmongo].

**Important note:** this library needs nodejs 8 or greater.

## Install

```
npm i multines --save
```

## Example

See the [examples](./examples/) folder.

## API

### Options

- `[type]` - `'redis'` or `'mongodb'`, if nothing is specified it will
  use the in-memory [MQEmitter][mqemitter]
- `[mq]` - an instance of [MQEmitter][mqemitter], if you do not want to
  leverage the embedded constructor

The `options` object is passed through to
[MQEmitterRedis][mqredis] and [MQEmitterMongodb][mqmongo], check their
documentation for broker-specific config.

### server.subscriptionFar(path, options)

Wrap nes [`server.subscription(path, options)`](https://github.com/hapijs/nes/blob/master/API.md#serversubscriptionpath-options) adding the ability to receive messages from the MQEmitter-based broker.

The subscription supported is slightly different from nes, as it allows
[wildcards](https://github.com/mcollina/mqemitter#wildcards).

### server.publishFar(path, message)

Publish a message to the MQEmitter-based broker.

## Acknowledgements

This project was kindly sponsored by [nearForm](http://nearform.com).

## License

MIT

[nes]: http://npm.im/nes
[hapi]: http://npm.im/hapi
[redis]: http://redis.io
[mongodb]: http://www.mongodb.org
[mqemitter]: https://github.com/mcollina/mqemitter
[mqredis]: https://github.com/mcollina/mqemitter-redis
[mqmongo]: https://github.com/mcollina/mqemitter-mongodb

