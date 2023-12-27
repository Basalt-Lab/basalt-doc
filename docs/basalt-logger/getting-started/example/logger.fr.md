## **Ajout d'une strategie de log**

=== "TypeScript"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy } from '@basalt-lab/basalt-logger';

    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    ```

=== "JavaScript"
    
    ```javascript
    const { BasaltLogger, ConsoleLoggerStrategy } = require('@basalt-lab/basalt-logger');

    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    ```

<!-- termynal -->

```bash
$ node example.js
[2023-11-21 00:00:00] LOG : hello world
```

## **Suppression d'une strategie specifique de log**

=== "TypeScript"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy } from '@basalt-lab/basalt-logger';

    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());

    BasaltLogger.removeStrategy('console');
    ```

=== "JavaScript"

    ```javascript 
    const { BasaltLogger, ConsoleLoggerStrategy } = require('@basalt-lab/basalt-logger');

    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());
    
    BasaltLogger.removeStrategy('console');
    ```

## **Suppression de toutes les strategies de log**

=== "TypeScript"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy } from '@basalt-lab/basalt-logger';
    
    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());
    
    BasaltLogger.clearStrategies();
    ```

=== "JavaScript"

    ```javascript
    const { BasaltLogger, ConsoleLoggerStrategy } = require('@basalt-lab/basalt-logger');

    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());

    BasaltLogger.clearStrategies();
    ```

## **Création d'une strategie de log**

=== "TypeScript"

    ```typescript
    import { appendFileSync } from 'fs';
    import { BasaltLogger, ILoggerStrategy, LogLevels}  from '@basalt-lab/basalt-logger';
    
    class FileLoggerStrategy implements ILoggerStrategy {
        public log(level: LogLevels, date: Date, object: unknown): void {
            const prefixDate: string = `[${date.toISOString().replace(/T/, ' ').replace(/\..+/, '')}]`;
            const sanitizedObject: string = typeof object === 'string' ? object : JSON.stringify(object);
            const message: string = `${prefixDate} ${level} : ${sanitizedObject}`;
            appendFile('./test.log', `${message}\n`, (err): void => {
                if (err) throw err;
            });
        }
    }
    BasaltLogger.addStrategy('file', new FileLoggerStrategy());
    BasaltLogger.log('Hello World');
    ```

=== "JavaScript"

    ```javascript
    const { appendFileSync } = require('fs');
    const { BasaltLogger, LogLevels } = require('@basalt-lab/basalt-logger');

    class FileLoggerStrategy {
        log(level, date, object) {
            const prefixDate = `[${date.toISOString().replace(/T/, ' ').replace(/\..+/, '')}]`;
            const sanitizedObject = typeof object === 'string' ? object : JSON.stringify(object);
            const message = `${prefixDate} ${level} : ${sanitizedObject}`;
            appendFile('./test.log', `${message}\n`, (err) => {
                if (err) throw err;
            });
        }
    }
    BasaltLogger.addStrategy('file', new FileLoggerStrategy());
    BasaltLogger.log('Hello World');
    ```

<!-- termynal -->

```bash
$ node example.js
$ cat test.log
[2023-11-21 00:00:00] LOG : Hello World
```

## **Ajout de plusieurs strategies de log**


=== "TypeScript"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy, FileLoggerStrategy}  from '@basalt-lab/basalt-logger';
    
    BasaltLogger.addStrategies([
        ['console', new ConsoleLoggerStrategy()],
        ['file', new FileLoggerStrategy('log.txt')]
    ]);
    
    BasaltLogger.log('Hello World');
    ```

=== "JavaScript"

    ```javascript
    const { BasaltLogger, ConsoleLoggerStrategy, FileLoggerStrategy } = require('@basalt-lab/basalt-logger');
    
    BasaltLogger.addStrategies([
        ['console', new ConsoleLoggerStrategy()],
        ['file', new FileLoggerStrategy('log.txt')]
    ]);

    BasaltLogger.log('Hello World');
    ```

<!-- termynal -->

```bash
$ node example.js
[2023-11-21 00:00:00] LOG : Hello World
$ cat log.txt
[2023-11-21 00:00:00] LOG : Hello World
```

## **Tout les niveaux de log**

=== "TypeScript"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy }  from '@basalt-lab/basalt-logger';
    
    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    BasaltLogger.info('hello world');
    BasaltLogger.debug('hello world');
    BasaltLogger.warn('hello world');
    BasaltLogger.error('hello world');
    ```
=== "JavaScript"
    
    ```javascript
    const { BasaltLogger, ConsoleLoggerStrategy } = require('@basalt-lab/basalt-logger');
    
    BasaltLogger.addStrategy('console', new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    BasaltLogger.info('hello world');
    BasaltLogger.debug('hello world');
    BasaltLogger.warn('hello world');
    BasaltLogger.error('hello world');
    ```

<!-- termynal -->

```bash
$ node example.js
[2023-11-21 00:00:00] LOG : hello world
[2023-11-21 00:00:00] INFO : hello world
[2023-11-21 00:00:00] DEBUG : hello world
[2023-11-21 00:00:00] WARN : hello world
[2023-11-21 00:00:00] ERROR : hello world
```

## **Log sur une strategie specifique**

=== "TypeScript"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy, FileLoggerStrategy}  from '@basalt-lab/basalt-logger';
    
    BasaltLogger.addStrategies([
        ['console', new ConsoleLoggerStrategy()],
        ['file', new FileLoggerStrategy('log.txt')]
    ]);
    
    BasaltLogger.log('console strategy', ['console']);
    BasaltLogger.log('file strategy', ['file']);
    BasaltLogger.log('console and file strategy', ['console', 'file']);
    BasaltLogger.log('all strategies');
    ```

=== "JavaScript"

    ```javascript
    const { BasaltLogger, ConsoleLoggerStrategy, FileLoggerStrategy } = require('@basalt-lab/basalt-logger');
    
    BasaltLogger.addStrategies([
        ['console', new ConsoleLoggerStrategy()],
        ['file', new FileLoggerStrategy('log.txt')]
    ]);

    BasaltLogger.log('console strategy', ['console']);
    BasaltLogger.log('file strategy', ['file']);
    BasaltLogger.log('console and file strategy', ['console', 'file']);
    BasaltLogger.log('all strategies');
    ```

<!-- termynal -->

```bash
$ node example.js
[2023-11-21 00:00:00] LOG : console strategy
[2023-11-21 00:00:00] LOG : console and file strategy
[2023-11-21 00:00:00] LOG : all strategies
$ cat log.txt
[2023-11-21 00:00:00] LOG : file strategy
[2023-11-21 00:00:00 LOG : console and file strategy
[2023-11-21 00:00:00 LOG : all strategies
```
