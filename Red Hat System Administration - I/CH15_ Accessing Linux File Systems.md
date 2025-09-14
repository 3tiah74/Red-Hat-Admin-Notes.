### Disk Usage and Storage

- **`df -h`**: Shows available disk space in a human-readable format.
- **`du -h`**: Shows disk usage of the current directory and its subdirectories in a human-readable format.
- **`lsblk`**: Lists information about all available block devices, such as hard drives and their partitions.

### Locate Command

- **`locate`**: Quickly finds files by searching a pre-built database.
  - **`-i`**: Makes the search case-insensitive.
  - **`-n <number>`**: Limits the number of search results returned.
- **`updatedb`**: Manually updates the database used by **`locate`**.

### Find Command

- **`find`**: Performs a slower but accurate real-time search for files based on various criteria:
  - **`-name <pattern>`**: Searches for files by exact name.
  - **`-iname <pattern>`**: Searches by name, ignoring case.
  - **`-size <size>`**: Searches for files by size.
  - **`-type <type>`**: Searches for files by their type (e.g., `f` for file, `d` for directory).
  - **`-perm 755`**: Searches for files with exact permissions.
  - **`-user <username>`**: Searches for files belonging to a specific user.
  - **`-group <groupname>`**: Searches for files belonging to a specific group.
  - **`-uid <uid>`**: Searches for files by user ID.
  - **`-gid <gid>`**: Searches for files by group ID.
