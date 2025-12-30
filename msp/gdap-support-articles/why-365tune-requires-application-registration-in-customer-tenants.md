# Why 365TUNE Requires Application Registration in Customer Tenants

When using 365TUNE, as a Managed Service Provider (MSP) with GDAP (Granular Delegated Admin Privileges), you'll need to register the 365TUNE application in each customer tenant you want to monitor. This article explains why this requirement exists, the security benefits it provides, and how it protects both you and your customers.

### Understanding the GDAP Context

GDAP represents Microsoft's modern approach to partner access, replacing the older Delegated Admin Privileges (DAP) model. With GDAP, you receive specific, time-limited permissions to customer tenants based on security group assignments in your partner tenant. This granular approach means you only have the permissions you actually need, reducing security risks for both parties.

However, GDAP alone only grants _your users_ access to customer resources. It doesn't automatically give applications the permissions they need to read tenant data on your behalf.

### Why Application Registration is Required

When 365TUNE needs to access Microsoft 365 data in a customer tenant, it must do so through the Microsoft Graph API and Office 365 Management Activity API. These APIs require explicit consent and permissions that can only be granted through an Azure AD application registration.

**Important: Understanding the Dual Permission Model**

{% hint style="info" %}
GDAP works on _user delegation_, which only functions when a user is actively logged in. This is perfect for secure, authenticated actions but has a limitation: it only works while someone is logged in. 365TUNE requires _Application delegation_ to collect data in the background 24/7.
{% endhint %}

365TUNE uses a dual permission model that combines both approaches:

**For background data collection (read-only):** 365TUNE uses application-level permissions via the Graph API to continuously collect license usage data, user activity, and generate insights. This happens in the background 24/7, even when no one is logged in, ensuring your dashboards are always up-to-date.

**For all edit actions (write operations):** 365TUNE uses logged-in user's GDAP delegated permissions, not the application's permissions. If you need to modify licenses, update user settings, or make any changes, those actions are performed through your active GDAP session. This means 365TUNE never makes changes on its own - every edit action requires a real, authenticated user with proper GDAP permissions to be logged in.

This architecture ensures that data collection is continuous and automated, while maintaining strict security controls that require human authorization for any modifications.

Here's what happens when you try to access customer data:

**Your GDAP permissions** allow you as an MSP technician to sign into the Microsoft 365 admin center and view customer data manually. However, when 365TUNE attempts to make API calls to Microsoft Graph on your behalf, those calls originate from the 365TUNE application, not from your user account.

**The Microsoft identity platform** checks two things: Does this application have permission to access this tenant? Does the current user have permission to consent to or use this application? Without an app registration in the customer tenant, the answer to the first question is "no," and the API calls will fail.

{% hint style="info" %}
365TUNE does not provide blanket access across all MSP users. Access is strictly limited to users explicitly granted permissions through GDAP relationships, and only for the specific tenant they are assigned to.
{% endhint %}

### The Security Benefits of This Model

This requirement might seem like extra work, but it provides important security advantages:

**Explicit customer consent** means that each customer must actively approve 365TUNE's access to their tenant. This prevents scenarios where an MSP could connect any third-party application to customer tenants without their knowledge or approval. Your customers maintain full control over which applications can access their data.

**Granular permission control** allows customers to see exactly what permissions 365TUNE requests before granting access. The application only requests the specific Microsoft Graph API permissions it needs to perform license auditing and activity monitoring. Customers can review these permissions and understand what data will be accessed.

**Separation of read and write operations** ensures that 365TUNE's application permissions are exclusively read-only. All modifications to user accounts, licenses, or configurations must be performed through a logged-in MSP technician's GDAP delegated permissions. This prevents any automated or unauthorized changes and ensures every modification has a human decision-maker and a clear audit trail tied to a specific user identity.

**Independent revocation** means that if a customer wants to remove 365TUNE's access, they can revoke it immediately through their Azure AD admin center without affecting your GDAP access or other services. This separation of concerns gives customers confidence that they can stop data access at any time.

**Audit trail preservation** ensures that all 365TUNE API calls are logged in the customer's Azure AD sign-in logs and audit logs with the application identity clearly identified. More importantly, any modifications made through 365TUNE are logged under the specific MSP technician's user identity who performed the action, providing complete accountability and traceability.

### How This Works With GDAP

365TUNE uses a dual authentication and permission model that leverages both application permissions and GDAP user delegation:

**For continuous data collection (read-only):** When you sign into 365TUNE with your MSP account, the platform detects your GDAP relationships through your security group memberships. This determines which customer tenants you should be able to access.

For each customer tenant, 365TUNE checks whether the application has been registered and granted permissions in that tenant. If it has, you can connect that customer to 365TUNE and begin monitoring their license usage.

365TUNE then uses its application-level permissions to collect data in the background—analyzing user activity, license assignments, and generating insights. This happens continuously, 24/7, keeping your dashboards current without requiring anyone to be logged in.

