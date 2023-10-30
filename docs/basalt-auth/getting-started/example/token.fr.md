## **Signature d'un token**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    console.log(tokenSignResult.token);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    console.log(tokenSignResult.token);
    ```

<!-- termynal -->

```bash
$ node example.js
eyJ1dWlkIjoiY2FhNWNlYzMtMGY5Ni00Y2E5LWJhMmEtM2JiZGE3OGRkMGExIiwiZXhwIjoiMjAyMy0xMC0zMVQxOTo0MDoxMy42NjRaIiwiaXNzdWVyIjoiWW91ckFwcE5hbWUtSXNzdWVyIiwiYXVkaWVuY2UiOiJZb3VyQXBwTmFtZS1BdWRpZW5jZSJ9.eyJ1c2VybmFtZSI6ImJhc2FsdCJ9.fT7a0dC4lHreUF/YsqOHgXuJo4toEMr8jmrWZhSa0LbHxwLTJj5k7mSxCmSLv9LWUg54Pmj7prRtgMPnFqAYDg==
```

## **Vérification d'un token**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    try {
        basaltToken.verify(tokenSignResult.token, tokenSignResult.publicKey);
        console.log('Token is valid');
    } catch (e) {
        console.log(e);
    }
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    try {
        basaltToken.verify(tokenSignResult.token, tokenSignResult.publicKey);
        console.log('Token is valid');
    } catch (e) {
        console.log(e);
    }
    ```

<!-- termynal -->

```bash
$ node example.js
Token is valid
```

## **Récupération de l'uuid du token**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token: string = tokenSignResult.token;
    const tokenUuid: string = basaltToken.getTokenUuid(token);
    console.log(tokenUuid);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token = tokenSignResult.token;
    const tokenUuid = basaltToken.getTokenUuid(token);
    console.log(tokenUuid);
    ```

<!-- termynal -->

```bash
$ node example.js
98926cf6-4eda-4b67-bb46-ba58329ca0b5
```

## **Recupération de la date du token**

=== "TypeScript"
    
        ```typescript
        import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
        
        const basaltToken: BasaltToken = new BasaltToken();
        const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
            1000 * 60 * 60 * 24, // 1 day
            {
                username: 'basalt',
            }
        );
        const token: string = tokenSignResult.token;
        const tokenDate: Date = basaltToken.getExpirationDate(token);
        console.log(tokenDate);
        ```

=== "JavaScript"

        ```javascript
        const { BasaltToken } = require('@basalt-lab/basalt-auth');
    
        const basaltToken = new BasaltToken();
        const tokenSignResult = basaltToken.sign(
            1000 * 60 * 60 * 24, // 1 day
            {
                username: 'basalt',
            }
        );
        const token = tokenSignResult.token;
        const tokenDate = basaltToken.getExpirationDate(token);
        console.log(tokenDate);
        ```
<!-- termynal -->

```bash
$ node example.js
2023-10-31T20:01:26.251Z
```

## **Récupération de l'audiance du token**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token: string = tokenSignResult.token;
    const audiance: string = basaltToken.getAudience(token);
    console.log(audiance);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');
    
    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token = tokenSignResult.token;
    const audiance = basaltToken.getAudience(token);
    console.log(audiance);
    ```

<!-- termynal -->

```bash
$ node example.js
YourAppName-Audience
```

## **Récupération de l'émetteur du token**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token: string = tokenSignResult.token;
    const issuer: string = basaltToken.getIssuer(token);
    console.log(issuer);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');
    
    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token = tokenSignResult.token;
    const issuer = basaltToken.getIssuer(token);
    console.log(issuer);
    ```

<!-- termynal -->

```bash
$ node example.js
YourAppName-Issuer
```

## **Récupération du header du token**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult, IBasaltTokenHeader } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token: string = tokenSignResult.token;
    const header: IBasaltTokenHeader = basaltToken.getHeader(token);
    console.log(header);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token = tokenSignResult.token;
    const header = basaltToken.getHeader(token);
    console.log(header);
    ```

<!-- termynal -->

```bash
$ node example.js
{
  uuid: '36abcb22-05d4-417a-a8c2-8d17b8dc631e',
  exp: '2023-10-31T20:25:34.429Z',
  issuer: 'YourAppName-Issuer',
  audience: 'YourAppName-Audience'
}

```

## **Récupération du payload du token**


=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token: string = tokenSignResult.token;
    const payload: {
        username: string;
    } = basaltToken.getPayload(token);
    console.log(payload);
    ```

=== "JavaScript"
    
    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');
    
    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token = tokenSignResult.token;
    const payload = basaltToken.getPayload(token);
    console.log(payload);
    ```

<!-- termynal -->

```bash
$ node example.js
{ username: 'basalt' }
```

## **Vérifier si le token a expiré**

=== "TypeScript"

    ```typescript
    import { BasaltToken, IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';
    
    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token: string = tokenSignResult.token;
    console.log(basaltToken.isExpired(token));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');
    
    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign(
        1000 * 60 * 60 * 24, // 1 day
        {
            username: 'basalt',
        }
    );
    const token = tokenSignResult.token;
    console.log(basaltToken.isExpired(token));
    ```

<!-- termynal -->

```bash
$ node example.js
false
```
