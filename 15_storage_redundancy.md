# Azure Storage Redundancy

Azure Storage ensures that your data is protected from both planned and unplanned events such as hardware failures, network outages, and natural disasters. Redundancy is built into Azure Storage to meet the availability and durability targets of your storage account, even in the face of failures.

When choosing a redundancy option, it's important to consider the trade-offs between cost and availability. Factors to consider include:

- How data is replicated in the primary region.
- Whether data is replicated to a geographically distant secondary region to protect against regional disasters.
- Whether your application needs read access to the secondary region if the primary region becomes unavailable.

## Redundancy in the Primary Region

### Locally Redundant Storage (LRS)
LRS replicates data three times within a single data center in the primary region. It offers durability of **99.999999999%** over a year.

**Pros**:
- Lowest-cost redundancy option.
- Provides protection against server rack and drive failures.

**Cons**:
- Vulnerable to disasters affecting the data center (e.g., fire, flooding), where all replicas could be lost.

**Recommendation**: Use LRS for non-critical applications, where disaster recovery is not a major concern.

### Zone-Redundant Storage (ZRS)
ZRS replicates data synchronously across three availability zones within the primary region. It offers **99.9999999999%** durability over a year.

**Pros**:
- Provides high availability and data durability, even if one zone fails.
- No need to remount Azure file shares if a zone becomes unavailable. Azure handles networking updates like DNS repointing.

**Recommendation**: Use ZRS in regions with availability zones for high availability and data governance compliance within a region.

## Redundancy in the Secondary Region

### Geo-Redundant Storage (GRS)
GRS replicates data three times within a single location in the primary region using LRS, and then asynchronously replicates it to a secondary region. GRS offers **99.99999999999999%** durability over a year.

**Pros**:
- Protects data against regional outages by replicating to a distant secondary region.
- Provides high durability (16 nines).

**Cons**:
- Data in the secondary region is not accessible for read or write operations unless a failover is initiated.

**Recommendation**: GRS is suitable for critical applications where regional disaster recovery is needed, but read access to the secondary region is not required.

### Geo-Zone-Redundant Storage (GZRS)
GZRS combines ZRS in the primary region (across three availability zones) with geo-replication to a secondary region using LRS. It provides **99.99999999999999%** durability over a year.

**Pros**:
- Offers high availability and protection from regional disasters.
- Supports both high availability (ZRS) and geo-replication (LRS) for maximum durability.

**Recommendation**: GZRS is ideal for applications requiring consistency, durability, high availability, and disaster recovery resilience.

## Read Access to Data in the Secondary Region

By default, data in the secondary region is not available for read or write operations unless you failover to the secondary region. However, if you enable read access, your data will always be available, even when the primary region is running optimally.

- **Read-Access Geo-Redundant Storage (RA-GRS)**: Enables read access to the secondary region.
- **Read-Access Geo-Zone-Redundant Storage (RA-GZRS)**: Enables read access to the secondary region in a GZRS setup.

**Important**: The data in the secondary region may not be up-to-date due to the **Recovery Point Objective (RPO)**. Azure typically has an RPO of less than 15 minutes, though there is no SLA for how long it takes to replicate data to the secondary region.

## Conclusion

Azure Storage redundancy options provide a range of choices depending on your needs for availability, durability, and cost. The redundancy options range from **Locally Redundant Storage (LRS)** for cost-effective solutions to **Geo-Zone-Redundant Storage (GZRS)** for maximum data durability and availability across regions. Enabling **read access** to the secondary region ensures that your data is always accessible, even during primary region outages, but comes with the trade-off of potential delays in data replication.
