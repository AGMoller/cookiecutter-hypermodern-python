# Quickstart Guide

## Requirements

Install [Cookiecutter]:

```console
$ pipx install cookiecutter
```

Install [Poetry] by downloading and running [install-poetry.py]:

```console
$ python install-poetry.py
```

Install [Nox] and [nox-poetry]:

```console
$ pipx install nox
$ pipx inject nox nox-poetry
```

[pipx] is preferred, but you can also install with `pip install --user`.

It is recommended to set up Python 3.7, 3.8, 3.9, 3.10, 3.11 using [pyenv].

## Creating a project

Generate a Python project:

```console
$ cookiecutter gh:AGMoller/cookiecutter-hypermodern-python --checkout="2022.6.3"
```

Change to the root directory of your new project,
and create a Git repository:

```console
$ git init
$ git add .
$ git commit
```

## Running

Run the command-line interface from the source tree:

```console
$ poetry install
$ poetry run <project>
```

Run an interactive Python session:

```console
$ poetry install
$ poetry run python
```

## Testing

Run the full test suite:

```console
$ nox
```

List the available Nox sessions:

```console
$ nox --list-sessions
```

Install the pre-commit hooks:

```console
$ nox -s pre-commit -- install
```

## Continuous Integration

### GitHub

1. Sign up at [GitHub].
2. Create an empty repository for your project.
3. Follow the instructions to push an existing repository from the command line.

### PyPI

1. Sign up at [PyPI].
2. Go to the Account Settings on PyPI,
   generate an API token, and copy it.
3. Go to the repository settings on GitHub, and
   add a secret named `PYPI_TOKEN` with the token you just copied.

### TestPyPI

1. Sign up at [TestPyPI].
2. Go to the Account Settings on TestPyPI,
   generate an API token, and copy it.
3. Go to the repository settings on GitHub, and
   add a secret named `TEST_PYPI_TOKEN` with the token you just copied.

### Codecov

1. Sign up at [Codecov].
2. Install their GitHub app.

### Read the Docs

1. Sign up at [Read the Docs].
2. Import your GitHub repository, using the button _Import a Project_.
3. Install the GitHub webhook,
   using the button _Add integration_
   on the _Integrations_ tab
   in the _Admin_ section of your project
   on Read the Docs.

## Releasing

Releases are triggered by a version bump on the default branch.
It is recommended to do this in a separate pull request:

1. Switch to a branch.
2. Bump the version using [poetry version].
3. Commit and push to GitHub.
4. Open a pull request.
5. Merge the pull request.

The Release workflow performs the following automated steps:

- Build and upload the package to PyPI.
- Apply a version tag to the repository.
- Publish a GitHub Release.

Release notes are populated with the titles and authors of merged pull requests.
You can group the pull requests into separate sections
by applying labels to them, like this:

<!-- table-release-drafter-sections-begin -->

| Pull Request Label | Section in Release Notes     |
| ------------------ | ---------------------------- |
| `breaking`         | 💥 Breaking Changes          |
| `enhancement`      | 🚀 Features                  |
| `removal`          | 🔥 Removals and Deprecations |
| `bug`              | 🐞 Fixes                     |
| `performance`      | 🐎 Performance               |
| `testing`          | 🚨 Testing                   |
| `ci`               | 👷 Continuous Integration    |
| `documentation`    | 📚 Documentation             |
| `refactoring`      | 🔨 Refactoring               |
| `style`            | 💄 Style                     |
| `dependencies`     | 📦 Dependencies              |

<!-- table-release-drafter-sections-end -->

[codecov]: https://codecov.io/
[cookiecutter]: https://github.com/audreyr/cookiecutter
[github]: https://github.com/
[install-poetry.py]: https://raw.githubusercontent.com/python-poetry/poetry/master/install-poetry.py
[nox]: https://nox.thea.codes/
[nox-poetry]: https://nox-poetry.readthedocs.io/
[pipx]: https://pipxproject.github.io/pipx/
[poetry]: https://python-poetry.org/
[poetry version]: https://python-poetry.org/docs/cli/#version
[pyenv]: https://github.com/pyenv/pyenv
[pypi]: https://pypi.org/
[read the docs]: https://readthedocs.org/
[testpypi]: https://test.pypi.org/
