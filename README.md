# WebSocket Echo Server and Client

This project is a WebSocket-based echo server and client implementation in Go, demonstrating basic WebSocket usage with the `gorilla/websocket` library.

The server echoes any message it receives back to the client, allowing you to test and understand WebSocket communications. The server and client communicate over WebSockets using `ws://localhost:8700/echo`.

## Project Structure

```
.
├── server/
│   └── server.go        # WebSocket server code
└── client/
    └── client.go        # WebSocket client code
```

## Prerequisites

- Go 1.15 or higher
- The `gorilla/websocket` package

To install the `gorilla/websocket` package, use:

```bash
go get -u github.com/gorilla/websocket
```

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/imkiptoo/web-sockets-echo.git
   cd web-sockets-echo
   ```

2. **Run the Server:**

   In one terminal window, navigate to the `server/` directory and run:

   ```bash
   go run server.go -addr="localhost:8700"
   ```

   This starts a WebSocket server listening on `localhost:8700`.

3. **Run the Client:**

   In another terminal window, navigate to the `client/` directory and run:

   ```bash
   go run client.go -addr="localhost:8700"
   ```

   The client will establish a WebSocket connection to the server and begin sending timestamped messages.

## Server Details

The server is set up to:
- Listen on `localhost:8700`.
- Serve an HTML page with JavaScript that opens a WebSocket connection to the server.
- Echo messages back to the client.

The WebSocket server endpoint is available at `ws://localhost:8700/echo`. You can interact with this endpoint through the HTML interface by:
1. Opening a WebSocket connection.
2. Sending a message.
3. Viewing the echoed response.

### Key Functions

- **`echo(w http.ResponseWriter, r *http.Request)`**: Handles WebSocket upgrades and echoes messages.
- **`home(w http.ResponseWriter, r *http.Request)`**: Serves the HTML interface for testing WebSocket interactions.

## Client Details

The client connects to the server at `localhost:8700` and:
- Sends timestamped messages to the server.
- Prints received messages to the console.
- Handles connection termination on interrupt signals (e.g., `Ctrl+C`).

### Key Functions

- **`main()`**: Connects to the server, listens for incoming messages, and sends periodic timestamped messages.

## Example Usage

1. Open the HTML page served by the server in a web browser.
2. Use the interface to open a WebSocket connection, send messages, and view responses.

Alternatively, use the Go client to see messages printed directly in the terminal.

## License

This project uses a BSD-style license. See the `LICENSE` file for details.