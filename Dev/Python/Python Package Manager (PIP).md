`pip` is the standard package manager for Python, used to install and manage libraries that aren’t part of the Python standard library. You use `pip` to manage dependencies and install packages from the Python Package Index (PyPI).

* `pip` stands for “pip installs packages”, indicating its primary function.
* `pip` manages packages that aren’t part of the standard library.
* You should use `pip` whenever you need **external Python packages** for your projects.
- You can **install and uninstall packages** with `pip`.
- You use **requirements files** to manage projects’ dependencies.

### Finding `pip` on Your System[](https://realpython.com/what-is-pip/#finding-pip-on-your-system "Permanent link")

The Python installer gives you the option to install `pip` when installing Python on your system. In fact, the option to install `pip` with Python is checked by default, so `pip` should be ready for you to use after installing Python.

<font color="#8064a2">**Note:** On some Linux (Unix) systems like Ubuntu, `pip` comes in a separate package called `python3-pip`, which you need to install with `sudo apt install python3-pip`. It’s not installed by default with the interpreter.</font>

| Windows Powershell | Linux + MacOS |
| ------------------ | ------------- |
| PS> where pip3     | $ which pip3  |

