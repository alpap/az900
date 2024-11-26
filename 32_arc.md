# The Purpose of Azure Arc

**Azure Arc** is a management solution designed to extend **Azure management capabilities** to **hybrid** and **multi-cloud environments**. As organizations increasingly operate across a mix of on-premises infrastructure, Azure, and other cloud providers, managing these diverse resources can become complex. **Azure Arc** simplifies governance and management by enabling a **consistent management experience** regardless of where the resources reside.

## Key Features and Benefits

1. **Unified Management Across Environments**
   Azure Arc allows you to manage both **Azure and non-Azure resources** (including on-premises and multi-cloud environments) within a single **Azure Resource Manager (ARM)** interface. This eliminates the need for separate management tools for different platforms.

2. **Multi-Cloud and Hybrid Management**
   With Azure Arc, you can manage **virtual machines (VMs)**, **Kubernetes clusters**, and **databases** across multiple clouds (such as AWS, GCP) and on-premises environments as if they were natively running within Azure.

3. **Leverage Azure Services Anywhere**
   Azure Arc enables the use of familiar **Azure services** and management capabilities (such as monitoring, governance, and security) for **non-Azure resources**, providing a seamless experience across various infrastructure types.

4. **Centralized Governance and Compliance**
   By using **Azure Arc**, organizations can extend their **Azure governance** model (such as **Azure Policy** and **Azure Security Center**) to resources outside of Azure, helping maintain compliance and security standards consistently.

5. **Support for Traditional IT and DevOps**
   Azure Arc enables organizations to continue using **traditional IT operations** (ITOps) while also adopting **DevOps practices** to modernize application deployment and management across hybrid and multi-cloud infrastructures.

6. **Custom Locations and Extensions**
   Azure Arc provides the ability to create **custom locations** for managing **Kubernetes clusters** and other extensions in **non-Azure environments**, allowing them to be treated as if they were part of Azure.

## What Can Azure Arc Manage Outside of Azure?

Currently, **Azure Arc** supports the following resource types outside of Azure:

- **Servers**: Manage both on-premises and multi-cloud servers within Azure's governance and security framework.
- **Kubernetes Clusters**: Extend Azure's Kubernetes management capabilities to clusters running outside of Azure, including in other cloud environments and on-premises.
- **Azure Data Services**: Bring Azure's data services (such as Azure SQL) to non-Azure environments.
- **SQL Server**: Manage SQL Server instances running outside of Azure through Azure Arc.
- **Virtual Machines (Preview)**: Extend management to virtual machines hosted in non-Azure environments, unifying their management under the Azure umbrella.

## Conclusion

Azure Arc simplifies hybrid and multi-cloud management by bringing **Azure’s powerful management tools** to environments outside of Azure. It allows organizations to manage and secure their entire infrastructure from a single interface, regardless of where the resources are located, while maintaining flexibility for both **traditional IT operations** and **cloud-native practices**.
