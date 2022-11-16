.PHONY: setup install pre-commit test format clean

setup: install pre-commit

install:
	@echo "Installing dependencies..."
	poetry install

pre-commit: install
	@echo "Setting up pre-commit..."
	poetry run pre-commit install -t commit-msg -t pre-commit

bump:
	@echo "Bumping version..."
	poetry run cz bump

bump-alpha:
	@echo "Bumping alpha pre-release version"
	poetry run cz bump --prerelease alpha

bump-beta:
	@echo "Bumping beta pre-release version"
	poetry run cz bump --prerelease beta

test: test-black test-flake8 test-isort

test-black:
	@echo "Checking format with black..."
	poetry run black --check {{ cookiecutter.project_slug }}

test-flake8:
	@echo "Checking format with flake8..."
	poetry run flake8 {{ cookiecutter.project_slug }} --count --statistics

test-isort:
	@echo "Checking format with isort..."
	poetry run isort --check --settings-path pyproject.toml {{ cookiecutter.project_slug }}

format:
	@echo "Formatting with black and isort..."
	poetry run black {{ cookiecutter.project_slug }}
	poetry run isort --settings-path pyproject.toml {{ cookiecutter.project_slug }}

clean:
	rm -rf build
	rm -rf dist
	rm -rf __pycache__
