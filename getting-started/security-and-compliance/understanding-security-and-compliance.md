---
description: >-
  This article documents the security and compliance analysis capabilities
  available in 365TUNE. Four distinct frameworks provide comprehensive security
  posture assessment for Microsoft 365 and Entra ID
---

# Understanding Security and Compliance

365TUNE Security and Compliance Analyzer, powered by Maester, consolidates multiple security frameworks into unified automation, providing comprehensive Microsoft 365 security posture assessment through four analysis engines. &#x20;

With 180+ controls, each framework serves specific organizational requirements ranging from federal regulatory compliance to threat-informed security operations. Understanding the scope, coverage, and technical implementation of these frameworks enables effective security assessment strategy and compliance reporting.&#x20;

{% hint style="info" %}
365TUNE automatically executes all tests & analysis. No scripting, coding, PowerShell modules, or manual setup required.
{% endhint %}

### Available Analysis Frameworks/Benchmarks

<table><thead><tr><th width="290">Framework</th><th width="126">Control Count</th><th>Primary Focus</th><th>Compliance Mapping</th></tr></thead><tbody><tr><td><a href="cis-microsoft-365-foundations-benchmark.md">CIS Microsoft 365 Benchmark</a></td><td>140</td><td>Prescriptive hardening guidance</td><td>NIST, ISO 27001, PCI DSS, HIPAA, SOC 2</td></tr><tr><td><a href="cisa-secure-cloud-business-applications.md">CISA Secure Cloud Business Applications</a></td><td>65-85</td><td>Federal security mandates</td><td>NIST 800-53, MITRE ATT&#x26;CK</td></tr><tr><td><a href="understanding-security-and-compliance.md#entra-id-security-config-analyzer">Entra ID Security Config Analyzer</a></td><td>46+</td><td>Attack-defense configuration analysis</td><td>MITRE ATT&#x26;CK</td></tr><tr><td><a href="understanding-security-and-compliance.md#community-recommended-controls">Community Recommended Controls</a></td><td>185+</td><td>Unified automation across multiple standards</td><td>CISA, CIS, EIDSCA, MITRE ATT&#x26;CK</td></tr></tbody></table>

### CIS Microsoft 365 Benchmark

Industry consensus security guidance with 140 prescriptive controls developed through the Center for Internet Security's expert community in partnership with Microsoft. 365TUNE automatically scans all automated CIS controls without requiring scripting, coding, or manual configuration.&#x20;

CIS Benchmark covers nine service areas: Admin Center, Defender, Purview, Data Management, Entra ID, SharePoint, Mobile Device Management, Teams, and Power BI.&#x20;

Structured profiles enable risk-proportionate implementation: Level 1 for essential security, Level 2 for enhanced protection, with separate E3/E5 licensing considerations. Direct compliance mappings to NIST CSF, ISO 27001, PCI DSS, HIPAA, SOC 2, CMMC, FedRAMP, and SOX enable single-assessment multi-framework compliance documentation. 365TUNE delivers instant CIS compliance scoring with automated remediation guidance.

#### Framework Highlights:

* 140 prescriptive controls across 9 service areas
* Level 1/Level 2 profiles, E3/E5 licensing awareness
* Comprehensive compliance mappings: NIST, ISO 27001, PCI DSS, HIPAA, SOC 2
* Focus: Industry-standard hardening guidance

### CISA Secure Cloud Business Applications

Security baseline providing 65-85 controls across seven Microsoft 365 workloads: Entra ID, Exchange Online, Defender, Teams, SharePoint/OneDrive, Power Platform, and Power BI.&#x20;

365TUNE implements automatic scanning for all CISA controls without scripting or coding requirements. Compliance assessment runs automatically on scheduled intervals, delivering pass/fail status for each control. Maps directly to NIST SP 800-53 Rev. 5 and MITRE ATT\&CK with 6,300+ technique mappings.&#x20;

Controls address critical security areas including legacy authentication blocking, phishing-resistant MFA, email authentication (SPF/DKIM/DMARC), anti-phishing policies, Safe Attachments/Links, external sharing restrictions, and DLP policies.&#x20;

365TUNE provides immediate CISA compliance reporting for organizations requiring NIST-aligned security standards and government-grade security configurations.

#### Framework Highlights:

* 65-85 controls across 7 Microsoft 365 workloads
* NIST 800-53 and MITRE ATT\&CK mappings
* Focus: Government-grade security validation

### Entra ID Security Config Analyzer

Attack-defense framework mapping 46+ security configurations to documented adversary techniques from the Microsoft Entra ID Attack and Defense Playbook. Available in 365TUNE with automatic scanning—no technical setup or coding required.&#x20;

Each control derives from offensive security research and maps to specific MITRE ATT\&CK techniques (phishing, valid accounts, brute force, token theft). Focuses on Entra ID authentication methods, authorization policies, consent framework, and password protection with Conditional Access visibility and sign-in effect analysis.&#x20;

365TUNE automatically assesses configurations against EIDSCA best practices on scheduled intervals, identifying security gaps that could enable documented attack techniques. Provides threat-informed security posture assessment with incident-ready findings for security operations teams without requiring Azure Logic App deployment or Sentinel integration overhead.

#### Framework Highlights:

* 46+ controls derived from attack research
* MITRE ATT\&CK technique mappings for each control
* 5 categories: Authentication, Authorization, Consent, Password, Conditional Access
* Focus: Threat-informed identity security

### Community Recommended Controls

Driven by Maester Community, this security framework with 185+ automated tests consolidating best practices from multiple authoritative sources. Available natively in 365TUNE with automatic scanning—no scripting or coding required. Provides comprehensive coverage across Conditional Access, Privileged Identity Management, authentication methods, Exchange Online security, and Microsoft Defender configurations.&#x20;

Unique capabilities include Conditional Access What-If simulation for policy validation, stale reference detection identifying deleted objects in policies, emergency account validation, and configuration drift monitoring. Covers Microsoft Entra ID, Exchange Online, SharePoint, Teams, and Intune with continuous community updates. 365TUNE automatically executes all tests on configurable schedules, delivering interactive reports with actionable remediation guidance and compliance scoring without technical overhead.

#### Framework Highlights:

* 185+ automated tests across 5 integrated frameworks
* Unique capabilities: What-If analysis, stale reference detection, drift monitoring
* Coverage: Entra ID, Exchange, Defender, SharePoint, Teams, Intune
* Focus: Unified automation with continuous community updates
