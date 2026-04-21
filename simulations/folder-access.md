## Folder Access Simulation

### Scenario Overview
In an enterprise environment, sensitive data such as payroll information is typically stored in protected network folders with restricted access. Only authorized personnel should be able to view or modify these files. In this scenario, an employee from the **HR department**, **Grace Brown**, needs access to a payroll file stored in a secured folder. The IT administrator must verify the restriction, update permissions, and confirm that access is successfully granted only to the appropriate user.

---

### Step 1: Verify Protected Folder Contents
The administrator navigates to the payroll directory to confirm the existence of the protected file within the secured folder.

![Payroll Folder](../screenshots/folder-access/payroll-folder.png)

---

### Step 2: Review Existing Permissions
The administrator opens the **Advanced Security Settings** for the payroll folder to review current permissions. At this stage, access is restricted and the folder is protected from general user access.

![Advanced Security Settings](../screenshots/folder-access/advanced-security.png)

---

### Step 3: Confirm Restricted Access Configuration
The administrator reviews the current permission entries for the payroll folder to verify that only the appropriate built-in and administrative accounts currently have access before adding the HR user.

![Permissions Overview](../screenshots/folder-access/permissions-overview.png)

---

### Step 4: Add HR User to Permissions
The administrator selects **Add** and enters the HR employee’s account (**Grace Brown**) to grant access to the folder.

![Add User](../screenshots/folder-access/add-user.png)

---

### Step 5: Assign Appropriate Permissions
Permissions are configured for **Grace Brown**, granting **Read & Execute** access so she can open and view the payroll file without being given unnecessary administrative control.

![User Permissions](../screenshots/folder-access/user-permissions.png)

---

### Step 6: Verify Authorized User Access
After permissions are applied, the administrator verifies that the correct domain user has access. The screenshot shows **Grace Brown** authenticated as `labdomain\gbrown` and successfully opening the sensitive payroll file, confirming that the assigned permissions work as intended.

![Grace Brown Access Verification](../screenshots/folder-access/whoami.png)

---

### Step 7: Confirm Unauthorized Users Are Blocked
To validate that the folder remains protected, a different user attempts to access the payroll folder and receives an error indicating insufficient permissions. This demonstrates that access is limited only to authorized users and that the protected folder is not broadly exposed across the network.

![Access Denied](../screenshots/folder-access/access-denied.png)

---

### Key Takeaways
- Sensitive folders should follow the principle of least privilege  
- Access should only be granted to users who require it for their role    
- Testing both authorized and unauthorized access helps confirm that permissions are configured correctly  

