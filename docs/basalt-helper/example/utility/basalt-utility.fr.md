## **Gestion des Singletons**

`SingletonManager` est une classe utilitaire qui permet d'enregistrer, de récupérer et de désenregistrer des singletons.

??? example "Enregistrement, Récupération et Désenregistrement (sans arguments)"
    ```typescript
    import { SingletonManager } from '@basalt-lab/basalt-helper/util';

    // Example class with a static counter allow to see the number of instances created of this class
    class Example {
        private static _count = 0;
        private readonly _id: number;
        
        public constructor() {
            Example._count += 1;
            this._id = Example._count;
            console.log(`Example created with ID: ${this._id}`);
        }

        public sayHello(): void {
            console.log(`Hello from instance ${this._id}!`);
        }
    }

    // allows to register the class Example as a singleton
    SingletonManager.register('Example', Example);

    // Get the singleton instance of Example
    SingletonManager.get<Example>('Example').sayHello();
    SingletonManager.get<Example>('Example').sayHello();

    // allows to unregister the class Example as a singleton
    SingletonManager.unregister('Example');
    ```

    <!-- termynal -->

    ```bash
    $ node example.js
    ExampleSingleton created with ID: 1
    Hello from instance 1!
    Hello from instance 1!
    ```

??? example "Enregistrement, Récupération et Désenregistrement (avec des arguments)"

    ```typescript
    import { SingletonManager } from '@basalt-lab/basalt-helper/util';

    // Example class with a static counter allow to see the number of instances created of this class
    class Example {
        private static _count = 0;
        private readonly _id: number;
        
        public constructor(name: string) {
            Example._count += 1;
            this._id = Example._count;
            console.log(`Example created with ID: ${this._id} and name: ${name}`);
        }

        public sayHello(): void {
            console.log(`Hello from instance ${this._id}!`);
        }
    }

    // allows to register the class Example as a singleton
    SingletonManager.register('Example', Example, 'John Doe');

    // Get the singleton instance of Example
    SingletonManager.get<Example>('Example').sayHello();
    SingletonManager.get<Example>('Example').sayHello();

    // allows to unregister the class Example as a singleton
    SingletonManager.unregister('Example');
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
    data-message="Merci de votre visite!"
    data-color="#5F7FFF"
    data-position="Right"
    data-x_margin="18"
    data-y_margin="22" />
