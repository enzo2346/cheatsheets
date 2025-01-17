## Summary

**-> [Back to Index](./README.md)**

* [Naming Conventions](#naming-conventions)
* [Code Layout](#code-layout)
* [Comments and Docstring](#comments-and-docstrings)
* [Project Structure](#project-structure)

## Naming Conventions

| Type      | Naming Convention                                                   | Examples                            |
|-----------|----------------------------------------------------------------------|-------------------------------------|
| Function  | Use a lowercase word or words. Separate words by underscores.      | function, my_function               |
| Variable  | Use a lowercase single letter, word, or words. Separate with underscores. | x, var, my_variable                 |
| Class     | Start each word with a capital letter. Do not use underscores. | Model, MyClass                      |
| Method    | Use a lowercase word or words. Separate with underscores.           | class_method, method                |
| Constant  | Use an uppercase single letter, word, or words. Separate with underscores. | CONSTANT, MY_CONSTANT, MY_LONG_CONSTANT |
| Module    | Use a short, lowercase word or words. Separate with underscores.    | module.py, my_module.py             |
| Package   | Use a short, lowercase word or words. Do not use underscores.       | package, mypackage                  |

Remark: Avoid abbreviations

[Back to top](#summary)

## Code Layout

### Spaces and indentation

- Use 4 spaces instead of tab
- Put a single space around assignment operators and logical operators. The only exception occurs when setting default values in function and method parameters
- Don’t put spaces directly after parentheses or square brackets
- Don’t put spaces between a function and its arguments
- Leave a space between an if/for statement and parentheses

Exemple :

```python
def protect_animals(animals, sanctuary="little farm", max_places=4):    
    """Place donated animals in a sanctuary."""
    is_little = "little" in sanctuary
		
    if max_places < 5 or is_little:        
        print("It's small, but it's better than nothing!")   
 
    protected = animals[:max_places]    
    print(f"We have protected these animals : {protected}")

animals = ["pig", "chicken", "cat", "dog"]
protect_animals(animals)
```

### Line breaks

- put 2 line breaks before a class definition or a function definition
- put 1 line break before a method definition
- Lines of code should not exceed 79 characters

[Back to top](#summary)

## Comments and Docstrings

### Comments
- Write complete sentences in English
- Avoid comments that contradict the code
- Use “docstrings” as much as possible
- A comment or docstring should be composed of one or more simple imperative sentences. Its sentences should not explain the code, but explain its usage, so its return, its parameters and its exceptions.

### Docstrings

Exemple :

```python
def search_film(name):      
    """Search for a movie based on a given name.      
    
    Attrs:      - name (str): the name used for the search.      
    
    Returns:      - a `film` object if a movie was found, or None.      
    """      
    films = Film.filter_by_name(name)
    if films:          
        return films.pop(0)      
    return None
```

Display the docstring of a function using the `__doc__` attribute :

```python
print(search_film.__doc__)
```

[Back to top](#summary)

## Project Structure

```bash
my_project/
├── src/                     # Main Python package/module directory
│   ├── __init__.py          # Initialize the package
│   ├── main.py              # main file
│   ├── module1/             # Subpackage for module1
│   │   ├── __init__.py
│   │   ├── module1.py
│   ├── module2/             # Subpackage for module2
│   │   ├── __init__.py
│   │   ├── module2.py
│   └── ...
├── tests/                   # Directory for unit tests
│   ├── __init__.py          # Initialize the test package
│   ├── test_module1.py      # Test module1
│   ├── test_module2.py      # Test module2
│   └── ...
├── README.md                # Project documentation
├── docs/                    # Additional project documentation (optional)
├── requirements.txt         # Project dependencies
├── .gitignore               # Git ignore file
└── sonar-project.properties # SonarQube file
```

In this structure:

- The **`src/`** directory is the main package/module directory.
- Inside **`src/`**, you have subdirectories for each module or component, such as **`module1/`** and **`module2/`**. These subdirectories contain their own **`__init__.py`** files to make them subpackages.
- Each subdirectory can contain its module file, such as **`module1.py`** and **`module2.py`**.

With this structure, you can import modules from the subpackages as follows:

```bash
from src.module1 import module1_function
from src.module2 import module2_function
```

[Back to top](#summary)