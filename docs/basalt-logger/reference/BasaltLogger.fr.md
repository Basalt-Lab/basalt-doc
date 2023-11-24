## **Référence de la classe BasaltLogger**

`BasaltLogger` est un système de journalisation flexible non bloquant, qui permet plusieurs stratégies pour la sortie des logs.

## **Diagramme**

```mermaid
classDiagram
    class BasaltLogger {
        -_strategies Map~string, ILoggerStrategy~
        -_logStream Writable
        +addStrategy(name, strategy) void
        +addStrategies(strategies) void
        +removeStrategy(name) void
        +removeStrategies(names) void
        +clearStrategies() void
        +error(message, strategiesNames) void
        +warn(message, strategiesNames) void
        +info(message, strategiesNames) void
        +debug(message, strategiesNames) void
        +log(message, strategiesNames) void
        -executeStrategies(level, message, strategiesNames) void
        -formatLogEntry(level, message, strategiesNames) string
        -out(level, message, strategiesNames) void
    }
```

## **Méthodes publiques**

Ci-dessous, vous trouverez les détails techniques de chaque méthode publique disponible.

### `addStrategy`

???+ info "addStrategy"

    - **Description** : Ajoute une stratégie de journalisation.
    - **Signature** :
        - `public static addStrategy(name: string, strategy: ILoggerStrategy): void`
    - **Paramètres** :
        - `name` : Le nom de la stratégie.
        - `strategy` : La stratégie de journalisation à ajouter.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si une stratégie avec le même nom existe déjà.

### `addStrategies`

???+ info "addStrategies"

    - **Description** : Ajoute plusieurs stratégies de journalisation.
    - **Signature** :
        - `public static addStrategies(strategies: [string, ILoggerStrategy][]): void`
    - **Paramètres** :
        - `strategies` : Un tableau de stratégies.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si une stratégie avec le même nom existe déjà.

### `removeStrategy`

???+ info "removeStrategy"

    - **Description** : Supprime une ou plusieurs stratégies de journalisation.
    - **Signature** :
        - `public static removeStrategy(name: string): void`
    - **Paramètres** :
        - `name` : Le nom de la stratégie à supprimer.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si la stratégie n'est pas trouvée.

### `removeStrategies`

???+ info "removeStrategies"

    - **Description** : Supprime une ou plusieurs stratégies de journalisation.
    - **Signature** :
        - `public static removeStrategies(names: string[]): void`
    - **Paramètres** :
        - `names` : Les noms des stratégies à supprimer.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si la stratégie n'est pas trouvée.

### `clearStrategies`

???+ info "clearStrategies"

    - **Description** : Efface toutes les stratégies de journalisation du logger.
    - **Signature** : `public static clearStrategies(): void`

### `log`

???+ info "log"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static log(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `message` : Le message à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

### `info`

???+ info "info"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static info(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `message` : Le message à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

### `debug`

???+ info "debug"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static debug(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `message` : Le message à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

### `warn`

???+ info "warn"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static warn(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `message` : Le message à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

### `error`

???+ info "error"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static error(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `message` : Le message à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

