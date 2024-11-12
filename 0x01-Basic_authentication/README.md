
# Basic Authentication

A simple HTTP API for handling user data and implementing Basic Authentication.

## Files

### `models/`

- `base.py`: Base for all models in the API, handles serialization to file.
- `user.py`: User model that defines user attributes and methods.

### `api/v1/`

- `app.py`: Entry point for the API, initializes Flask app and routes.
- `auth/auth.py`: Defines the `Auth` class, the base authentication manager.
- `auth/basic_auth.py`: Defines the `BasicAuth` class, extending `Auth` for Basic Authentication.
- `views/index.py`: Basic endpoints of the API: `/status`, `/unauthorized`, and `/forbidden`.
- `views/users.py`: Endpoints to manage users in the API.

## Setup

To install the required dependencies, run:

    ```bash
    $ pip2 install -r requirements.txt
    ```

### Requirements

- Python 3.7
- Flask 1.1.2
- Flask-Cors 3.0.8
- Additional libraries listed in `requirements.txt`

## Run

Start the API by setting environment variables for the host and port:

    ```bash
    $ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
    ```

## Routes

- `GET /api/v1/status`: Returns the status of the API.
- `GET /api/v1/unauthorized`: Simulates a 401 Unauthorized error.
- `GET /api/v1/forbidden`: Simulates a 403 Forbidden error.
- `GET /api/v1/users`: Returns the list of users.
- `GET /api/v1/users/:id`: Retrieves a user by their ID.
- `DELETE /api/v1/users/:id`: Deletes a user based on the ID.
- `POST /api/v1/users`: Creates a new user. JSON parameters: `email`, `password`, `last_name` (optional), and `first_name` (optional).
- `PUT /api/v1/users/:id`: Updates an existing user. JSON parameters: `last_name` and `first_name`.

## Authentication

The API implements Basic Authentication using the `Authorization` header with a Base64 encoded `username:password` format. It includes custom error handling for unauthorized and forbidden access scenarios.