## **Deep cloning data**

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
    const data4: ({ test: number[] })[] = [
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
    const clonedData4: ({ test: number[] })[] = deepClone(data4);

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
        
    ```

<!-- termynal -->

```bash
$ node example.js
false
false
false
false
```
