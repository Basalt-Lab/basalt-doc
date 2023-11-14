## **Deep cloning data**

=== "TypeScript"

    ```typescript
    import { BasaltDeepCloneUtility } from '@basalt-lab/basalt-helper';
    
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
    
    const clonedData1: { test: { test: string } } = BasaltDeepCloneUtility.deepClone(data1);
    const clonedData2: number[][] = BasaltDeepCloneUtility.deepClone(data2);
    const clonedData3: { test: { test: number[] } } = BasaltDeepCloneUtility.deepClone(data3);
    const clonedData4: ({ test: number[] })[] = BasaltDeepCloneUtility.deepClone(data4);
    
    console.log(clonedData1 === data1);
    console.log(clonedData2 === data2);
    console.log(clonedData3 === data3);
    console.log(clonedData4 === data4);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltDeepCloneUtility } = require('@basalt-lab/basalt-helper');
    
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
    
    const clonedData1 = BasaltDeepCloneUtility.deepClone(data1);
    const clonedData2 = BasaltDeepCloneUtility.deepClone(data2);
    const clonedData3 = BasaltDeepCloneUtility.deepClone(data3);
    const clonedData4 = BasaltDeepCloneUtility.deepClone(data4);
    
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
