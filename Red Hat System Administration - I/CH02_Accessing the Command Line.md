### Command Prompt Symbols
- The **`$`** character at the end of a command prompt indicates you are a **regular user**.
- The **`#`** character indicates you are the **superuser (root)**.

### Structure of a Linux Command
A Linux command typically consists of three parts in order:
1. **Command**: The action you want to perform.
2. **Option(s)**: Modifies the behavior of the command.
3. **Argument(s)**: The target that the command acts upon.

### Common Commands
- **`passwd`**: Change a user's password. A regular user can change their own password, while the superuser can change any user's password.
- **`date`**: Displays the current date and time. The output can be formatted using the **`+`** sign.
- **`file`**: Scans a file to determine and display its type.
- **`cat`**: Displays the content of one or more files or concatenates them.
- **`head`** / **`tail`**: Show the beginning or end of a file (default 10 lines). Use **`-n`** to specify a different number of lines.
- **`less`**: Displays a file one page at a time, allowing scrolling.
- **`history`**: Shows a numbered list of previously executed commands.
- **`!`**: Executes commands from history.
    - **`!number`**: Re-runs the command with that specific history number (e.g., **`!54`**).
    - **`!string`**: Re-runs the most recent command starting with that string (e.g., **`!ls`**).
- The **`\`** character allows you to **continue a long command on a new line** for better readability.

### **TAB Completion**
- Press **TAB** once to auto-complete a command or filename if unique.
- Press **TAB** twice to show all possible completions if not unique.

### Command Line Shortcuts
- **`Ctrl + A`**: Jump to the beginning of the command line.
- **`Ctrl + E`**: Jump to the end of the command line.
- **`Ctrl + U`**: Clear the line from the cursor to the beginning.
- **`Ctrl + K`**: Clear the line from the cursor to the end.
- **`Ctrl + Left Arrow`**: Jump to the beginning of the previous word.
- **`Ctrl + Right Arrow`**: Jump to the end of the next word.
- **`Ctrl + R`**: Search through your command history.
