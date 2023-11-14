## **Cycle de Vie des Connexions Basalt Socket**

Comprendre le cycle de vie des connexions socket dans **Basalt Socket** est essentiel pour gérer efficacement la communication en temps réel.  
Voici un aperçu des étapes clés, depuis l'initiation d'une connexion jusqu'à sa fermeture.

## **Diagramme de Cycle de Vie**

### **Diagramme de Cycle de Vie des Connexions**

!!! Quote inline end ""
    ```mermaid
    stateDiagram-v2
        [*] --> GLOBAL_onUpgradeHook
        GLOBAL_onUpgradeHook --> EVENT_onUpgradeHook
        EVENT_onUpgradeHook --> GLOBAL_onConnectHook
        GLOBAL_onConnectHook --> EVENT_onConnectHook
        EVENT_onConnectHook --> [*]
    ```

`GLOBAL_onUpgradeHook`:
C'est l'état initial où une demande de connexion entrante est interceptée. Il permet au serveur de gérer la logique préalable à la mise à niveau applicable à tous les événements.

`EVENT_onUpgradeHook`:
Après l'accroche globale, cette accroche de mise à niveau spécifique à l'événement est invoquée. Elle permet une logique personnalisée avant que la connexion socket ne soit complètement établie.

`GLOBAL_onConnectHook`:
À ce stade, le serveur effectue des actions globales nécessaires à l'établissement d'une nouvelle connexion. Cela peut servir à configurer l'état global ou à effectuer des logs.

`EVENT_onConnectHook`:
Similaire à l'accroche de mise à niveau, l'accroche de connexion au niveau de l'événement permet de gérer la logique de connexion pour des événements ou routes spécifiques.

<br/>



### **Diagramme de Cycle de Vie des Messages**

!!! Quote inline end ""

    ```mermaid
    stateDiagram-v2
    [*] --> GLOBAL_onUpgradeHook
    GLOBAL_onUpgradeHook --> EVENT_onUpgradeHook
    EVENT_onUpgradeHook --> GLOBAL_onConnectHook
    GLOBAL_onConnectHook --> EVENT_onConnectHook
    EVENT_onConnectHook --> GLOBAL_onReceivedHook
    GLOBAL_onReceivedHook --> EVENT_onReceivedHook
    EVENT_onReceivedHook --> EVENT_preHandler
    EVENT_preHandler --> EVENT_handler
    EVENT_handler --> GLOBAL_onDisconnectHook
    GLOBAL_onDisconnectHook --> [*]
    ```

`GLOBAL_onReceivedHook`:
Avant de traiter le message reçu, le serveur déclenche cette accroche globale, qui peut être utilisée pour gérer des tâches telles que l'authentification ou les logs pour tous les messages.

`EVENT_onReceivedHook`:
L'accroche de réception pour des événements spécifiques est ensuite appelée, offrant l'opportunité de traiter le message dans le contexte de son événement destiné.

`EVENT_preHandler`:
Ce pré-manipulateur peut être utilisé comme middleware pour traiter ou modifier le message avant qu'il n'atteigne le manipulateur d'événement final.

`EVENT_handler`:
La logique principale pour traiter un message pour un événement particulier est exécutée ici. C'est là que résidera généralement la fonctionnalité principale de votre application.

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>

<br/>
### **Diagramme de Cycle de Vie de Déconnexion**

!!! Quote inline end ""

    ```mermaid
    stateDiagram-v2
        [*] --> GLOBAL_onDisconnectHook
        GLOBAL_onDisconnectHook --> EVENT_onDisconnectHook
        EVENT_onDisconnectHook --> [*]
    ```

`GLOBAL_onDisconnectHook`:
Lorsqu'une connexion est sur le point de se fermer, le serveur passe d'abord par la logique globale de déconnexion, qui pourrait gérer des tâches de nettoyage ou de logs.

`EVENT_onDisconnectHook`:
Enfin, toute logique de déconnexion spécifique à l'événement est traitée, ce qui pourrait être utile pour libérer des ressources liées à un événement spécifique.


<br/>

<br/>

<br/>

Le cycle de vie des connexions avec **Basalt Socket** est conçu pour fournir des accroches tant au niveau global qu'au niveau de l'événement, vous donnant la flexibilité d'incorporer une logique personnalisée à différentes étapes du cycle de vie de la connexion socket.


