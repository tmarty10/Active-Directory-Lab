## New Employee Onboarding Simulation

### Scenario Overview
In an enterprise environment, onboarding a new employee involves creating a user account, assigning appropriate organizational placement, and ensuring the user can successfully authenticate within the domain. In this scenario, a new employee, **Emily Carter**, is added to the **Finance** department. The IT administrator creates the account, assigns credentials, and verifies successful domain access.

---

### Step 1: Navigate to Finance Organizational Unit
The administrator opens **Active Directory Users and Computers (ADUC)** and navigates to the **Finance** organizational unit where the new employee account will be created.

![Finance OU](../screenshots/new-employee-onboarding/finance-ou.png)

---

### Step 2: Create New User Account
A new user object is created by entering the employee’s details, including name and username.

- First Name: Emily  
- Last Name: Carter  
- Username: ecarter  

![Create User](../screenshots/new-employee-onboarding/create-user.png)

---

### Step 3: Set Initial Password
The administrator assigns an initial password and enables the option requiring the user to change their password at first login. This ensures security and user ownership of credentials.

![Set Password](../screenshots/new-employee-onboarding/set-password.png)

---

### Step 4: Verify User Creation
The new user account (**Emily Carter**) now appears in the **Finance** organizational unit alongside other users, confirming successful account creation.

![User Created](../screenshots/new-employee-onboarding/user-created.png)

---

### Step 5: Validate Domain Access
The administrator verifies that the new account can successfully authenticate by logging in and confirming the domain identity using a command prompt.

![Whoami Verification](../screenshots/new-employee-onboarding/whoami.png)

---

### Key Takeaways
- Proper onboarding ensures users are placed in the correct organizational unit  
- Enforcing password change at first login improves security  
- Active Directory simplifies user creation and management  
- Verifying login confirms successful integration into the domain environment  
