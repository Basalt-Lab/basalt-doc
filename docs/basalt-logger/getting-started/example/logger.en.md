## **Adding a Log Strategy**

=== "TypeScript"

    ```typescript
    import { BasaltLogger } from './BasaltLogger';
    import { ConsoleLoggerStrategy } from '@/Strategies';
    
    BasaltLogger.addStrategy(new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    ```

=== "JavaScript"
    
    ```javascript
    const { BasaltLogger } = require('./BasaltLogger');
    const { ConsoleLoggerStrategy } = require('@/Strategies');

    BasaltLogger.addStrategy(new ConsoleLoggerStrategy());
    BasaltLogger.log('hello world');
    ```

<!-- termynal -->

```bash
$ node example.js
[2023-11-20 18:46:20] LOG : hello world
```

## **Removing a Specific Log Strategy**

=== "TypeScript"

    ```typescript
    import { BasaltLogger } from './BasaltLogger';
    import { ConsoleLoggerStrategy } from '@/Strategies';
    
    const consoleStrategy = new ConsoleLoggerStrategy();
    
    BasaltLogger.addStrategy(consoleStrategy);
    BasaltLogger.removeStrategy(consoleStrategy);
    ```

=== "JavaScript"

    ```javascript
    const { BasaltLogger } = require('./BasaltLogger');
    const { ConsoleLoggerStrategy } = require('@/Strategies');

    const consoleStrategy = new ConsoleLoggerStrategy();

    BasaltLogger.addStrategy(consoleStrategy);
    BasaltLogger.removeStrategy(consoleStrategy);
    ```

## **Removing All Log Strategies**

=== "TypeScript"

    ```typescript
    import { BasaltLogger } from './BasaltLogger';
    import { ConsoleLoggerStrategy } from '@/Strategies';
    
    const consoleStrategy = new ConsoleLoggerStrategy();
    
    BasaltLogger.addStrategy(consoleStrategy);
    BasaltLogger.clearStrategies();
    ```

=== "JavaScript"

    ```javascript
    const { BasaltLogger } = require('./BasaltLogger');
    const { ConsoleLoggerStrategy } = require('@/Strategies');

    const consoleStrategy = new ConsoleLoggerStrategy();

    BasaltLogger.addStrategy(consoleStrategy);
    BasaltLogger.clearStrategies();
    ```

## **Creating a Log Strategy**

=== "TypeScript"

    ```typescript
    import { appendFileSync } from 'fs';
    
    import { BasaltLogger } from './BasaltLogger';
    import { ILoggerStrategy } from '@/Interfaces';
    import { LogLevels } from '@/Enums';
    
    class FileLoggerStrategy implements ILoggerStrategy {
        public log(level: LogLevels, message: string, object?: unknown): void {
            appendFileSync('./test.log', `${level}: ${message}\n`);
        }
    }
    
    BasaltLogger.addStrategy(new FileLoggerStrategy());
    BasaltLogger.log('hello world');
    ```

=== "JavaScript"

    ```javascript
    const { appendFileSync } = require('fs');

    const { BasaltLogger } = require('./BasaltLogger');
    const { LogLevels } = require('@/Enums');
    
    class FileLoggerStrategy {
        log(level, message, object) {
            appendFileSync('./test.log', `${level}: ${message}\n`);
        }
    }

    BasaltLogger.addStrategy(new FileLoggerStrategy());
    BasaltLogger.log('hello world');
    ```

<!-- termynal -->

```bash
$ node example.js
$ cat test.log
[2023-11-21 20:24:00] LOG : hello world
```

## **Adding Multiple Log Strategies**


=== "TypeScript"

    ```typescript
    import { appendFileSync } from 'fs';
    
    import { BasaltLogger } from './BasaltLogger';
    import { ConsoleLoggerStrategy } from '@/Strategies';
    import { ILoggerStrategy } from '@/Interfaces';
    import { LogLevels } from '@/Enums';
    
    class FileLoggerStrategy implements ILoggerStrategy {
        public log(level: LogLevels, message: string, object?: unknown): void {
            appendFileSync('./test.log', `${level}: ${message}\n`);
        }
    }
    
    BasaltLogger.addStrategies([
        new ConsoleLoggerStrategy(),
        new FileLoggerStrategy(),
    ]);
    
    BasaltLogger.log('hello world');
    ```

=== "JavaScript"

    ```javascript
    const { appendFileSync } = require('fs');

    const { BasaltLogger } = require('./BasaltLogger');
    const { ConsoleLoggerStrategy } = require('@/Strategies');
    const { LogLevels } = require('@/Enums');
    
    class FileLoggerStrategy {
        log(level, message, object) {
            appendFileSync('./test.log', `${level}: ${message}\n`);
        }
    }

    BasaltLogger.addStrategies([
        new ConsoleLoggerStrategy(),
        new FileLoggerStrategy(),
    ]);

    BasaltLogger.log('hello world');
    ```

<!-- termynal -->

```bash
$ node example.js
[2023-11-21 20:27:06] LOG : hello world
$ cat test.log
[2023-11-21 20:24:00] LOG : hello world
```

## **All Log Levels**

=== "TypeScript"

    ```typescript
    import { BasaltLogger } from './BasaltLogger';
    import { ConsoleLoggerStrategy } from '@/Strategies';
    
    BasaltLogger.addStrategy(new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    BasaltLogger.info('hello world');
    BasaltLogger.debug('hello world');
    BasaltLogger.warn('hello world');
    BasaltLogger.error('hello world');
    ```
=== "JavaScript"
    
    ```javascript
    const { BasaltLogger } = require('./BasaltLogger');
    const { ConsoleLoggerStrategy } = require('@/Strategies');
    
    BasaltLogger.addStrategy(new ConsoleLoggerStrategy());
    
    BasaltLogger.log('hello world');
    BasaltLogger.info('hello world');
    BasaltLogger.debug('hello world');
    BasaltLogger.warn('hello world');
    BasaltLogger.error('hello world');
    ```
<!-- termynal -->

```bash
$ node example.js
[2023-11-20 18:49:47] LOG : hello world
[2023-11-20 18:49:47] INFO : hello world
[2023-11-20 18:49:47] DEBUG : hello world
[2023-11-20 18:49:47] WARN : hello world
[2023-11-20 18:49:47] ERROR : hello world
```
