### tar Options

- **`-c`**, **`--create`**: Create a new archive.
- **`-x`**, **`--extract`**: Extract from an existing archive.
- **`-t`**, **`--list`**: List the contents of an archive.
- **`-v`**, **`--verbose`**: Show which files are archived or extracted.
- **`-f <file>`**, **`--file=<file>`**: Specify the archive file name to use or create (must be followed by the filename).
- **`-p`**, **`--preserve-permissions`**: Preserve file and directory permissions when extracting (ignores umask).
- **`-z`**, **`--gzip`**: Use gzip compression (`.tar.gz`).
- **`-j`**, **`--bzip2`**: Use bzip2 compression (`.tar.bz2`), usually better compression than gzip.
- **`-J`**, **`--xz`**: Use xz compression (`.tar.xz`), typically achieves the best compression ratio.

### scp

- **`scp <source> <user>@<server>:/path`**: Copies files to a server over an SSH connection.
