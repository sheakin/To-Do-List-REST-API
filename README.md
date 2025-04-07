# Django To-Do List REST API

A simple RESTful API for managing to-do items built with Django and Django REST Framework.

## Features

- Create, read, update, and delete to-do items
- Full REST API implementation
- Input validation and error handling
- Pagination support
- SQLite database (default Django configuration)

## Requirements

- Python 3.x
- Django
- Django REST Framework

## Installation

1. Clone the repository:

```bash
git clone <your-repository-url>
cd todolistapi
```

2. Create and activate a virtual environment:

```bash
python -m venv env
source env/bin/activate  # On Windows: env\Scripts\activate
```

3. Install dependencies:

```bash
pip install django djangorestframework
```

4. Run migrations:

```bash
python manage.py migrate
```

5. Start the development server:

```bash
python manage.py runserver
```

The API will be available at `http://127.0.0.1:8000/api/`

## API Endpoints

### Create To-Do Item

- **POST** `/api/todos/`
- Required fields: `title` (max 100 characters)
- Optional fields: `description` (max 500 characters), `completed` (boolean)
- Returns: 201 Created

Example request:

```bash
curl -X POST http://127.0.0.1:8000/api/todos/ \
-H "Content-Type: application/json" \
-d '{"title": "My first todo", "description": "This is a test todo", "completed": false}'
```

### List All To-Do Items

- **GET** `/api/todos/`
- Returns: 200 OK
- Paginated response (10 items per page)

Example request:

```bash
curl http://127.0.0.1:8000/api/todos/
```

### Get To-Do Item Details

- **GET** `/api/todos/<id>/`
- Returns: 200 OK or 404 Not Found

Example request:

```bash
curl http://127.0.0.1:8000/api/todos/1/
```

### Update To-Do Item

- **PUT** `/api/todos/<id>/`
- Returns: 200 OK or 404 Not Found

Example request:

```bash
curl -X PUT http://127.0.0.1:8000/api/todos/1/ \
-H "Content-Type: application/json" \
-d '{"title": "Updated title", "completed": true}'
```

### Delete To-Do Item

- **DELETE** `/api/todos/<id>/`
- Returns: 204 No Content or 404 Not Found

Example request:

```bash
curl -X DELETE http://127.0.0.1:8000/api/todos/1/
```

## Error Handling

The API returns appropriate HTTP status codes:

- 201: Created (successful POST)
- 200: OK (successful GET/PUT)
- 204: No Content (successful DELETE)
- 400: Bad Request (validation error)
- 404: Not Found (resource doesn't exist)

## Project Structure

```
todolistapi/
├── manage.py
├── todolistapi/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
└── todos/
    ├── __init__.py
    ├── admin.py
    ├── apps.py
    ├── models.py
    ├── serializers.py
    ├── urls.py
    └── views.py
```

## License

This project is open source and available under the MIT License.
