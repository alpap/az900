# Azure Virtual Private Networks (VPNs)

A **Virtual Private Network (VPN)** creates a secure, encrypted tunnel within a network, enabling communication between trusted private networks over an untrusted network, like the internet. VPNs are commonly used to protect sensitive data as it travels across public networks, preventing eavesdropping or unauthorized access.

## VPN Gateways in Azure

In Azure, a **VPN Gateway** is a type of virtual network gateway that enables secure connectivity between on-premises data centers, virtual networks, or individual devices. VPN Gateways are deployed in a dedicated subnet within an Azure Virtual Network and provide the following key features:

- **Site-to-Site Connections**: Connect on-premises data centers to Azure virtual networks.
- **Point-to-Site Connections**: Allow individual devices to securely connect to a virtual network from anywhere.
- **Network-to-Network Connections**: Enable communication between virtual networks in Azure.

Data passing through a VPN gateway is always encrypted within a private tunnel to ensure confidentiality and integrity over the internet. Each virtual network can have only one VPN gateway, but that gateway can support multiple connections to other virtual networks or on-premises locations.

## Types of VPN Gateways

When setting up a VPN Gateway in Azure, you must choose between two types of VPNs:

### 1. **Policy-based VPN Gateways**
Policy-based VPNs statically define which traffic should be encrypted by specifying the source and destination IP addresses. Each data packet is evaluated against these IP rules to decide the appropriate tunnel to use.

- **Use Case**: Commonly used in legacy or simple VPN scenarios where specific IP addresses need encryption.

### 2. **Route-based VPN Gateways**
Route-based VPNs are more flexible and modern. They treat each tunnel as a virtual network interface and use IP routing (either static or dynamic routing protocols like BGP) to determine which tunnel a packet should go through. This makes them more resilient to changes in network topology (e.g., adding new subnets).

- **Use Case**: Preferred for more complex or dynamic setups, including:
  - Connecting multiple virtual networks
  - Point-to-site connections
  - Multisite connections
  - Coexisting with an Azure **ExpressRoute** gateway
  - High-availability configurations

## High Availability for VPN Gateways

To ensure your VPN connection remains reliable and resilient, Azure offers several high-availability configurations for VPN Gateways:

### 1. **Active/Standby Configuration**
- **Default Setup**: By default, VPN gateways in Azure are deployed in an **active/standby** configuration. This means that if the active instance of the gateway is disrupted (due to maintenance or an unplanned event), the standby instance automatically takes over the traffic routing.
- **Failover Time**: For planned maintenance, failover occurs quickly, usually within a few seconds. For unplanned disruptions, it may take up to 90 seconds.

### 2. **Active/Active Configuration**
- With the **Active/Active** setup, both instances of the VPN gateway are operational at the same time. Each instance is assigned a unique public IP address, and separate tunnels are created to each IP.
- **BGP Routing Protocol**: This setup uses **Border Gateway Protocol (BGP)** to manage routing between on-premises devices and the Azure VPN gateways.
- **High Availability**: Active/active VPNs provide more robust failover and load balancing.

### 3. **ExpressRoute Failover**
For critical high-availability scenarios, you can configure a VPN gateway as a backup for **ExpressRoute** connections. While **ExpressRoute** offers high resilience, it's still vulnerable to certain physical failures (e.g., cable issues or outages at the provider level). In such cases, a VPN Gateway over the internet can act as a failover mechanism to ensure continued connectivity.

### 4. **Zone-Redundant Gateways**
In Azure regions that support **Availability Zones**, you can deploy VPN Gateways in a **zone-redundant configuration**. This approach offers increased resilience, scalability, and fault tolerance by distributing the VPN gateways across different physical and logical zones within a region.
- **Benefits**: Protects against zone-level failures, ensuring uninterrupted on-premises connectivity to Azure.
- **Requirements**: Requires specific gateway SKUs and Standard public IP addresses.

## Benefits of Azure VPN Gateways

- **Security**: Encryption ensures that sensitive data remains protected during transit.
- **Connectivity**: Supports a variety of connection types, including site-to-site, point-to-site, and virtual network-to-virtual network.
- **Flexibility**: The route-based configuration allows for easy adjustments and is suitable for complex networking scenarios.
- **High Availability**: Several failover and redundancy options (active/standby, active/active, ExpressRoute failover) ensure continuous connectivity.

In conclusion, Azure VPN Gateways provide a secure and reliable way to connect on-premises networks with Azure virtual networks. With options for various types of VPN connections and high-availability configurations, VPN Gateways ensure optimal performance, security, and fault tolerance for your cloud infrastructure.
