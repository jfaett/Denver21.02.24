### Standard Operating Procedure (SOP) for Managing Informatica Services

#### Purpose
Provide a systematic procedure for the Operations Team to monitor, restart, and verify the status of Informatica services on a Red Hat Enterprise Linux (RHEL) server.

#### Scope
Intended for the Level 1 Support Operations Team.

#### Responsibilities
- Operations Team executes these procedures.
- Escalate issues to Level 2 Support as necessary.

#### Prerequisites
- SSH client and administrative server access.
- Knowledge of Informatica domain and service names.

#### Procedure with Time Estimates

1. **Log into the RHEL Server** _(Estimated Time: 2-5 minutes)_
   ```
   ssh username@server_ip
   ```

2. **Check the Status of Informatica Services** _(Estimated Time: 3-5 minutes)_
   ```
   infacmd.sh ping -dn Domain_Name -sn Service_Name
   ```

3. **Restart the Informatica Service** _(Estimated Time: 10-15 minutes)_
   - Stop the service:
     ```
     infaservice.sh shutdown -dn Domain_Name -sn Service_Name
     ```
   - Wait for a complete shutdown.
   - Start the service:
     ```
     infaservice.sh startup -dn Domain_Name -sn Service_Name
     ```

4. **Verify Informatica Service is Running** _(Estimated Time: 3-5 minutes)_
   ```
   infacmd.sh ping -dn Domain_Name -sn Service_Name
   ```

5. **Server Restart (if Informatica Services do not respond)** _(Estimated Time: 20-30 minutes)_
   - Notify stakeholders of the impending restart.
   - Execute a graceful server restart:
     ```
     sudo shutdown -r now
     ```
   - After reboot, repeat steps 2 to 4.

6. **Log Activity** _(Estimated Time: 5-10 minutes)_
   - Document the process, issues, and resolutions.

#### Additional Notes
- Time estimates may vary based on system and network conditions.
- Ensure maintenance activities comply with operational policies.
