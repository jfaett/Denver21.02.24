To enhance the Standard Operating Procedure (SOP) for resetting a user's Red Hat Enterprise Linux (RHEL) password with specific commands, we will include the necessary terminal commands the operations team should run at each relevant step. This detailed guidance ensures that the process is clear and actionable.

### Standard Operating Procedure (SOP) for Resetting a User's RHEL Password with Commands

#### Objective, Scope, Responsibility, and Time Estimates
(Refer to the previous overview for these sections.)

#### Pre-Procedure Steps:
1. **Verify User Identity:**  
   (Procedural, no commands involved)

2. **Log the Request:**  
   (Procedural, no commands involved)

#### Procedure:

1. **Access the Server:**
   - Command: Use SSH to log into the server. Replace `servername` with the actual server name or IP address.
     ```
     ssh root@servername
     ```
   - If not using the root account to SSH, you'll need to switch to root after logging in:
     ```
     su -  // If you have the root password
     ```
     or
     ```
     sudo -i  // If your user has sudo privileges to elevate to root
     ```

2. **Reset the Password:**
   - Switch to the root user (if not already):
     ```
     su -  // or use sudo -i if you're using a non-root account with sudo privileges
     ```
   - Reset the user's password. Replace `username` with the actual username:
     ```
     passwd username
     ```
     Then, follow the prompts to enter and confirm the new password.

3. **Ensure Password Policy Compliance:**
   - (No specific command, ensure the new password meets your organization's policy during the reset process.)

4. **Force Password Change on Next Login (Optional):**
   - To require the user to change the password at next login:
     ```
     chage -d 0 username
     ```
     Replace `username` with the actual username.

#### Post-Procedure Steps:

1. **Notify the User:**  
   (Procedural, no commands involved)

2. **Documentation and Closure:**  
   (Procedural, no commands involved)

3. **Follow-Up:**  
   (Procedural, no commands involved)

#### Notes:
- Ensure you have a secure method of communicating the new password to the user, adhering to your organization's security policies.
- Always operate under the principle of least privilege, using root access only when necessary.
- Regularly review and update this SOP to align with the latest security practices and organizational policies.
