### Network Interfaces and IP Information

- **`ip link`**: Displays all network interfaces.  
  - Add **`-s`** to show detailed statistics for each interface.
- **`ip address show`**: Displays IP address information.

### Connectivity Tests

- **`ping -c <x>`**: Sends a specified number of ping requests.
- **`tracepath <host>`**: Traces the network path to a host and shows where any issues occur along the route.

### NetworkManager (nmcli)

- **`nmcli device status`**: Shows the status of all network interfaces.
- **`nmcli connection show`**: Displays details of all saved connections.
- **`nmcli connection add`**: Adds a new network connection.

### Hostname Management

- **`hostname`**: Displays the current system hostname.
- **`hostnamectl set-hostname <name>`**: Sets a new hostname.
- **`hostnamectl status`**: Shows the current hostname status.
