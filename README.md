# fullstackopen-part-0

# 0.4: New note diagram
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
    server-->>browser: URL Redirect (status code 302 and location '/exampleapp/notes')
    deactivate server

    Note right of browser: The status code 302 indicates a URL redirect.<br>The browser will make a HTTP GET request to the location address ('/exampleapp/notes'). <br>Since the returned address is the same as the current address, <br>the page will be reloaded repeating all the requests done when the page was first loaded

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{content: "@Kane_gonzl", date: "2024-04-27T14:40:07.704Z"},…]
    deactivate server
    
    Note right of browser: The browser executes the callback function that renders the notes
```
# 0.5: Single page app diagram
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    Note right of browser: Same css file retrieved for the example app

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server
    
    Note right of browser: Similarly to what happened with the example app the browser executes the spa.js code that fetches the JSON from the server
    
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{content: "sdad", date: "2024-04-27T14:35:55.839Z"},…]
    deactivate server
    
    Note right of browser: The browser executes the callback function that renders the notes
```
# 0.6: New note in Single page app diagram
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    server-->>browser: {message: "note created"}
    deactivate server
    
    Note right of browser: The browser do a POST request, sending the note text and the date of creation<br>The request is returned with status code 201 created<br>and a message saying that the note was created<br>With that information, the spa.js code will handle the updates on the DOM
```
