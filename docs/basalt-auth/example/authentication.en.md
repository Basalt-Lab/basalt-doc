## **Token Signature**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});
    console.log(tokenSignResult.token);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});
    console.log(tokenSignResult.token);
    ```

<!-- termynal -->

```bash
$ node example.js
eyJ1dWlkIjoiZDk4MTcwMjgtM2EzZS00YWYyLTgwNzYtOTExZGFlZThiMGIzIiwiZXhwIjoiMjAyNC0wMy0yMlQxMjowOTo0MS4yNThaIiwiaXNzdWVyIjoiQmFzYWx0LUlzc3VlciIsImF1ZGllbmNlIjoiQmFzYWx0LUF1ZGllbmNlIn0=.e30=.PJpP4zbxX4SaYD7hIj0wZGIqhSs8SbGdJ0W+o/Pr6WJyOhJTvRsIqQpf8sCvTFWWGyCx5ZGeczT0E1RHBE7GBg==
```

## **Token Signature with Payload**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({
        usename: 'User1',
    });
    console.log(tokenSignResult.token);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({
        usename: 'User1',
    });
    console.log(tokenSignResult.token);
    ```

<!-- termynal -->

```bash
$ node example.js
eyJ1dWlkIjoiMzAzNjQ2ODMtYWYxMC00NjcyLTkwNTQtMmY2YWNmM2E1ZGNlIiwiZXhwIjoiMjAyNC0wMy0yMlQxMjoxMjo1NS41NjlaIiwiaXNzdWVyIjoiQmFzYWx0LUlzc3VlciIsImF1ZGllbmNlIjoiQmFzYWx0LUF1ZGllbmNlIn0=.eyJ1c2VuYW1lIjoiVXNlcjEifQ==.heBWyPtSqmwR/FTShaeqBm7NtCxxE2/faIRc1vQG80mMwOlTTzeWcPD8iNecwtkij/GW6RlEADex4uxCjULFAw==
```

## **Token Signature with Expiration Time**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult, BasaltTokenExpiry } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    // you can use enum or number (default is 1 hour)
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({}, BasaltTokenExpiry.ONE_DAY);
    console.log(tokenSignResult.token);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken, BasaltTokenExpiry } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    // you can use enum or number (default is 1 hour)
    const tokenSignResult = basaltToken.sign({}, BasaltTokenExpiry.ONE_DAY);
    console.log(tokenSignResult.token);
    ```

<!-- termynal -->

```bash
$ node example.js
eyJ1dWlkIjoiZTg5YjYzYTAtMjY0NS00ZjQwLWE5YzYtOGM1Yzg0NmIwNzNlIiwiZXhwIjoiMjAyNC0wMy0yM1QxMToxMDoyMC43NjVaIiwiaXNzdWVyIjoiQmFzYWx0LUlzc3VlciIsImF1ZGllbmNlIjoiQmFzYWx0LUF1ZGllbmNlIn0=.e30=.8f72CeURHH/lYENBqozW1PsmVAr3RLHtBm6hbk/TY1VoamD4WYm1TakCdVQhlUVCL3nYRaFzyQ8zhuS5b3vlCg==
```

## **Token Signature with Issuer and Audience**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult, BasaltTokenExpiry } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    // default issuer is 'Basalt-Issuer' and default audience is 'Basalt-Audience'
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign(
        {}, BasaltTokenExpiry.ONE_HOUR, 'Basalt-issuer', 'Basalt-audience'
    );
    console.log(tokenSignResult.token);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken, BasaltTokenExpiry } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    // default issuer is 'Basalt-Issuer' and default audience is 'Basalt-Audience'
    const tokenSignResult = basaltToken.sign(
        {}, BasaltTokenExpiry.ONE_HOUR, 'Basalt-issuer', 'Basalt-audience'
    );
    console.log(tokenSignResult.token);
    ```

<!-- termynal -->

