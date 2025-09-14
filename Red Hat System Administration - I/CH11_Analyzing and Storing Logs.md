### Log Files and Configuration

- **`/var/log`**: Directory where system log files are stored.
- **`/etc/rsyslog.conf`**: Configuration file that defines how logs are written.

### Writing and Viewing Logs

- **`logger`**: Used to write custom messages into the system logs.
- **`journalctl -n`**: Displays the most recent logs of all types.
- **`journalctl -p <priority>`**: Shows logs filtered by a specific priority level.
- **`journalctl --since <date>`**: Displays logs starting from a specified date.
- **`journalctl _PID=<x>`**: Shows logs for a specific process ID.
- **`journalctl _UID=<x>`**: Shows logs for a specific user ID.
- **`journalctl _SYSTEMD_UNIT=<unit>`**: Shows logs for a specific systemd service unit.

### Timezone Management

- **`timedatectl`**: Displays the current system timezone and time settings.
- **`timedatectl set-timezone <zone>`**: Changes the system timezone.
