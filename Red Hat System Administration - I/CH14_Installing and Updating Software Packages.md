### RPM Package Name Example
```
coreutils - 8.30 - 4.el8 . x86_64 .rpm
	|         |       |         |
  (Name)  (Version)(Release)(Architecture)
```
### RPM Commands

- **`rpm -qa`**: Lists all installed packages.
- **`rpm -qf FILENAME`**: Finds which package provides a specific file.
- **`rpm -q yum`**: Shows the version of the `yum` package currently installed.
- **`rpm -qi yum`**: Displays detailed information about the `yum` package.
- **`rpm -ql yum`**: Lists the files installed by the `yum` package.
- **`rpm -qc yum`**: Lists only the configuration files of the `yum` package.
- **`rpm -qd yum`**: Lists only the documentation files of the `yum` package.
- **`rpm -q --scripts openssh-server`**: Lists shell scripts that run before or after installing/removing a package.
- **`rpm -q --changelog`**: Shows the changelog information for a package.
#### RPM Options
- **`-i`**: Install package(s).  
- **`-v`**: Verbose mode—provides more detailed output.  
- **`-h`**: Displays installation progress with hash marks.

---

### YUM Commands

- **`yum help`**: Displays usage information.  
- **`yum list`**: Shows installed and available packages.  
- **`yum search <KEYWORD>`**: Lists packages with keywords in the name or summary fields.  
- **`yum info <PACKAGENAME>`**: Returns detailed information about a package, including disk space needed.  
- **`yum provides <PATHNAME>`**: Displays packages that match the specified path name (wildcards allowed).  
- **`yum install <PACKAGENAME>`**: Installs a software package and any required dependencies.  
- **`yum update <PACKAGENAME>`**: Updates to a newer version of the specified package (or all packages if none specified).  
- **`yum remove <PACKAGENAME>`**: Removes an installed package and its dependencies if no longer needed.  
- **`yum history`**: Shows a summary of install and remove transactions.