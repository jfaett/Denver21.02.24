### Standard Operating Procedure (SOP) for Managing Informatica Services

#### Purpose
This SOP provides a systematic procedure for the Operations Team to monitor, restart, and verify the status of Informatica services on a Red Hat Enterprise Linux (RHEL) server.

#### Scope
This procedure is intended for use by the Level 1 Support Operations Team responsible for the maintenance and uptime of Informatica services.

#### Responsibilities
- The Operations Team is responsible for executing these procedures.
- Team members must have the necessary permissions to perform server restarts and service checks.
- The team should report any issues encountered during the procedure to the Level 2 Support Team for further assistance.

#### Prerequisites
- SSH client installed on the local machine (e.g., PuTTY for Windows, Terminal for macOS).
- Administrative credentials for accessing the RHEL server.
- Informatica domain name or service name is known.

#### Procedure

1. **Log into the RHEL Server**
    - Open your SSH client.
    - Connect to the RHEL server using the command:
      ```
      ssh username@server_ip
      ```
    - Enter your password when prompted.

2. **Check the Status of Informatica Services**
    - To check the status of Informatica services, use the command:
      ```
      infacmd.sh ping -dn Domain_Name -sn Service_Name
      ```
    - Replace `Domain_Name` with your Informatica domain name and `Service_Name` with the name of the Informatica service you want to check.
    - If the service is running, you will receive a confirmation message. If not, proceed to the next step to restart the server.

3. **Restart the Informatica Service**
    - Before restarting Informatica services, ensure that it is safe to do so without disrupting ongoing processes or data flows.
    - Use the following command to stop the Informatica service:
      ```
      infaservice.sh shutdown -dn Domain_Name -sn Service_Name
      ```
    - Wait for the service to shut down completely. This might take a few minutes.
    - Start the Informatica service using:
      ```
      infaservice.sh startup -dn Domain_Name -sn Service_Name
      ```
    - Replace `Domain_Name` and `Service_Name` with your actual domain and service names respectively.

4. **Verify Informatica Service is Running**
    - After restarting, verify that the Informatica service is running with:
      ```
      infacmd.sh ping -dn Domain_Name -sn Service_Name
      ```
    - Ensure you receive a confirmation message indicating that the service is running.

5. **Log Activity**
    - Document the restart process, including the time and date of the operation, any issues encountered, and how they were resolved.
    - Report any unresolved issues to the Level 2 Support Team for further investigation.

#### Additional Notes
- This SOP assumes basic knowledge of Linux commands and the Informatica command-line interface.
- Always check for any specific maintenance windows or operational restrictions before performing restarts.
- Ensure that all actions are logged and reported according to the organization's IT governance policies.

If the initial attempt to restart Informatica services does not resolve the issue, the Operations Team may need to perform additional steps, including a full server restart. This section expands on the previous SOP with added steps for attempting a server restart if Informatica services aren't working properly after the initial restart attempt.

#### 6. **Attempt to Restart the RHEL Server**
If restarting Informatica services does not resolve the issue, a full server restart may be necessary. Ensure to communicate and schedule this action to minimize the impact on users and ongoing processes.

- **Communicate the Planned Restart**
  - Notify all stakeholders of the planned server restart, providing the expected downtime and impact.

- **Check Running Processes**
  - Before restarting the server, check for any critical processes that might be affected using:
    ```
    ps aux
    ```
  - If any critical processes are identified, assess whether they can be safely stopped or if they need to be migrated to another time.

- **Perform a Graceful Server Restart**
  - Execute the following command to restart the RHEL server gracefully:
    ```
    sudo shutdown -r now
    ```
  - This command will immediately begin the shutdown process and then restart the server.

#### 7. **Verify Server and Informatica Service Status Post-Restart**
After the server has restarted, it's essential to verify both the server's health and the status of Informatica services.

- **Log back into the RHEL Server**
  - Use SSH to reconnect to the server as outlined in Step 1.

- **Check Server Health**
  - Perform a quick check to ensure that the server is running optimally. Review system logs for any errors that might indicate problems:
    ```
    sudo journalctl -xe
    ```

- **Verify Informatica Service is Running**
  - Repeat Step 4 to ensure that the Informatica service is running correctly after the server restart.

#### 8. **Post-Restart Actions**
- **Monitor the System and Application Logs**
  - Monitor the system and Informatica logs for any unusual activity or errors that could indicate problems:
    ```
    tail -f /var/log/messages
    tail -f /path/to/informatica/logs
    ```
- **Document the Restart Process**
  - Document the server restart process, including the reason for the restart, any issues encountered during the restart, and how those issues were resolved.

- **Notify Stakeholders**
  - Once everything is confirmed to be running smoothly, notify all stakeholders that the system is back online and operational.
