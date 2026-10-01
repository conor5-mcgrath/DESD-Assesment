# DESD-Assesment
This is a repo containing the distributed and enterprise software development assessment code and information.

## Django project setup

### Prerequisites

- Windows with PowerShell.
- Python 3.12 or newer. Check with:

	```pwsh
	py --version
	```

	The output should report `Python 3.12` or a newer version. If `py` is not recognised, install Python 3.12 or newer from [python.org](https://www.python.org/downloads/windows/) and enable the Python Launcher during installation. Open a new terminal after installing, then check again.
- uv. Check whether it is installed with:

	```pwsh
	uv --version
	```

	If PowerShell says `uv` is not recognised, install it with the official Windows installer:

	```pwsh
	powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
	```

	Close existing integrated terminals and open a new one, then run `uv --version` again. The workspace settings add uv's standard Windows install directory to the PATH of new VS Code terminals.

### Install dependencies

Open a PowerShell terminal in the `DESD-Assesment` folder, the one containing `pyproject.toml`. Confirm the location with:

```pwsh
Test-Path .\pyproject.toml
```

It should return `True`. Then sync the project dependencies:

```pwsh
uv sync
```

This creates the virtual environment at `DESD-Assesment\.venv` and installs the locked dependencies, including Django. The environment is local to this repository and is excluded from Git. You do not need to activate it when using `uv run`.

`uv sync` does not activate the environment in the current terminal. If you want to activate it for commands such as `python`, run this from the project folder in PowerShell:

```pwsh
.\.venv\Scripts\Activate.ps1
```

The terminal prompt will show `(.venv)` when it is active. When you are finished, run `deactivate`. Alternatively, leave it inactive and prefix commands with `uv run`, for example `uv run python --version`.

Verify Python and Django are available in that environment:

```pwsh
uv run python --version
uv run python -m django --version
```

### Run the development server

Once the Django project has a `manage.py` file in this folder, start the server with:

```pwsh
uv run python manage.py runserver
```

To add another dependency later, use `uv add <package-name>` (for example, `uv add requests`). This updates the project configuration and lockfile.

### Troubleshooting

- If `uv` is not recognised, its install directory is missing from that terminal's `PATH`. Restart VS Code after installing uv, or open a new integrated terminal. A terminal inherits its PATH when it starts, so changing the Windows user PATH does not update terminals that are already open.
- If uv was installed with `pip --user`, its Scripts directory depends on the Python installation and version used by pip. On this computer it is `%APPDATA%\Python\Python312\Scripts`; on another computer it may differ. The official uv installer avoids tying uv to a particular Python version.
- Run `uv sync` from the folder containing `pyproject.toml`. Running it from the parent folder will not sync this project.
- If uv runs but cannot find a compatible Python, check `py --version`; this project requires Python 3.12 or newer.

