## **Transforming the keys of an object into camelCase**

=== "TypeScript"

    ```typescript
    import { BasaltKeyTransformerUtility, BasaltCamelCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };
    
    const basaltKeyTransformerUtility: BasaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltCamelCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyTransformerUtility, BasaltCamelCaseTransformer } = require('@basalt-lab/basalt-helper');

    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };
    
    const basaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltCamelCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  camelCase: 'camelCase',
  pascalCase: 'PascalCase',
  kebabCase: 'kebab-case',
  snakeCase: 'snake_case'
}
```

## **Transforming the keys of an object into PascalCase**

=== "TypeScript"

    ```typescript
    import { BasaltKeyTransformerUtility, BasaltPascalCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };
    
    const basaltKeyTransformerUtility: BasaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltPascalCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyTransformerUtility, BasaltPascalCaseTransformer } = require('@basalt-lab/basalt-helper');
    
    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };

    const basaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltPascalCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  CamelCase: 'camelCase',
  PascalCase: 'PascalCase',
  KebabCase: 'kebab-case',
  SnakeCase: 'snake_case'
}
```

## **Transforming the keys of an object into kebab-case**

=== "TypeScript"

    ```typescript
    import { BasaltKeyTransformerUtility, BasaltKebabCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };
    
    const basaltKeyTransformerUtility: BasaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltKebabCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyTransformerUtility, BasaltKebabCaseTransformer } = require('@basalt-lab/basalt-helper');
    
    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };

    const basaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltKebabCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  'camel-case': 'camelCase',
  'pascal-case': 'PascalCase',
  'kebab-case': 'kebab-case',
  'snake-case': 'snake_case'
}
```

## **Transforming the keys of an object into snake_case**

=== "TypeScript"

    ```typescript
    import { BasaltKeyTransformerUtility, BasaltSnakeCaseTransformer } from '@basalt-lab/basalt-helper';

    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };
    
    const basaltKeyTransformerUtility: BasaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltSnakeCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyTransformerUtility, BasaltSnakeCaseTransformer } = require('@basalt-lab/basalt-helper');
    
    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };

    const basaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltSnakeCaseTransformer());
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  camel_case: 'camelCase',
  pascal_case: 'PascalCase',
  kebab_case: 'kebab-case',
  snake_case: 'snake_case'
}
```

## **Change in the key transformation format**

=== "TypeScript"

    ```typescript
    import { BasaltKeyTransformerUtility, BasaltCamelCaseTransformer, BasaltPascalCaseTransformer } from '@basalt-lab/basalt-helper';
    
    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };
    
    const basaltKeyTransformerUtility: BasaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltCamelCaseTransformer());
    basaltKeyTransformerUtility.transformer = new BasaltPascalCaseTransformer(); // Change the transformer
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

=== "JavaScript"

    ```javascript
    const { BasaltKeyTransformerUtility, BasaltCamelCaseTransformer, BasaltPascalCaseTransformer } = require('@basalt-lab/basalt-helper');

    const data = {
        'camelCase': 'camelCase',
        'PascalCase': 'PascalCase',
        'kebab-case': 'kebab-case',
        'snake_case': 'snake_case',
    };


    const basaltKeyTransformerUtility = new BasaltKeyTransformerUtility(new BasaltCamelCaseTransformer());
    basaltKeyTransformerUtility.transformer = new BasaltPascalCaseTransformer(); // Change the transformer
    console.log(basaltKeyTransformerUtility.transformKeys(data));
    ```

<!-- termynal -->

```bash
$ node example.js
{
  CamelCase: 'camelCase',
  PascalCase: 'PascalCase',
  KebabCase: 'kebab-case',
  SnakeCase: 'snake_case'
}
```
