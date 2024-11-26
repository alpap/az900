# Purpose of Resource Locks

Resource locks in Azure are designed to prevent accidental deletion or modification of resources, ensuring critical resources remain protected from unintended changes. While Azure Role-Based Access Control (RBAC) can manage user access, resource locks provide an additional layer of security by enforcing rules that control the ability to delete or modify resources.

## Key Functions of Resource Locks

1. **Prevent Accidental Deletion**: Even users with the necessary access level may accidentally delete critical resources. Resource locks help safeguard against this risk by preventing deletion, even if users have the necessary permissions.

2. **Prevent Unauthorized Changes**: Resource locks can also prevent resources from being updated, which is especially useful for ensuring that certain resources remain in a stable, unaltered state.

3. **Inheritance**: Resource locks can be applied to individual resources, resource groups, or entire subscriptions. Locks are inherited, meaning that if a lock is applied to a resource group, all resources within that group are also locked.

4. **Applicable Across Management Levels**: You can apply resource locks at different levels of your environment, from individual resources to entire subscriptions, to ensure broad or specific protection.

## Types of Resource Locks

There are two primary types of resource locks:

1. **Delete Lock**:
   - This lock prevents authorized users from **deleting** the resource.
   - Users can still **read** and **modify** the resource but cannot delete it.
   - This type of lock is helpful for safeguarding against accidental or unauthorized deletions while allowing resource updates.

2. **ReadOnly Lock**:
   - This lock makes the resource **read-only**, meaning users can only **read** the resource but cannot delete or modify it.
   - This is similar to the **Reader** role in RBAC, where users have no permissions to modify the resource but can view it.
   - It's useful for ensuring that critical resources remain intact and unchanged.

## Managing Resource Locks

Resource locks can be managed in several ways:

- **Azure Portal**: You can view, add, or delete resource locks from the **Settings** section of a resource's **Settings pane** in the Azure portal.
- **PowerShell and Azure CLI**: Resource locks can also be configured and managed using PowerShell or Azure CLI commands.
- **Azure Resource Manager (ARM) Template**: You can define resource locks as part of your infrastructure as code using an ARM template.

## How to Modify or Delete a Locked Resource

Although resource locks help prevent changes, you can still modify or delete a locked resource by following a two-step process:

1. **Remove the Lock**: To modify or delete a locked resource, you first need to **remove the lock**.
2. **Make Changes**: After removing the lock, you can apply the changes or delete the resource, assuming you have the required permissions.

It’s important to note that even if you have owner-level permissions, you cannot bypass the resource lock. You must first remove the lock before making any modifications.

### Example Use Cases

- **Prevent accidental deletions**: Locking a critical resource like a production database to prevent unauthorized or accidental deletions.
- **Ensure stability**: Locking a resource in a "ReadOnly" state ensures that no one can modify its settings or configuration unless the lock is removed.
- **Governance**: Use resource locks to enforce governance by preventing certain resources from being modified or deleted without proper authorization.

By utilizing resource locks, you can safeguard your critical Azure resources and reduce the risk of accidental changes or deletions.
