# Python Project Setup (uv)

This skill automates the creation of a standardized Python project using `uv`, FastAPI, and Pytest, adhering to the `AGENTS.md` specifications.

## Instructions

When this skill is invoked, perform the following steps in the target directory:

1. **Initialize Project**:
   ```bash
   uv init
   ```

2. **Add Core Dependencies**:
   ```bash
   uv add fastapi uvicorn ruff pytest httpx
   ```

3. **Setup Directory Structure**:
   ```bash
   mkdir -p app tests
   touch app/__init__.py tests/__init__.py
   ```

4. **Create Starter Application**:
   Create `app/main.py` with the following content:
   ```python
   from fastapi import FastAPI

   app = FastAPI()

   @app.get("/")
   async def root():
       return {"message": "Hello from Openchattt Backend"}
   ```

5. **Create Starter Test**:
   Create `tests/test_main.py` with the following content:
   ```python
   from fastapi.testclient import TestClient
   from app.main import app

   client = TestClient(app)

   def test_root():
       response = client.get("/")
       assert response.status_code == 200
       assert response.json() == {"message": "Hello from Openchattt Backend"}
   ```

6. **Verify Installation**:
   Run the following commands to ensure everything is working correctly:
   ```bash
   uv run pytest
   uv run ruff check . --fix
   ```

## Verification Checklist
- [ ] `pyproject.toml` exists and contains the correct dependencies.
- [ ] `.venv` is created.
- [ ] `app/main.py` and `tests/test_main.py` are present.
- [ ] `pytest` passes.
- [ ] `ruff` reports no errors.
