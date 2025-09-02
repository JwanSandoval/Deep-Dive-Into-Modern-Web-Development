```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: Get https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document

    Note right of browser: To reduce Diagram initial css, js and json calls were skipped

    Note right of browser:Browser starts executing javascript to send Json from form fields(Content,Date)
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa 
    activate server
    server-->>browser: StatusCode:201 Json:{"message":"note created"}

    Note right of browser:Browser stays on the same page, and it sends no further HTTP requests
