Every file and directory in Linux has a defined set of permissions that control who can access it and what they can do.

- Each file has an **owner** and is assigned to a **group**.
- Only the file's **owner** or the **root** user can change its permissions.
- Permissions are managed for three categories of users:
  1. **User (u)**: The owner of the file.
  2. **Group (g)**: Other users who are members of the file's group.
  3. **Other (o)**: All other users on the system.

The **`ls -l`** command provides a detailed, long-format listing of files and directories.  
Example output for a file named **test**:

-rwxr-x--- # walbert support 0 Oct 31 11:06 test

- **File Type**: The first character. **`-`** = regular file, **`d`** = directory.
- **Permissions**: Next nine characters (`rwxr-x---`), grouped as:
  - **`rwx`**: Permissions for the **User** (owner).
  - **`r-x`**: Permissions for the **Group**.
  - **`---`**: Permissions for **Other** users.
- **# of Hard Links**: Number of hard links to the file.
- **Owners**: **User** owner (`walbert`) and **Group** owner (`support`).
- **File Size**: File size in bytes.
- **Last Modify Time**: Last time the file was modified.
- **File Name**: Name of the file or directory (`test`).

### Useful Commands
- **`ls -l`**: Shows detailed, long-format listing for files and directory contents.
- **`ls -ld`**: Shows detailed info for a **directory itself**, not its contents.

### Permission Types and Effects

- **`r` (read)**  
  - *File*: Contents of the file can be read.  
  - *Directory*: Names of files inside the directory can be listed.

- **`w` (write)**  
  - *File*: Contents of the file can be changed.  
  - *Directory*: Files inside can be created or deleted.

- **`x` (execute)**  
  - *File*: File can be executed as a command.  
  - *Directory*: Directory can be accessed (you can `cd` into it and interact with its files).

## Changing Permissions with `chmod`

### Symbolic Method
This method uses letters and symbols to modify permissions.

**Who to change**
- **`u`**: user/owner
- **`g`**: group
- **`o`**: other
- **`a`**: all

**What to do**
- **`+`**: add a permission
- **`-`**: remove a permission
- **`=`**: set the permissions exactly

**Which permission**
- **`r`**: read
- **`w`**: write
- **`x`**: execute

**Examples**
- **`chmod g+w file.txt`**: Adds write permission for the group.
- **`chmod o-r file.txt`**: Removes read permission for others.
- **`chmod u=rw,go=r file.txt`**: Sets user permissions to read/write, and group/other permissions to read only.

---

### Numeric (Octal) Method
This method uses a three-digit number to represent permissions for user, group, and other.

**Values**
- read (**`r`**) = 4  
- write (**`w`**) = 2  
- execute (**`x`**) = 1  

Combine these numbers for each category:
- **`rwx`** = 4 + 2 + 1 = **7**
- **`r-x`** = 4 + 0 + 1 = **5**

**Examples**
- **`chmod 754 file1`**: Sets permissions to **rwxr-xr--**  
  - 7 for User (4+2+1)  
  - 5 for Group (4+0+1)  
  - 4 for Other (4+0+0)
- **`chmod -R 755 dir1`**: The **-R** (recursive) option applies the change to the directory and everything inside it.

---

### Required Permissions for Common Commands

- **`cd`**  
  - *Source directory*: **x**  
  - *Source file*: N/A  
  - *Target directory*: N/A

- **`ls`**  
  - *Source directory*: **x, r**  
  - *Source file*: N/A  
  - *Target directory*: N/A

- **`mkdir`**, **`rmdir`**  
  - *Source directory*: **x, w**  
  - *Source file*: N/A  
  - *Target directory*: N/A

- **`cat`**, **`less`**  
  - *Source directory*: **x**  
  - *Source file*: **r**  
  - *Target directory*: N/A

- **`cp`**  
  - *Source directory*: **x**  
  - *Source file*: **r**  
  - *Target directory*: **x, w**

- **`cp -r`**  
  - *Source directory*: **x, r**  
  - *Source file*: **r**  
  - *Target directory*: **x, w**

- **`mv`**  
  - *Source directory*: **x, w**  
  - *Source file*: *none*  
  - *Target directory*: **x, w**

- **`vi`**  
  - *Source directory*: **x, r**  
  - *Source file*: **r, w**  
  - *Target directory*: N/A

- **`rm`**  
  - *Source directory*: **x, w**  
  - *Source file*: *none*  
  - *Target directory*: N/A
## Changing Ownership

- **`chown`**: Change the **user owner** of a file.  
  - Only the **root** user can change ownership.  
  - **Usage**: **`chown <new_user> <file>`**  
  - To change both **user and group**: **`chown <user>:<group> <file>`**

- **`chgrp`**: Change the **group** of a file.  
  - Can be done by the **file’s owner** or **root**.  
  - **Usage**: **`chgrp <new_group> <file>`**

- **Recursive Option**:  
  - Add **`-R`** to either command to apply the change to a directory **and all its contents**.
## Special Permissions

- **`suid (u+s)`**: File runs with the **owner’s** privileges. *(No effect on directories)*  
- **`sgid (g+s)`**: File runs with the **group’s** privileges.  
  - On directories: new files inherit the directory’s group.
- **`sticky bit (o+t)`**: On directories, users can delete **only their own files** even if others have write access.

**Set with `chmod`**
- Symbolic: **`chmod u+s file`**, **`chmod g+s dir`**, **`chmod o+t dir`**
- Numeric (fourth digit): **4 = suid**, **2 = sgid**, **1 = sticky**  
  - Example: **`chmod 2770 dir`** → sets sgid and permissions `rwxrws---`.

---

## Default Permissions (umask)

- **Base defaults:** Directories `777`, Files `666`.
- **Default umask values:**
  - **Regular user:** `002`  → new directory = `775`, new file = `664`.
  - **Root user:**    `022`  → new directory = `755`, new file = `644`.
- **Final permissions = Base − umask**  
  - Example: umask `022` → new dir `755`, new file `644`.
- **`umask`**: View current umask value.
- **Set permanently:** Add **`umask <value>`** to **`~/.bashrc`** and re-login.
