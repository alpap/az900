# Azure Role-Based Access Control (RBAC)

When managing multiple IT and engineering teams, controlling their access to cloud resources is crucial. The **principle of least privilege** dictates that users should only be granted the minimum necessary access to complete their tasks. For example, if a user only needs read access to a storage blob, they should be granted read access, not write access, and certainly not access to other storage blobs.

However, managing access for every individual, especially in large teams, can become tedious. Azure enables you to efficiently control access through **Azure Role-Based Access Control (Azure RBAC)**.

### What is Azure RBAC?

Azure RBAC is a system for managing access to Azure resources. It allows you to assign roles to individuals or groups, granting them specific permissions to manage or access Azure resources. Instead of defining access for each individual, Azure RBAC uses **built-in roles** that describe common access requirements for cloud resources. You can also define **custom roles** to meet your unique needs.

When an individual or group is assigned a role, they automatically inherit the permissions associated with that role. For example, if a new engineer joins the team and is added to an **Azure RBAC group for engineers**, they will automatically receive the same access as the other engineers in the group.

Similarly, if new resources are added, everyone in the RBAC group will gain the required permissions for those resources without needing individual updates.

### How is Azure RBAC Applied to Resources?

Azure RBAC is applied to a **scope**, which defines the level of access a user has to a specific resource or set of resources.

#### Scopes include:
- **Management group** (a collection of multiple subscriptions)
- **Subscription**
- **Resource group**
- **Individual resource**

For example, a **management group** might be given an **Owner** role, granting greater control over all resources within the management group. On the other hand, an **Observer** might be assigned the **Reader** role to only view the resources without making changes.

Roles and scopes combine to define access levels for specific users or accounts.

#### Hierarchical Access:
Azure RBAC is hierarchical, meaning that when you assign access at a **parent scope**, the permissions are inherited by **child scopes**. For instance:
- If you assign the **Owner** role at the **management group** level, the user can manage all resources within all subscriptions in that management group.
- If you assign the **Reader** role at the **subscription** level, the user can view resources in all resource groups within that subscription.

### How is Azure RBAC Enforced?

Azure RBAC is enforced on any action that interacts with Azure resources through **Azure Resource Manager** (ARM). Resource Manager acts as a service to organize and secure your cloud resources. You can interact with ARM via the Azure portal, Azure Cloud Shell, Azure PowerShell, or the Azure CLI.

However, Azure RBAC does **not** enforce permissions at the **application** or **data** level. For managing application-level security, you'll need to implement additional measures within your application.

### Azure RBAC Allow Model

Azure RBAC follows an **allow model**. When a user is assigned a role, Azure RBAC allows them to perform actions within the scope of that role. If a user is assigned both **read** and **write** roles to the same resource group, they will have both **read** and **write** access to that resource group.

This system simplifies access management, ensuring users can only perform actions they are permitted to do, based on their roles and assigned permissions.
