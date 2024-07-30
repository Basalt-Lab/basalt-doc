## **Retrieve current directory name (Useful in ESM, otherwise use `__dirname`)**

=== "TypeScript"

    ```typescript
    import { getDirname } from '@basalt-lab/basalt-helper';

    const __dirname: string = getDirname();

    console.log(__dirname);
    ```

=== "JavaScript"

    ```javascript
    const { getDirname } = require('@basalt-lab/basalt-helper');

    const __dirname = getDirname();

    console.log(__dirname);
    ```

<!-- termynal -->

```bash
$ node example.js
/home/user/basalt-helper/example/filesystem
```

## **Check permissions of a path**

=== "TypeScript"

    ```typescript
    import { Path } from '@basalt-lab/basalt-helper';

    const path: Path = new Path('./');

    console.log(path.checkAccess()); // check constants.F_OK || constants.W_OK || constants.R_OK
    ```

=== "JavaScript"

    ```javascript
    const { Path } = require('@basalt-lab/basalt-helper');

    const path = new Path('./');

    console.log(path.checkAccess()); // check constants.F_OK || constants.W_OK || constants.R_OK
    ```

<!-- termynal -->
    
```bash
$ node example.js
true
```

## **Check if the path exists**

=== "TypeScript"

    ```typescript
    import { Path } from '@basalt-lab/basalt-helper';

    const path: Path = new Path('./example.js');

    console.log(path.exists());
    ```

=== "JavaScript"

    ```javascript
    const { Path } = require('@basalt-lab/basalt-helper');

    const path = new Path('./example.js');

    console.log(path.exists());
    ```

<!-- termynal -->
    
```bash
$ node example.js
true
```

## **Get the path**

=== "TypeScript"

    ```typescript
    import { Path } from '@basalt-lab/basalt-helper';

    const path: Path = new Path('./example.js');

    console.log(path.path);
    ```

=== "JavaScript"

    ```javascript
    const { Path } = require('@basalt-lab/basalt-helper');

    const path = new Path('./example.js');

    console.log(path.path);
    ```

<!-- termynal -->

```bash
$ node example.js
/home/user/basalt-helper/example/filesystem/example.js
```

## **Read the file**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(file.read());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(file.read());
    ```

<!-- termynal -->

```bash
$ node example.js
// Contenu du fichier
```

## **Write to a file**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.txt');

    file.write('Hello World!');
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.txt');

    file.write('Hello World!');
    ```

<!-- termynal -->

```bash
$ node example.js
$ cat example.txt
Hello World!
```

## **Watch a file**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.txt');

    // 50ms
    file.watch(50, () => {
        console.log('File changed');
    });
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.txt');

    // 50ms
    file.watch(50, () => {
        console.log('File changed');
    });
    ```

<!-- termynal -->
    
```bash
$ node example.js & echo "Hello World!" > example.txt
File changed
```

## **Calculate the MD5 hash of a file using a stream**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(await file.calculateStreamHashMD5());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(await file.calculateStreamHashMD5());
    ```

<!-- termynal -->

```bash
$ node example.js
// Hash MD5
```

## **Calculate the MD5 hash of a file using a buffer**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(file.calculateHashMD5());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(file.calculateHashMD5());
    ```

<!-- termynal -->

```bash
$ node example.js
// Hash MD5
```

## **Calculate the SHA256 hash of a file using a stream**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(await file.calculateStreamHashSHA256());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(await file.calculateStreamHashSHA256());
    ```

<!-- termynal -->

```bash
$ node example.js
// Hash SHA256
```

## **Calculate the SHA256 hash of a file using a buffer**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(file.calculateHashSHA256());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(file.calculateHashSHA256());
    ```

<!-- termynal -->
    
```bash
$ node example.js
// Hash SHA256
```

## **Calculate the SHA512 hash of a file using a stream**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(await file.calculateStreamHashSHA512());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(await file.calculateStreamHashSHA512());
    ```

<!-- termynal -->

```bash
$ node example.js
// Hash SHA512
```

## **Calculate the SHA512 hash of a file using a buffer**

=== "TypeScript"

    ```typescript
    import { File } from '@basalt-lab/basalt-helper';

    const file = new File('./example.js');

    console.log(file.calculateHashSHA512());
    ```

=== "JavaScript"

    ```javascript
    const { File } = require('@basalt-lab/basalt-helper');

    const file = new File('./example.js');

    console.log(file.calculateHashSHA512());
    ```

<!-- termynal -->

```bash
$ node example.js
// Hash SHA512
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
