# ft_onion (Tor Web Server)

`ft_onion` is a project that allows you to run a web server on the Tor network. It utilizes Nginx to configure the web server and provides access to a static webpage through a .onion address. The server also enables SSH access on port 4242 for remote administration. It also displays a simple html page. The whole project has been done in a Linux Docker container, here are the instructions to build it using the files provided.

## Prerequisites

Before running the program, ensure you have the following dependencies installed:

- Linux-based operating system (e.g., Ubuntu)
- Nginx
- OpenSSH server
- Tor

## Usage

To set up and run the Tor web server, follow these steps:

1. Install Nginx, OpenSSH server, and Tor using the package manager of your Linux distribution.
2. Clone or download the project repository to your server.
3. Configure Nginx by updating the nginx.conf file with the appropriate settings. Make sure to set the correct paths and options. Sample configurations are provided in the repository.

4. Place your static webpage content in the /var/www/html directory. Replace the existing index.html file with your own.
5. Enable access to the static page via HTTP on port 80. By default, Nginx listens on port 80, so no additional configuration is needed.
6. Enable access to the server via SSH on port 4242. Update the SSH server configuration file (sshd_config) to allow SSH access on port 4242.
7. Start the Nginx service using the following command:
`sudo systemctl start nginx`
8. Start the SSH service using the following command:
`sudo systemctl start ssh`
9. Verify that the Nginx and SSH services are running:
   `sudo systemctl status nginx`
   `sudo systemctl status ssh`.
Ensure that the services are active and running without any errors.
10. Configure Tor by updating the torrc file with the necessary settings. The file should be located in the Tor configuration directory (typically /etc/tor/). Sample configurations are provided in the repository.
11. Restart the Tor service to apply the new configuration:
`sudo systemctl restart tor`
12. Wait for Tor to establish a connection to the Tor network. You can check the status using the following command:
`sudo systemctl status tor`
Ensure that Tor is active and successfully connected to the network.
13. Once Tor is connected, it will generate a .onion address for your web server. The address can be found in the Tor log file (/var/log/tor/log) or by running the following command:
`sudo cat /var/lib/tor/hidden_service/hostname`
This address will be of the form xxxxxxx.onion.
14. Access your web server by entering the generated .onion address in the Tor browser or any other Tor-enabled browser. The content displayed on the webpage will be the one you placed in the index.html file.

## Accessing the Webpage

To access the static webpage hosted on your Tor web server, follow these steps:

1. Connect to the server via SSH using the following command:
`ssh -p 4242 username@server_ip`
Replace `username` with your SSH username and `server_ip` with the IP address of your server.
2. Once connected to the server, navigate to the web server's root directory:
`cd /var/www/html`. Remember to replace the index.html file in /var/www/html with the one provided.
3. Open a web browser and enter the generated .onion address in the URL bar. The webpage content will be displayed.

## Files Uploaded

The following files are uploaded for this progect:

- `index.html`: The static webpage content file.
- `nginx.conf`: The Nginx configuration file.
- `sshd_config`: The OpenSSH server configuration file.
- `torrc`: The Tor configuration file.
