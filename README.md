# Nextcloud Whiteboard

This Docker Compose file helps you run [Nextcloud's Whiteboard app](https://apps.nextcloud.com/apps/whiteboard).

## Installation & configuration

### Docker

1. Download the Compose file:

   `git clone https://github.com/Longjogger/nextcloud-whiteboard /your/target/folder`

2. Set the environment variables:

   `vi /your/target/folder/.env`

3. Run the Docker Compose file:

   `docker compose -f /your/target/folder/compose.yaml up -d`

4. Check the state:

   `docker ps -a`

### Apache

1. Configure your Nextcloud Apache configuration file:

   Open the Apache configuration:

   `sudo vi /etc/apache2/sites-available/nextcloud.conf`

   Add the following line to your virtual host configuration:
   
   `ProxyPass /whiteboard/ http://localhost:3002/ upgrade=websocket`

2. Reload the configuration:

   `sudo systemctl reload-or-restart apache2.service`

### Nextcloud

1. Download the Whiteboard app from Nextcloud's App Store.

2. Open the Whiteboard administration settings:

   - Set WebSocket server URL: `https://your-nextcloud-domain.de/whiteboard`
   - Shared Secret: `some_random_secret`

   Save!