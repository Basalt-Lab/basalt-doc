## **Server connection**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketClient
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketClient: BasaltSocketClient = new BasaltSocketClient('ws://localhost:3000/test');
    
    basaltSocketClient.connect()
        .then((): void => {
            console.log('Connected');
            basaltSocketClient.send('Hello World');
        })
        .catch((err: Error): void => {
            console.error(err);
        });
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketClient
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketClient = new BasaltSocketClient('ws://localhost:3000/test');

    basaltSocketClient.connect()
        .then(() => {
            console.log('Connected');
            basaltSocketClient.send('Hello World');
        })
        .catch((err) => {
            console.error(err);
        });
    ```

<!-- termynal -->

```bash
$ node client.js
Connected
```

## **Adding a listener**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketClient
    } from '@basalt-lab/basalt-socket';

    const basaltSocketClient: BasaltSocketClient = new BasaltSocketClient('ws://localhost:3000/test/health');

    basaltSocketClient.connect()
        .then((): void => {
            console.log('Connected');
            basaltSocketClient.send('Hello World');
            basaltSocketClient.addListener('message', (message: unknown): void => {
                console.log(message);
            });
    })
    .catch((err: Error): void => {
        console.error(err);
    });
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketClient
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketClient = new BasaltSocketClient('ws://localhost:3000/test/health');

    basaltSocketClient.connect()
        .then(() => {
            console.log('Connected');
            basaltSocketClient.send('Hello World');
            basaltSocketClient.addListener('message', (message) => {
                console.log(message);
            });
        })
        .catch((err) => {
            console.error(err);
        });
    ```

<!-- termynal -->

```bash
$ node client.js
Connected
Hello World
```

## **Server disconnection**

=== "TypeScript"

    ```typescript
    import {
        BasaltSocketClient
    } from '@basalt-lab/basalt-socket';
    
    const basaltSocketClient: BasaltSocketClient = new BasaltSocketClient('ws://localhost:3000/test/health');
    
    basaltSocketClient.connect()
        .then(async (): Promise<void> => {
            console.log('Connected');
            basaltSocketClient.send('Hello World');

        basaltSocketClient.addListener('message', (message: unknown): void => {
            console.log(message);
        });
        await basaltSocketClient.disconnect();
        console.log('Disconnected');
    })
    .catch((err: Error): void => {
        console.error(err);
    });
    ```

=== "JavaScript"

    ```javascript
    const {
        BasaltSocketClient
    } = require('@basalt-lab/basalt-socket');

    const basaltSocketClient = new BasaltSocketClient('ws://localhost:3000/test/health');

    basaltSocketClient.connect()
        .then(async () => {
            console.log('Connected');
            basaltSocketClient.send('Hello World');

            basaltSocketClient.addListener('message', (message) => {
                console.log(message);
            });
            await basaltSocketClient.disconnect();
            console.log('Disconnected');
        })
        .catch((err) => {
            console.error(err);
        });
    ```

<!-- termynal -->

```bash
$ node client.js
Connected
Hello World
Disconnected
```
