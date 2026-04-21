## Account Disable Simulation

### Scenario Overview
In an enterprise environment, when an employee leaves the organization, it is critical to immediately revoke their access to company systems to protect sensitive data and maintain security. In this scenario, **Emily Carter** is being terminated, and the IT administrator is responsible for disabling her Active Directory account to prevent any further access to the domain.

---

### Step 1: Locate User Account in Active Directory
The administrator opens **Active Directory Users and Computers (ADUC)** and locates the user account (**Emily Carter**) within the domain.

![Locate User](../screenshots/account-disabled/locate-user.png)

---

### Step 2: Disable the User Account
The administrator disables the account, and the system confirms that the user object has been successfully disabled. This action immediately prevents the user from authenticating to the domain.

![Account Disabled Confirmation](../screenshots/account-disabled/account-disabled-confirmation.png)

---

### Step 3: Verify Access is Revoked
After the account is disabled, the user attempts to log in and receives a message indicating that the account has been disabled. This confirms that access has been successfully revoked.

![Login Blocked](../screenshots/account-disabled/login-blocked.png)

---

### Step 4: Move Account to Disabled Users OU
To maintain proper organization and follow best practices, the administrator moves the disabled account to a designated **Disabled Users** organizational unit. This helps separate inactive accounts from active users and supports account management and auditing.

![Disabled Users OU](../screenshots/account-disabled/disabled-users-ou.png)

---

### Key Takeaways
- Disabling accounts is a critical step in offboarding employees  
- Immediate access revocation helps protect organizational data  
- Moving disabled accounts to a separate OU improves organization and auditing  
- Active Directory provides a quick and effective method for managing account status  
