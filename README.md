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

## Add pre-commit hook

`.pre-commit-config.yaml` need to change `entry: ruff check` to `entry: poetry run ruff check` and `entry: ruff format` to `entry: poetry run ruff format`. With `language: python` into `language: system`.

```bash
poetry add --group dev pre-commit
poetry run pre-commit autoupdate
poetry run pre-commit install
poetry run pre-commit run --all-files
```

git commit hook seems not working, so you need to run `pre-commit run --all-files` manually before commit.