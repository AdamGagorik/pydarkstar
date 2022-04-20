# Usage

#### Example

```bash
# Windows

> cd /D "C:\path\to\pydarkstar\bin"
> conda activate pydarkstar
> .\broker.py

# Linux

bash:~$ cd /path/to/pydarkstar/bin
bash:~$ conda activate pydarkstar
bash:~$ ./broker.py
```

#### Parameters

* You should set your mysql parameters!
* Parameters can be set in the config.yaml file
* You can also override parameters on the command line
* Please do not edit source code files to configure your apps

###### Example

```yaml
# ah
name: Zissou          # Name that appears on AH when buying and selling

# basic
verbose: true         # ERROR, INFO, DEBUG in log file
silent: false         # ERROR

# input
data: ['items.csv']   # comma seperated list of CSV files

# output
stub: items           # output name when scrubbing
overwrite: false      # overwrite existing output?
backup: true          # backup existing output?

# sql
hostname: 127.0.0.1   # SQL parameter
database: dspdb       # SQL parameter
username: root        # SQL parameter
password: ????        # SQL parameter
fail: true            # fail on SQL database errors?

# broker/seller
restock: 3600         # seconds between selling

# broker/buyer
tick: 30              # seconds between buying

# scrub
server: bahamut       # FFXI server to query
threads: -1           # number of CPU threads
itemids: []           # list of itemids to scrub
stock01: 5            # default stock01 when scrubbing
stock12: 5            # default stock12 when scrubbing
urls: []              # list of category urls to scrub
```

#### Item Database

Item data is stored in a **CSV** file called *items.csv*.
Please see the [scrubbing](./scrubbing.md) guide info on generating this **CSV**.

#### Apps

* There are many apps
* You may use the scrub app
* You will probably only use the broker app

| app    | description                                                         |
|--------|---------------------------------------------------------------------|
| scrub  | download data from the web to create a database of items and prices |
| broker | server that buys and sells items on the AH from players             |
| buyer  | server that buys items on the AH from players                       |
| seller | server that sells items on the AH to players                        |
| clear  | clear the AH of all transactions                                    |
| refill  | fill the AH with items for sale and exit                             |
