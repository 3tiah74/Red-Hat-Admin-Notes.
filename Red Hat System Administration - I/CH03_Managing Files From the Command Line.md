## Linux File System, Navigation, and Listing Commands

### File Naming
- **Case-sensitive**: `File.txt` ≠ `file.txt`
- **Hidden files**: Names beginning with `.` (dot) are hidden by default.
- **Length limit**: Up to 255 characters.

**Good practices**
- Use descriptive names: `september_sales_report.csv`
- Stick to letters, numbers, underscores `_`, hyphens `-`, and periods `.`

**Avoid**
- Spaces (use `_` or `-` instead).
- Shell metacharacters with special meanings: `* ? > < ; & ! ( ) { }`

---

### File Types (first character in `ls -l`)
| Symbol | Type                        |
|--------|------------------------------|
| `-`    | Regular file                |
| `d`    | Directory                   |
| `l`    | Symbolic link (shortcut)    |
| `c`    | Character device            |
| `b`    | Block device               |
| `s`    | Socket                      |
| `p`    | Named pipe (FIFO)           |

---

### Key Directories
| Path    | Purpose                                                        |
|---------|-----------------------------------------------------------------|
| `/`     | Root of the entire file system.                                |
| `/home` | Home directories for regular users.                             |
| `/root` | Home directory for the root user.                               |
| `/usr`  | Installed software, libraries, user commands (`/usr/bin`).      |
| `/etc`  | System-wide configuration files.                                |
| `/var`  | Variable data: logs, databases, websites.                       |
| `/tmp`  | Temporary files (often cleared on reboot).                      |
| `/boot` | Bootloader files and Linux kernel.                              |
| `/dev`  | Device files representing hardware.                             |
| `/run`  | Runtime data for processes since last boot.                     |

---

### Paths
- **Absolute path**: Starts at `/` and gives the full location.  
  Example: `/home/karim/Documents/report.txt`
- **Relative path**: Starts from the current directory.  
  Example (if inside `/home/karim`): `Documents/report.txt`

---

### Navigation Commands
- **`pwd`**: Show the full absolute path of the current directory.
- **`cd <dir>`**: Change directory.

Special `cd` shortcuts:
- `cd` or `cd ~` → Home directory
- `cd ~username` → Another user’s home
- `cd -` → Previous directory
- `cd ..` → Up one level
- `cd ../..` → Up two levels

---

### Listing Files with `ls` and `dir`

Both **`ls`** and **`dir`** list the contents of a directory and share many options:

| Option | Description |
|--------|------------|
| **-l** | Long format: shows permissions, owner, size, and modification date. |
| **-a** | Include hidden files (names starting with `.`). |
| **-R** | Recursively list all subdirectories. |
| **-h** | Human-readable sizes (KB, MB, GB). Often combined with `-l` → `ls -lh`. |
| **-t** | Sort by modification time, newest first. |
| **-r** | Reverse the sort order. |
| **--color** | Add colors to distinguish file types (e.g., directories in blue, executables in green). |

- **`dir`** works almost the same as `ls`, providing a directory listing with these same options.

## Basic File and Directory Management

### Core Commands
| Command | Task |
|--------|------|
| `touch file` | Create empty file / update timestamp |
| `mkdir directory` | Create directory |
| `cp source destination` | Copy file |
| `cp -r source_dir new_dir` | Copy directory (recursive) |
| `mv source destination` | Move or rename |
| `rm file` | Remove file |
| `rm -r directory` | Remove non-empty directory |
| `rmdir directory` | Remove empty directory |

**Key `rm` options**  
- `-f` : Force deletion without confirmation  
- `-r` : Recursively delete a directory and all its contents  

---

## Inodes and Links

### Inode
An **inode** stores a file’s metadata (type, permissions, owner/group IDs, size, timestamps, hard-link count) and pointers to its data blocks.  
It does **not** store the filename itself.

---

### Links
A **link** is another name that points to a file’s inode.

#### Hard Link
- Points **directly to the same inode** as the original file.  
- Create with: `ln target_file hardlink_name`  
- File data remains until **all** hard links are removed.

#### Soft (Symbolic) Link
- A small file containing a **path** to the target.  
- Create with: `ln -s target_file softlink_name`  
- Breaks if the target is moved or deleted.

| Command/Feature         | Soft Link (Symbolic)        | Hard Link                          |
|-------------------------|-----------------------------|-------------------------------------|
| Inode                  | Different from target       | Same as target                     |
| Points to              | File **path**               | File **inode**                     |
| Cross-filesystem       | Allowed                     | Not allowed                        |
| If target is deleted   | Becomes broken              | Data remains accessible            |
| Can link directories   | Yes                         | No                                  |

## Searching Text with `grep`

`grep` scans files or input for a **pattern** and prints matching lines.

### Common Options
| Command / Option | Purpose |
|------------------|--------|
| `-i` | Case-insensitive search |
| `-v` | Invert match (show lines **not** matching) |
| `-r` | Recursive search through subdirectories |
| `-n` | Show line numbers of matches |
| `-A3` | Show 3 lines **After** each match |
| `-B3` | Show 3 lines **Before** each match |
| `-e` | Add multiple patterns in one command |

---

## Regular Expressions (Patterns)

Patterns define what to match and can include **metacharacters**.

### Basic Symbols
| Symbol | Meaning |
|--------|--------|
| `.` | Any single character |
| `^` | Start of a line |
| `$` | End of a line |
| `*` | Previous character zero or more times |
| `\` | Escape a special character |
| `()` | Group expressions |
| `?` | Previous character zero or one time |

### Advanced Bracket Expressions
| Pattern | Matches |
|---------|--------|
| `*` | Any string (when used with shell globbing) |
| `?` | Any single character |
| `[abc]` | One character: a, b, or c |
| `[!abc]` | Any character **not** a, b, or c |
| `[[:alpha:]]` | Any letter |
| `[[:lower:]]` | Lowercase letter |
| `[[:upper:]]` | Uppercase letter |
| `[[:digit:]]` | Digit 0–9 |
| `[[:space:]]` | Whitespace (space, tab, etc.) |

---

## Extracting & Manipulating Text

### `cut`
Extract specific columns, fields, or characters.

| Option | Function |
|--------|---------|
| `-d <delimiter>` | Specify field delimiter (e.g., `-d':'`) |
| `-f <fields>` | Show specific fields (columns) |
| `-c <positions>` | Show specific character positions |

Example:  
`cut -d':' -f1 /etc/passwd` → list all usernames.

---

### `tr`
Translate or delete characters.

| Usage | Result |
|-------|-------|
| `echo "hello" \| tr 'a-z' 'A-Z'` | Convert to uppercase → `HELLO` |
| `echo "a b c" \| tr ' ' '\t'` | Replace spaces with tabs |
| `echo "Welcome" \| tr -d 'W'` | Delete `W` → `elcome` |
