# Advanced

#### Shell Scripts : PYTHONPATH

**The pydarkstar package will not work unless you tell python where pydarkstar is located**.

We accomplish this by writing shell scripts that set an environment variable called PYTHONPATH to the absolute path of the pydarkstar root directory.

The process of setting the PYTHONPATH is not needed in the case that pydarkstar is in the current directory of an executing python interpreter.

#### Shell Scripts : Anaconda Environment

It is very important that the correct Python interpreter is used.  If you use Anaconda, you must activate the environment you want to use.  This can be done with the `conda activate command`.

To check what Python interpreter is being used, you can run `python --version`.

##### Linux

* Create the following text file.

```bash
#!/bin/bash
export PYTHONPATH=$PYTHONPATH:/path/to/pydarkstar
conda activate pydarkstar
python -m pydarkstar.apps.scrub.run $*
```

* Make the file executable.

```bash
bash:~$ chmod +x scrub.sh
```

* Run the app.

```bash
bash:~$ ./scrub.sh --help
```

##### Windows

* Create the following text file.
* Please note that spaces in directory names can cause issues to arise when quotes are not used.

```bat
@ECHO OFF
set PYTHONPATH="%PYTHONPATH%;C:\Path\To\pydarkstar"
conda activate pydarkstar
python3 -m pydarkstar.apps.scrub.run %*
```

#### Shell Scripts : Running Apps

**Please note that pydarkstar takes advantage of python's -m flag to run library modules as scripts**.  Python modules are just python files beneath the pydarkstar top level directory.  There is no other way to run the apps.

* This will work

```bash
bash:~$ cd /path/to/pydarkstar
bash:~$ conda activate pydarkstar
bash:~$ python3 -m pydarkstar.apps.scrub.run --help
```

* This will not work

```bash
bash:~$ cd /path/to/pydarkstar
bash:~$ conda activate pydarkstar
bash:~$ python3 ./pydarkstar/apps/scrub/run.py --help
```
