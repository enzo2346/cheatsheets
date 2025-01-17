## Summary

* [Useful Packages](#useful-packages)
* [Logger](#logger)

## Useful Packages

| Package       | Description                                                  | Link                                   |
|---------------|--------------------------------------------------------------|----------------------------------------|
| subprocess    | Automate system administration tasks                         | integrated to python                   |
| smtplib       | Manage mails                                                 | integrated to python                   |
| coverage      | Allow to generate a code coverage report for Python UT       | https://pypi.org/project/coverage/     |
| pyinstaller   | Allow to generate a .exe from python code                    | https://pypi.org/project/pyinstaller/  |
| requests      | Allow to do HTTP requests                                    | https://pypi.org/project/requests/     |
| pathlib       | Allow to manipulate PATH with Python on Windows and on linux | https://pypi.org/project/pathlib2/     |
| jira          | Allow to interact with Jira API                              | https://pypi.org/project/jira/         |
| fire          | Automatically generate command line interfaces (CLIs)        | https://pypi.org/project/fire/         |
| BeautifulSoup | Scrape data from websites                                    | https://pypi.org/project/BeautifulSoup/|
| selenium      | automate data entry tasks                                    | https://pypi.org/project/selenium/     |
| nox           | automate code tasks                                          | https://pypi.org/project/nox/          |

[Back to top](#summary)

## Logger

### 1. Import the logging module

```python
import logging
```

### 2. Basic Configuration

Configure the logging module to set the logging level and specify the output destination (e.g., console or a file). You typically do this in your application's setup or main script:

```python
logging.basicConfig(level=logging.DEBUG,  # Set the logging level
                    format='%(asctime)s - %(name)s - %(levelname)s - %(message)s',
                    handlers=[logging.StreamHandler()])
```

- **`level`**: Set the logging level (e.g., **`logging.DEBUG`**, **`logging.INFO`**, **`logging.WARNING`**, **`logging.ERROR`**, **`logging.CRITICAL`**).
- **`format`**: Define the log message format.
- **`handlers`**: Specify where log messages should be directed (e.g., console or files).

### 3. Create a Logger

In each module or script where you want to log messages, create a logger with a unique name:

```python
logger = logging.getLogger('my_logger')
```

### 4. Log Messages

Use the logger to log messages with different log levels:

```python
logger.debug("Debug message")
logger.info("Information message")
logger.warning("Warning message")
logger.error("Error message")
logger.critical("Critical message")
```

### 5. Logging Variables

You can log variables and other information alongside messages:

```python
variable = 42
logger.debug("The value of the variable is %d", variable)
```

### 6. Log Exceptions

To log exceptions, you can use the **`exception`** method:

```python
try:
    # Code that may raise an exception
except Exception as e:
    logger.error("An error occurred: %s", str(e), exc_info=True)
```

### 7. Log to a File

To log messages to a file, you can add a **`FileHandler`** to your logger:

```python
file_handler = logging.FileHandler('my_log.log')
file_handler.setFormatter(logging.Formatter('%(asctime)s - %(name)s - %(levelname)s - %(message)s'))
logger.addHandler(file_handler)
```

### 8. Change Logging Level

You can change the logging level during runtime if needed:

```python
logger.setLevel(logging.INFO)
```

### 9. Rotating Log Files

To limit the size of log files and keep multiple log files, you can use a **`RotatingFileHandler`**:

```python
rotating_handler = logging.handlers.RotatingFileHandler('my_log.log', maxBytes=1024, backupCount=3)
```

[Back to top](#summary)