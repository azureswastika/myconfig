# Myconfig

![PyPI](/logos/logo.png)

[![PyPI](https://img.shields.io/pypi/v/myconfig.svg)](https://pypi.python.org/pypi/myconfig)
[![PyPI](https://img.shields.io/pypi/pyversions/myconfig.svg)](https://img.shields.io/pypi/pyversions/myconfig.svg)
[![Build Status](https://travis-ci.org/azureswastika/myconfig.svg?branch=main)](https://travis-ci.org/azureswastika/myconfig)
[![GitHub](https://img.shields.io/github/license/azureswastika/myconfig)](/LICENSE)

## Quick start

### Install

```bash
pip install myconfig
```

### Initialize Myconfig on project root directory

```bash
cd project/path/
myconfig init json


Configuring your Python project environment
--------------------------------------------
File `settings.py` was created.
The `settings.json` file was created to hold public settings and `.secrets.json` file was created to hold private settings.
Also `.secrets.*` was added to `.gitignore`.
```

> You can also use other formats: myconfig init \<*format*> (**json** | **yaml** | **toml**)

### Using Myconfig

Add to `settings.py` common project settings:

```json
{
    "username": "admin",
    "ips": ["127.0.0.1", "198.*.*.*"],
    "database": {
        "name": "database_name",
        "port": 5555}
}
```

Or put private settings in `.secrets.py`:

```json
{
    "password": 53156
}
```

Import the `config` object from `settings.py` in your code

```py
from settings import config

print(config.username)
print(config.database.get('name'))
```

>File `settings.py`
>
>```py
>from myconfig import MyConfig
>
>config = MyConfig(['settings.json', '.secrets.json'])
>```
