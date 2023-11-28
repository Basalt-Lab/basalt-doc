## **Server listen**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    basaltSocketServer.listen({
        port: 3000
    }); // default verbose is true
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    basaltSocketServer.listen({
        port: 3000
    }); // default verbose is true
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

## **Server stop**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    basaltSocketServer.listen({
        port: 3000
    }); // default verbose is true
    basaltSocketServer.stop();
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    basaltSocketServer.listen({
        port: 3000
    }); // default verbose is true
    basaltSocketServer.stop();
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

## **Add CORS**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketServer,
        BasaltSocketEvents
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer({
        origins: ['yourdomain.com']
    });
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketServer,
        BasaltSocketEvents
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer({
        origins: ['yourdomain.com']
    });
    const basaltSocketEvents = new BasaltSocketEvents();
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' 
```
![](img.png "Example")

## **Pub Sub : example alert**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents, IBasaltWebSocket } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('alert', {
        onConnectHook: (ws: IBasaltWebSocket): void => {
            ws.subscribe('alert');
        },
        onDisconnectHook: (): void => {
            // ws.unsubscribe('alert'); // This is not needed, as the unsubscribe is done automatically on disconnect, but can be used to Handler or PreHandler
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    
    setInterval((): void => {
        basaltSocketServer.publish('alert', 'Hello World!');
    }, 1000);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');

    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('alert', {
        onConnectHook: (ws) => {
            ws.subscribe('alert');
        },
        onDisconnectHook: () => {
            // ws.unsubscribe('alert'); // This is not needed, as the unsubscribe is done automatically on disconnect, but can be used to Handler or PreHandler
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });

    setInterval(() => {
        basaltSocketServer.publish('alert', 'Hello World!');
    }, 1000);
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'alert' and client subscribe to 'alert'
```
![](img_2.png "Example")

## **Event**

### **Add an event into events router**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

### **Add multiple events into events router**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEvents.add('event1', {});
    basaltSocketEvents.add('event2', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents = new BasaltSocketEvents();

    basaltSocketEvents.add('event1', {});
    basaltSocketEvents.add('event2', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

### **Add multiple events routers**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';

    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEventsA: BasaltSocketEvents = new BasaltSocketEvents();
    const basaltSocketEventsB: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEventsA.add('foo', {});
    basaltSocketEventsB.add('bar', {});
    basaltSocketServer.use('/', [basaltSocketEventsA, basaltSocketEventsB]);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

=== "JavaScript"

    ```javascript
    const { BasaltSocketServer, BasaltSocketEvents } = require('@basalt-lab/basalt-socket');
    
    const basaltSocketServer = new BasaltSocketServer();
    const basaltSocketEventsA: BasaltSocketEvents = new BasaltSocketEvents();
    const basaltSocketEventsB: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketEventsA.add('foo', {});
    basaltSocketEventsB.add('bar', {});
    basaltSocketServer.use('/', [basaltSocketEventsA, basaltSocketEventsB]);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
```

### **Add an event with a handler**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client transmit twice
test
test
```

### **Add an event with a handler and a preHandler**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client transmit twice
preHandler 1
test
preHandler 1
test
```

### **Add an event with a handler and multiple preHandler**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client transmit twice
preHandler 1
preHandler 2
test
preHandler 1
preHandler 2
test
```

### **Handler emit to client**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client emit and server emit message 'test' to client
```
![](img_1.png "Example")

### **Handler get message**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send message 'test'
test
```

## **Hooks**

### **Global onUpgradeHook**

=== "TypeScript"

    ```typescript
    import { BasaltSocketServer, BasaltSocketEvents } from '@basalt-lab/basalt-socket';
    
    const basaltSocketServer: BasaltSocketServer = new BasaltSocketServer();
    const basaltSocketEvents: BasaltSocketEvents = new BasaltSocketEvents();
    
    basaltSocketServer.onUpgradeHook = (): void => {
        console.log('onUpgradeHook');
    };
    basaltSocketEvents.add('test', {});
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' 
onUpgradeHook
```

### **Event onUpgradeHook**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
onUpgradeHook
```

### **Global onUpgradeHook set data in UserData**

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
    
    basaltSocketServer.onUpgradeHook = (_: IBasaltHttpResponse, req: IBasaltHttpRequest): unknown => {
        const cookie: string = req.getHeader('cookie');
        return { cookie };
    };
    
    basaltSocketEvents.add('test', {
        handler: (ws: IBasaltWebSocket): void => {
            console.log(ws.getUserData());
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
        const cookie = req.getHeader('cookie');
        return { cookie };
    };
    
    basaltSocketEvents.add('test', {
        handler: (ws) => {
            console.log(ws.getUserData());
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client emit
uWS.WebSocket {
  cookie: 'token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
}
```

### **Event onUpgradeHook set data in UserData**

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
    
    basaltSocketEvents.add('test', {
        onUpgradeHook: (_: IBasaltHttpResponse, req: IBasaltHttpRequest): unknown => {
            const cookie: string = req.getHeader('cookie');
            return { cookie };
        },
        handler: (ws: IBasaltWebSocket): void => {
        console.log(ws.getUserData());
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
            const cookie = req.getHeader('cookie');
            return { cookie };
        },
        handler: (ws) => {
            console.log(ws.getUserData());
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client emit
uWS.WebSocket {
  cookie: 'token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
}
```

### **Global and Event onUpgradeHook set data in UserData**

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
    
    basaltSocketServer.onUpgradeHook = (_: IBasaltHttpResponse, req: IBasaltHttpRequest): unknown => {
        const host: string = req.getHeader('host');
        return { host };
    };
    
    basaltSocketEvents.add('test', {
        onUpgradeHook: (_: IBasaltHttpResponse, req: IBasaltHttpRequest): unknown => {
            const cookie: string = req.getHeader('cookie');
            return { cookie };
        },
        handler: (ws: IBasaltWebSocket): void => {
            console.log(ws.getUserData());
        }
    });
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
        const host = req.getHeader('host');
        return { host };
    };

    basaltSocketEvents.add('test', {
        onUpgradeHook: (_, req) => {
            const cookie = req.getHeader('cookie');
            return { cookie };
        },
        handler: (ws) => {
            console.log(ws.getUserData());
        }
    });

    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
uWS.WebSocket {
  host: 'localhost:3000',
  cookie: 'token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c'
}
```

### **Global onConnectHook**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
Client connected
```

### **Event onConnectHook**

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
    
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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

    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test'
Client connected
```

### **Global onReceivedHook**

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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send message
onReceivedHook
```

### **Event onReceivedHook**

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
    
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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

    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```

<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client send message
onReceivedHook
```

### **Global onDisconnectHook**

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
    
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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

    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client disconnect
onDisconnectHook
```

### **Event onDisconnectHook**

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
    
    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
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

    basaltSocketServer.use('/', basaltSocketEvents);
    basaltSocketServer.listen({
        port: 3000
    });
    ```
<!-- termynal -->

```bash
$ node server.js
Listening to port 3000
# example : connect to the server on the event 'test' and client disconnect
onDisconnectHook
```
