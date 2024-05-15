```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a note and clicks the save button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note right of server: Server processes the new note and updates the data store
    server-->>browser: { "message": "note created" }
    deactivate server

    Note right of browser: Browser updates the notes view without reloading the page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, { "content": "New note", "date": "2024-5-15" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the updated notes in the SPA
