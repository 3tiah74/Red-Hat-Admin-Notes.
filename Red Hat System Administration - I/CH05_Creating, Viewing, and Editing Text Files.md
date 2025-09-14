## I/O Redirection & Pipelines

### Standard Streams
| Stream    | FD | Default Destination      |
|-----------|----|--------------------------|
| **stdin** | 0  | Keyboard input           |
| **stdout**| 1  | Normal output to screen  |
| **stderr**| 2  | Error messages to screen |

---

### Redirecting Output
| Command               | Description                                   |
|-----------------------|-----------------------------------------------|
| `> file`             | Redirect **stdout** to a file (overwrite).    |
| `>> file`            | Append **stdout** to a file.                  |
| `2> file`            | Redirect **stderr** to a file.                |
| `2>&1` or `&> file`  | Redirect both **stdout** and **stderr**.       |
| `> /dev/null`        | Discard output (send to “black hole”).         |

---

### Pipelines (`|`)
Connect the **stdout** of one command to the **stdin** of another.

**Examples**
**echo "foo bar baz" | wc -w** # → 3 words  
**ls -t | head -n 10 > /tmp/files.txt** # 10 newest files → /tmp/files.txt
# Vim Text Editor

## Modes
| Mode              | Purpose                    | Enter Key(s)                |
|-------------------|----------------------------|------------------------------|
| **Command (Normal)** | Navigate & run commands     | `Esc`                        |
| **Insert**          | Type and edit text         | `i`, `a`, `I`, `A`, `o`, `O` |
| **Extended (Ex)**    | Save, quit, run commands   | `:`                          |
| **Visual**          | Select text blocks         | `v`, `Shift+V`, `Ctrl+V`     |

---

## Command (Normal) Mode

### Movement
- `h` → left, `j` → down, `k` → up, `l` → right  
- `^` → start of line, `$` → end of line  
- `G` → last line, `1G` → first line

### Editing
- `yy` → copy line  
- `dd` → delete line  
- `dw` → delete word  
- `x` → delete character  
- `p` → paste  
- `u` → undo  
- `J` → join with next line

### Searching
- `/pattern` → search forward  
- `?pattern` → search backward  
- `n` → next match  
- `N` → previous match

---

## Insert Mode
- `i` → insert before cursor  
- `a` → append after cursor  
- `I` → insert at beginning of line  
- `A` → append at end of line  
- `o` → new line below  
- `O` → new line above

---

## Extended (Ex) Mode
- `:w` → save  
- `:q` → quit  
- `:wq` or `:x` or `ZZ` → save & quit  
- `:q!` → quit without saving  
- `:set number` / `:set nonumber` → toggle line numbers  
- `:%s/old/new/g` → replace all “old” with “new”  
- `:!command` → run a shell command

---

## Visual Mode
Used to highlight and act on blocks of text.

| Enter Key | Type            | Description                       |
|-----------|-----------------|-----------------------------------|
| `v`       | Character Mode  | Select text character by character |
| `Shift+V` | Line Mode       | Select entire lines               |
| `Ctrl+V`  | Block Mode      | Select rectangular block          |

### Actions
- `d` → delete (cut)  
- `y` → yank (copy)  
- `p` → paste/replace  
- `c` → change then enter Insert mode  
- `u` → undo last change

## Shell Variables

Shell variables store temporary data—like text, numbers, or paths—inside a terminal session.

### Assign & View
| Action                 | Command / Example                                  |
|------------------------|-----------------------------------------------------|
| **Assign value**       | **VAR=value** (no spaces) &nbsp;&nbsp; e.g. **COUNT=40** |
| **Show value**         | **echo $VAR** &nbsp;&nbsp; e.g. **echo $COUNT**     |
| **List all variables** | **set \| less**                                     |

*Variable names may include letters, numbers, and underscores.*  
*These variables exist only in the current shell session.*

---

### The `PATH` Environment Variable
- Holds a **colon-separated** list of directories to search for executables.
- When you type a command (e.g., **ls**), the shell checks each directory in **$PATH** in order.

Example: **echo $PATH**

---

### Make Variables Permanent
Add to your **~/.bashrc** (or **~/.bash_profile**) and export:
**export EDITOR=nano**  
This ensures the variable is set every time you start a new shell.

---

### Remove or Unexport
| Action                    | Command                                  |
|---------------------------|-------------------------------------------|
| **Remove completely**     | **unset VAR**                             |
| **Unexport (keep local)** | **export -n VAR** (stops inheritance)     |
