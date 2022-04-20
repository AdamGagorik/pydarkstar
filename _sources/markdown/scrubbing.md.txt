#### Scrubbing

* Item data is stored in *items.csv*
* *items.csv* is just a simple text file that you can edit with excel
* The *items.csv* can be created with the scrub app
* There is an already generated *items.csv* in the bin folder for you
* You do not need to run the *scrub* app unless you want to recreate the database
* You can change many properties be editing the *items.csv.* manually
* You can change the FFXI `--server` that is used to download info from

| column   | description                     | value             |
| ---------|---------------------------------|-------------------|
| itemid   | unique item id                  | integer >=0       |
| name     | item name                       | string            |
| sell01   | sell single?                    | 0=false 1=true    |
| buy01    | buy single?                     | 0=false 1=true    |
| price01  | price for single                | integer >=1       |
| stock01  | restock count (single)          | integer >=0       |
| rate01   | buy rate (single) **not used**  | float 0 <= x <= 1  |
| sell12   | sell stack?                     | 0=false 1=true    |
| buy12    | buy stack?                      | 0=false 1=true    |
| price12  | price for stack                 | integer >=1       |
| stock12  | restock count (stack)           | integer >=0       |
| rate12   | buy rate (stack) **not used**   | float 0 <= x <= 1  |

##### Example

```bash
# Navigate to the bin directory
(base) ➜ pwd
/Users/adam/workspace/pydarkstar/bin
# Activate the correct Python environment
(base) ➜ conda activate pydarkstar
```

---

```bash
# In this example we will just scrub 3 different items from the cerberus server
# Run scrub with the desired opts (set in config.yaml & override with command line flags)
(pydarkstar) ➜ python ./scrub.py --backup --threads 8 --itemids 0 1 2 --server cerberus
[INFO ]: (0x7f7ff00b4240) Options: config     = config.yaml
[INFO ]: (0x7f7ff00b4240) Options: verbose    = True
[INFO ]: (0x7f7ff00b4240) Options: silent     = False
[INFO ]: (0x7f7ff00b4240) Options: stub       = items
[INFO ]: (0x7f7ff00b4240) Options: overwrite  = False
[INFO ]: (0x7f7ff00b4240) Options: backup     = True
[INFO ]: (0x7f7ff00b4240) Options: stock01    = 5
[INFO ]: (0x7f7ff00b4240) Options: stock12    = 5
[INFO ]: (0x7f7ff00b4240) Options: itemids    = ????
[INFO ]: (0x7f7ff00b4240) Options: threads    = 8
[INFO ]: (0x7f7ff00b4240) Options: server     = cerberus
[INFO ]: (0x7f7ff00b4240) Options: urls       = ????
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: init
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: forcing redownload of data
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: using passed ids
[INFO ]: (0x7f800045d4a8) FFXIAHScrubber: getting data
[INFO ]: (0x7f800045d4a8) FFXIAHScrubber: executing in parallel with threads=8
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: open server=cerberus (0/3,  0.00)
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: open server=cerberus (1/3, 33.33)
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: open server=cerberus (2/3, 66.67)
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: item count = 3
[DEBUG]: (0x7f800045d4a8) FFXIAHScrubber: data count = 3
[DEBUG]: (0x7f800046ac88) ItemList: init
[INFO ]: (0x7f800046ac88) ItemList: save /Users/adam/workspace/pydarkstar/bin/items.csv
[INFO ]: exit
```

---

```bash
# Using the --backup argument will save the results to items.csv and backup the old one
# Leave out the --threads argument if you want it to use all the cores on your computer
# If you want to download all items from a server, leave out the --itemids argument
(pydarkstar) ➜ python ./scrub.py --backup --server cerberus
...
... # Downloading all items will take awhile!
...
[DEBUG]: (0x7ff078c2a4a8) ItemList: init
[DEBUG]: backup (old): /Users/adam/workspace/pydarkstar/bin/items.csv
# notice that the old CSV is backed up so we dont loose it
[DEBUG]: backup (new): /Users/adam/workspace/pydarkstar/bin/items.csv.1
[INFO ]: (0x7ff078c2a4a8) ItemList: overwriting file...
[INFO ]: (0x7ff078c2a4a8) ItemList: save /Users/adam/workspace/pydarkstar/bin/items.csv
[INFO ]: exit
```

---

```bash
# You can always use the --help argument on any of the apps
(pydarkstar) ➜ python ./scrub.py --help                                                
usage: scrub.py [-h] [--verbose] [--silent] [--overwrite] [--backup]
                [--urls [url [url ...]]] [--itemids [itemids [itemids ...]]]
                [--stock01 5] [--stock12 5] [--threads int]
                [--server str | int]
                [stub]

Create item database.

positional arguments:
  stub                  output file stub

optional arguments:
  -h, --help            show this help message and exit
  --verbose             report debug, info, and error
  --silent              report error only
  --overwrite           overwrite output file
  --backup              backup output file
  --urls [url [url ...]]
                        a list of category urls
  --itemids [itemids [itemids ...]]
                        a list of item ids
  --stock01 5           default stock for singles
  --stock12 5           default stock for stacks
  --threads int         the number of threads (default is CPU dependent)
  --server str | int    the name of the FFXI server to scrub (ex: bahamut)
                        this can be a string or a number between 1 and 32
```
