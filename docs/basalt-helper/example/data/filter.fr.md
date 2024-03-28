## **Inclure uniquement certaines clés**

=== "TypeScript"

    ```typescript
    import { filterByKeyInclusion } from '@basalt-lab/basalt-helper';
        
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByKeyInclusion(data, ['a', 'b', 'c']);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByKeyInclusion } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByKeyInclusion(data, ['a', 'b', 'c']);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ a: 'a', b: 'b', c: 'c' }
```

## **Inclure uniquement certaines clés et seulement si elles ont une valeur**

=== "TypeScript"

    ```typescript
    import { filterByKeyInclusion } from '@basalt-lab/basalt-helper';

    const data: { a: string; b: undefined; c: null; d: string } = {
        a: 'a',
        b: undefined,
        c: null,
        d: 'd',
    };

    const filteredData = filterByKeyInclusion(data, ['a', 'b', 'c'], true);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByKeyInclusion } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: undefined,
        c: null,
        d: 'd',
    };

    const filteredData = filterByKeyInclusion(data, ['a', 'b', 'c'], true);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ a: 'a' }
```


## **Exclure certaines clés**

=== "TypeScript"

    ```typescript
    import { filterByKeyExclusion } from '@basalt-lab/basalt-helper';
        
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByKeyExclusion(data, ['a', 'b']);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByKeyExclusion } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByKeyExclusion(data, ['a', 'b']);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ c: 'c', d: 'd' }
```

## **Exclure certaines clés et exclure ceux qui n'ont pas de valeur**

=== "TypeScript"

    ```typescript
    import { filterByKeyExclusion } from '@basalt-lab/basalt-helper';
        
    const data: { a: string; b: null; c: undefined; d: string } = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };

    const filteredData = filterByKeyExclusion(data, ['a'], true);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByKeyExclusion } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };

    const filteredData = filterByKeyExclusion(data, ['a'], true);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ d: 'd' }
```

## **Inclure les clefs selon un pattern**

=== "TypeScript"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper';
        
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByValue(data, (value: string): boolean => value === 'a' || value === 'b');
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByValue } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByValue(data, (value) => value === 'a' || value === 'b');
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ a: 'a', b: 'b' }
```

## **Exclure les clefs selon un pattern**

=== "TypeScript"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper';
        
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByValue(data, (value: string): boolean => value !== 'a' && value !== 'b');
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByValue } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const filteredData = filterByValue(data, (value) => value !== 'a' && value !== 'b');
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ c: 'c', d: 'd' }
```

## **Exclure les clefs selon un pattern et exclure ceux qui n'ont pas de valeur**

=== "TypeScript"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper';

    const data: { a: string; b: null; c: undefined; d: string } = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };

    const filteredData = filterByValue(data, (value: unknown): boolean => value !== 'a', true);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { filterByValue } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };

    const filteredData = filterByValue(data, (value) => value !== 'a', true);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ d: 'd' }
```
