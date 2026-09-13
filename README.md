# FastAPI Blog

A small blogging application built with **FastAPI** and **SQLAlchemy (async)**. It serves a server-rendered site (Jinja2 templates) for browsing posts, alongside a JSON REST API for managing users and posts.

## Features

- Server-rendered pages: home/post list, single post view, and per-user post listings
- REST API for `users` and `posts` (create, read, update, delete)
- Async SQLAlchemy ORM backed by SQLite (`aiosqlite`)
- Request/response validation via Pydantic schemas
- Custom error pages for HTML routes, JSON error responses for `/api/*` routes
- User avatars served from `/media`, static assets (CSS/JS/icons) served from `/static`

## Tech Stack

- [FastAPI](https://fastapi.tiangolo.com/)
- [SQLAlchemy 2.0](https://www.sqlalchemy.org/) (async engine)
- [SQLite](https://www.sqlite.org/) via `aiosqlite`
- [Jinja2](https://jinja.palletsprojects.com/) templates
- [Pydantic](https://docs.pydantic.dev/) for schema validation
- [Uvicorn](https://www.uvicorn.org/) ASGI server

## Getting Started

### Prerequisites

- Python 3.11+

### Installation

```bash
git clone https://github.com/Eduardo-Lucas/fastapi_blog.git
cd fastapi_blog

python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate

pip install -r requirements.txt
```

### Running the app

```bash
uvicorn main:app --reload
```

The app will be available at `http://127.0.0.1:8000`.

- Web UI: `http://127.0.0.1:8000/`
- Interactive API docs (Swagger UI): `http://127.0.0.1:8000/docs`
- Alternative API docs (ReDoc): `http://127.0.0.1:8000/redoc`

A SQLite database file (`blog.db`) is created automatically on startup if it doesn't already exist.

## Project Structure

```
.
├── main.py           # FastAPI app, routes, and exception handlers
├── models.py          # SQLAlchemy ORM models (User, Post)
├── schemas.py          # Pydantic request/response schemas
├── database.py         # Async engine/session setup
├── templates/          # Jinja2 templates for the server-rendered pages
├── static/            # CSS, JS, icons, and default assets
└── media/             # User-uploaded content (e.g. profile pictures)
```

## API Overview

| Method | Endpoint                     | Description                     |
|--------|-------------------------------|----------------------------------|
| POST   | `/api/users`                  | Create a new user                |
| GET    | `/api/users/{user_id}`        | Get a user by ID                 |
| GET    | `/api/users/{user_id}/posts`  | List a user's posts              |
| PATCH  | `/api/users/{user_id}`        | Update a user                    |
| DELETE | `/api/users/{user_id}`        | Delete a user                    |
| GET    | `/api/posts`                  | List all posts                   |
| POST   | `/api/posts`                  | Create a new post                |
| GET    | `/api/posts/{post_id}`        | Get a post by ID                 |
| PUT    | `/api/posts/{post_id}`        | Replace a post                   |
| PATCH  | `/api/posts/{post_id}`        | Partially update a post          |
| DELETE | `/api/posts/{post_id}`        | Delete a post                    |

Full request/response schemas are available at `/docs` once the app is running.

## Web Routes

| Route                     | Description                  |
|----------------------------|-------------------------------|
| `/`, `/posts`              | Home page — list of all posts |
| `/posts/{post_id}`         | Single post view              |
| `/users/{user_id}/posts`   | Posts by a specific user      |

## License

This project currently has no license specified.
