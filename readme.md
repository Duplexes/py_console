
# pyconsole
`pyconsole` is a Python library designed to help developers make nicer command line applications faster. It has cross-platform compatibility for Windows and Linux and supports color on both as well. There are also numerous small quality of life features that will make your programming easier, such as a built-in error logger, message handler, and progress bars.
## Installation
Use the package manager [pip](https://pip.pypa.io/en/stable/) to install `pyconsole`. 
```bash
pip install -i https://test.pypi.org/simple/ pyconsole
```
Note: This package is on the Test instance of the Python Package Index. We plan on changing this soon.
## Usage
### Printing Messages
#### Syntax
`PrintMessage(message, prefix, messageColor, prefixColor, colorBrackets, forceLog)`

Prefixes are automatically enclosed in square brackets.
Certain prefix types like `Error` and `Success` are automatically highlighted in the appropriate color.
You may override preset colors.
#### Parameters
`message` - The message you want to print in the console. Default is `""`.  
`prefix` - The prefix before the message. Default is `"none"`.  
`messageColor` - The color of the message. Default is `Color.White`.  
`prefixColor` - The color of the prefix. Default is `Color.White`.  
`colorBrackets` - Specify whether to color the brackets surrounding the prefix or not. Default is `False`.  
`forceLog` - Force the message to be logged in the log file. Default is `False`.
#### Example
##### Code
```python
from pyconsole import *

PrintMessage("Generic message.")
PrintMessage("Error message.", "Error")
PrintMessage("Warning message.", "Warning")
PrintMessage("Success message.", "Success")
PrintMessage("Info message.", "Info")
PrintMessage("Message in pink.", "none", Color.BrightMagenta)
PrintMessage("Message in blue.", "Green prefix", Color.BrightBlue, Color.Green)
PrintMessage("Message in cyan. The brackets around the prefix are also colored.", "Custom Prefix", Color.BrightCyan, Color.Red, True)
PrintMessage("This message has been logged in the log file.","Info", None, None, False, True)
```
##### Output
[Insert image here]
### Input Prompts
#### Syntax
`UserInput(prefix, prefixColor, inputColor)`
#### Parameters
`prefix` - The prompt or question before the user's input. Default is `""`.  
`prefixColor` - The color of the prefix. Default is `Color.White`.  
`inputColor` - The color of the user's input. Default is `Color.White`.
#### Example
##### Code
```python
from pyconsole import *

UserInput("Prompt. ")
UserInput("Prompt in green. ", Color.Green)
UserInput("Prompt in green, user input in blue. ", Color.Green, Color.Blue)
```
##### Output
[Insert image here]
### Progress Bars
#### Syntax
`progressBar = ProgressBar(iteration, total, prefix, suffix, length, fill, decimals, printEnd)`
`progressBar.update(counter)`
#### Parameters
`iteration` - The iteration of progress bar (how full it is). Default is `0`.  
`total` - The total number of iterations the progress bar has. Default is `100`.  
`prefix` - The prefix before the progress bar. Default is `""`.  
`suffix` - The suffix after the progress bar. Default is `""`.  
`length` - The number of characters in the progress bar. Default is `100`.  
`fill` - The character to use for the progress bar fill. Default is `"█"`.  
`decimals` - The number of decimals to show in the percent. Default is `1`.  
`printEnd` - The character(s) to print at the end. Default is `"\r"`.
#### Example
##### Code
```python
from pyconsole import *

progressBar = ProgressBar()
for item in range(1, 101):
    progressBar.update(item)
```
##### Output
[Insert image here]
### Error Logging
#### Syntax
`Logger.Log(message, prefix, prefixBrackets)`  
`Logger.ClearLog()`  
`Logger.Set(messageLogging, inputLogging)`
`Logger.SetLogLevel(level)`
#### Parameters
`message` - The message in the log entry. Default is `""`.  
`prefix` - The prefix before the messsage. Default is `""`.  
`prefixBrackets` - Specify whether to enclose the prefix in square brackets or not. Default is `True`.  

`messageLogging` - Enable or disable message logging. Default is `True`.  
`inputLogging` - Enable or disable user input logging. Default is `True`.  

`level` - Log level from the Levels class. Default is `Logger.Levels.warning`.  
`Logger.Levels.none` - Don't log any messages.  
`Logger.Levels.error` - Log errors.  
`Logger.Levels.warning` - Log warnings and errors.  
`Logger.Levels.success` - Log successes, warnings, and errors.  
`Logger.Levels.info` - Log info, successes, warnings, and errors.  
`Logger.Levels.everything` - Log everything.  
#### Example
##### Code
```python
from pyconsole import *

# Clear the log file
Logger.ClearLog()
# Set the logger to log all messages
Logger.SetLogLevel(Logger.Levels.everything)
# Log a message
Logger.Log("This is a log message.", "Log prefix")
# Disable logging
Logger.Set(False, False)
```
##### Output
[Insert image here]
### Colors
`pyconsole` has a built-in color system that is designed to be intuitive to use. `pyconsole` automatically clears the console on Windows consoles to properly display color codes.
#### Normal Colors
```python
from pyconsole import *

print(Color.Red + "I'm red!")
```
#### Bright Colors
```python
from pyconsole import *

print(Color.BrightRed + "I'm bright red!")
```
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
Please make sure to update tests as appropriate.
## License
[MIT License](https://choosealicense.com/licenses/mit/)
