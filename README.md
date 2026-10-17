# RestForge - API Testing Client

RestForge is a fast, lightweight, single-file API testing workstation built with vanilla JavaScript and the native Fetch API. It features a modern, dark-zinc interface inspired by the shadcn/ui design system.

---

## Features

- **Standard HTTP Methods**: Full support for GET, POST, PUT, PATCH, and DELETE.
- **Query Parameter Sync**: Automatically parses URL search parameters into a key-value editor, and updates the URL bar in real time as keys and values change.
- **Dynamic Headers and Presets**: Add or remove custom request headers, or load common presets (such as application/json, Bearer Token, and No-Cache).
- **Request Body and Validation**: Dedicated JSON editor with one-click syntax validation and auto-formatting (beautification). Automatically disables body input for GET and DELETE requests.
- **Authentication Modes**: Built-in support for Bearer Token and Basic Auth (base64-encoded credentials).
- **Request Cancellation**: Abort in-flight requests at any time via native AbortController.
- **Response Inspection**:
  - HTTP status badges with standard status code coloring.
  - Round-trip latency calculation in milliseconds.
  - Estimated payload transfer size.
  - Syntax-highlighted collapsible JSON tree view.
  - Raw response view, parsed headers table, and sandboxed HTML preview.
- **Persistent History**: Saves recent requests to browser localStorage for quick re-testing.
- **Export and Copy**: One-click actions to copy formatted payloads or download response files directly.
- **Zero Build Step**: Fully self-contained in a single index.html file. No bundlers, Node.js runtime, or compilation needed.

---

## Running with VS Code Extensions

Running the client over a local HTTP server ensures that request headers (such as the `Origin` header) are correctly formed for local API development and CORS compliance.

### Using Live Server (Extension by Ritwick Dey)

1. Open the Extensions panel in VS Code (`Ctrl + Shift + X` on Windows/Linux, `Cmd + Shift + X` on macOS).
2. Search for **Live Server** and install it.
3. Open the folder containing `index.html`.
4. Right-click `index.html` in the Explorer pane and choose **Open with Live Server**, or click **Go Live** in the status bar at the bottom.
5. The application will launch at `http://127.0.0.1:5500/index.html`.

### Using Live Preview (Official Microsoft Extension)

1. Open the Extensions panel in VS Code (`Ctrl + Shift + X` or `Cmd + Shift + X`).
2. Search for **Live Preview** (by Microsoft) and click Install.
3. Open the project folder.
4. Right-click `index.html` and choose **Live Preview: Show Preview**.
5. The client will open inside an internal VS Code preview tab at `http://127.0.0.1:3000`, with optional pop-out to an external browser window.

---

## Testing Local and Remote APIs

### Understanding CORS

Because RestForge runs directly inside the client browser, all HTTP calls originate from the browser runtime and are governed by the Same-Origin Policy:

- **Browser Security**: The browser blocks access to responses from cross-origin APIs unless the API returns an `Access-Control-Allow-Origin` header matching your origin or `*`.
- **Local Services**: When testing your own local services (such as Express, Flask, FastAPI, or Spring Boot), enable CORS middleware locally:
  - Express: `app.use(require('cors')())`
  - FastAPI: `app.add_middleware(CORSMiddleware, allow_origins=["*"])`
  - Flask: `from flask_cors import CORS; CORS(app)`
- **Public Sandbox APIs**: Pre-configured test URLs like `https://jsonplaceholder.typicode.com/posts/1` work out of the box because they include open CORS headers.

---

## Keyboard Shortcuts

- `Ctrl + Enter` (or `Cmd + Enter`): Send the current request.
- `Escape`: Abort the active request if running.

---

## Technical Stack

- **Markup**: Semantic HTML5.
- **Styling**: Tailwind CSS via CDN with customized dark zinc theme tokens matching shadcn/ui.
- **Icons**: Lucide Icons CDN.
- **Scripting**: Pure Vanilla JavaScript (ES6+ native Fetch API, async/await, DOM APIs).
- **Storage**: Browser localStorage API for historical session persistence.

---

## License

MIT License. Free to use, adapt, and distribute for personal or commercial development.
