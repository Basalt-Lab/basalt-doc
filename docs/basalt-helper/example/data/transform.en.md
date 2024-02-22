## **Transforming object keys to camelCase**

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

## **Transforming object keys to PascalCase**

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

## **Transforming object keys to kebab-case**

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

## **Transforming object keys to snake_case**

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
