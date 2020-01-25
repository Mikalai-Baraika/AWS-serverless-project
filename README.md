# AWS-severless-project

AWS Iot lifecycle and regular topic subscription events

## Prerequisites
* serverless@1.x
* redis

## Install

1) `npm install --save AWS-severless-project`

2) In `serverless.yml` add `AWS-severless-project` to plugins:

```yaml
plugins:
  - AWS-severless-project
```

## Usage
1. Start redis:  
    `redis-server`

2. Run 
    
    `sls iot start`

CLI options are optional:

```
--port                -p  Port to listen on. Default: 1883
--httpPort            -h  Port for WebSocket connections. Default: 1884
--noStart             -n  Prevent Iot broker (Mosca MQTT brorker) from being started (if you already have one)
--skipCacheValidation -c  Tells the plugin to skip require cache invalidation. A script reloading tool like Nodemon might then be needed (same as serverless-offline)
```

The above options can be added to serverless.yml to set default configuration, e.g.:

```yml
custom:
  serverless-iot-local:
    start:
      port: 1884
    # Uncomment only if you already have an MQTT server running locally
    # noStart: true
    redis:
      host: 'localhost'
      port: 6379
      db: 12
```

### Using with serverless-offline plugin

Place `AWS-severless-project` above `serverless-offline`

```yaml
plugins:
  - AWS-severless-project
  - serverless-offline
```

## Todo

- Improve support of AWS Iot SQL syntax

## License
[MIT](LICENSE)
