# BeyondRL

## Development
The following tools are used for this project:

- [Poetry](https://python-poetry.org/) is used for dependency and package managment
- [Nox](https://nox.thea.codes/en/stable/) is used as automation tool, mainly for testing
- [Black](https://black.readthedocs.io/en/stable/) is the mandatory formatter tool
- [PyEnv](https://github.com/pyenv/pyenv) is recommended as a tool to handle multiple python versions in developers machines. 

### Setup the development environment on MAC

1. Install PyEnv:
    ```
    brew update
    brew install pyenv
    ```

2. Select the desired Python version (3.10 recommended):
    ```
    pyenv install 3.10.8
    pyenv global 3.10.8
    ```

3. Install poetry:
    ```
    curl -sSL https://install.python-poetry.org | python3 - 
    ```

4. Make sure poetry is the PATH running `poetry --version`. If not add the following to your rc file:
    ```
    export PATH=$HOME/.local/bin:$PATH
    ```
    If you would like to have tab completion, you can follow instructions [here](https://python-poetry.org/docs/#enable-tab-completion-for-bash-fish-or-zsh).


5. Install the global Python required dependencies: 

    ```
    pip install nox black flake8
    ```

6. Clone this repository, and execute the following command in the repository root folder:

    ```
    poetry install
    ``` 
    This will install all the dependencies for `brl` in a virtual environment created by Poetry for your project. 
    All the required dependencies for development are installed in that virtual environment.
    By default poetry will create the virtual env in special directory. If you want
    to set that directory you can do it with the following command:
    ```
    poetry config virtualenvs.path my/custom/path
    ```
    Additional poetry options to consider could be the following:
    ```
    poetry config virtualenvs.options.always-copy true
    poetry config virtualenvs.options.system-site-packages true
    poetry config virtualenvs.prefer-active-python true
    ```

7. Configure your IDE to work with the virtual environment or the command line if you use an editor. 

    To activate the virtual environment on your terminal (MacOS, Linux) you can execute:
    ```
    source $(poetry env info --path)/bin/activate
    ```

    The path to your virtual environment location can be found with `poetry env info` [command](https://python-poetry.org/docs/managing-environments#displaying-the-environment-information). 


If you need to add new dependencies use the following commands:
- Normal dependency: `poetry add my-package`
- Development dependency: `poetry add my-package --group dev`
- Documentation dependency: `poetry add my-package --group docs`

### Testing
