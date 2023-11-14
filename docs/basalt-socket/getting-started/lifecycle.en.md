## **Basalt Socket Connection Lifecycle**

Understanding the lifecycle of socket connections in **Basalt Socket** is essential for effectively managing real-time communication.
Here's an overview of the key stages from the initiation of a connection to its closure.

## **Lifecycle Diagram**

### **Connection Lifecycle Diagram**

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
This is the initial state where an incoming connection request is intercepted. It allows the server to handle pre-upgrade logic that's applicable to all events.

`EVENT_onUpgradeHook`:
Following the global hook, this event-specific onUpgrade hook is invoked. It allows for custom logic before the socket connection is fully established.

`GLOBAL_onConnectHook`:
At this point, the server performs global actions required upon establishing a new connection. This can be used to set up global state or perform logging.

`EVENT_onConnectHook`:
Similar to the onUpgrade hook, the onConnect hook at the event level allows for handling connection logic for specific events or routes.

<br/>

<br/>

<br/>

### **Message Lifecycle Diagram**

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
Before processing the received message, the server triggers this global hook, which can be used to manage tasks such as authentication or logging for all messages.

`EVENT_onReceivedHook`:
The reception hook for specific events is then called, providing an opportunity to process the message in the context of its intended event.

`EVENT_preHandler`:
This pre-handler can be used as middleware to process or modify the message before it reaches the final event handler.

`EVENT_handler`:
The main logic for handling a message for a particular event is executed here. This is typically where the core functionality of your application will reside.

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
### **Disconnection Lifecycle Diagram**

!!! Quote inline end ""

    ```mermaid
    stateDiagram-v2
        [*] --> GLOBAL_onDisconnectHook
        GLOBAL_onDisconnectHook --> EVENT_onDisconnectHook
        EVENT_onDisconnectHook --> [*]
    ```

`GLOBAL_onDisconnectHook`:
When a connection is about to close, the server first goes through the global disconnection logic, which could handle tasks such as cleanup or logging.

`EVENT_onDisconnectHook`:
Lastly, any event-specific disconnection logic is processed, which could be useful for releasing resources tied to a specific event.


<br/>

<br/>

<br/>

The connection lifecycle with **Basalt Socket** is designed to provide hooks at both the global and event levels, giving you the flexibility to embed custom logic at different stages of the socket connection lifecycle.
