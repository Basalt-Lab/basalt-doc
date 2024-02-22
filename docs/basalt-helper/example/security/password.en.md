## **Hashing a Password**

=== "TypeScript"

    ```typescript
    import { BasaltPassword } from '@basalt-lab/basalt-core';

    const main = async (): Promise<void> => {
        const password: string = 'password';
        const hashedPassword: string = await BasaltPassword.hashPassword(password);
        console.log(hashedPassword);
    };
    main();
    ```

=== "JavaScript"

    ```javascript
    const { BasaltPassword } = require('@basalt-lab/basalt-core');

    const main = async () => {
        const password = 'password';
        const hashedPassword = await BasaltPassword.hashPassword(password);
        console.log(hashedPassword);
    };
    main();
    ```

<!-- termynal -->

```bash
$ node example.js
$argon2id$v=19$m=65536,t=3,p=20$W1Qv4XJ+jaVDI04sLFukTYXI/7FYuyeavMLNUXnnrPQ$JfQgEbewRGjjGIpGEIDp/vIqeX7avK2DqYIddilsqng
```

## **Verifying a Password**

=== "TypeScript"

    ```typescript
    import { BasaltPassword } from '@basalt-lab/basalt-core';

    const main = async (): Promise<void> => {
        const password: string = 'password';
        const hashedPassword: string = await BasaltPassword.hashPassword(password);
        const isPasswordValid: boolean = await BasaltPassword.verifyPassword(password, hashedPassword);
        console.log(isPasswordValid);
    };
    main();
    ```
=== "JavaScript"

    ```javascript
    const { BasaltPassword } = require('@basalt-lab/basalt-core');
    
    const main = async () => {
        const password = 'password';
        const hashedPassword = await BasaltPassword.hashPassword(password);
        const isPasswordValid = await BasaltPassword.verifyPassword(password, hashedPassword);
        console.log(isPasswordValid);
    };
    main();
    ```
<!-- termynal -->

```bash
$ node example.js
true
```
