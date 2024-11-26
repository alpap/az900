# Use Roles to Control Resource Access in Azure

Azure provides built-in **Role-Based Access Control (RBAC)** roles to manage access to resources. These roles simplify assigning permissions by defining sets of actions users can perform. If necessary, custom roles can be created for specific needs.


## Built-In Roles

Azure offers three primary built-in roles applicable to all resource types:

1. **Owner**
   - Full access to all resources.
   - Can delegate access to others.
   - Actions: `*` (all actions).
   - Assignable Scopes: `/` (global scope).

2. **Contributor**
   - Can create and manage Azure resources.
   - Cannot assign or manage access to others.
   - Actions: `*` (all actions except restricted ones).
   - NotActions:
     - `Microsoft.Authorization/*/Delete`
     - `Microsoft.Authorization/*/Write`
     - `Microsoft.Authorization/elevateAccess/Action`

3. **Reader**
   - Read-only access to resources.
   - Actions: `*/read`.

---

## Role Definitions

Roles are defined as JSON objects containing the following properties:

| Property          | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| **Name**           | Name of the role.                                                         |
| **Id**             | Unique role identifier.                                                   |
| **IsCustom**       | Indicates if the role is custom or built-in.                              |
| **Description**    | Human-readable description of the role's purpose.                         |
| **Actions**        | List of permissions granted by the role. Wildcard (`*`) allows all.       |
| **NotActions**     | Permissions excluded from the role.                                       |
| **DataActions**    | Data-specific actions allowed by the role.                                |
| **NotDataActions** | Data-specific actions excluded from the role.                             |
| **AssignableScopes** | Defines the scope where the role is available for assignment.            |

### Example: Contributor Role (JSON)

```json
{
  "Name": "Contributor",
  "Id": "b24988ac-6180-42a0-ab88-20f7382dd24c",
  "IsCustom": false,
  "Description": "Lets you manage everything except access to resources.",
  "Actions": ["*"],
  "NotActions": [
    "Microsoft.Authorization/*/Delete",
    "Microsoft.Authorization/*/Write",
    "Microsoft.Authorization/elevateAccess/Action"
  ],
  "DataActions": [],
  "NotDataActions": [],
  "AssignableScopes": ["/"]
}
```

## Custom Roles
Custom roles can be created to define specific permissions tailored to your requirements. These require Microsoft Entra ID P1 or P2 licenses.

### Methods to Create Custom Roles:
1. Microsoft Entra Admin Center
   - Navigate to Roles & admins > New custom role.

2. Azure Portal
   - Go to Microsoft Entra ID > Roles and administrators > New custom role.

3. Azure PowerShell
   - Use the New-AzRoleDefinition cmdlet.

4. Azure Graph API
   - Make REST API calls to create roles programmatically.

### Understanding Role Properties
Actions and NotActions
- Actions: Specify permissions granted to the role (e.g., * for all, */read for read-only).
- NotActions: Exclude specific permissions from the granted actions.

#### DataActions and NotDataActions
These focus on operations related to data (e.g., reading blobs, sending messages). Unlike management actions, data actions are explicitly defined to prevent unintended data access.

Data Operation	Description
Microsoft.Storage/storageAccounts/blobServices/containers/blobs/delete	Delete blob data.
Microsoft.Compute/virtualMachines/login/action	Log in to a VM as a regular user.
Microsoft.EventHub/namespaces/messages/send/action	Send messages on an event hub.


## Assignable Scopes
Defines where a role is valid. Examples:

- Restrict to a subscription: "/subscriptions/{sub-id}"
- Restrict to a resource group: "/subscriptions/{sub-id}/resourceGroups/{rg-name}"
- Restrict to a resource: "/subscriptions/{sub-id}/resourceGroups/{rg-name}/{resource-name}"


## Example PowerShell Commands


### View Role Definitions
Use PowerShell to examine built-in roles:

```powershell
Get-AzRoleDefinition Owner
Get-AzRoleDefinition Contributor
Get-AzRoleDefinition Reader
#Create a Custom Role
Use New-AzRoleDefinition for creating custom roles:
```

``` powershell
New-AzRoleDefinition -InputFile "customRoleDefinition.json"
```

## Summary
- Azure roles define access permissions for resources using RBAC.
- Built-in roles like Owner, Contributor, and Reader cover most scenarios.
- Custom roles can provide granular control but require higher-tier licenses.
- Actions, NotActions, DataActions, and AssignableScopes enable precise permission configurations.

Properly managing roles ensures secure and efficient access control across your Azure environment.