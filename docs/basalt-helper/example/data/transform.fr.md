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
