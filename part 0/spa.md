```mermaid
sequenceDiagram
    participant browser
    participant spa_server
    participant api_server
    participant database

    browser->>spa_server: Access https://studies.cs.helsinki.fi/exampleapp/spa
    activate spa_server

    spa_server->>browser: HTML document (SPA)
    deactivate spa_server

    Note right of browser: The SPA is loaded, and the user interacts with it

    browser->>api_server: API Request for Notes Data
    activate api_server

    api_server-->>database: Retrieve Notes Data
    activate database
    database-->>api_server: Notes Data
    deactivate database

    api_server-->>browser: Notes Data
    deactivate api_server

    Note right of browser: The SPA dynamically updates the UI using the Notes Data
```
