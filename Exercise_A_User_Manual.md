# Exercise A: User Manual Procedure

## Creating and Activating a Python Virtual Environment and Installing a Package

### Introduction

A Python virtual environment is an isolated workspace that allows a developer to manage the packages and dependencies used by a particular Python project. Using a virtual environment is important because different projects may require different versions of the same package. Without a virtual environment, installing or updating a package for one project could affect other projects on the same computer.

This procedure explains how a beginner can create a Python project folder, create a virtual environment, activate it, install a Python package, and confirm that the installation was successful. The instructions are written for a first-semester computing student who has basic computer literacy but has not previously worked with Python virtual environments.

### Prerequisites

Before beginning the procedure, the student needs a Windows computer with Python installed. The student also needs access to a terminal application such as Command Prompt, PowerShell, or Git Bash. Basic knowledge of opening a terminal and entering commands is helpful, although no previous experience with Python virtual environments is required.

An internet connection is needed because the procedure includes downloading the Requests package. The student should also have permission to create folders and files on the computer.

### Procedure

#### Step 1: Open the terminal

Open Command Prompt, PowerShell, or Git Bash on the computer.

**Expected result:** A terminal window opens and displays a command prompt where commands can be entered.

#### Step 2: Create a project folder

Enter the following command in the terminal:

```bash
mkdir python_project
```

The `mkdir` command means "make directory." It creates a new folder that will be used to store the Python project.

**Expected result:** A new folder named `python_project` is created in the current location.

#### Step 3: Open the project folder

Enter the following command:

```bash
cd python_project
```

The `cd` command means "change directory." It moves the terminal into the project folder so that the remaining commands are performed inside the correct location.

**Expected result:** The terminal changes to the `python_project` directory.

#### Step 4: Create the virtual environment

Enter the following command:

```bash
python -m venv venv
```

This command uses Python's built-in `venv` module to create an isolated environment. The final `venv` specifies the name of the environment.

**Expected result:** A folder named `venv` is created inside the `python_project` folder.

If the `python` command is not recognized on a Windows computer, use the Python launcher instead:

```bash
py -m venv venv
```

#### Step 5: Activate the virtual environment

Enter the following command:

```bash
venv\Scripts\activate
```

Activating the environment tells the computer to use the Python interpreter and packages associated with the new virtual environment.

**Expected result:** `(venv)` appears at the beginning of the terminal prompt. This indicates that the virtual environment is active.

#### Step 6: Install the Requests package

Enter the following command:

```bash
pip install requests
```

The `pip` command is Python's package management tool. It downloads and installs the Requests package and any dependencies required by the package into the active virtual environment.

**Expected result:** The terminal displays messages showing that the Requests package has been downloaded and installed successfully.

#### Step 7: Verify the package installation

Enter the following command:

```bash
pip show requests
```

The `pip show` command displays information about an installed Python package. It can be used to confirm that the Requests package is available in the active environment.

**Expected result:** The terminal displays information about the Requests package, including its name, version, and installation location.

### Screenshot Description

A screenshot should be included after the package has been installed and verified. The screenshot should show the terminal window with `(venv)` displayed at the beginning of the command prompt. It should also show the output from the `pip show requests` command, including information such as the package name and version.

The screenshot would provide visual evidence that the virtual environment has been activated and that the Requests package has been installed successfully. The screenshot should be clear enough for the reader to identify the command that was entered and the resulting output.

### Troubleshooting

One common problem that a beginner may encounter is an error stating that the `python` command is not recognized. This error usually occurs when Python is not installed correctly, when Python is not available through the `python` command, or when Python has not been added to the system PATH.

The student can first check whether Python is available by entering:

```bash
py --version
```

If this command displays a Python version number, Python is installed and the student can create the virtual environment by using:

```bash
py -m venv venv
```

instead of:

```bash
python -m venv venv
```

If neither command works, Python may not be installed correctly. The student should install Python and make sure it is properly configured before continuing with the procedure.

### Conclusion

Following these steps creates an isolated Python environment for the project and installs the Requests package inside that environment. Using a virtual environment helps keep project dependencies organized and prevents packages installed for one project from unnecessarily affecting other Python projects.
