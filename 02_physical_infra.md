# Azure Physical Infrastructure

Azure’s physical infrastructure consists of datacenters grouped into regions, availability zones, and region pairs. These elements work together to ensure scalability, resiliency, and reliability for your workloads.

## Core Concepts

### 1. **Datacenters**
- Facilities with resources organized in racks.
- Equipped with dedicated power, cooling, and networking.
- **Global Cloud Provider**:
  - Azure datacenters are spread worldwide.
  - Individual datacenters are grouped into **Regions** or **Availability Zones** for increased resiliency.


### 2. **Regions**
- **Definition**: A geographical area containing one or more datacenters connected by a low-latency network.
- **Features**:
  - Workloads are intelligently balanced within regions.
  - Users must choose a region when deploying a resource.
  - Some services or features are region-specific, while others, like Microsoft Entra ID, are global.
- **Examples**:
  - East US, West Europe, Southeast Asia.


### 3. **Availability Zones**
- **Definition**: Physically separate datacenters within an Azure region.
- **Features**:
  - Independent power, cooling, and networking for each zone.
  - Designed as isolation boundaries for high availability.
  - Connected via high-speed, private fiber-optic networks.
- **Use Cases**:
  - Run mission-critical applications with high availability.
  - Co-locate compute, storage, networking, and data resources within zones and replicate across zones for redundancy.
- **Categories of Services**:
  - **Zonal Services**: Resources pinned to specific zones (e.g., VMs, managed disks).
  - **Zone-Redundant Services**: Automatically replicated across zones (e.g., zone-redundant storage).
  - **Non-Regional Services**: Resilient to zone and region-wide outages (e.g., Azure DNS).
- **Important**: Availability zones are not supported in all regions.


### 4. **Region Pairs**
- **Definition**: Most Azure regions are paired with another region within the same geography (300+ miles apart).
- **Features**:
  - Enables replication of resources across geographies for disaster recovery.
  - Provides redundancy to reduce interruptions from regional events.
- **Advantages**:
  - In large-scale outages, one region in the pair is prioritized for recovery.
  - Updates are rolled out sequentially to paired regions to minimize risk.
  - Data remains in the same geography for compliance, except Brazil South.
- **Examples**:
  - West US paired with East US.
  - Southeast Asia paired with East Asia.
- **Special Cases**:
  - Brazil South is paired with South Central US (outside its geography).
  - Some regions have one-way pairings (e.g., West India and South India).


### 5. **Sovereign Regions**
- **Definition**: Isolated instances of Azure designed for compliance or legal requirements.
- **Examples**:
  - **US Government Regions**: US DoD Central, US Gov Virginia, etc.
    - Operated by screened U.S. personnel with enhanced compliance certifications.
  - **China Regions**: China East, China North.
    - Operated through a partnership between Microsoft and 21Vianet.


## Summary
Azure’s physical infrastructure leverages a global network of datacenters, regions, availability zones, and region pairs to provide reliable, scalable, and compliant cloud services. With the addition of sovereign regions, Azure ensures compliance with specific regulatory and legal needs while maintaining high availability and performance for a wide range of workloads.