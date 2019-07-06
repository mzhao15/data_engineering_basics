# How to set up python virtual environment in Windows

## using [**venv**](https://docs.python.org/3/library/venv.html) module

The 'venv' module provides support for creating lightweight “virtual environments” with their own site directories, optionally isolated from system site directories. Each virtual environment has its own Python binary (which matches the version of the binary that was used to create this environment) and can have its own independent set of installed Python packages in its site directories.

- Create a virtual environment  
    ```
    $ python -m venv myenv
    ```
    `myenv` is the name of the created virtual environment.
- Install packages  
    ``` 
    $ pip install [package name]
    ```
    Or to use a spec file ('spec-file.txt') which includes information of the versions of packages
    ``` 
    $ pip install -r spec-file.txt
    ```
- Activate the virtual environment  
    ```
    $ myenv/Scripts/activate.bat
    ```
- Deactivate the virtual environment  
    ```
    $ deactivate
    ```
- Delete the virtual environment  
    ```
    $ rmdir myenv /s
    ```
    `/s` removes all the subfolders, too.
- Export the active environment to a new file  
    ```
    $ myenv/bin/pip freeze > spec-file.txt
    ```
    `freeze` lists the versions of all packages.
- Add system packages to the virtual environment  
    ```
    $ python -m venv myenv --system-site-packages
    ```

## using **[`conda`](https://docs.conda.io/en/latest/)**

`Conda` is an open source package management system and environment management system that runs on Windows, macOS and Linux. `Conda` quickly installs, runs and updates packages and their dependencies. `Conda` easily creates, saves, loads and switches between environments on your local computer. It was created for Python programs, but it can package and distribute software for any language. 


- Create a virtual environment  

    Create a virtual environment with some initial packages:
    ```
    $ conda create --name myenv [list of packages (at least one)]
    ```
    Create a virtual environment using a spec file:
    ```
    $ conda create --name myenv --file spec-file.txt
    ```
- Install packages  

    To install a specific package such as SciPy into an existing environment `myenv`:
    ```
    $ conda install --name myenv [package names]
    ```
    If you do not specify the environment name, which in this example is done by `--name myenv`, the package installs into the current environment:
    ```
    $ conda install [package names]
    ```
    To use a spec file to install its listed packages into an existing environment:
    ```
    $ conda install --name myenv --file spec-file.txt   
    ```  
- Activate the virtual environment
    ```
    $ conda activate myenv
    ```
- Deactivate the virtual environment
    ```
    $ conda deactivate
    ```
- View all virtual environment
    ```
    $ conda env list
    ```
- Delete the virtual environment
    ```
    $ conda remove --name myenv --all
    ```
- View the list of all packages in a virtual environment  

    When the environment is not activated:
        ```
        $ conda list -n myenv
        ```
    When the environment is activated:
        ```
        $ conda list
        ```
- Export your active environment to a new file:
    ```
    $ conda env export > environment.yml
    ```


