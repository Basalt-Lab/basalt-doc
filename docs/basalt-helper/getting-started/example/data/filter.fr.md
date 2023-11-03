## **Inclure uniquement certaines clés**

=== "TypeScript"

    ```typescript
    import { BasaltKeyInclusionFilter } from '@basalt-lab/basalt-helper';
    
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const basaltKeyInclusionFilter: BasaltKeyInclusionFilter = new BasaltKeyInclusionFilter();
    const filteredData = basaltKeyInclusionFilter.filter(data, ['a', 'b', 'c']);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyInclusionFilter } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const basaltKeyInclusionFilter = new BasaltKeyInclusionFilter();
    const filteredData = basaltKeyInclusionFilter.filter(data, ['a', 'b', 'c']);
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
    import { BasaltKeyInclusionFilter } from '@basalt-lab/basalt-helper';

    const data: { a: string; b: undefined; c: null; d: string } = {
        a: 'a',
        b: undefined,
        c: null,
        d: 'd',
    };
    
    const basaltKeyInclusionFilter: BasaltKeyInclusionFilter = new BasaltKeyInclusionFilter();
    const filteredData = basaltKeyInclusionFilter.filter(data, ['a', 'b', 'c'], true);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyInclusionFilter } = require('@basalt-lab/basalt-helper');
    
    const data = {
        a: 'a',
        b: undefined,
        c: null,
        d: 'd',
    };
    
    const basaltKeyInclusionFilter = new BasaltKeyInclusionFilter();
    const filteredData = basaltKeyInclusionFilter.filter(data, ['a', 'b', 'c'], true);
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
    import { BasaltKeyExclusionFilter } from '@basalt-lab/basalt-helper';
    
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };
    
    const basaltKeyExclusionFilter: BasaltKeyExclusionFilter = new BasaltKeyExclusionFilter();
    const filteredData = basaltKeyExclusionFilter.filter(data, ['a', 'b']);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyExclusionFilter } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const basaltKeyExclusionFilter = new BasaltKeyExclusionFilter();
    const filteredData = basaltKeyExclusionFilter.filter(data, ['a', 'b']);
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
    import { BasaltKeyExclusionFilter } from '@basalt-lab/basalt-helper';
    
    const data: { a: string; b: null; c: undefined; d: string } = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };
    
    const basaltKeyExclusionFilter: BasaltKeyExclusionFilter = new BasaltKeyExclusionFilter();
    const filteredData = basaltKeyExclusionFilter.filter(data, ['a'], true);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyExclusionFilter } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };

    const basaltKeyExclusionFilter = new BasaltKeyExclusionFilter();
    const filteredData = basaltKeyExclusionFilter.filter(data, ['a'], true);
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
    import { BasaltValueFilter } from '@basalt-lab/basalt-helper';
    
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };
    
    const basaltValueFilter: BasaltValueFilter = new BasaltValueFilter();
    const filteredData = basaltValueFilter.filter(data, (value: string): boolean => value === 'a' || value === 'b');
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltValueFilter } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const basaltValueFilter = new BasaltValueFilter();
    const filteredData = basaltValueFilter.filter(data, (value) => value === 'a' || value === 'b');
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
    import { BasaltValueFilter } from '@basalt-lab/basalt-helper';
    
    const data: { a: string; b: string; c: string; d: string } = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };
    
    const basaltValueFilter: BasaltValueFilter = new BasaltValueFilter();
    const filteredData = basaltValueFilter.filter(data, (value: string): boolean => value !== 'a' && value !== 'b');
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltValueFilter } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    };

    const basaltValueFilter = new BasaltValueFilter();
    const filteredData = basaltValueFilter.filter(data, (value) => value !== 'a' && value !== 'b');
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
    import { BasaltValueFilter } from '@basalt-lab/basalt-helper';
    
    const data: { a: string; b: null; c: undefined; d: string } = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };
    
    const basaltValueFilter: BasaltValueFilter = new BasaltValueFilter();
    const filteredData = basaltValueFilter.filter(data, (value: unknown): boolean => value !== 'a', true);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltValueFilter } = require('@basalt-lab/basalt-helper');

    const data = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    };

    const basaltValueFilter = new BasaltValueFilter();
    const filteredData = basaltValueFilter.filter(data, (value) => value !== 'a', true);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ d: 'd' }
```
