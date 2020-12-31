# Service Runner

A utility script for running services via programmable handlers.

## Service

A service is something that can be started and stopped.
An [Example shell service](./services/example) is provided, which simply echoes whether the service was started or stopped.

## Handler

A handler is something that sits between the service runner and the service itself. A [shell service handler](./handlers/shell) is provided for reference.

## Creating a handler

In order to create a handler, you should create a shell script under [/handlers](./handlers). The shell script must use a shebang and must not have a file extension, since the script's basename will be used as the handler's name. The shell script must export a function `srv_{NAME}` where `{NAME}` matches the handler's name. Eg: `shell` should export the function `srv_shell`. The function should use the variables below for handling the starting and stopping of the service.

## Available variables

`SR_PATH` - The absolute path to the the services directory.
This defaults to the [./services](./services) but can be changed using environment variables. <br />
`SR_ACTION` - The action (start|stop). <br />
`SR_HANDLER_NAME` - The handler name. <br />
`SR_HANDLER_FUNC` - The handler function. <br />
`SR_SERVICE_NAME` - The name of the service. <br />
`SR_SERVICE_PATH` - The absolute path to the service. <br />
