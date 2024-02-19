### SOP for Configuring a New User Environment on RHEL Server

#### Purpose:
To provide a standardized process for the Level 1 Support Operations Team to configure a new user environment on a RHEL server upon receiving a request through the ITSM portal.

#### Scope:
This SOP applies to the operations team responsible for managing RHEL servers within an enterprise organization.

#### Prerequisites:
- Access to the ITSM portal.
- Sudo or root access on the RHEL server.
- Basic knowledge of Linux commands and server administration.

#### Estimated Time: 30 minutes

#### Procedure:

1. **Ticket Receipt and Acknowledgment** (Estimated Time: 2 minutes)
   - Monitor the ITSM portal for new user configuration requests.
   - Acknowledge the ticket and take ownership within the ITSM tool.

2. **Log into the RHEL Server** (Estimated Time: 3 minutes)
   - Use SSH to connect to the specified RHEL server.
     ```bash
     ssh user@your-server-ip
     ```
   - Ensure you have root privileges or are able to use sudo commands.

3. **Add the New User** (Estimated Time: 5 minutes)
   - Add a new user account on the server.
     ```bash
     sudo adduser newusername
     ```
   - Set or change the user's password.
     ```bash
     sudo passwd newusername
     ```
   - Follow prompts to enter and confirm the password.

4. **Update the Server** (Estimated Time: 5 minutes)
   - Ensure the server's packages are up-to-date.
     ```bash
     sudo yum update -y
     ```

5. **Install Necessary Applications** (Estimated Time: 5 minutes)
   - Install applications as requested or required for the new user. Replace `application_name` with the actual application name.
     ```bash
     sudo yum install application_name -y
     ```

6. **Configure Firewall Rules** (Estimated Time: 3 minutes)
   - Add necessary firewall rules. Adjust the command based on the specific ports or services needed.
     ```bash
     sudo firewall-cmd --permanent --add-service=serviceName
     ```
   - Reload the firewall to apply the changes.
     ```bash
     sudo firewall-cmd --reload
     ```

7. **Reboot the Server** (Estimated Time: 3 minutes)
   - Reboot the server to ensure all configurations are applied correctly. This step should be scheduled during a maintenance window to minimize disruption.
     ```bash
     sudo reboot
     ```

8. **Verify the Configuration** (Post-Reboot Check, Estimated Time: 2 minutes)
   - After the server restarts, log back in and verify the new user environment is configured correctly, and the application(s) are functioning as expected.

9. **Update and Close the Ticket** (Estimated Time: 2 minutes)
   - Update the ticket in the ITSM portal with the actions taken and the outcome.
   - Notify the customer through the ITSM tool that the configuration is complete and verify if any further actions are required.
   - Close the ticket once the customer confirms the setup meets their needs, or according to your organization's policy.

#### Completion:
The new user environment on the RHEL server is successfully configured, verified, and documented in the ITSM portal. The customer is notified, and the ticket is closed.

#### Documentation:
- Document each step taken in the ITSM portal, including any issues encountered and their resolutions.
- Maintain a log of configurations and installations for future reference.

#### Notes:
- Adapt firewall and application installation steps based on the specific requirements of the user or the organization's security policies.
- Regularly review and update this SOP to incorporate improvements and changes in technology or organizational policies.
