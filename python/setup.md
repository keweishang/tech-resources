# Python3
Python3 and Python2 are not compatible. Please use Python3, because it’s 2018 :)

- Install
    - `brew install python3`
    - check the version: `python3 --version`
- Usage
    - Launch interactive python interpreter
        - `python3`

# pip
pip is a tool for installing Python packages from the [Python Package Index] (a.k.a PyPI), which is a repository for open-source third-party Python packages.

Python actually has another, more primitive, package manager called easy_install, which is installed automatically when you install Python itself. pip is vastly superior to easy_install for lots of reasons, and so should generally be used instead. You can use easy_install to install pip as follows:

- Install
    - `sudo easy_install pip`
    - check the version: `pip --version`
- Usage
    - Install third-party Python package globally
        - `sudo pip install [package name]`. e.p. `sudo pip install requests`
        - You can also precise the version: `pip install airflow==1.8.0`
    - Upgrate a third-party Python package globally
        - `sudo pip install --upgrade [package name]` e.p. `sudo pip install --upgrade requests`
    - Install third-party Python package in a virtualenv
        - Refer to virtualenv

# virtualenv (optional)
virtualenv allows multiple Python projects that have different (and often conflicting) requirements, to coexist on the same computer. For more info, read this [virtualenv article]. The TL;DR version is, it puts an isolated python environment (including a copy of the python binary itself, a copy of the entire Python standard library, a copy of the pip installer, and (crucially) a copy of the `site-packages` directory where `pip` installs third-party Python packages) into a directory and you use everything about Python from that directory.

- Install
    - `sudo pip install virtualenv`
    - check the version: `virtualenv --version`
- Usage
    - Create a virtual environment into the root of your project directory (e.p. `cd ~/code/myproject/`)
        - `virtualenv -p [python binary path] [virtual environment directory]`. e.p. ```virtualenv -p `which python3` venv```
    - Activate a virtual environement
        - When at the root of your project directory, run `source [virtual environment directory]/bin/activate`. e.p. `source venv/bin/activate`


[Python Package Index]: http://pypi.python.org/
[virtualenv article]: https://www.dabapps.com/blog/introduction-to-pip-and-virtualenv-python/