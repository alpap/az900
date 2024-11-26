# Create and Manage Users in Microsoft Entra ID

## Overview

Every user needing access to Azure resources must have an **Azure user account**. This account enables authentication and provides the access token to authorize actions based on user permissions.

The **Microsoft Entra admin center** is a centralized portal for managing Microsoft Entra ID. You can use it to create, view, and manage users and their associated permissions.

---

## Types of User Accounts in Microsoft Entra ID

Microsoft Entra ID supports three main types of user identities:

1. **Cloud Identities**:
   - Managed solely within Microsoft Entra ID.
   - Common for administrator accounts and users created directly in Microsoft Entra ID.
   - Example Source: `Microsoft Entra ID` or `External Microsoft Entra ID`.

2. **Directory-Synchronized Identities**:
   - Synchronized from an on-premises **Windows Server Active Directory** using Microsoft Entra Connect.
   - Example Source: `Windows Server AD`.

3. **Guest Users**:
   - External accounts invited to access Azure resources (e.g., vendors, contractors).
   - Example Source: `Invited User`.

---

## Viewing Users

1. **Access the User List**:
   - Navigate to the **Microsoft Entra admin center**.
   - Select **Users** in the left pane and click **All Users**.

2. **Key Columns in User List**:
   - **User Type**: Indicates if the user is a cloud identity, directory-synchronized identity, or guest user.
   - **Identities**: Lists external or synchronized accounts.

---

## Adding Users to Microsoft Entra ID

### Methods to Add Users:
1. **Synchronize an On-Premises Directory**:
   - Use **Microsoft Entra Connect** to synchronize users from a Windows Server Active Directory.
   - Supports single sign-on (SSO) for seamless access.

2. **Using Microsoft Entra Admin Center**:
   - Navigate to **Users** and select **New User**.
   - Choose between:
     - **Create New User**: Generates a user within the directory (e.g., `username@organization.onmicrosoft.com`).
     - **Invite User**: Sends an invitation to an external email address to create a guest user account.

3. **Using Command-Line Tools**:
   - **PowerShell**:
     ```powershell
     # Create a password profile
     $PasswordProfile = @{ Password = "<Password>" }

     # Add a new user
     New-MgUser -DisplayName "Abby Brown" `
                -PasswordProfile $PasswordProfile `
                -MailNickName "AbbyB" `
                -UserPrincipalName "AbbyB@contoso.com" `
                -AccountEnabled
     ```
   - **Azure CLI**:
     ```bash
     az ad user create --display-name "Abby Brown" \
                       --password "<password>" \
                       --user-principal-name "AbbyB@contoso.com" \
                       --force-change-password-next-login true \
                       --mail-nickname "AbbyB"
     ```

4. **Importing Users via CSV**:
   - Prepare a CSV file with details like username, email, and job title.
   - Import and create users programmatically using:
     - PowerShell (`Import-CSV` and `New-MgUser` commands).
     - Custom scripts for bulk uploads.

5. **Using APIs or Other Portals**:
   - Use the **Microsoft Graph API** for programmatic user management.
   - Manage users via the **Microsoft 365 Admin Center** or **Microsoft Intune Admin Console** if sharing the same directory.

---

## Key Considerations

1. **Naming Conventions**:
   - Establish clear conventions for usernames, display names, and email aliases (e.g., `firstname.lastname@contoso.com`).

2. **Password Management**:
   - Ensure passwords adhere to complexity rules.
   - Securely communicate initial passwords to users.

3. **Role Assignments**:
   - Assign appropriate roles (e.g., User Administrator) to manage users effectively.

4. **Directory Switching**:
   - If managing multiple directories, use the **Directory + Subscription** menu in the admin center to switch directories.

---

By leveraging these tools and methods, organizations can efficiently manage user identities and access in Microsoft Entra ID while ensuring security and compliance.
