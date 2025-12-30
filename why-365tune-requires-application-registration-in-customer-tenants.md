# Why 365tune Requires Application Registration in Customer Tenants

When using 365TUNE, as a Managed Service Provider (MSP) with GDAP (Granular Delegated Admin Privileges), you'll need to register the 365TUNE application in each customer tenant you want to monitor. This article explains why this requirement exists, the security benefits it provides, and how it protects both you and your customers.

### Understanding the GDAP Context

GDAP represents Microsoft's modern approach to partner access, replacing the older Delegated Admin Privileges (DAP) model. With GDAP, you receive specific, time-limited permissions to customer tenants based on security group assignments in your partner tenant. This granular approach means you only have the permissions you actually need, reducing security risks for both parties.

However, GDAP alone only grants _your users_ access to customer resources. It doesn't automatically give applications the permissions they need to read tenant data on your behalf.

### Why Application Registration is Required

When 365TUNE needs to access Microsoft 365 data in a customer tenant, it must do so through the Microsoft Graph API and Office 365 Management Activity API. These APIs require explicit consent and permissions that can only be granted through an Azure AD application registration.

{% hint style="info" %}
**Important:** GDAP works based on '_user delegation_', which only functions (securely) when a user is actively logged in. However, 365TUNE needs to collect data in the background using read-only '_application delegation_' permissions via the Graph API to keep the platform up-to-date and generate insights. This backend data collection happens continuously, even when no user is logged in, which is why application-level permissions are essential.
{% endhint %}

Here's what happens when you try to access customer data:

**Your GDAP permissions** allow you as an MSP technician to sign into the Microsoft 365 admin center and view customer data manually. However, when 365TUNE attempts to make API calls to Microsoft Graph on your behalf, those calls originate from the 365TUNE application, not from your user account.

**The Microsoft identity platform** checks two things: Does this application have permission to access this tenant? Does the current user have permission to consent to or use this application? Without an app registration in the customer tenant, the answer to the first question is "no," and the API calls will fail.

### How This Works With GDAP

365TUNE uses a combined authentication model that leverages both GDAP and application permissions:

When you sign into 365TUNE with your MSP account, the platform detects your GDAP relationships through your security group memberships. This determines which customer tenants you should be able to access.

For each customer tenant, 365TUNE checks whether the application has been registered and granted permissions in that tenant. If it has, you can connect that customer to 365TUNE and begin monitoring their license usage.

When 365TUNE makes API calls to collect data, it uses the application permissions granted in the customer tenant. However, 365TUNE enforces that you can only access customer data if you have valid GDAP permissions for that customer. This means even if the application has broad permissions in a customer tenant, individual MSP technicians can only see the customers they're authorized to manage.

This creates a security boundary at both the application level and the user level, ensuring that access control is properly enforced throughout the stack.

{% hint style="info" %}
365TUNE does not provide blanket access across all MSP users. Access is strictly limited to users explicitly granted permissions through GDAP relationships, and only for the specific tenant they are assigned to.
{% endhint %}

### The Security Benefits of This Model

This requirement might seem like extra work, but it provides important security advantages:

**Explicit customer consent** means that each customer must actively approve 365TUNE's access to their tenant. This prevents scenarios where an MSP could connect any third-party application to customer tenants without their knowledge or approval. Your customers maintain full control over which applications can access their data.

**Granular permission control** allows customers to see exactly what permissions 365TUNE requests before granting access. The application only requests the specific Microsoft Graph API permissions it needs to perform license auditing and activity monitoring. Customers can review these permissions and understand what data will be accessed.

**Independent revocation** means that if a customer wants to remove 365TUNE's access, they can revoke it immediately through their Azure AD admin center without affecting your GDAP access or other services. This separation of concerns gives customers confidence that they can stop data access at any time.

**Audit trail preservation** ensures that all 365TUNE API calls are logged in the customer's Azure AD sign-in logs and audit logs with the application identity clearly identified. This provides transparency and accountability for all data access.

### Common Questions and Concerns

**Why can't 365TUNE use my GDAP permissions directly?**

GDAP permissions are user-level permissions that allow you to interact with customer tenants through Microsoft's admin portals. When an application makes API calls, those calls are made in the application's context, not your user context. Microsoft's security model requires applications to have their own explicitly granted permissions, separate from user permissions.

**Do customers need to trust our MSP for this to work?**

Yes, but this is already inherent in the MSP relationship. When customers grant you GDAP access, they're already trusting you to manage their Microsoft 365 environment. The app registration requirement simply extends that trust to include the tools you use to perform that management. Customers can review exactly what 365TUNE will access before granting consent.

**What happens if a customer revokes the application?**

If a customer revokes 365TUNE's application permissions, you'll lose access to their data in the 365TUNE platform, even if you still have GDAP access to their tenant. This is by design—it gives customers granular control over which management tools can access their data.

**Can we use a single app registration for all customers?**

No, each customer tenant requires its own app registration and consent. This is a fundamental aspect of Microsoft's multi-tenant security model. Each tenant maintains its own security boundary, and applications must be explicitly registered and consented to within each tenant.

**Is this the same as the old DAP model?**

No, this is more secure than DAP. With the old DAP model, partners had broad, permanent admin access to customer tenants with limited visibility into what actions were performed. The GDAP + application registration model provides granular, time-limited permissions, clear audit trails, and explicit consent requirements that give customers much better control and visibility.

### Summary

The requirement to register 365TUNE in each customer tenant represents a security best practice that protects both MSPs and their customers. While it adds a setup step, it ensures that customers maintain full control over their data, that all access is properly audited, and that permissions are granted explicitly rather than implicitly.

This architecture aligns with Microsoft's Zero Trust security principles and provides the transparency and accountability that modern security practices demand. By understanding why this requirement exists, you can confidently explain it to your customers and demonstrate 365TUNE's commitment to secure, controlled access to their Microsoft 365 environment.