```bash
$ node example.js
eyJ1dWlkIjoiNzBmYTFiZDEtOWEwNy00Mzk5LWI4Y2YtZTg3ZTNkNDVhNzU2IiwiZXhwIjoiMjAyNC0wMy0yMlQxMjoxMTozOS4zNDZaIiwiaXNzdWVyIjoiQmFzYWx0LWlzc3VlciIsImF1ZGllbmNlIjoiQmFzYWx0LWF1ZGllbmNlIn0=.e30=.3teaXCzVkSLI5+1Hr84le4l9FqqZFjLeHAYGqSDOzK9453tI276ysihygMA5oq8aabYSl4/Fn6Hm5T/p+88ZDQ==
```

## **Token Verification**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});

    try {
        basaltToken.verify(tokenSignResult.token, tokenSignResult.publicKey)
        console.log('Token is valid');
    } catch (error) {
        console.error(error);
    }
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});

    try {
        basaltToken.verify(tokenSignResult.token, tokenSignResult.publicKey)
        console.log('Token is valid');
    } catch (error) {
        console.error(error);
    }
    ```

<!-- termynal -->

```bash
$ node example.js
Token is valid
```

## **Token UUID Retrieval**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getTokenUuid(tokenSignResult.token));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken, BasaltTokenExpiry } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getTokenUuid(tokenSignResult.token));
    ```

<!-- termynal -->

```bash
$ node example.js
c4a198c4-2717-470d-886f-bc2921badd8f
```

## **Expiration Retrieval**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getExpirationDate(tokenSignResult.token));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken, BasaltTokenExpiry } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getExpirationDate(tokenSignResult.token));
    ```
<!-- termynal -->

```bash
$ node example.js
2024-03-22T12:03:38.266Z
```

## **Token Audience Retrieval**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getAudience(tokenSignResult.token));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken, BasaltTokenExpiry } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getAudience(tokenSignResult.token));
    ```

<!-- termynal -->

```bash
$ node example.js
Basalt-Audience
```

## **Token Issuer Retrieval**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getIssuer(tokenSignResult.token));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken, BasaltTokenExpiry } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});

    console.log(basaltToken.getIssuer(tokenSignResult.token));
    ```

<!-- termynal -->

```bash
$ node example.js
Basalt-Issuer
```

## **Token Header Retrieval**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult, type IBasaltTokenHeader } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});

    const tokenHeader: IBasaltTokenHeader = basaltToken.getHeader(tokenSignResult.token);
    console.log(tokenHeader);
    ```


=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});

    const tokenHeader = basaltToken.getHeader(tokenSignResult.token);
    console.log(tokenHeader);
    ```

<!-- termynal -->

```bash
$ node example.js
{
  uuid: '82e7fa41-44b4-4fa8-ac31-ae309234bb8b',
  exp: '2024-03-22T12:19:58.187Z',
  issuer: 'Basalt-Audience',
  audience: 'Basalt-Audience'
}

```

## **Token Payload Retrieval**


=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({
        username: 'user1'
    });
    const tokenPayload: { username: string } = basaltToken.getPayload(tokenSignResult.token);
    console.log(tokenPayload);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({
        username: 'user1'
    });
    const tokenPayload = basaltToken.getPayload(tokenSignResult.token);
    console.log(tokenPayload);
    ```    

<!-- termynal -->

```bash
$ node example.js
{ username: 'user1' }
```

## **Check if the token has expired**

=== "TypeScript"

    ```typescript
    import { BasaltToken, type IBasaltTokenSignResult } from '@basalt-lab/basalt-auth';

    const basaltToken: BasaltToken = new BasaltToken();
    const tokenSignResult: IBasaltTokenSignResult = basaltToken.sign({});
    console.log(basaltToken.isExpired(tokenSignResult.token));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltToken } = require('@basalt-lab/basalt-auth');

    const basaltToken = new BasaltToken();
    const tokenSignResult = basaltToken.sign({});
    console.log(basaltToken.isExpired(tokenSignResult.token));
    ```

<!-- termynal -->

```bash
$ node example.js
false
```
