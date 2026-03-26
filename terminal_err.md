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