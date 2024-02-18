### Standard Operating Procedure (SOP): Configuring a New User Environment on RHEL

**Objective**: Efficiently configure a new user environment on RHEL, including user creation, password management, application installation, firewall configuration, and server restart.

**Scope**: Operations team responsible for Level 1 support within an enterprise environment.

**Prerequisites**:
- Administrative access to the RHEL server.
- Installation files or repository access for the specified IDE with a web interface.
- Familiarity with the RHEL command-line interface.

#### Steps:

1. **Add a New User**
   ```bash
   sudo adduser newusername
   ```
   - Adds a new user to the system.
   - **Estimated Time**: 2 minutes

2. **Set a Temporary Password**
   ```bash
   sudo passwd newusername
   ```
   - Assigns a temporary password to the new user. You will be prompted to enter and confirm the password.
   - **Estimated Time**: 1 minute

3. **Force Password Reset on Next Login**
   ```bash
   sudo chage -d 0 newusername
   ```
   - Forces the user to change their password the next time they log in.
   - **Estimated Time**: 1 minute

4. **Install an Application (IDE with a Web Interface)**
   - Before Installation:
     ```bash
     sudo yum update
     ```
     - Updates package lists. This command refreshes repository metadata and ensures your system is up-to-date.
   
   - Installation Command:
     ```bash
     sudo yum install application-name
     ```
     - Installs the specified IDE on the user's environment. Replace `application-name` with the actual name of the IDE package.
   - **Estimated Time**: 5-10 minutes, depending on network speed and application size.

5. **Open a Firewall Port for the Application**
   ```bash
   sudo firewall-cmd --zone=public --add-port=port_number/tcp --permanent
   sudo firewall-cmd --reload
   ```
   - Opens the specified port in the firewall for TCP traffic, where `port_number` is the port required by the installed IDE.
   - **Estimated Time**: 2 minutes

6. **Restart the Server**
   ```bash
   sudo reboot
   ```
   - Safely restarts the server to ensure all configurations are applied and services start fresh.
   - **Estimated Time**: 3-5 minutes, depending on the server's hardware and startup processes.

#### Post-Procedure Steps:

- **Verification**: After the server restarts, verify the IDE is accessible through the specified port by attempting to access it from a web browser.
- **User Notification**: Inform the new user that their environment is set up. Provide them with login instructions and prompt them to change their temporary password.
- **Documentation**: Document the procedure's completion in the IT support system or documentation platform, including user-specific configuration details.

#### Notes:

- Adjust the IDE installation command according to the specific software and your organization's policies.
- Always verify the application's required port and ensure it does not conflict with other services.
- Consider creating scripts for these tasks to improve efficiency and consistency across user setups.
