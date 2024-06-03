# Real-time Terminal Emulation with Flask and Socket.IO

This application is a real-time terminal emulator that uses Flask and Socket.IO to execute shell commands received from the client and send the output back to the client.

## Dependencies

- `flask`: A lightweight WSGI web application framework.
- `flask_socketio`: Flask-SocketIO gives Flask applications access to low latency bi-directional communications between the clients and the server.
- `uuid`: The uuid module provides immutable UUID objects (the UUID class) and the functions uuid1(), uuid3(), uuid4(), uuid5() for generating version 1, 3, 4, and 5 UUIDs as specified in RFC 4122.

## How it works

The application creates a Flask server and a Socket.IO server. When a client connects and sends a 'message' event, the server executes the command received from the client. The output of the command is then sent back to the client as a 'response' event.

## How to run

1. Install Python and pip if you haven't done so already. You can download them from [here](https://www.python.org/downloads/).

2. Clone this repository to your local machine.

    ```bash
    git clone <repository-url>
    ```

3. Navigate to the project directory.

    ```bash
    cd <project-directory>
    ```

4. Install the dependencies.

    ```bash
    pip install flask flask_socketio uuid
    ```

5. Start the server.

    ```bash
    python app.py
    ```

The server will start running on port 5000. You can connect to it using a Socket.IO client and send 'message' events with the command you want to execute.

## Security Note

Running commands received from the client can be very dangerous if not properly sanitized, as it can lead to arbitrary command execution. Be sure to validate and sanitize any input received from the client before running it as a command.
