# tmplpython setup

This file describes how to setup this template.

## Features

- poetry support
- pytest, flake8, mypy, autopep, tox support
- GitHub workflow for tests on multiple platforms and versions

## Usage

### Setup

1. Create a project based on this template
   - Select this template when creating a new project on GitHub
   - Go to [https://github.com/yawn77/tmplpython/](https://github.com/yawn77/tmplpython/) and click on _Use this template_
2. Adapt `README.md`. Enter the project name and adapt sections to your needs (further inspiration: [https://www.makeareadme.com/](https://www.makeareadme.com/))
3. Select a license (e.g., from [https://choosealicense.com/](https://choosealicense.com/))
   - Replace the `LICENSE` file
   - Edit the license link at the end of this file
4. Rename directory `tmplpython` according to your needs
5. Replace `tmplpython` to the new name in all files (i.e., .coveragerc, pyproject.toml, tox.ini, .vscode/launch.json, tests/test_main.py)
6. Change `name`, `description`, `author`, `license`, `repository`, `classifiers` and `python` in `pyproject.toml`
7. Change python versions in `tox.ini`
8. Adapt versions `os` and `python-version` in GitHub Workflow `test.yml`
9. Enable [mypy](https://marketplace.visualstudio.com/items?itemName=ms-python.mypy-type-checker) and [flake8](https://marketplace.visualstudio.com/items?itemName=ms-python.flake8) by installing the corresponding VS Code extensions
10. Remove `setup.md`

### Intsall poetry

```bash
brew install poetry
```

### Poetry commands

#### Manage dependencies

```bash
# install all dependencies
poetry install
# install dependencies for execution only
poetry install --without dev
# add a dependency
poetry add <dependency==x.x.x>
# add a dev dependency
poetry add --group dev <dependency==x.x.x>
# update dependencies
poetry update
# list available updates
poetry show -l
```

#### Run commands

```bash
# Run program
poetry run python tmplpython/main.py
# Run tests
poetry run pytest tests/
# Run linter (flake8)
poetry run flake8 tmplpython/ tests/
# Run type checker (mypy)
poetry run mypy tmplpython/ tests/
# Run tox (tests, linter, type checker with different python versions)
poetry run tox
```

## Maintenance

- Update date in `LICENSE` file on new year's day

## Recommendations

- Use [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) to be compatible with future versions of this template
- Maintain the [changelog](https://keepachangelog.com/en/1.0.0/) with each commit. There will be features which will automate the maintenance of this file to some extent in the future.
- Branch protection for `main` and `v[0-9]*`
  - _Enable:_ Require a pull request before merging
  - _Enable:_ Require status checks to pass before merging
    - _Enable:_ Require branches to be up to date before merging
    - Select status checks
  - _Enable:_ Require conversation resolution before merging
  - _Enable:_ Do not allow bypassing the above settings

## Create a new release

1. Determine the next version number (e.g., by using [getNextVersion](https://github.com/thenativeweb/get-next-version) when you use conventional commits)
2. Update version number in `pyproject.toml`
3. Update README.md
4. Maintain CHANGELOG.md
5. Create a release in GitHub. Make use of your changelog to describe it
6. Add version tag (v0.1.0)
