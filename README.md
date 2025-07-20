# uvicorn-poetry-project-template
Pratice of uvicorn-poetry-project-template

## Installation

```bash
pipx install poetry
pipx install cookiecutter
cookiecutter https://github.com/max-pfeiffer/uvicorn-poetry-project-template
cd uvicorn-poetry-project-template
```

Update `pyproject.toml`:

Add `packages = [{include = "app"}]` to `[tool.poetry]` section.

Update `[tool.poetry.dev-dependencies]` into `[tool.poetry.group.dev.dependencies].


### Run with Poetry
In project directory install dependencies:
```shell
poetry lock
poetry install
```
Run application in project directory:
```shell
poetry run uvicorn --workers 1 --host 0.0.0.0 --port 8000 app.main:app
```

Open your browser and navigate to `http://localhost:8000/docs` to see the API documentation.

### Build and run Docker image
Build the production Docker image:
```shell
podman build --tag uvicorn-poetry-project-template:1.0.0 .
```
Run the containerized application:
```shell
podman run -it --rm uvicorn-poetry-project-template:1.0.0
```

## Fix GitHub Actions

```bash
poetry add --group dev pre-commit
poetry run pre-commit autoupdate
poetry run pre-commit install
poetry run pre-commit run --all-files
```
