## **Création d'un serveur**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    basaltSocketServer.listen(3000); // default verbose is true
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    basaltSocketServer.listen(3000); // default verbose is true
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

## **Ajout d'un evenement**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

## **Ajout d'un evenement avec un handler**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        handler: (): void => {
            console.log('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        handler: () => {
            console.log('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send two messages
test
test
```

## **Ajout d'un evenement avec un handler et un preHandler**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        preHandler: [
            (): void => {
                console.log('preHandler 1');
            }
        ],
        handler: (): void => {
            console.log('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        preHandler: [
            () => {
                console.log('preHandler 1');
            }
        ],
        handler: () => {
            console.log('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send two messages
preHandler 1
test
preHandler 1
test
```

## **Ajout d'un evenement avec un handler et multiple preHandler**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        preHandler: [
            (): void => {
                console.log('preHandler 1');
            },
            (): void => {
                console.log('preHandler 2');
            }
        ],
        handler: (): void => {
            console.log('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        preHandler: [
            () => {
                console.log('preHandler 1');
            },
            () => {
                console.log('preHandler 2');
            }
        ],
        handler: () => {
            console.log('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send two messages
preHandler 1
preHandler 2
test
preHandler 1
preHandler 2
test
```


## **PubSub**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents, IBasaltWebSocket } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('health', {
    
        onConnectHook: (ws: IBasaltWebSocket): void => {
            ws.subscribe('test');
        },
    
        handler: (ws: IBasaltWebSocket): void => {
            ws.publish('test', 'Hello World');
        }
    });
    
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('health', {
    
        onConnectHook: (ws) => {
            ws.subscribe('test');
        },
    
        handler: (ws) => {
            ws.publish('test', 'Hello World');
        }
    });

    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```
example : two client connect to the server on the event 'health' and client subscribe to 'test' and server publish 'Hello World'
And client listen to 'message' event.
<!-- termynal -->

```bash
Connected
```

<!-- termynal -->
```bash
Connected
Hello World
```


## **Handler emit**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents, IBasaltWebSocket } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        handler: (ws: IBasaltWebSocket): void => {
            ws.send('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        handler: (ws) => {
            ws.send('test');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000

# example : connect to the server on the event 'test' and client send message and server emit message
```

## **Handler get message**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents, IBasaltWebSocket } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        handler: (_: IBasaltWebSocket, message: ArrayBuffer ): void => {
            const messageString: string = Buffer.from(message).toString();
            console.log(messageString);
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        handler: (_, message) => {
            const messageString = Buffer.from(message).toString();
            console.log(messageString);
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send message 'test' and server log message
test
```

## **Global onUpgradeHook**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketServer.onUpgradeHook = (): void => {
        console.log('onUpgradeHook');
    };
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketServer.onUpgradeHook = () => {
        console.log('onUpgradeHook');
    };
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' 
onUpgradeHook
```

## **Event onUpgradeHook**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        onUpgradeHook: (): void => {
            console.log('onUpgradeHook');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onUpgradeHook: () => {
            console.log('onUpgradeHook');
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
onUpgradeHook
```

## **Global onUpgradeHook set data in UserData**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
        IBasaltHttpResponse,
        IBasaltHttpRequest,
        IBasaltWebSocket
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    interface IUserData {
        host: string;
    }
    
    basaltSocketServer.onUpgradeHook = (_: IBasaltHttpResponse, req: IBasaltHttpRequest): IUserData => {
        console.log('Upgrade hook');
    const host: string = req.getHeader('host');
        return {
            host,
        };
    };
    
    basaltSocketEvents.add('test', {
        handler: (ws: IBasaltWebSocket): void => {
            const userData: IUserData = ws.getUserData() as IUserData;
            console.log(userData.host);
        },
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketServer.onUpgradeHook = (_, req) => {
        console.log('Upgrade hook');
        const host = req.getHeader('host');
        return {
            host,
        };
    };

    basaltSocketEvents.add('test', {
        handler: (ws) => {
            const userData = ws.getUserData();
            console.log(userData.host);
        },
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
Upgrade hook
# example : client send message
localhost:3000
```

## **Event onUpgradeHook set data in UserData**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
        IBasaltHttpResponse,
        IBasaltHttpRequest,
        IBasaltWebSocket
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    interface IUserData {
        host: string;
    }

    basaltSocketEvents.add('test', {
        onUpgradeHook: (_: IBasaltHttpResponse, req: IBasaltHttpRequest): IUserData => {
            console.log('Upgrade hook');
            const host: string = req.getHeader('host');
            return {
                host,
            };
        },
        handler: (ws: IBasaltWebSocket): void => {
            const userData: IUserData = ws.getUserData() as IUserData;
            console.log(userData.host);
        },
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onUpgradeHook: (_, req) => {
            console.log('Upgrade hook');
            const host: string = req.getHeader('host');
            return {
                host,
            };
        },
        handler: (ws) => {
            const userData = ws.getUserData();
            console.log(userData.host);
        },
    });
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
Upgrade hook
# example : client send message
localhost:3000
```

## **Global onConnectHook**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketServer.onConnectHook = (): void => {
        console.log('Client connected');
    };
    
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketServer.onConnectHook = () => {
        console.log('Client connected');
    };

    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
Client connected
```

## **Event onConnectHook**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {
        onConnectHook: (): void => {
            console.log('Client connected');
        }
    });
    
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onConnectHook: () => {
            console.log('Client connected');
        }
    });

    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
Client connected
```

## **Global onReceivedHook**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
        IBasaltWebSocket
    } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketServer.onReceivedHook = (): void => {
        console.log('onReceivedHook');
    };
    
    basaltSocketEvents.add('test', {}); 
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketServer.onReceivedHook = () => {
        console.log('onReceivedHook');
    };

    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send message
onReceivedHook
```

## **Event onReceivedHook**

=== "TypeScript"
    
    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
        IBasaltWebSocket
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onReceivedHook: (): void => {
            console.log('onReceivedHook');
        }
    });
    
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onReceivedHook: () => {
            console.log('onReceivedHook');
        }
    });

    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send message
onReceivedHook
```

## **Global onDisconnectHook**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketServer.onDisconnectHook = (): void => {
        console.log('onDisconnectHook');
    };
    
    basaltSocketEvents.add('test', {});
    
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketServer.onDisconnectHook = () => {
        console.log('onDisconnectHook');
    };

    basaltSocketEvents.add('test', {});

    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client disconnect
onDisconnectHook
```

## **Event onDisconnectHook**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents,
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onDisconnectHook: (): void => {
            console.log('onDisconnectHook');
        }
    });
    
    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {
        onDisconnectHook: () => {
            console.log('onDisconnectHook');
        }
    });

    basaltSocketServer.use('/', basaltSocketEvents.events);
    basaltSocketServer.listen(3000);
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client disconnect
onDisconnectHook
```
