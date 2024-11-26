# Azure Conditional Access

**Conditional Access** is a tool within Microsoft Entra ID that helps control access to resources based on identity signals. These signals include factors such as **who the user is**, **where the user is located**, and **what device** the user is requesting access from.

Conditional Access enables IT administrators to:

- Empower users to be productive anywhere, anytime.
- Protect the organization's assets and data.

### How Conditional Access Works

Conditional Access provides a more **granular multifactor authentication (MFA)** experience for users. For example, a user might not need to authenticate a second time if they’re logging in from a known location. However, if the user's sign-in attempt originates from an unfamiliar or risky location, they might be prompted for additional authentication, like MFA.

#### The Flow of Conditional Access:
1. **Signals**: During sign-in, Conditional Access collects signals from the user, such as their **location**, **device**, or the **application** they are trying to access.

2. **Decision**: Based on the gathered signals, a decision is made. For instance:
   - Allow access if the user is signing in from a familiar, trusted location.
   - Block access if the user is attempting to sign in from an unexpected or risky location, or if they fail to meet security requirements.

3. **Enforcement**: Once a decision is made, the system enforces it by either allowing access or requesting additional steps, such as **multifactor authentication (MFA)**.

![Conditional Access Flow Diagram](image-link-placeholder)

### Use Cases for Conditional Access

You can implement Conditional Access in various scenarios, such as:

1. **Require MFA**: Enforce multifactor authentication based on conditions like the user’s role, location, or the network they are connecting from. For instance, MFA can be required for administrators but not for regular users, or for users accessing resources outside the corporate network.

2. **Approve Client Applications**: Only allow access to resources via approved applications. For example, you could restrict access to email services to certain approved email clients.

3. **Managed Devices**: Require users to access applications only from **managed devices** that meet specific security and compliance standards. Managed devices typically have policies in place to ensure they are secure.

4. **Block Access from Untrusted Sources**: Block access from unknown or unexpected locations, helping to protect your environment from potential security threats.

### Summary

Conditional Access helps ensure that only trusted and compliant users, devices, and locations can access sensitive resources. It adds a layer of security by adjusting access levels based on contextual factors and can prompt users for additional authentication when necessary.
