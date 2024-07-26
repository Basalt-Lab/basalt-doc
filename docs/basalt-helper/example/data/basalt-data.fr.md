## **Clonage profond**

=== "TypeScript"

    ```typescript
    import { deepClone } from '@basalt-lab/basalt-helper';

    const data1: { test: { test: string } } = {
        test: {
            test: 'test'
        }
    };
    const data2: number[][] = [[1, 2, 3], [4, 5, 6]];
    const data3: { test: { test: number[] } } = {
        test: {
            test: [1, 2, 3]
        }
    };
    const data4: Array<{ test: number[] }> = [
        {
            test: [1, 2, 3]
        },
        {
            test: [4, 5, 6]
        }
    ];

    const clonedData1: { test: { test: string } } = deepClone(data1);
    const clonedData2: number[][] = deepClone(data2);
    const clonedData3: { test: { test: number[] } } = deepClone(data3);
    const clonedData4: Array<{ test: number[] }> = deepClone(data4);

    console.log(clonedData1 === data1);
    console.log(clonedData2 === data2);
    console.log(clonedData3 === data3);
    console.log(clonedData4 === data4);
    ```

=== "JavaScript"

    ```javascript
    const { deepClone } = require('@basalt-lab/basalt-helper');

    const data1 = {
        test: {
            test: 'test'
        }
    };
    const data2 = [[1, 2, 3], [4, 5, 6]];
    const data3 = {
        test: {
            test: [1, 2, 3]
        }
    };
    const data4 = [
        {
            test: [1, 2, 3]
        },
        {
            test: [4, 5, 6]
        }
    ];

    const clonedData1 = deepClone(data1);
    const clonedData2 = deepClone(data2);
    const clonedData3 = deepClone(data3);
    const clonedData4 = deepClone(data4);

    console.log(clonedData1 === data1);
    console.log(clonedData2 === data2);
    console.log(clonedData3 === data3);
    console.log(clonedData4 === data4);
    ```

<!-- termynal -->

```bash
$ node example.js
false
false
false
false
```

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

## **Transformation des clés d'un objet en camelCase**

=== "TypeScript"

    ```typescript
    import { transformKeys, BasaltCamelCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltCamelCaseTransformer()));
    ```

=== "JavaScript"

    ```javascript
    const { transformKeys, BasaltCamelCaseTransformer } = require('@basalt-lab/basalt-helper');

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltCamelCaseTransformer()));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  camelCase: undefined,
  pascalCase: undefined,
  kebabCase: undefined,
  snakeCase: undefined
}
```

## **Transformation des clés d'un objet en PascalCase**

=== "TypeScript"

    ```typescript
    import { transformKeys, BasaltPascalCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltPascalCaseTransformer()));
    ```

=== "JavaScript"

    ```javascript
    const { transformKeys, BasaltPascalCaseTransformer } = require('@basalt-lab/basalt-helper');

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltPascalCaseTransformer()));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  CamelCase: undefined,
  PascalCase: undefined,
  KebabCase: undefined,
  SnakeCase: undefined
}
```

## **Transformation des clés d'un objet en kebab-case**

=== "TypeScript"

    ```typescript
    import { transformKeys, BasaltKebabCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltKebabCaseTransformer()));
    ```

=== "JavaScript"

    ```javascript
    const { transformKeys, BasaltKebabCaseTransformer } = require('@basalt-lab/basalt-helper');

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltKebabCaseTransformer()));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  'camel-case': undefined,
  'pascal-case': undefined,
  'kebab-case': undefined,
  'snake-case': undefined
}
```

## **Transformation des clés d'un objet en snake_case**

=== "TypeScript"

    ```typescript
    import { transformKeys, BasaltSnakeCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltSnakeCaseTransformer()));
    ```

=== "JavaScript"

    ```javascript
    const { transformKeys, BasaltSnakeCaseTransformer } = require('@basalt-lab/basalt-helper');

    const data = {
        'camelCase': undefined,
        'PascalCase': undefined,
        'kebab-case': undefined,
        'snake_case': undefined
    };

    console.log(transformKeys(data, new BasaltSnakeCaseTransformer()));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  camel_case: undefined,
  pascal_case: undefined,
  kebab_case: undefined,
  snake_case: undefined
}
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
