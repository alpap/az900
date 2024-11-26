# Azure Storage Accounts

An **Azure Storage Account** provides a unique namespace for your data stored in Azure, which is accessible globally over HTTP or HTTPS. It ensures that your data is secure, highly available, durable, and massively scalable.

## Types of Azure Storage Accounts

When creating a storage account, you select the account type, which determines the services and redundancy options available. These factors affect the use cases and the storage solutions you can implement.

### Supported Redundancy Options:
- **Locally Redundant Storage (LRS)**: Data is replicated three times within a single data center.
- **Geo-Redundant Storage (GRS)**: Data is replicated across two geographically separated regions.
- **Read-Access Geo-Redundant Storage (RA-GRS)**: Similar to GRS but allows read access to the secondary region.
- **Zone-Redundant Storage (ZRS)**: Data is replicated across availability zones within a region.
- **Geo-Zone-Redundant Storage (GZRS)**: A combination of GRS and ZRS, replicating data across both regions and availability zones.
- **Read-Access Geo-Zone-Redundant Storage (RA-GZRS)**: A read-access version of GZRS, allowing read access to the secondary region with zone redundancy.

### Storage Account Types:

| Type                        | Supported Services                                          | Redundancy Options                                          | Usage                                                                 |
|-----------------------------|------------------------------------------------------------|------------------------------------------------------------|-----------------------------------------------------------------------|
| **Standard general-purpose v2** | Blob Storage (including Data Lake Storage), Queue Storage, Table Storage, Azure Files | LRS, GRS, RA-GRS, ZRS, GZRS, RA-GZRS                       | Recommended for most scenarios using Azure Storage. Includes support for blobs, files, queues, and tables. |
| **Premium block blobs**      | Blob Storage (including Data Lake Storage)                 | LRS, ZRS                                                   | Recommended for scenarios with high transaction rates or requiring low latency. |
| **Premium file shares**      | Azure Files                                                | LRS, ZRS                                                   | For enterprise or high-performance applications using SMB and NFS file shares. |
| **Premium page blobs**       | Page blobs only                                             | LRS                                                        | Ideal for high-performance applications using page blobs. |

## Storage Account Endpoints

Every Azure Storage account provides a unique namespace, which is defined by the combination of your storage account name and the corresponding endpoint. The endpoint allows for access to the various storage services.

### Naming Rules for Storage Accounts:
- **Length**: The name must be between 3 and 24 characters.
- **Characters**: Only lowercase letters and numbers are allowed.
- **Uniqueness**: The storage account name must be unique across Azure.

### Endpoint Format:

| Storage Service          | Endpoint Format                                            |
|--------------------------|------------------------------------------------------------|
| **Blob Storage**          | `https://<storage-account-name>.blob.core.windows.net`      |
| **Data Lake Storage Gen2**| `https://<storage-account-name>.dfs.core.windows.net`       |
| **Azure Files**           | `https://<storage-account-name>.file.core.windows.net`      |
| **Queue Storage**         | `https://<storage-account-name>.queue.core.windows.net`     |
| **Table Storage**         | `https://<storage-account-name>.table.core.windows.net`     |

## Summary

Azure Storage Accounts provide a centralized, scalable, and secure solution for managing data across various storage services like Blob Storage, Azure Files, Queue Storage, and Table Storage. With multiple redundancy options and flexibility in service types, Azure Storage accounts are suited for a wide range of use cases and workloads, from general-purpose to high-performance applications.
