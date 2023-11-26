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
        public log(level: LogLevels, message: string): void {
            appendFileSync('./test.log', `${level}: ${message}\n`);
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
        log(level, message) {
            appendFileSync('./test.log', `${level}: ${message}\n`);
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
[2023-11-24 10:58:23] LOG : console and file strategy
[2023-11-24 10:58:23] LOG : all strategies
```
