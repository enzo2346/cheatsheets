## Summary

* [Code Formatter](#code-formatter)
* [Pip](#pip)
* [Script Folder](#script-folder)

## Code Formatter

Before auto-formatting your code, remember to commit it. Then, review the diff after formatting.

### JetBrains IDE

If you are using JetBrains IDE, a code formatter is already installed in the IDE. You just need to configure it :

Go to `settings >> Editor >> Code style`

Change the `Hard warp at` to 79 and check `Wrap on typing`

Then to format your code, you just need to select `Code | Reformat  Code` or press `CTRL + ALT + L`

### Visual Studio Code

If you are using Visual Studio Code, you can install the Python Black extension from Microsoft.

Then, you can configure the formatter opening the command palette and typing `Preferences: Open Settings (JSON)`

Add the following lines to your settings :

```json
  "[python]": {
    "editor.defaultFormatter": "ms-python.black-formatter",
    "editor.formatOnSave": true
  },
```

### Others IDE

If you are using another IDE or text editor, we recommend using black to format your code in PEP8.

To install black, run the following command in the terminal :

```bash
pip install black
```

Then to reformat you code or folder, just type the following :

```bash
black {source_file_or_directory}
```

[Back to top](#summary)

## Pip

**1. Installing Packages**

- Install a package: **`pip install package_name`**
- Install a specific version: **`pip install package_name==version`**
- Install from a requirements file: **`pip install -r requirements.txt`**

**2. Upgrading Packages**

- Upgrade a package: **`pip install --upgrade package_name`**

**3. Listing Packages**

- List installed packages: **`pip list`**
- List outdated packages: **`pip list --outdated`**

**4. Removing Packages**

- Uninstall a package: **`pip uninstall package_name`**

**5. Searching Packages**

- Search for a package: **`pip search package_name`**

**6. Managing Virtual Environments**

- Create a virtual environment: **`python -m venv venv`**
- Activate a virtual environment:
   - Windows: **`venv\Scripts\activate`**
   - macOS and Linux: **`source venv/bin/activate`**
- Deactivate a virtual environment: **`deactivate`**

**7. Miscellaneous**

- Show package information: **`pip show package_name`**
- Freeze installed packages to a requirements file: **`pip freeze > requirements.txt`**
- Check PIP version: **`pip --version`**

[Back to top](#summary)

## Script Folder

1. Create a directory to put all your python scripts in. E.g. "C:\Users\Your Name\My Scripts"

2. Add to the PATH the created directory, e.g "C:\Users\Your Name\My Scripts"

3. Set Python as default to open *.py files

4. You should now be able to call your scripts like the following in a terminal:

```shell
script.py
```

[Back to top](#summary)