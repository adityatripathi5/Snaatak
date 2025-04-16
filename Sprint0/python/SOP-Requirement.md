# Python requirements.txt Guide

This document provides a comprehensive guide to using `requirements.txt` for managing Python project dependencies, with a focus on Observability Tools (OT) and microservice development.

## Table of Contents

1.  [What is a requirements.txt file?](#what-is-a-requirements.txt-file)
2.  [Commands to Create a requirements.txt file](#commands-to-create-a-requirements.txt-file)
3.  [Commands to Use a requirements.txt file](#commands-to-use-a-requirements.txt-file)
4.  [Pre-Checks](#pre-checks)
5.  [Installation for OT/Microservices](#installation-for-otmicroservices)
6.  [Post-Checks](#post-checks)
7.  [Best Practices](#best-practices)

## What is a requirements.txt file?

A `requirements.txt` file is a text file that lists the Python packages and their versions that a project depends on.  It's used to ensure that anyone working on the project, or deploying the project, has the exact same dependencies.  This helps avoid "it works on my machine" problems.

## Commands to Create a requirements.txt file

The most common way to create a `requirements.txt` file is using `pip`:

```bash
pip freeze > requirements.txt
```
This command does the following:

* `pip freeze`:  Lists all installed packages in the current Python environment (including transitive dependencies).
* `>`:  Redirects the output of `pip freeze` to a file named `requirements.txt`.

It is highly recommended to create and activate a virtual environment (`venv`) \*before\* running this command.  This ensures that the `requirements.txt` file only contains the dependencies for your specific project, and not globally installed packages.

## Commands to Use a requirements.txt file

The primary command to use a `requirements.txt` file is:

```bash
pip install -r requirements.txt
```

## Pre-Checks

Before using a `requirements.txt` file, ensure the following:

* **Python and pip are installed:** You need a working Python installation with `pip` available.
* **Virtual environment (Recommended):** It's highly recommended to create and activate a virtual environment before installing dependencies.  This isolates your project's dependencies.
* **requirements.txt exists:** The `requirements.txt` file should be in the directory where you will run the `pip install -r requirements.txt` command.

## Installation for OT/Microservices

For OT (Observability Tools) and microservice development, the following packages are commonly used.  This section provides a consolidated installation approach using `requirements.txt`.

**Create a `requirements.txt` file with the following content:**

```txt
python-json-logger
Flask
flasgger
prometheus-flask-exporter
voluptuous
psycopg2-binary
redis
flask-caching
peewee
```

**Then, install the dependencies:**

1.  **Create a virtual environment (if you haven't already):**

    ```bash
    python3 -m venv venv
    ```

2.  **Activate the virtual environment:**

    * **Linux/macOS:**

        ```bash
        source venv/bin/activate
        ```

    * **Windows:**

        ```powershell
        .venv\Scripts\activate
        ```

3.  **Install the packages from `requirements.txt`:**

    ```bash
    pip install -r requirements.txt
    ```

**Explanation of Packages:**

* `python-json-logger`: For logging in JSON format, useful for centralized logging systems.
* `Flask`: A microframework for building web applications.
* `flasgger`: For generating Swagger/OpenAPI documentation for Flask APIs.
* `prometheus-flask-exporter`: For exporting Prometheus metrics from Flask applications.
* `voluptuous`: A Python data validation library.
* `psycopg2-binary`: A PostgreSQL database adapter (the `binary` version is often easier to install).
* `redis`: A Python client for Redis, an in-memory data store.
* `flask-caching`: Adds caching support to Flask applications.
* `peewee`: A simple and small ORM.

**To show information about a specific package (as requested for flask-caching and peewee):**

```bash
pip show flask-caching
pip show peewee
```

## Post-Checks

After installing the dependencies, verify the installation:

* **List installed packages:**

    ```bash
    pip list
    ```

    This will show all the packages installed in the current environment. Check that the packages listed in your `requirements.txt` file are present.
* **Run your application:** Start your Flask application or microservice and ensure that it runs without any import errors related to the installed packages.
* **Check package details:**

    ```bash
    pip show <package_name> # e.g., pip show flask
    ```

    Use this to confirm the correct versions are installed.

## Best Practices

* **Use Virtual Environments:** Always use virtual environments to isolate project dependencies.
* **Pin Dependencies:** Specify exact versions in your `requirements.txt` file (e.g., `Flask==2.3.2` instead of `Flask`). This ensures consistent builds across different environments.
* **Update requirements.txt Regularly:** When you add, update, or remove a package, update your `requirements.txt` file.
* **Document Why a Package is Needed:** For complex projects, consider adding comments to your `requirements.txt` file to explain why a particular package is required.
* **Use `pip-tools` for Complex Projects:** For more complex projects, consider using `pip-tools` (`pip install pip-tools`). It provides `pip-compile` (which generates a `requirements.txt` file with pinned, transitive dependencies) and `pip-sync` (which synchronizes a virtual environment with a compiled `requirements.txt`).
* **Commit requirements.txt to Version Control:** Always include your `requirements.txt` file in your project's version control system (e.g., Git).
