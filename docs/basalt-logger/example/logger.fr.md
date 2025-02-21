## **BasaltLogger**

`BasaltLogger` est une classe qui vous permettra d'enregistrer des stratégies de log pour votre application ainsi de loguer des messages.

??? example "Ajout d'une strategie de log"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy } from '@basalt-lab/basalt-logger';

    const logger = new BasaltLogger();

    logger.registerStrategy('console', new ConsoleLoggerStrategy());
    
    logger.log('hello world');
    ```

    <!-- termynal -->

    ```bash
    $ node example.js
    [2023-11-21 00:00:00] LOG : hello world
    ```

??? example "Suppression d'une strategie specifique de log"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy } from '@basalt-lab/basalt-logger';

    const logger = new BasaltLogger();

    logger.registerStrategy('console', new ConsoleLoggerStrategy());

    logger.unregisterStrategy('console');
    ```

    <!-- termynal -->

    ```bash
    $ node example.js
    ```


??? example "Suppression de toutes les strategies de log"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy } from '@basalt-lab/basalt-logger';
    
    const logger = new BasaltLogger();

    logger.registerStrategy('console', new ConsoleLoggerStrategy());
    
    logger.clearStrategies();
    ```

    <!-- termynal -->

    ```bash
    $ node example.js
    ```



??? example "Création d'une strategie de log"

    ```typescript
    import { appendFile } from 'fs/promises';
    import { BasaltLogger, LoggerStrategy, LogLevels}  from '@basalt-lab/basalt-logger';
    
    class FileLoggerStrategy implements LoggerStrategy {
            public log(level: LogLevels, date: Date, object: unknown): void {
            const prefixDate = `[${date.toISOString().replace(/T/, ' ').replace(/\..+/, '')}]`;
            const sanitizedObject: string = typeof object === 'string' ? object : JSON.stringify(object);
            const message = `${prefixDate} ${level} : ${sanitizedObject}`;
            await appendFile(this._path, `${message}\n`);
        }
    }

    const logger = new BasaltLogger();

    logger.registerStrategy('file', new FileLoggerStrategy());
    logger.log('Hello World');
    ```

    <!-- termynal -->

    ```bash
    $ node example.js
    $ cat test.log
    [2023-11-21 00:00:00] LOG : Hello World
    ```

??? example "Ajout de plusieurs strategies de log"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy, FileLoggerStrategy}  from '@basalt-lab/basalt-logger';
    
    const logger = new BasaltLogger();

    logger.registerStrategies([
        ['console', new ConsoleLoggerStrategy()],
        ['file', new FileLoggerStrategy('log.txt')]
    ]);
    
    logger.log('Hello World');
    ```

    <!-- termynal -->

    ```bash
    $ node example.js
    [2023-11-21 00:00:00] LOG : Hello World
    $ cat log.txt
    [2023-11-21 00:00:00] LOG : Hello World
    ```

??? example "Tout les niveaux de log"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy }  from '@basalt-lab/basalt-logger';
    
    const logger = new BasaltLogger();

    logger.registerStrategy('console', new ConsoleLoggerStrategy());
    
    logger.log('hello world');
    logger.info('hello world');
    logger.debug('hello world');
    logger.warn('hello world');
    logger.error('hello world');
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

??? example "Log sur une strategie specifique"

    ```typescript
    import { BasaltLogger, ConsoleLoggerStrategy, FileLoggerStrategy}  from '@basalt-lab/basalt-logger';
    
    const logger = new BasaltLogger();

    logger.registerStrategies([
        ['console', new ConsoleLoggerStrategy()],
        ['file', new FileLoggerStrategy('log.txt')]
    ]);
    
    logger.log('console strategy', ['console']);
    logger.log('file strategy', ['file']);
    logger.log('console and file strategy', ['console', 'file']);
    logger.log('all strategies');
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
