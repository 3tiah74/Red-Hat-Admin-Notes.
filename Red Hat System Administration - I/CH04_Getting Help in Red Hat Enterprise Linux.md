## Getting Help in Linux 

### Quick Help
- **`<command> --help`**: Shows a brief summary of usage and options.  
  *Example:* **`who --help`**

### Find Command Location
- **`whereis <command>`**: Displays the path of the binary, source, and manual page.  
  *Example:* **`whereis passwd`**

### Detailed Documentation
- **`man <command>`**: Opens the full manual page with comprehensive documentation.  
  *Example:* **`man ls`**

---

## Understanding `man` Pages

### Manual Sections
Each man page belongs to a numbered section:

1. **User commands** (e.g., `ls`)  
2. **System calls**  
3. **Library functions**  
4. **Special files** (e.g., `/dev/null`)  
5. **File formats & conventions** (e.g., `man 5 passwd`)  
6. **Games**  
7. **Miscellaneous** (standards, protocols, etc.)  
8. **System administration commands** (root only)  
9. **Linux kernel API**

### Page Layout
Common headings inside a man page:
- **NAME** – One-line summary  
- **SYNOPSIS** – Command syntax & arguments  
- **DESCRIPTION** – What the command does  
- **OPTIONS** – All command-line options explained  
- **EXAMPLES** – Practical usage examples  
- **FILES** – Related files  
- **SEE ALSO** – Related commands  
- **BUGS** – Known issues  
- **AUTHOR** – Documentation author
