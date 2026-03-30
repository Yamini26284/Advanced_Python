### Handling filesystem via Terminal
##### Method 1 
The Direct Command
You can run the file without leaving your current directory by providing the relative path to the file.

If your folder structure looks like main/subfolder/your_file.py, run this:

    python subfolder/your_file.py
##### Method 2
To move the terminal's focus into that subfolder, you use the cd (Change Directory) command.

Move into the subfolder:

    cd subfolder_name

Verify you are in the right place:

    Windows: type dir

Run the file now that you are "inside":

    python your_file.py

### Case Sensitivity : depends on your OS
The terminal itself isn't what decides case sensitivity; it’s the File System underneath it. Here is how it breaks down across the major platforms:

1.  **Linux (Case-Sensitive)**
    On Linux, the terminal is strictly case-sensitive.

    Folders: MyFolder and myfolder are two completely different directories.

    Files: Script.py and script.py are two different files.

    Behavior: If you try to cd myfolder but the folder is named MyFolder, the terminal will throw a "No such file or directory" error.

2.  **Windows (Case-Insensitive)**
    Windows (using the NTFS file system) is case-insensitive but case-preserving.

    Folders & Files: Folder, FOLDER, and folder are all seen as the same entity.

    Behavior: You can type cd myfolder even if it’s named MyFolder, and it will work perfectly. However, Windows will "remember" that you capitalized it when it displays the name in the file explorer. 

3.  **macOS (Mostly Case-Insensitive)**
    By default, Mac uses a file system (APFS) that behaves like Windows: case-insensitive.

    Behavior: MyFile.txt and myfile.txt are treated as the same file.

    Note: You can technically format a Mac drive to be case-sensitive, but it is rare and often breaks apps (like Adobe or Steam).
### Python - Executing of code
1.  The Compilation Phase (Source Code to Bytecode)
    When you run a Python file, the first thing the CPython (the standard Python implementation) interpreter does is check for a compiled version of your code.[This happens all at once, not line by line.]

    Syntax Checking: The compiler parses your .py file. If there is a syntax error, it stops here.

    Bytecode Generation: If the syntax is correct, the compiler translates your human-readable code into Bytecode.

    The .pyc File: This bytecode is stored in a directory named __pycache__. These files end in .pyc (compiled Python).

2.  What exactly is Bytecode?
    Bytecode is not machine code (code that your CPU can understand directly). Instead, it is a set of lower-level, platform-independent instructions designed specifically for the Python Virtual Machine (PVM).

    Why use Bytecode? It makes Python portable. You can generate bytecode on a Windows machine and run it on a Linux machine without changes, as long as both have a PVM installed.

3.  The Interpretation Phase (PVM)
    Once the bytecode is ready, it is sent to the Python Virtual Machine (PVM). This is the heart of Python's execution engine.

    The PVM is a giant loop that iterates through your bytecode instructions one by one, which happens during runtime

    It converts each bytecode instruction into Machine Code (binary) that your computer’s processor can actually execute.

    This is the "interpreted" part of the process, which is why Python is generally slower than languages like C++ that compile directly to machine code beforehand.

Note : The label "interpreted" in Interpreted language refers to when the translation happens and who does the final execution.

1. The "When": Runtime vs. Build Time
    In a purely compiled language (like C++ or Go), you must run a "build" or "compiler" step to create an executable file (like an .exe) before you can run the program. If you don't do this, the program literally doesn't exist in a runnable state.

    In Python, the compilation to bytecode happens automatically and transparently the moment you hit "run." Because the user experience is "I write code and it immediately runs," it fits the definition of an interpreted workflow.
### Seperators

**separators** are primarily used in the print() function to control output formatting and in string methods like split() and join() for parsing and combining strings.

The sep parameter in the built-in print() function defines the separator between multiple values passed to it.

*Default behavior*: By default, print() separates values with a single space (" ").

*Custom separators*: You can specify any string as a separator

### Type Casting
Type Casting is essentially the process of converting one data type into another 

**Implicit Type Casting** : Implicit casting happens automatically. The Python interpreter is smart enough to convert a "lower" data type (like an integer) to a "higher" data type (like a float) to prevent data loss.

How it works: Python does the work for you.

Why it happens: To make sure you don't lose the decimal precision in a calculation.
    num_int = 10    # Integer
    num_float = 1.5 # Float

    # Python automatically converts num_int to a float before adding
    result = num_int + num_float 

    print(result)       # Output: 11.5
    print(type(result)) # Output: <class 'float'>
**Explicit Type Casting**  : Explicit casting (also called Type Conversion) is when you tell the computer exactly what type you want a value to be. You use built-in functions like int(), float(), or str().

How it works: You wrap the variable in a constructor function.

Why it happens: Because sometimes Python won't "guess" correctly, or you're dealing with external data (like a user input or an API response) that comes in as the wrong type.
    price_str = "199"  # This is a String (text)
    tax = 0.18

    # result = price_str * tax  <-- This would throw an ERROR! 

    # Explicitly converting string to integer to perform math
    total_price = int(price_str) * (1 + tax)

    print(total_price) # Output: 234.82

### len()
The len() function is actually one of the most versatile tools in Python. It isn't limited to just strings or arrays; it can be used with almost any data type that holds a collection of items.

In Python, we call these "Sized" objects. Think of len() as a tape measure: if you can count the "pieces" inside a container, len() can measure it.

**1. Where can you use it?**
Beyond strings, you will use len() constantly with these common data types:

    Lists (Arrays): To count how many items are in a list.

    len([10, 20, 30]) → 3

    Dictionaries: To count how many "Key-Value" pairs exist.

    len({"name": "Priya", "age": 22}) → 2

    Tuples: Similar to lists, but they can't be changed.

    len((1, 2)) → 2

    Sets: To count unique items.

    len({1, 2, 2, 3}) → 3 (because sets remove duplicates!)

**2. What are the limits? (Where it fails)**
You cannot use len() on data types that represent a single, solid value rather than a collection.

    Integers/Floats: You can't ask "how long is the number 100?" Python will give you a TypeError.

    len(100) → Error (If you want to count digits, you'd have to turn it into a string first!)

    Booleans: You can't measure True or False.

    len(True) → Error