## Linux Users, Groups, and Permissions

### Users
- **Types**
  - **Superuser (root)**: Full system access; can read/write any file and change any setting.
  - **System users**: Accounts used by services (e.g., `apache`, `mysql`) to run background processes.
  - **Regular users**: Standard login accounts for people.
- **UID Ranges**
  - `0` → root  
  - `1–999` → system users  
  - `1000+` → regular users (default range for new human users)
- **`/etc/passwd` Fields**  
  Format: `username:x:UID:GID:comment:home:shell`  
  - `x` means the encrypted password is stored in `/etc/shadow`.

### Useful Commands
- **`id`**: Show UID, GID, and all group memberships.  
  - `id` → current user  
  - `id <user>` → specified user

### Groups
- **Purpose**: Allow shared permissions for multiple users at once.
- **Primary group**: The default group for a user’s files.
- **Supplementary groups**: Extra groups a user belongs to for additional access.
- **`/etc/group` Fields**  
  Format: `group_name:x:GID:member1,member2,...`

### Switching or Elevating Privileges
- **`su <user>`**: Switch to another user (requires that user’s password).  
  - `su` or `su -` → switch to root’s environment.
- **`sudo`**: Run commands as root using your own password.  
  - Config file: **`/etc/sudoers`** (edit safely with **`visudo`**).  
  - Example rule: **`%wheel ALL=(ALL) ALL`** → members of `wheel` group can run any command as any user.

---

## Managing Users

### Creating Users
- **`useradd <username>`**: Creates a user, a home directory under `/home`, and a private group.
- New accounts have no password until one is set with **`passwd <username>`**.
- Default settings (UID range, home path, shell) are defined in **`/etc/login.defs`**.

### Modifying Users
- Change primary group: **`usermod -g <group> <user>`**
- Add to supplementary group(s): **`usermod -aG <group> <user>`**  
  *(use `-a` to append without removing current groups)*

### Securing Accounts
- **`/etc/shadow`**: Stores encrypted passwords and password-aging info  
  (last change date, min/max days, warning period, inactivity limit).
- Configure password aging:  
  **`chage -m <min> -M <max> -W <warn> -I <inactive> <user>`**
- Lock an account: **`usermod -L <user>`**
- Set account expiration date: **`usermod -e YYYY-MM-DD <user>`**
- Disable interactive login (service accounts):  
  **`usermod -s /sbin/nologin <user>`**

---

## Managing Groups
- Create group: **`groupadd [-g <GID>] <group>`**
- Rename group: **`groupmod -n <newname> <oldname>`**
- Delete group: **`groupdel <group>`**
