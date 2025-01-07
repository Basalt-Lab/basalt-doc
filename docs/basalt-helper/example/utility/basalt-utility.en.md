## **Singleton Management: Registration, Retrieval, and Unregistration**

=== "TypeScript"

    ```typescript
    import { SingletonManager } from '@basalt-lab/basalt-helper';

    class ExampleSingleton {
        private static _count = 0;
        private readonly _id: number;
        
        public constructor() {
            ExampleSingleton._count += 1;
            this._id = ExampleSingleton._count;
            console.log(`ExampleSingleton created with ID: ${this._id}`);
        }

        public sayHello(): void {
            console.log(`Hello from instance ${this._id}!`);
        }
    }

    SingletonManager.register('ExampleSingleton', ExampleSingleton);
    SingletonManager.get<ExampleSingleton>('ExampleSingleton').sayHello();
    SingletonManager.get<ExampleSingleton>('ExampleSingleton').sayHello();
    SingletonManager.unregister('ExampleSingleton');
    ```

=== "JavaScript"

    ```javascript
    const { SingletonManager } = require('@basalt-lab/basalt-helper');

    class ExampleSingleton {
        static _count = 0;
        _id;
        
        constructor() {
            ExampleSingleton._count += 1;
            this._id = ExampleSingleton._count;
            console.log(`ExampleSingleton created with ID: ${this._id}`);
        }

        sayHello() {
            console.log(`Hello from instance ${this._id}!`);
        }
    }

    SingletonManager.register('ExampleSingleton', ExampleSingleton);
    SingletonManager.get('ExampleSingleton').sayHello();
    SingletonManager.get('ExampleSingleton').sayHello();
    SingletonManager.unregister('ExampleSingleton');
    ```

<!-- termynal -->

```bash
$ node example.js
ExampleSingleton created with ID: 1
Hello from instance 1!
Hello from instance 1!
```

## **Singleton Management: Registration, Retrieval, and Unregistration (with arguments)**

=== "TypeScript"

    ```typescript
    import { SingletonManager } from '@basalt-lab/basalt-helper';

    class ExampleSingleton {
        private static _count = 0;
        private readonly _id: number;
        
        public constructor(name: string) {
            ExampleSingleton._count += 1;
            this._id = ExampleSingleton._count;
            console.log(`ExampleSingleton created with ID: ${this._id} and name: ${name}`);
        }

        public sayHello(): void {
            console.log(`Hello from instance ${this._id}!`);
        }
    }

    SingletonManager.register('ExampleSingleton', ExampleSingleton, 'John Doe');
    SingletonManager.get<ExampleSingleton>('ExampleSingleton').sayHello();
    SingletonManager.get<ExampleSingleton>('ExampleSingleton').sayHello();
    SingletonManager.unregister('ExampleSingleton');
    ```

=== "JavaScript"

    ```javascript
    const { SingletonManager } = require('@basalt-lab/basalt-helper');

    class ExampleSingleton {
        static _count = 0;
        _id;
        
        constructor(name) {
            ExampleSingleton._count += 1;
            this._id = ExampleSingleton._count;
            console.log(`ExampleSingleton created with ID: ${this._id} and name: ${name}`);
        }

        sayHello() {
            console.log(`Hello from instance ${this._id}!`);
        }
    }

    SingletonManager.register('ExampleSingleton', ExampleSingleton, 'John Doe');
    SingletonManager.get('ExampleSingleton').sayHello();
    SingletonManager.get('ExampleSingleton').sayHello();
    SingletonManager.unregister('ExampleSingleton');
    ```

<!-- termynal -->

```bash
$ node example.js
ExampleSingleton created with ID: 1 and name: John Doe
Hello from instance 1!
Hello from instance 1!
```

<script data-name="BMC-Widget"
    data-cfasync="false"
    src="https://cdnjs.buymeacoffee.com/1.0.0/widget.prod.min.js"
    data-id="necrelox"
    data-description="Support me on Buy me a coffee!"
    data-message="Thank you for your visit!"
    data-color="#5F7FFF"
    data-position="Right"
    data-x_margin="18"
    data-y_margin="22" />
