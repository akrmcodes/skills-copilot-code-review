# Copilot Instructions - Mergington High School Activities API

## Project Overview

This is a **FastAPI + MongoDB web application** for managing extracurricular activities at Mergington High School. It provides an API for viewing and signing up for activities, with a responsive frontend for student interaction.

- **Backend**: Python FastAPI with MongoDB
- **Frontend**: HTML, CSS, JavaScript
- **Database**: MongoDB (local instance on port 27017)
- **Run command**: `python src/app.py` from workspace root, then visit http://localhost:8000

## Quick Start

1. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

2. **Ensure MongoDB is running**:
   ```bash
   # MongoDB must be accessible at mongodb://localhost:27017/
   ```

3. **Run the application**:
   ```bash
   python src/app.py
   ```
   - API docs: http://localhost:8000/docs
   - App: http://localhost:8000

## Architecture

### Directory Structure
```
src/
├── app.py                 # Main FastAPI application
├── backend/
│   ├── database.py       # MongoDB connections and utilities
│   └── routers/
│       ├── activities.py # Activity endpoints
│       └── auth.py       # Authentication endpoints
└── static/               # Frontend (HTML, CSS, JS)
```

### Key Components

- **FastAPI App** (`app.py`): Initializes the API, mounts static files, includes routers
- **Database** (`database.py`): MongoDB config, sample data initialization, password hashing with Argon2
- **Routers** (`routers/`): RESTful endpoints organized by feature (activities, auth)
- **Frontend**: Single-page app with filters, search, and user authentication

## Domain-Specific Guidelines

This workspace uses focused instruction files for different areas:

- **Backend Development** → [backend.instructions.md](./instructions/backend.instructions.md)
  - API endpoint organization
  - Database integration patterns
  - Error handling and logging
  - Documentation requirements

- **Frontend Development** → [frontend.instructions.md](./instructions/frontend.instructions.md)
  - Accessibility standards
  - Responsive design principles
  - HTML semantic structure

## Common Conventions & Patterns

### Backend Patterns
- **Routers**: All API endpoints in `backend/routers/*/`
- **Database**: MongoDB collections accessed via `activities_collection`, `teachers_collection`
- **Sample Data**: Initialized in `database.py` if collections are empty
- **Password Security**: Use `hash_password()` and `verify_password()` from database module
- **Response Format**: Endpoints return dictionaries; use `response_model` type hints

### Frontend Patterns
- **Static Files**: Served from `src/static/` at `/static` path
- **User State**: Managed via `user-controls` and `user-info` elements
- **API Calls**: Fetch from `/activities` and `/auth/` endpoints
- **Styling**: CSS in `styles.css`, responsive design for mobile

## Critical Reminders

⚠️ **Backend-Frontend Integration**
- Any changes to API structure or response format must be reflected in frontend
- Monitor breaking changes between backend and frontend code
- Test endpoints before integration

⚠️ **Database Requirements**
- MongoDB must be running locally on port 27017
- Sample data auto-initializes on first run
- Activities use name as `_id`, teachers use username as `_id`

⚠️ **Security**
- Use Argon2 for all password operations (never plaintext)
- Validate and sanitize all user inputs
- Avoid hardcoding sensitive data—use environment variables
- Log errors on server, don't propagate details to frontend

⚠️ **Error Handling**
- Backend: Log errors appropriately
- Frontend: Handle API errors gracefully without exposing implementation details

## Development Workflow

1. **Code Quality First**: See [pilot-instructions.md](./pilot-instructions.md) for code quality standards
2. **Consistency**: Follow naming conventions and patterns established in existing code
3. **Documentation**: API endpoints should be self-documenting via docstrings
4. **Testing**: Verify changes locally before submitting (use FastAPI's automatic docs to test endpoints)

## Useful References

- [Source Code README](../src/README.md) — API endpoints and data models
- [FastAPI Docs](https://fastapi.tiangolo.com/) — Framework reference
- [MongoDB Python Driver](https://pymongo.readthedocs.io/) — Database operations
