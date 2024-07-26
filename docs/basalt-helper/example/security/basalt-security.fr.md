## **Hasher un mot de passe**

=== "TypeScript"

    ```typescript
    import { hashPassword } from '@basalt-lab/basalt-helper';

    const password: string = 'password';
    const hashedPassword: string = await hashPassword(password);
    console.log(hashedPassword);
    ```

=== "JavaScript"

    ```javascript
    const { hashPassword } = require('@basalt-lab/basalt-helper');

    const password = 'password';
    const hashedPassword = await hashPassword(password);
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
    import { hashPassword, verifyPassword } from '@basalt-lab/basalt-helper';

    const password: string = 'password';
    const hashedPassword: string = await hashPassword(password);
    const isPasswordValid: boolean = await verifyPassword(password, hashedPassword);
    console.log(isPasswordValid);
    ```
=== "JavaScript"

    ```javascript
    const { hashPassword, verifyPassword } = require('@basalt-lab/basalt-helper');

    const password = 'password';
    const hashedPassword = await hashPassword(password);
    const isPasswordValid = await verifyPassword(password, hashedPassword);
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
