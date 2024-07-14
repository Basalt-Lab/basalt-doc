## **Hasher un mot de passe**

=== "TypeScript"

    ```typescript
    import { basaltPassword } from '@basalt-lab/basalt-core';

    const password: string = 'password';
    const hashedPassword: string = await basaltPassword.hashPassword(password);
    console.log(hashedPassword);
    ```

=== "JavaScript"

    ```javascript
    const { basaltPassword } = require('@basalt-lab/basalt-core');

    const password = 'password';
    const hashedPassword = await basaltPassword.hashPassword(password);
    console.log(hashedPassword);
    ```

<!-- termynal -->

```bash
$ node example.js
$argon2id$v=19$m=65536,t=3,p=20$W1Qv4XJ+jaVDI04sLFukTYXI/7FYuyeavMLNUXnnrPQ$JfQgEbewRGjjGIpGEIDp/vIqeX7avK2DqYIddilsqng
```

## **Vérifier un mot de passe**

=== "TypeScript"

    ```typescript
    import { basaltPassword } from '@basalt-lab/basalt-core';

    const password: string = 'password';
    const hashedPassword: string = await basaltPassword.hashPassword(password);
    const isPasswordValid: boolean = await basaltPassword.verifyPassword(password, hashedPassword);
    console.log(isPasswordValid);
    ```
=== "JavaScript"

    ```javascript
    const { basaltPassword } = require('@basalt-lab/basalt-core');

    const password = 'password';
    const hashedPassword = await basaltPassword.hashPassword(password);
    const isPasswordValid = await basaltPassword.verifyPassword(password, hashedPassword);
    console.log(isPasswordValid);
    ```
<!-- termynal -->

```bash
$ node example.js
true
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
