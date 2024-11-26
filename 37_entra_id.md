# Microsoft Entra ID Overview

## What is Microsoft Entra ID?

Microsoft Entra ID (formerly Azure Active Directory or Azure AD) is a **cloud-based identity and access management service**. It provides organizations with a secure and scalable way to manage users and control access to applications, resources, and services. While it integrates with on-premises **Windows Server Active Directory (AD)**, Microsoft Entra ID is not a direct replacement for it. Instead, it extends identity management to the cloud.

### Key Features:
1. **Hybrid Integration**: Connects on-premises AD to extend user credentials to Azure, enabling seamless access to both local and cloud-based resources.
2. **Standalone Use**: Can operate independently as the only directory for smaller organizations, managing access to apps like **Microsoft 365**, **Salesforce**, and **Dropbox**.
3. **Application Integration**: Supports authentication and authorization for custom and third-party applications.

---

## Components of Microsoft Entra ID

### Directories, Subscriptions, and Tenants
- **Directory (Tenant)**: A directory in Microsoft Entra ID represents an organization. When an organization signs up for services like **Azure**, **Microsoft 365**, or **Dynamics 365**, a directory is automatically created for user and group management.
- **Subscription**: Each Azure subscription is linked to a single directory and represents a billing entity. Multiple subscriptions can use the same directory for user authentication and resource access.

### Directory Features:
- **Multiple Directories**: Organizations can create additional directories for testing, development, or syncing with separate AD forests.
- **Switching Directories**: Users with access to multiple directories can switch between them through the **Directory + subscription** menu in the Azure portal.

---

## Common Use Cases

1. **Hybrid Identity Management**:
   Organizations with on-premises Windows Server AD can synchronize it with Microsoft Entra ID, allowing users to use the same credentials across local and cloud environments.

2. **Cloud-Only Identity Management**:
   Small businesses can use Microsoft Entra ID as their sole identity provider, enabling centralized control for apps and services like Microsoft 365.

3. **Access Control**:
   Entra ID supports role-based access control (RBAC) to secure access to Azure resources, apps, and data.


## Creating a New Directory

### Steps to Create a Directory:
1. **Sign in to the Azure Portal**.
2. **Navigate to Azure Services**: Select **Create a resource**.
3. **Search for Microsoft Entra ID**: From the **Identity** category.
4. **Configure the Directory**:
   - **Organization Name**: A recognizable name for your directory.
   - **Initial Domain Name**: A domain ending with `.onmicrosoft.com` (e.g., `contoso.onmicrosoft.com`).
   - **Country/Region**: Specifies the region for the directory's data residency.
5. **Select Create**: This creates a free-tier directory that allows user additions, role creations, app registrations, and license management.


## Benefits of Microsoft Entra ID

1. **Secure Access Management**:
   - Protects resources with **multi-factor authentication (MFA)** and **conditional access policies**.
2. **Scalable Directory Services**:
   - Supports large enterprises and small businesses alike, with the flexibility to scale.
3. **Simplified User Experience**:
   - Enables Single Sign-On (SSO) for seamless access to cloud and on-premises applications.
4. **Custom Domains**:
   - Allows organizations to integrate their email domains for personalized user accounts.
5. **Integration with Other Microsoft Services**:
   - Automatically integrates with Microsoft 365, Dynamics 365, and Azure, providing centralized identity management.

Microsoft Entra ID empowers organizations with secure, scalable, and flexible identity management, bridging the gap between on-premises infrastructure and the cloud.
