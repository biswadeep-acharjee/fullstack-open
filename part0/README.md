# Part 0 Exercises

## Exercise 0.4: New note diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser,server: User writes a note and clicks Save
    browser->>server: POST [https://studies.cs.helsinki.fi/exampleapp/new_note](https://studies.cs.helsinki.fi/exampleapp/new_note)
    activate server
    Note over server: Server creates a new note object and pushes it to notes array
    server-->>browser: HTTP 302 Redirect (Location: /notes)
    deactivate server

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/notes](https://studies.cs.helsinki.fi/exampleapp/notes)
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/main.css](https://studies.cs.helsinki.fi/exampleapp/main.css)
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/main.js](https://studies.cs.helsinki.fi/exampleapp/main.js)
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET [https://studies.cs.helsinki.fi/exampleapp/data.json](https://studies.cs.helsinki.fi/exampleapp/data.json)
    activate server
    server-->>browser: [{"content": "hi", "date": "2026-11-01T13:20:28.678Z"}, {"content": "test", "date": "2026-11-01T14:01:47.000Z"}, {"content": "new", "date": "2026-11-01T14:17:45.217Z"}, {"content": "assignment", "date": "2026-11-01T14:18:10.608Z"}, {"content": "assignment", "date": "2026-11-01T14:18:42.399Z"}]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes to the DOM
