```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: Get https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2025-09-02" }, ... ]
    deactivate server

    Note right of browser: User enters new note into text field and click save button

    Note right of browser:Browser starts executing javascript to send Json from form fields(Content,Date)
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa 
    activate server
    server-->>browser: StatusCode:201 Json:{"message":"note created"}

    Note right of browser:Browser stays on the same page, and it sends no further HTTP requests
