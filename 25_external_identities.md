# Azure External Identities

An **external identity** refers to a person, device, service, or entity that is outside your organization. Microsoft Entra External ID encompasses all the ways you can securely interact with users outside your organization. It allows organizations to collaborate with external parties such as partners, distributors, suppliers, or vendors and manage access to resources securely. If you're a developer creating consumer-facing apps, it helps manage customers' identity experiences.

### External Identities Overview

External Identities is different from **Single Sign-On (SSO)**. With External Identities, external users can **"bring their own identities"**. Whether they have a corporate or government-issued digital identity, or a social identity like Google or Facebook, they can use their existing credentials to sign in. The identity provider (such as Google, Facebook, or a company’s internal identity provider) manages the user's identity, while you manage access to your apps and resources using Microsoft Entra ID or Azure AD B2C.

The key capabilities of External Identities include:

## Key Capabilities of External Identities

### 1. **Business to Business (B2B) Collaboration**
   - **B2B Collaboration** allows you to collaborate with external users by letting them use their preferred identity to sign in to your Microsoft applications or other enterprise applications (such as SaaS apps or custom-developed apps).
   - These external users are typically represented as **guest users** in your directory.
   - This provides an easy way to grant access to external partners, suppliers, or vendors using their existing credentials.

### 2. **B2B Direct Connect**
   - **B2B Direct Connect** allows you to establish a mutual, two-way trust with another Microsoft Entra organization for seamless collaboration.
   - Currently, this is used in scenarios such as **Teams shared channels**, where external users can access your resources from within their own Microsoft Teams instance.
   - B2B Direct Connect users are not represented in your directory, but they are visible in Teams shared channels, and their activities can be monitored in the **Teams Admin Center** reports.

### 3. **Microsoft Azure Active Directory Business to Customer (B2C)**
   - With **Azure AD B2C**, you can publish modern SaaS apps or custom-developed apps to external consumers and customers while using Azure AD B2C for identity and access management.
   - This approach is often used for customer-facing applications, where identity management is outsourced to Azure AD B2C, which supports social logins (like Google, Facebook, or LinkedIn) in addition to custom identity providers.

## Types of External Identity Scenarios

1. **Collaborating with Partners & Vendors**: With **Microsoft Entra ID B2B**, you can easily enable collaboration with external organizations. You can invite guest users from other tenants into your environment. These guest users can be invited by either administrators or even other users.

2. **Managing Access for External Users**: It’s important to ensure that external or guest users have appropriate access to your resources. **Access Reviews** in Microsoft Entra ID let you involve decision-makers or even the guests themselves in determining if they still need access. After the review, any unnecessary access can be revoked.

3. **Social Identity Integration**: External identities also support social logins, such as **Microsoft accounts** or other common social media accounts. This simplifies the login process for users from outside your organization.

## Benefits of External Identities

- **Security**: External Identities allows you to securely share resources with external parties while keeping your internal resources protected.
- **Convenience**: External users can use their existing credentials, avoiding the need to manage additional accounts or passwords.
- **Flexibility**: You can collaborate with both business partners (via B2B) and customers (via B2C) while maintaining control over access and security.

## Conclusion
Microsoft Entra External Identities enables seamless collaboration and access management for external users, offering a secure way to interact with partners, vendors, and customers. With features like **B2B collaboration**, **B2B direct connect**, and **Azure AD B2C**, you can easily manage guest access, integrate social identities, and ensure appropriate access control across organizational boundaries.
