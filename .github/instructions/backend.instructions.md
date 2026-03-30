---
applyTo: "backend/**/*,*.py"
---

## Backend Guidelines

### API Organization
- **All endpoints** must be defined in the `routers/` folder (e.g., `routers/activities.py`, `routers/auth.py`)
- Use `APIRouter` with descriptive prefixes and tags
- Include docstrings on all endpoints explaining parameters and return values
- Use FastAPI's `response_model` parameter for type hints

### Database Integration
- Import collections from `database.py`: `from ..database import activities_collection, teachers_collection`
- Sample data auto-initializes in `database.py` via `init_database()`
- Use MongoDB `_id` field as primary key: activity names for activities, usernames for teachers
- Remember: MongoDB collections are accessed via `find()`, `find_one()`, `insert_one()`, etc.

### Password & Security
- **Always** use `hash_password()` and `verify_password()` from `database.py`
- Never store or handle plaintext passwords
- These functions use Argon2 hashing (already imported and configured)

### Error Handling & Logging
- Log full errors server-side (stack traces, exception details are for server debugging only)
- Raise `HTTPException` with appropriate status codes and safe, user-friendly `detail` messages
- Do NOT propagate implementation details, stack traces, or sensitive data to the frontend
- Example: Use status 404 for missing resources, 400 for bad input, 401 for auth failures

### Integration with Frontend
- Frontend consumes `/activities` and `/auth/` endpoints—**verify changes don't break the UI**
- Check assumptions about response format; breaking changes must be synchronized with `src/static/app.js`
- Test endpoints via FastAPI auto-generated docs at `/docs` before confirming complete

### Code Quality
- Follow naming conventions: `snake_case` for variables/functions, `PascalCase` for classes
- Keep functions focused and reusable
- Prefer explicit error handling over silent failures
- Add type hints using `typing` module (Optional, Dict, List, etc.)