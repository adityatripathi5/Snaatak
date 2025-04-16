![image](https://github.com/user-attachments/assets/83c710bd-f6b7-42bf-a2c5-042d4fe43d60)


| Author      | Created on  | Version    | Last updated by | Last edited on |
|-------------|-------------|------------|-----------------|----------------|
| Aditya Tripathi   | 15-04-25    | version 1  | N/A       | N/A       |

# Python Installation Guide

This document provides a comprehensive guide to installing Python across multiple operating systems, with a focus on best practices and managing multiple versions.

## Table of Contents

1.  [Pre-Checks](#pre-checks)
2.  [Installation](#installation)
    * [Most Widely Used Python Version](#most-widely-used-python-version)
    * [Latest Python Version](#latest-python-version)
    * [Legacy Applications (Older Python Versions)](#legacy-applications-older-python-versions)
    * [OT/Microservices (python3-pip, python3-venv)](#otmicroservices-python3-pip-python3-venv)
3.  [Post-Checks](#post-checks)
4.  [Active Supported Python Version](#active-supported-python-version)
5.  [Multiple OS Installation Guide](#multiple-os-installation-guide)
    * [Linux (Ubuntu/Debian)](#linux-ubuntudebian)
    * [macOS](#macos)
    * [Windows](#windows)
6.  [Environment Variables](#environment-variables)
7.  [Python Virtual Environments (venv)](#python-virtual-environments-venv)
    * [Using venv](#using-venv)
8.  [Managing Multiple Python Versions](#managing-multiple-python-versions)
9.  [Best Practices](#best-practices)

## Pre-Checks

Before installing Python, ensure the following:

* **System Compatibility:** Verify your operating system version is supported by the Python version you intend to install.
* **Administrative Privileges:** You may need administrator or superuser privileges for installation.
* **Internet Access:** An active internet connection is recommended for downloading the installer or packages.
* **Disk Space:** Ensure sufficient disk space is available for the Python installation and any additional packages.

## Installation

This section covers installing different Python versions for various needs.

### Most Widely Used Python Version

Currently, Python 3.9 and 3.10 are widely used.  Here's how to install them:

* **Ubuntu/Debian:**

    ```bash
    sudo apt update
    sudo apt install python3.9 # or sudo apt install python3.10
    sudo apt install python3-pip # Install pip for the specific version
    sudo apt install python3-venv # Install venv
    ```

* **macOS (using Homebrew):**

    ```bash
    brew install python@3.9 # or brew install python@3.10
    #  Homebrew usually installs pip with Python
    ```

* **Windows:**
    1.  Download the installer from [https://www.python.org/downloads/](https://www.python.org/downloads/)
    2.  Run the installer.
    3.  Select the desired version (3.9 or 3.10).
    4.  **Important:**
        * Check "Add Python to PATH" during installation.
        * Ensure "pip" and "venv" are included in the installation.

### Latest Python Version

To install the latest Python version:

* Always download the latest stable release from the official Python website: [https://www.python.org/downloads/](https://www.python.org/downloads/)

    * **Ubuntu/Debian:**

        ```bash
        sudo apt update
        sudo apt install python3 # Installs the latest python 3
        sudo apt install python3-pip
        sudo apt install python3-venv
        ```

    * **macOS (using Homebrew):**

        ```bash
        brew install python # Installs the latest python
        ```

    * **Windows:**
        1.  Download the installer from [https://www.python.org/downloads/](https://www.python.org/downloads/)
        2.  Run the installer.
        3.  Select the latest version.
        4.  **Important:**
            * Check "Add Python to PATH" during installation.
            * Ensure "pip" and "venv" are included in the installation.

### Legacy Applications (Older Python Versions)

For legacy applications requiring specific older Python versions (e.g., Python 2.7), follow these steps:

* **Download:** Download the specific version from the Python archives: [https://www.python.org/downloads/source/](https://www.python.org/downloads/source/)
* **Installation:**
    * **Linux/macOS (from source):**

        ```bash
        tar xzf Python-2.7.18.tgz # Replace with actual filename
        cd Python-2.7.18
        ./configure --enable-optimizations # Recommended optimization
        make -j $(nproc) # Use all available cores for faster build
        sudo make altinstall # Important: Use altinstall
        ```

        * **Important:** When installing from source, especially for older versions, use `sudo make altinstall`.  This prevents overwriting the system's default Python.  You will likely also need to download and install `setuptools` separately for Python 2.7 to get `pip`.
    * **Windows:** Download the appropriate installer from the Python archives and run it. Be sure to select a custom installation location and \*do not\* overwrite your main Python installation.

### OT/Microservices (python3-pip, python3-venv)

For development related to Observability Tools (OT) and microservices, ensure you have `pip` and `venv` installed.  These are essential for managing dependencies and creating isolated environments.

* **Ubuntu/Debian:**

    ```bash
    sudo apt update
    sudo apt install python3-pip python3-venv
    ```

* **Other Linux:** Use your distribution's package manager (e.g., `yum` on CentOS/RHEL, `dnf` on Fedora).
* **macOS:** `pip` is often included with the installer from python.org. `venv` is part of the standard library. If you use Homebrew: `brew install python`.
* **Windows:** Ensure "pip" and "venv" are checked during the Python installation.

## Post-Checks

After installation, verify it by:

* **Check Python Version:** Open a terminal or command prompt and run:

    ```bash
    python3 --version  # or python --version, depending on your setup
    ```
* **Check pip Version:**

    ```bash
    pip3 --version # or pip --version
    ```
* **Run Python Interactively:** Type `python3` (or `python`) to start the interactive interpreter.
* **Run a Simple Script:** Create a file named `test.py` with the line `print("Python is working!")` and run it:

    ```bash
    python3 test.py
    ```

## Active Supported Python Version

The actively supported Python versions generally include the latest stable release and several older versions that receive security updates. It's important to use a version that is still actively maintained. As of late 2024, Python 3.9, 3.10, 3.11 and 3.12 are actively supported. Python 3.8 is in security fix only mode.

## Multiple OS Installation Guide

This section provides installation instructions for different operating systems.

### Linux (Ubuntu/Debian)

```bash
sudo apt update
sudo apt install python3  # Installs the latest stable Python 3
sudo apt install python3-pip python3-venv #install pip and venv
```

## macOS

* **Using the official installer:**

    1.  Download the installer from [https://www.python.org/downloads/](https://www.python.org/downloads/)
    2.  Run the installer.
    3.  Follow the on-screen instructions.
* **Using Homebrew:**

    ```bash
    brew install python  # Installs the latest stable Python 3
    ```

## Windows

1.  Download the installer from [https://www.python.org/downloads/](https://www.python.org/downloads/)
2.  Run the installer.
3.  **Important:**
    * Check "Add Python to PATH" during installation.
    * Consider customizing the installation location.

## Environment Variables

To access Python from any command prompt location, add Python to your system's PATH environment variable.

* **Linux/macOS:** The installers or package managers usually handle this automatically. If you install from source, you might need to add the Python executable's directory (e.g., `/usr/local/bin`) to your `~/.bashrc`, `~/.zshrc`, or similar shell configuration file.
* **Windows:**
    * The Python installer has an option to "Add Python to PATH." Check this option during installation.
    * If you forgot, you can add it manually:
        1.  Search for "Environment Variables" in the Start menu.
        2.  Click "Edit the system environment variables."
        3.  Click "Environment Variables..."
        4.  In the "System variables" section, find the "Path" variable and click "Edit..."
        5.  Click "New" and add the path to your Python installation (e.g., `C:\Python312`, `C:\Python312\Scripts`).

## Python Virtual Environments (venv)

Virtual environments isolate Python projects and their dependencies.

### Using venv

Here's how to use `venv`:

1.  **Create a virtual environment:**

    ```bash
    python3 -m venv myenv  # "myenv" is the environment name
    ```
2.  **Activate the environment:**

    * **Linux/macOS:**

        ```bash
        source myenv/bin/activate
        ```
    * **Windows:**

        ```powershell
        .\\myenv\\Scripts\\activate
        ```
3.  **Install packages:**

    ```bash
    pip install <package_name>
    ```
4.  **Deactivate the environment:**

    ```bash
    deactivate
    ```

## Managing Multiple Python Versions

Having multiple Python versions is crucial for compatibility. Here's how to manage them:

* **Linux/macOS:**
    * Use `make altinstall` when building from source to avoid replacing the system Python.
    * Use a version manager like `pyenv` to easily switch between versions.
* **Windows:**
    * Install each version to a different directory (e.g., `C:\\Python38`, `C:\\Python312`).
    * Use the `py` launcher (`py -3.8`, `py -3.12`) to specify the Python version.

## Best Practices

* **Use a Virtual Environment:** Always create a virtual environment for each project to isolate dependencies.
* **Install the Latest Stable Release:** For new projects, use the latest stable Python version.
* **Keep Python Updated:** Regularly update your Python installation to get the latest features and security patches.
* **Use `pip` for Packages:** Use `pip` to install and manage external packages.
* **Check for Compatibility:** Before installing a new Python version, check if your existing projects and dependencies are compatible.
* **Document Dependencies:** Use a `requirements.txt` file to list project dependencies. Generate it with `pip freeze > requirements.txt` and install from it with `pip install -r requirements.txt`.

## Contact Information
| Name         | Email address          |
|--------------|------------------------|
| Aditya Tripathi          | aditya.tripathi.snaatak@mygurukulam.co     |

## Reference Links
| Links        | Descriptions         |
|--------------|------------------------|
|    https://shorturl.at/Xi9Xo | A detailed Python Installation Guide on Mac |
https://shorturl.at/fmSFf     |   A detailed Python Installation Guide on Ubuntu    |
