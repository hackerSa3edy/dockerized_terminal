# Flask Docker Terminal with JWT Authentication

This is a Flask application that provides a web-based terminal interface to Docker containers. It uses Flask-SocketIO for real-time communication between the client and server, Flask-JWT-Extended for handling JSON Web Tokens (JWTs) and Docker for creating and managing containers.

## Features

- User authentication with JWTs
- Real-time terminal interface to Docker containers
- Terminal sessions are isolated per user and role
- Terminal sessions are automatically cleaned up when the user disconnects

## Installation

1. Clone the repository:

```bash
git clone https://github.com/hackerSa3edy/dockerized_terminal.git
cd dockerized_terminal
```

2. Install the dependencies:

```bash
pip install -r requirements.txt
```

3. Run the application:

```bash
# In development environment
python app.py

# In production environment
gunicorn --worker-class eventlet -w 1 app:app --bind 0.0.0.0:5000
```

The application will be available at `http://localhost:5000`.

## Usage

The application provides several routes and socket events:

- `@app.route('/')`: The main route. Requires JWT authentication.
- `@socketio.on('connect')`: Handles a new client connection. Requires JWT authentication.
- `@socketio.on('disconnect')`: Handles a client disconnection. Requires JWT authentication and stops the Docker container associated with the user.
- `@socketio.on('start_terminal')`: Starts a new terminal session. Requires JWT authentication and starts a new Docker container.
- `@socketio.on('input')`: Handles input from the client to the terminal. Requires JWT authentication and sends the input to the Docker container.

## Dependencies

- Flask
- Flask-SocketIO
- Flask-JWT-Extended
- Docker
