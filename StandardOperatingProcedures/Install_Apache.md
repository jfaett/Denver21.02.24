### Standard Operating Procedure (SOP) for Apache Installation and Configuration on RHEL Server

#### Purpose:
To standardize the installation of Apache HTTP Server, enable the service at boot, configure firewall rules to allow web traffic, and safely restart the RHEL server.

#### Scope:
This SOP is intended for use by the Level 1 Support Operations Team within an enterprise organization managing RHEL servers.

#### Prerequisites:
- A RHEL server with internet access.
- Sudo or root access to the server.
- Basic familiarity with the Linux command line.

#### Estimated Time: 15 minutes

#### Procedure:

1. **Log into the RHEL Server**
   - Use SSH to connect to your RHEL server.
     ```bash
     ssh user@your-server-ip
     ```
   - Ensure you have root privileges or sudo access.

2. **Update the System** (Estimated Time: 2 minutes)
   - Update your system to ensure all packages are up to date.
     ```bash
     sudo yum update -y
     ```

3. **Install Apache HTTP Server** (Estimated Time: 3 minutes)
   - Install the Apache package using the YUM package manager.
     ```bash
     sudo yum install httpd -y
     ```
   - Verify the installation.
     ```bash
     httpd -v
     ```

4. **Enable and Start Apache Service** (Estimated Time: 1 minute)
   - Enable the Apache service to start on boot.
     ```bash
     sudo systemctl enable httpd
     ```
   - Start the Apache service.
     ```bash
     sudo systemctl start httpd
     ```

5. **Open Firewall Ports for Web Traffic** (Estimated Time: 3 minutes)
   - Allow HTTP (port 80) and HTTPS (port 443) through the firewall.
     ```bash
     sudo firewall-cmd --permanent --add-service=http
     sudo firewall-cmd --permanent --add-service=https
     ```
   - Reload the firewall to apply changes.
     ```bash
     sudo firewall-cmd --reload
     ```

6. **Restart the Server** (Estimated Time: 3 minutes)
   - It's often a good practice to restart the server to ensure all configurations are applied correctly. However, schedule this step during a maintenance window to avoid service disruption.
     ```bash
     sudo reboot
     ```

7. **Verify the Apache Service Status** (Post-Restart Check, Estimated Time: 1 minute)
   - After the server restarts, log back in and check the status of the Apache service to ensure it's running.
     ```bash
     sudo systemctl status httpd
     ```

#### Completion:
- The Apache HTTP Server is installed and running on the RHEL server.
- The service is enabled to start on boot.
- Firewall ports for HTTP and HTTPS are configured and open.
- The server has been restarted and verified to be operational with the Apache service running.

#### Documentation:
- Document the installation process, including any issues encountered and how they were resolved.
- Update the server inventory to include this server and its services.

#### Notes:
- Always check for any RHEL-specific or Apache version-specific considerations.
- Ensure to follow security best practices, including using firewalls and secure connections.
