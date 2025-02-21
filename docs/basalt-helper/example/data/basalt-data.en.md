## **Filter keys by inclusion**

`filterByKeyInclusion` is a function that filters an object by including only the specified keys.

??? example "Include only specific keys"

    ```typescript
    import { filterByKeyInclusion } from '@basalt-lab/basalt-helper/data';
            
    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    } as const;

    const filteredData = filterByKeyInclusion(data, ['a', 'b', 'c']);
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { a: 'a', b: 'b', c: 'c' }
    ```

??? example "Include only specific keys and only if they have a value"

    ```typescript
    import { filterByKeyInclusion } from '@basalt-lab/basalt-helper/data';

    const data = {
        a: 'a',
        b: undefined,
        c: null,
        d: 'd',
    } as const;

    const filteredData = filterByKeyInclusion(data, ['a', 'b', 'c'], true);
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { a: 'a' }
    ```

## **Filter keys by exclusion**

`filterByKeyExclusion` is a function that filters an object by excluding specified keys.

??? example "Exclude specific keys"

    ```typescript
    import { filterByKeyExclusion } from '@basalt-lab/basalt-helper/data';
        
    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    } as const;

    const filteredData = filterByKeyExclusion(data, ['a', 'b']);
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { c: 'c', d: 'd' }
    ```

??? example "Exclude specific keys and those without values"

    ```typescript
    import { filterByKeyExclusion } from '@basalt-lab/basalt-helper/data';
        
    const data = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    } as const;

    const filteredData = filterByKeyExclusion(data, ['a'], true);
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { d: 'd' }
    ```

## **Include keys by pattern**

`filterByKey` is a function that filters an object by including keys according to a pattern.

??? example "Include keys by pattern"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper/data';
        
    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    } as const;

    const filteredData = filterByValue(data, (value: string): boolean => value === 'a' || value === 'b');
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { a: 'a', b: 'b' }
    ```

??? example "Include keys by pattern and only if they have a value"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper/data';

    const data = {
        a: 'a',
        b: undefined,
        c: null,
        d: 'd',
    } as const;

    const filteredData = filterByValue(data, (value: unknown): boolean => value === 'a', true);
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { a: 'a' }
    ```

## **Exclude keys by pattern**

`filterByValue` is a function that filters an object by excluding keys according to a pattern.

??? example "Exclude keys by pattern"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper/data';
        
    const data = {
        a: 'a',
        b: 'b',
        c: 'c',
        d: 'd',
    } as const;

    const filteredData = filterByValue(data, (value: string): boolean => value !== 'a' && value !== 'b');
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { c: 'c', d: 'd' }
    ```

??? example "Exclude keys by pattern and those without values"

    ```typescript
    import { filterByValue } from '@basalt-lab/basalt-helper/data';

    const data = {
        a: 'a',
        b: null,
        c: undefined,
        d: 'd',
    } as const;

    const filteredData = filterByValue(data, (value: unknown): boolean => value !== 'a', true);
    console.log(filteredData);
    ```

    <!-- termynal -->

    ```bash
    $ bun example.ts
    { d: 'd' }
    ```

## **Transform object keys**

`transformKeys` is a function that transforms object keys according to a specified transformer.

??? example "Transform object keys to camelCase"

    ```typescript
    import { transformKeys } from '@basalt-lab/basalt-helper/data';
    import { BasaltCamelCaseTransformer } from '@basalt-lab/basalt-helper/data/transformer';

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
    $ bun example.ts
    {
    camelCase: undefined,
    pascalCase: undefined,
    kebabCase: undefined,
    snakeCase: undefined
    }
    ```

??? example "Transform object keys to PascalCase"

    ```typescript
    import { transformKeys } from '@basalt-lab/basalt-helper/data';
    import { BasaltPascalCaseTransformer } from '@basalt-lab/basalt-helper/data/transformer';

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
    $ bun example.ts
    {
    CamelCase: undefined,
    PascalCase: undefined,
    KebabCase: undefined,
    SnakeCase: undefined
    }
    ```

??? example "Transform object keys to kebab-case"

    ```typescript
    import { transformKeys } from '@basalt-lab/basalt-helper/data';
    import { BasaltKebabCaseTransformer } from '@basalt-lab/basalt-helper/data/transformer';

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
    $ bun example.ts
    {
    'camel-case': undefined,
    'pascal-case': undefined,
    'kebab-case': undefined,
    'snake-case': undefined
    }
    ```

??? example "Transform object keys to snake_case"

    ```typescript
    import { transformKeys } from '@basalt-lab/basalt-helper/data';
    import { BasaltSnakeCaseTransformer } from '@basalt-lab/basalt-helper/data/transformer';

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
    $ bun example.ts
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
        data-message="Thank you for your visit!"
        data-color="#5F7FFF"
        data-position="Right"
        data-x_margin="18"
        data-y_margin="22" />
