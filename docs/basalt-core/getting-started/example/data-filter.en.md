## **Filter the Object to Include Only Certain Keys**

=== "TypeScript"

    ```typescript
    import { BasaltDataFilter } from '@basalt-lab/basalt-core';

    interface IUserData {
        nom: string;
        age: number;
        pays: string;
    }

    const data: IUserData = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const filteredData: IUserData = BasaltDataFilter.filterByKeys(data, ['nom', 'age']);
    console.log(filteredData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltDataFilter } = require('@basalt-lab/basalt-core');

    const data = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const filteredData = BasaltDataFilter.filterByKeys(data, ['nom', 'age']);
    console.log(filteredData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ nom: 'Alice', age: 25 }
```

## **Excluding Specified Keys from Data**

=== "TypeScript"

    ```typescript
    import { BasaltDataFilter } from '@basalt-lab/basalt-core';

    interface IUserData {
        nom: string;
        age: number;
        pays: string;
    }

    const data: IUserData = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const dataWithExcludedKeys: IUserData = BasaltDataFilter.excludeByKeys(data, ['age']);
    console.log(dataWithExcludedKeys);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltDataFilter } = require('@basalt-lab/basalt-core');

    const data = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const dataWithExcludedKeys = BasaltDataFilter.excludeByKeys(data, ['age']);
    console.log(dataWithExcludedKeys);
    ```

<!-- termynal -->

```bash
$ node example.js
{ nom: 'Alice', pays: 'France' }
```

## **Transforming Object Keys into a Different Case**

=== "TypeScript"

    ```typescript
    import { BasaltDataFilter } from '@basalt-lab/basalt-core';

    interface IUserData {
        nom: string;
        age: number;
        pays: string;
    }

    const data: IUserData = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const dataWithPascalCaseKeys: IUserData = BasaltDataFilter.transformKeyToAnotherCase(data, 'pascal');
    console.log(dataWithPascalCaseKeys);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltDataFilter } = require('@basalt-lab/basalt-core');

    const data = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const dataWithPascalCaseKeys = BasaltDataFilter.transformKeyToAnotherCase(data, 'pascal');
    console.log(dataWithPascalCaseKeys);
    ```

<!-- termynal -->

```bash
$ node example.js
{ Nom: 'Alice', Age: 25, Pays: 'France' }
```

## **Filtering Data by Specified Value**

=== "TypeScript"

    ```typescript
    import { BasaltDataFilter } from '@basalt-lab/basalt-core';

    interface IUserData {
        nom: string;
        age: number;
        pays: string;
    }

    const data: IUserData = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const filteredByValue: IUserData = BasaltDataFilter.filterByValue(data, (value): boolean => {
        return value !== 'France';
    });
    console.log(filteredByValue);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltDataFilter } = require('@basalt-lab/basalt-core');

    const data = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const filteredByValue = BasaltDataFilter.filterByValue(data, (value) => {
        return value !== 'France';
    });
    ```

<!-- termynal -->

```bash
$ node example.js
{ nom: 'Alice', age: 25 }
```

## **Deep Cloning Data**

=== "TypeScript"

    ```typescript
    import { BasaltDataFilter } from '@basalt-lab/basalt-core';

    interface IUserData {
        nom: string;
        age: number;
        pays: string;
    }

    const data: IUserData = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const clonedData: IUserData = BasaltDataFilter.deepClone(data);
    console.log(clonedData);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltDataFilter } = require('@basalt-lab/basalt-core');

    const data = {
        nom: 'Alice',
        age: 25,
        pays: 'France',
    };

    const clonedData = BasaltDataFilter.deepClone(data);
    console.log(clonedData);
    ```

<!-- termynal -->

```bash
$ node example.js
{ nom: 'Alice', age: 25, pays: 'France' }
```
