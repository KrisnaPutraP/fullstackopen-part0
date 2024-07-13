
```mermaid

sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: Write a new note and click "Save" button
    Note right of User: The browser captures the user's input and prepares to send it to the server

    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate Server
    Server-->>Browser: Tell to GET https://studies.cs.helsinki.fi/exampleapp/notes
    deactivate Server

    Note right of Browser: The data is sent via POST, then the server-side app saves the data to JSON. Finally, the server-side app redirects the browser to GET /notes page

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate Server
    Server-->>Browser: HTML document
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate Server
    Server-->>Browser: CSS file
    deactivate Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate Server
    Server-->>Browser: JavaScript file
    deactivate Server

    Note right of Browser: The browser starts executing the JavaScript code that fetches the JSON from the Server

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate Server
    Server-->>Browser: [{"content":"tes","date":"2024-07-12T06:36:48.205Z"},...]
    deactivate Server

    Note right of Browser: The browser executes the callback function that renders the notes