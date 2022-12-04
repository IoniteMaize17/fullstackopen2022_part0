```mermaid
sequenceDiagram
loop
actor A
browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
server-->>browser: HTML - Code
browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
server-->>browser: main.css
browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.js
server->>browser: main.js

note over browser: browser starts executing js-code <br>that requests JSON data from server 


browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
server-->>browser: [{"content":"Carbon copy","date":"2022-12-03T15:48:46.908Z"}, ...]

note over browser: browser executes the event handler <br>that renders notes to display


A->>browser: writing input field
note over browser: browser waiting for click on submit button

browser->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
server-->>browser: status code 302: redirect location: /exampleapp/notes
end
```