**For any edit operations (write actions):** When you need to make changes—such as modifying licenses, updating user properties, or adjusting configurations—365TUNE uses logged-in user's GDAP delegated permissions to perform these actions. The platform never makes modifications using application permissions.

**Security enforcement at multiple layers:** 365TUNE enforces that you can only access customer data if you have valid GDAP permissions for that customer. This means even if the application has been granted permissions in a customer tenant, individual MSP technicians can only see the customers they're authorized to manage through their GDAP relationships.

Additionally, any write operations are governed by your GDAP permission boundaries—if your GDAP role doesn't allow license modifications, for example, you won't be able to make those changes through 365TUNE either.

This creates a security boundary at both the application level (for read operations) and the user level (for write operations), ensuring that access control and modification rights are properly enforced throughout the stack.

**All edit operations—such as modifying licenses, updating user properties, or making configuration changes—are performed using your logged-in user's GDAP delegated permissions.**&#x20;

This ensures that every modification is:

* Performed by an authenticated human user
* Logged under that specific user's identity in audit logs
* Governed by that user's GDAP permission boundaries
* Requiring active user login and cannot happen automatically

This separation between read (application permissions) and write (user GDAP permissions) provides robust security controls and clear audit trails for all actions taken in customer tenants.

### Common Questions and Concerns

**Why can't 365TUNE use my GDAP permissions directly?**

365TUNE actually DOES use your GDAP permissions directly—but only for write operations (modifications to users, licenses, configurations).

The application-level permissions are needed for a different purpose: continuous background data collection. GDAP permissions are user-level permissions that only work when you're actively logged in. If 365TUNE relied solely on GDAP permissions, it would need someone to stay logged in 24/7 just to collect activity data and keep dashboards updated.

Instead, 365TUNE uses application permissions for read-only background monitoring, which runs continuously even when no one is logged in. But when you actually need to make changes, those actions use YOUR GDAP delegated permissions, ensuring that modifications require human authorization and are logged under your user identity.

This dual approach gives you the best of both worlds: always-current data without requiring constant logins, plus secure, accountable modifications that require authenticated users with proper permissions.

**Do customers need to trust our MSP for this to work?**

Yes, but this is already inherent in the MSP relationship. When customers grant you GDAP access, they're already trusting you to manage their Microsoft 365 environment. The app registration requirement simply extends that trust to include the tools you use to perform that management. Customers can review exactly what 365TUNE will access before granting consent.

**What happens if a customer revokes the application?**

If a customer revokes 365TUNE's application permissions, the platform will lose the ability to collect data in the background for that tenant. Your dashboards and reports for that customer will stop updating, even if you still have GDAP access to their tenant.

However, you would still be able to make manual changes in the Microsoft 365 admin center using your GDAP permissions directly—365TUNE just wouldn't be able to monitor or analyze that tenant's license usage anymore.

This is by design—it gives customers granular control over which management tools can access their data for monitoring purposes, while keeping your direct GDAP access intact for manual administration.

**Can we use a single app registration for all customers?**

No, each customer tenant requires its own app registration and consent. This is a fundamental aspect of Microsoft's multi-tenant security model. Each tenant maintains its own security boundary, and applications must be explicitly registered and consented to within each tenant.

**How does 365TUNE handle read vs. write operations?**

365TUNE uses a dual permission model for maximum security. Application permissions (granted through app registration) are used exclusively for read-only background data collection—analyzing licenses, monitoring activity, and generating insights. These operations happen continuously without requiring a user to be logged in.

However, any write operations—modifying licenses, changing user settings, or updating configurations—are performed using YOUR GDAP delegated permissions while you're logged in. This means 365TUNE never makes changes autonomously. Every modification requires an authenticated MSP technician with proper GDAP permissions to be actively logged in, ensuring full accountability and a complete audit trail.

This architecture prevents unauthorized automated changes while still allowing 365TUNE to keep your data current with continuous background monitoring.

**Is this the same as the old DAP model?**

No, this is more secure than DAP. With the old DAP model, partners had broad, permanent admin access to customer tenants with limited visibility into what actions were performed. The GDAP + application registration model provides granular, time-limited permissions, clear audit trails, and explicit consent requirements that give customers much better control and visibility.

### Summary

The requirement to register 365TUNE in each customer tenant represents a security best practice that protects both MSPs and their customers. While it adds a setup step, it ensures that customers maintain full control over their data, that all access is properly audited, and that permissions are granted explicitly rather than implicitly.

365TUNE's dual permission model—using application permissions exclusively for read-only data collection and GDAP user permissions for all modifications—provides robust security controls that prevent unauthorized automated changes while ensuring continuous monitoring. Every edit operation requires an authenticated human user with proper GDAP permissions, creating clear accountability and complete audit trails.

This architecture aligns with Microsoft's Zero Trust security principles and provides the transparency and accountability that modern security practices demand. By understanding why this requirement exists, you can confidently explain it to your customers and demonstrate 365TUNE's commitment to secure, controlled access to their Microsoft 365 environment.
