## **Référence de la classe BasaltLogger**

`BasaltLogger` est un système de journalisation flexible non bloquant, qui permet plusieurs stratégies pour la sortie des logs.

## **Diagramme**

```mermaid
classDiagram
    class BasaltLogger {
        -_strategies Map<string, ILoggerStrategy>
        -_logStream Writable
        +get strategies() Map<string, ILoggerStrategy>
        +addStrategy(name: string, strategy: ILoggerStrategy) void
        +addStrategies(strategies: [string, ILoggerStrategy][]) void
        +removeStrategy(name: string) void
        +removeStrategies(names: string[]) void
        +clearStrategies() void
        +error(object: unknown, strategiesNames?: string[]) void
        +warn(object: unknown, strategiesNames?: string[]) void
        +info(object: unknown, strategiesNames?: string[]) void
        +debug(object: unknown, strategiesNames?: string[]) void
        +log(object: unknown, strategiesNames?: string[]) void
        -executeStrategies(level: LogLevels, prefixDate: string, object: unknown, strategiesNames: string[]) void
        -out(level: LogLevels, object: unknown, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]) void
    }
```

## **Méthodes publiques**

Ci-dessous, vous trouverez les détails techniques de chaque méthode publique disponible.

### `get strategies`

???+ info "get strategies"

    - **Description** : Retourne les stratégies de journalisation.
    - **Signature** : `public static get strategies(): Map<string, ILoggerStrategy>`

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
        - `object` : L'objet à enregistrer.
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
        - `object` : L'objet à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

### `warn`

???+ info "warn"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static warn(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `object` : L'objet à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

### `error`

???+ info "error"

    - **Description** : Méthodes pour enregistrer des messages de différents niveaux de gravité.
    - **Signature** : `public static error(message: string, strategiesNames: string[] = [...BasaltLogger._strategies.keys()]): void`
    - **Paramètres** :
        - `object` : L'objet à enregistrer.
        - `strategiesNames` : Les noms des stratégies à utiliser.
    - **Exceptions** : Lance une erreur `BasaltLoggerError` si aucune stratégie n'est ajoutée.

