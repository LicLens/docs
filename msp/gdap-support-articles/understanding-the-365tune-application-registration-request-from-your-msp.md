# Understanding the 365TUNE Application Registration Request from Your MSP

Your Managed Service Provider (MSP) has asked you to register the 365TUNE application in your Microsoft 365 tenant. This article explains what 365TUNE does, why your MSP needs this access, and most importantly, how this approach actually protects your organization better than older methods of MSP access.

### What is 365TUNE?

365TUNE is a Microsoft 365 management, monitoring and reporting platform that your MSP uses to help manage your environment. It continuously analyzes your license usage, tracks user activity, identifies optimization opportunities, and generates security insights that help your MSP provide better service and potentially reduce your Microsoft 365 costs.

Think of it as a specialized dashboard that gives your MSP detailed visibility into how your organization uses Microsoft 365 - information that helps them proactively manage your environment and make informed recommendations.

### Why Your MSP Needs Application Registration

You may already have a GDAP (Granular Delegated Admin Privileges) relationship with your MSP, which allows their technicians to access your Microsoft 365 admin center and make necessary changes. You might be wondering: "If they already have access through GDAP, why do they need to register another application?"

The answer lies in how different types of access work in Microsoft 365:

#### Understanding the Two Types of Access

**GDAP provides user-level access:** When an MSP technician logs into your environment using GDAP, they're accessing your systems as an authenticated user. This is perfect for making changes, troubleshooting issues, and performing administrative tasks—but it only works while someone is actively logged in.

**365TUNE needs application-level access:** To provide continuous monitoring and keep dashboards current, 365TUNE needs to collect data 24/7 in the background—even when no MSP technicians are logged in. This requires a different type of permission called "application permissions."

#### The Critical Security Distinction

Here's what makes this approach secure for your organization:

**For background monitoring (read-only):** 365TUNE uses application permissions to continuously collect license usage data, user activity metrics, and generate insights. This data collection is entirely read-only—the application cannot make any changes to your environment on its own.

**For any changes (write operations):** When your MSP needs to modify licenses, update user settings, or make any configuration changes, those actions are performed by a logged-in MSP technician using their GDAP permissions—not by the 365TUNE application. This means no automated changes can happen; every modification requires a real person with proper credentials to be actively logged in and explicitly perform the action.

### Why This Protects Your Organization

While granting application access might seem like giving away control, this model actually provides several important security benefits for your organization:

#### 1. You Maintain Explicit Control

Every application that accesses your tenant must be explicitly registered and consented to by your administrators. Your MSP cannot simply connect any tool they want to your environment without your knowledge and approval. You get to review and approve what 365TUNE can access before granting permissions.

#### 2. You Can See Exactly What's Requested

During the registration process, you'll see exactly which Microsoft Graph API permissions 365TUNE is requesting. These are limited to the specific read permissions needed for license auditing and activity monitoring. You're not granting broad or undefined access—you can review the specific capabilities being requested.

#### 3. Read-Only Monitoring, Human-Authorized Changes

365TUNE's application permissions are exclusively read-only. The application cannot make any changes to user accounts, licenses, or configurations on its own. All modifications must be performed by a logged-in MSP technician using their GDAP permissions, ensuring:

* Every change requires human authorization
* All modifications are logged under a specific person's identity
* No automated or unexpected changes can occur
* Complete accountability for all actions

#### 4. Independent Revocation Rights

If you ever want to remove 365TUNE's access, you can revoke it immediately through your Azure AD admin center without affecting your MSP's GDAP access or their ability to provide other services. This separation means you control access to the monitoring tool independently from your overall MSP relationship.

#### 5. Complete Audit Trails

All 365TUNE API calls are logged in your Azure AD sign-in logs and audit logs with the application identity clearly identified. More importantly, any changes made by your MSP technicians—whether through 365TUNE or directly—are logged under that specific technician's identity, providing complete traceability of who did what and when.

### Common Questions

**Can my MSP access our tenant without this application registration?**

Yes, your MSP can still use their GDAP permissions (if you have provided) to access your Microsoft 365 admin center and make changes manually. The application registration is specifically for the 365TUNE monitoring tool. Without it, they lose the ability to use 365TUNE's automated monitoring and reporting features for your tenant, but their direct GDAP access for manual administration remains unchanged.

**What happens if we revoke 365TUNE's access?**

If you revoke the application, 365TUNE will immediately stop collecting data from your tenant, and your MSP's dashboards and reports for your organization will stop updating. However, your MSP will still have their GDAP access for manual administration—they just won't have the automated monitoring and insights that 365TUNE provides.

**How do we revoke access if needed?**

You can revoke 365TUNE's access at any time through your Azure Active Directory admin center under "Enterprise Applications." Simply locate the 365TUNE application and remove it. The access revocation takes effect immediately.

**Will 365TUNE ever make changes without our MSP's involvement?**

No, absolutely not. 365TUNE's application permissions are read-only and cannot make any modifications to your environment. All changes—whether to licenses, users, or configurations—must be performed by a logged-in MSP technician using their GDAP permissions. This ensures every change has human authorization and is traceable to a specific person.

**Is our data being shared outside our MSP relationship?**

365TUNE collects and processes data to provide monitoring and reporting services to your MSP. You should ask your MSP about 365TUNE's data handling practices, including where data is stored and how it's protected. Your MSP should be able to provide this information or connect you with 365TUNE's documentation.

**Can we limit what 365TUNE can see?**

The permissions granted during app registration define what 365TUNE can access. These permissions are set at registration time, and the application can only access what was explicitly consented to. You cannot fine-tune permissions after registration, but you can revoke access entirely if the permissions are too broad for your comfort level.

### Making an Informed Decision

Granting application registration is a trust decision, but it's built on several security principles that protect your organization:

* **Explicit consent** ensures you control what tools access your environment
* **Read-only monitoring** prevents unauthorized automated changes
* **User-authorized modifications** ensure all changes require human decision-making
* **Independent revocation** gives you control to remove access anytime
* **Complete audit trails** provide accountability and transparency

Your MSP relationship already involves a significant level of trust—GDAP access gives them administrative capabilities in your environment. The 365TUNE application registration extends that trust to include a monitoring tool that helps them provide better service, but with the added benefit that this access is separately granted, limited to read operations, and independently revocable.

### Summary

When your MSP asks to register 365TUNE in your tenant, they're requesting explicit permission to use a monitoring tool that helps them manage your Microsoft 365 environment more effectively. This registration is required because:

1. GDAP user permissions alone don't allow continuous background monitoring
2. Application permissions enable 24/7 data collection for always-current insights
3. The dual permission model ensures monitoring is automated but changes require human authorization

The security model protects your organization by:

* Separating read (application) from write (user GDAP) operations
* Requiring explicit consent for the specific permissions needed
* Logging all activities with clear identity attribution
* Allowing independent revocation of monitoring access

This approach aligns with Microsoft's modern security practices and gives you better visibility and control than older MSP access methods. By understanding what you're granting and why it's structured this way, you can make an informed decision that balances security with the operational benefits your MSP provides.

If you have concerns or questions about the specific permissions being requested, don't hesitate to discuss them with your MSP before granting consent. A good MSP relationship includes transparency about the tools they use and how they access your environment.
