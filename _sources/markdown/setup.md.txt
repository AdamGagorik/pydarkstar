# Setup

This is a giude to getting pydarkstar running.

### Step 0: Install Git and Clone pydarkstar

* You installed **git** already when you setup [darkstar][DARKS]
* Clone the pydarkstar repository from [here][GITPG]

### Step 1: Install Python Anaconda

* Install [Python Anaconda][CONDA]
* You need **Python3.7** or greater.

### Step 2: Create Python Environment

```{warning}
Use the Anaconda Command Prompt on Windows (search for it in the start menu)
```

* Open a command prompt in the bin folder.

```bash
# Windows

> cd /D "C:\path\to\pydarkstar\bin"
> conda env remove --name pydarkstar
> conda env create -f environment.yml

# Linux

bash:~$ cd /path/to/pydarkstar/bin
bash:~$ conda env remove --name pydarkstar
bash:~$ conda env create -f environment.yml
```

### Step 3: Configure pydarkstar

Follow the instructions on the [usage][USAGE] page.

[CONDA]: https://www.anaconda.com
[PYPIP]: https://pip.pypa.io/en/stable/
[PYOFF]: https://www.python.org/downloads
[USAGE]: http://adamgagorik.github.io/pydarkstar/generated/usage.html
[GITPG]: https://github.com/AdamGagorik/pydarkstar
[DARKS]: https://github.com/DarkstarProject/darkstar
[TOPAZ]: https://github.com/project-topaz/topaz
[TNEXT]: https://github.com/topaz-next/topaz
