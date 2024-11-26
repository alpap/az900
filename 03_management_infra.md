


# Resource groups

## Resource Groups Basics

- Resource groups are groupings of resources.
- When creating a resource, it must be placed into a resource group.
- A resource group can contain many resources, but each resource can belong to only one resource group at a time.
- Some resources can be moved between resource groups, but once moved, they are no longer associated with the original group.
- Resource groups cannot be nested; for example, resource group B cannot be placed inside resource group A.

## Actions and Effects

- Actions applied to a resource group affect all resources within that group.
- Deleting a resource group will delete all resources it contains.
- Granting or denying access to a resource group applies the same permissions to all resources in that group.

## Planning Resource Group Structures:

- When provisioning resources, think about the structure that best meets your needs.
- For temporary environments (e.g., a dev environment), grouping all resources together allows for easy deprovisioning by deleting the resource group.
- For compute resources requiring different access schemas, consider grouping resources based on access needs and assigning permissions at the group level.

## General Guidelines:

- There are no strict rules for using resource groups.
- Optimize resource group structures to maximize their usefulness for your specific scenarios.


# Azure Subscriptions

## Overview
- Subscriptions are units of management, billing, and scale in Azure.
- Similar to how resource groups organize resources, subscriptions organize resource groups and facilitate billing.

## Essentials
- **Using Azure requires an Azure subscription**:
  - Provides authenticated and authorized access to Azure products and services.
  - Enables the provisioning of resources.
- **Azure subscriptions link to Azure accounts**:
  - An Azure account is an identity in Microsoft Entra ID or a trusted directory.
  - A single Azure account can have multiple subscriptions, though only one is required.

## Purpose of Subscriptions
- Subscriptions allow for:
  - Configuring different billing models.
  - Applying distinct access-management policies.
  - Defining boundaries for Azure products, services, and resources.

## Types of Subscription Boundaries
1. **Billing Boundary**:
   - Determines how an Azure account is billed.
   - Multiple subscriptions can meet different billing requirements.
   - Separate billing reports and invoices are generated for each subscription to organize and manage costs.

2. **Access Control Boundary**:
   - Access-management policies are applied at the subscription level.
   - Separate subscriptions can reflect different organizational structures (e.g., departments within a business).
   - Allows distinct subscription policies for managing and controlling access to resources.


# Creating Additional Azure Subscriptions

Similar to using resource groups to separate resources by function or access, you may want to create additional subscriptions for resource or billing management purposes. Below are some common scenarios for creating additional subscriptions:

## Scenarios for Additional Subscriptions

### 1. **Environments**
- Create subscriptions to set up separate environments such as:
  - Development and testing.
  - Security-related projects.
  - Isolated data for compliance requirements.
- This approach is beneficial because resource access control occurs at the subscription level.

### 2. **Organizational Structures**
- Reflect different organizational structures by creating subscriptions:
  - For example, limit one team to lower-cost resources while granting the IT department access to a full range of resources.
- This design helps manage and control access to resources provisioned within each subscription.

### 3. **Billing**
- Create subscriptions to meet billing needs:
  - Costs are aggregated at the subscription level, making it easier to track and manage expenses.
  - Example:
    - One subscription for production workloads.
    - Another subscription for development and testing workloads.

By leveraging additional subscriptions, you can better organize, manage, and monitor your Azure resources and costs.


# Azure Management Groups

## Overview
- Azure management groups provide a level of scope above subscriptions.
- They help manage access, policies, and compliance across multiple subscriptions.
- Subscriptions are organized into containers called **management groups**, enabling governance at a higher level.

## Key Features
- **Inheritance**:
  - All subscriptions within a management group automatically inherit the conditions applied to the management group.
  - Similar inheritance hierarchy:
    - Management groups → Subscriptions → Resource groups → Resources.
- **Scalability**:
  - Designed for enterprise-grade management at large scales.
  - Suitable for managing multiple applications, teams, and geographies.
- **Nested Management Groups**:
  - Management groups can be nested, allowing for hierarchical organization and fine-grained governance.

## Use Cases
- **Efficient Management**:
  - Streamline governance for organizations with many subscriptions.
- **Centralized Control**:
  - Apply consistent policies and compliance requirements across all subscriptions in a management group.
- **Flexibility**:
  - Support various subscription types while maintaining centralized control.

Management groups help simplify and standardize governance, making them an essential tool for large-scale Azure deployments.

# Management Group, Subscriptions, and Resource Group Hierarchy

## Overview
- You can build a flexible hierarchy of **management groups**, **subscriptions**, and **resource groups** for unified policy and access management.
- This structure enables centralized governance and consistent access management across your organization.

## Use Cases for Management Groups

### 1. **Applying Policies**
- Create a hierarchy to enforce policies.
  - Example: Restrict VM locations to the **US West Region** within a management group called **Production**.
  - This policy will:
    - Be inherited by all subscriptions and resources under the management group.
    - Remain unalterable by resource or subscription owners, ensuring improved governance.

### 2. **Providing Access to Multiple Subscriptions**
- Consolidate multiple subscriptions under a single management group.
- Use **Azure Role-Based Access Control (Azure RBAC)**:
  - Assign one Azure RBAC role at the management group level.
  - Permissions are inherited by all sub-management groups, subscriptions, resource groups, and resources.
  - Simplifies access management by eliminating the need to script Azure RBAC roles for individual subscriptions.

## Key Facts About Management Groups
- A single directory can support up to **10,000 management groups**.
- A management group tree can have up to **six levels of depth** (excluding the root and subscription levels).
- Each management group and subscription can have **only one parent**.

## Benefits of Hierarchical Structure
- Enables centralized policy enforcement and governance.
- Simplifies user and access management across multiple levels.
- Ensures consistency across resources, subscriptions, and teams.