### Managing systemd Services

- **`systemctl list-units --type=service`**: Displays all active services.
- **`systemctl status "service"`**: Shows the status of a specific service.

### Starting, Restarting, and Masking Services

- **`systemctl start "service"`**: Starts a specific service.
- **`systemctl restart "service"`**: Restarts a specific service.
- **`systemctl mask "service"`**: Masks (disables) a service so it cannot be started until it is unmasked.
- **`systemctl enable "service"`**: Enables the service to start automatically at boot.
- **`systemctl disable "service"`**: Disables the service from starting automatically at boot.
