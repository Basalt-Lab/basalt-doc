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

## **Hasher en md5**

=== "TypeScript"

    ```typescript
    import { md5 } from '@basalt-lab/basalt-helper';

    const hash1: string = md5('test');
    const hash2: string = md5({ test: 'test' });

    console.log(hash1);
    console.log(hash2);
    ```
=== "JavaScript"

    ```javascript
    const { md5 } = require('@basalt-lab/basalt-helper');

    const hash1 = md5('test');
    const hash2 = md5({ test: 'test' });

    console.log(hash1);
    console.log(hash2);
    ```

<!-- termynal -->
    
```bash
$ node example.js
098f6bcd4621d373cade4e832627b4f6
828bcef8763c1bc616e25a06be4b90ff
```

## **Hasher en sha256**

=== "TypeScript"

    ```typescript
    import { sha256 } from '@basalt-lab/basalt-helper';

    const hash1: string = sha256('test');
    const hash2: string = sha256({ test: 'test' });

    console.log(hash1);
    console.log(hash2);
    ```
=== "JavaScript"

    ```javascript
    const { sha256 } = require('@basalt-lab/basalt-helper');

    const hash1 = sha256('test');
    const hash2 = sha256({ test: 'test' });

    console.log(hash1);
    console.log(hash2);
    ```

<!-- termynal -->
    
```bash
$ node example.js
9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08
3e80b3778b3b03766e7be993131c0af2ad05630c5d96fb7fa132d05b77336e04
```

## **Hasher en sha512**

=== "TypeScript"

    ```typescript
    import { sha512 } from '@basalt-lab/basalt-helper';

    const hash1: string = sha512('test');
    const hash2: string = sha512({ test: 'test' });

    console.log(hash1);
    console.log(hash2);
    ```
=== "JavaScript"

    ```javascript
    const { sha512 } = require('@basalt-lab/basalt-helper');

    const hash1 = sha512('test');
    const hash2 = sha512({ test: 'test' });

    console.log(hash1);
    console.log(hash2);
    ```

<!-- termynal -->
    
```bash
$ node example.js
ee26b0dd4af7e749aa1a8ee3c10ae9923f618980772e473f8819a5d4940e0db27ac185f8a0e1d5f84f88bc887fd67b143732c304cc5fa9ad8e6f57f50028a8ff
2ecf9ae5d4988977ce5e465b2a8335eed6096c6df958bcd11825e1bc14b277a92e8ccde46f3cd74ad59aa7eeaca021f5ea7df801c61c021cf71c9edd7b6dfa16
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
