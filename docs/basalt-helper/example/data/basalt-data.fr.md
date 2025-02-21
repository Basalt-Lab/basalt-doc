## **Filter les clés par inclusion**

`filterByKeyInclusion` est une fonction permettant de filtrer un objet en incluant uniquement les clés spécifiées.

??? example "Inclure uniquement certaines clés"

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

??? example "Inclure uniquement certaines clés et seulement si elles ont une valeur"

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

## **Filter les clés par exclusion**

`filterByKeyExclusion` est une fonction permettant de filtrer un objet en excluant les clés spécifiées.

??? example "Exclure certaines clés"

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

??? example "Exclure certaines clés et exclure ceux qui n'ont pas de valeur"

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

## **Inclure les clefs selon un pattern**

`filterByKey` est une fonction permettant de filtrer un objet en incluant les clefs selon un pattern.

??? example "Inclure les clefs selon un pattern"

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

??? example "Inclure les clefs selon un pattern et seulement si elles ont une valeur"

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

## **Exclure les clefs selon un pattern**

`filterByValue` est une fonction permettant de filtrer un objet en excluant les clefs selon un pattern.

??? example "Exclure les clefs selon un pattern"

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

??? example "Exclure les clefs selon un pattern et exclure ceux qui n'ont pas de valeur"

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

## **Transformer les clés d'un objet**

`transformKeys` est une fonction permettant de transformer les clés d'un objet selon un transformateur spécifié.

??? example "Transformation des clés d'un objet en camelCase"

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

??? example "Transformation des clés d'un objet en PascalCase"

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

??? example "**Transformation des clés d'un objet en kebab-case**"

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

??? example "Transformation des clés d'un objet en snake_case"

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
        data-message="Merci pour votre visite !"
        data-color="#5F7FFF"
        data-position="Right"
        data-x_margin="18"
        data-y_margin="22" />