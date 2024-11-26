# Create and Manage Groups in Microsoft Entra ID

## Overview
Groups in **Microsoft Entra ID** help organize users and simplify permissions management. By grouping users, you can assign access rights to all group members at once instead of managing permissions individually. Groups also allow defining membership rules, such as department or job title, enabling dynamic and automated access control.

---

## Types of Groups in Microsoft Entra ID

### 1. **Security Groups**
   - Used to manage member and computer access to shared resources.
   - Ideal for enforcing security policies.
   - Requires a **Microsoft Entra administrator** to manage.
   - Provides a streamlined way to assign permissions to all members.

### 2. **Microsoft 365 Groups**
   - Designed for collaboration.
   - Provides access to:
     - Shared mailboxes
     - Calendars
     - Files
     - SharePoint sites
   - Can include external users for cross-organization collaboration.
   - Manageable by both admins and users.

---

## Viewing Available Groups

1. Open the **Microsoft Entra admin center**.
2. Navigate to **Groups** > **Overview** in the left pane.
3. If no groups are defined, you'll see an empty list, as new Microsoft Entra ID instances don't have predefined groups.

---

## Adding Groups in Microsoft Entra ID

### Steps to Create a Group
1. Open the **Groups** section in the admin center.
2. Select **Create Group**.
3. Fill in the details:
   - **Group Type**: Choose between **Security** or **Microsoft 365**.
   - **Group Name**: Enter a unique name.
   - **Description**: Optional, but recommended for context.
   - **Membership Type**: Choose one of the following:
     - **Assigned**: Manually select users or groups.
     - **Dynamic User**: Define membership based on user attributes (e.g., department = "Sales").
     - **Dynamic Device**: Define membership based on device attributes (e.g., device type = "Service").

4. **Group Ownership**:
   - Assign one or more owners to manage group membership and settings.

5. **Group Members**:
   - Add individual users or other groups as members.

---

### Dynamic Membership

Dynamic membership automates the addition or removal of members based on attributes. This feature is available with a **Microsoft Entra ID P1 license**.

- **Dynamic User Membership**:
  - Example: Users in the **Sales** department are dynamically added to the Sales group.
  - Changes to user attributes trigger automatic updates to group membership.

- **Dynamic Device Membership**:
  - Example: Devices associated with the **Service** department are added to the Service group.
  - Device attribute changes trigger updates to group assignments.

---

## Managing Group Membership

1. Select the group in the **Microsoft Entra admin center**.
2. Use the options under the **Manage** section to:
   - Add or remove users/groups.
   - Adjust group settings as needed.

---

## Automating Group Creation with Scripts

Groups can also be created programmatically using **Microsoft Graph PowerShell**.

### Example Command
```powershell
New-MgGroup -Description "Marketing" `
            -DisplayName "Marketing" `
            -MailNickName "Marketing" `
            -SecurityEnabled `
            -MailEnabled:$False

```

## Benefits of Scripting
- Automates bulk group creation.
- Ensures consistency in group configurations.
- Reduces manual effort for large-scale implementations.

## Key Considerations
1. Licensing:
    * Dynamic memberships require a Microsoft Entra ID P1 license.

2. Group Ownership:
    * Assign responsible owners to ensure proper group management.

3. Security:
    * Regularly audit group memberships to prevent unauthorized access.

4. Membership Rules:
    * Use dynamic rules where applicable to reduce administrative overhead.

By leveraging Microsoft Entra groups effectively, you can streamline user access management and ensure a secure and efficient permissions structure across your organization.