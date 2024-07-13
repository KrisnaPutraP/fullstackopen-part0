```mermaid

sequenceDiagram
    participant User
    participant Browser
    participant Server

    User->>Browser: User writes note and click Save
    Browser->>Browser: Prevent default form submission
    Browser->>Browser: Create new note and add to notes list
    Browser->>Browser: Render note list on page
    Note right of Server: Server recieves the new note data and saves it
    Browser->>Server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate Server
    Server-->>Browser: Respond with status 201 (note created)
    deactivate Server
    Note right of Browser: The Browser updates the list without reloading the page