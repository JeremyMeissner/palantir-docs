---
source_url: "https://www.palantir.com/docs/gotham/security/"
title: "Documentation | Security > Overview"
---
# Security

Palantir helps organizations solve real-world problems using powerful, secure software platforms. For more than a decade, we’ve worked with customers in the most secure and highly-regulated industries to build software for their most sensitive data. Today, security and privacy remain the cornerstone of our product development, company culture, and internal operations.

Palantir's software is used by healthcare providers, financial institutions, utility providers, manufacturers, telecoms, airlines, and pharmaceutical companies around the globe to handle their most sensitive workflows. We built our software for security-conscious customers who need the capability to handle financial data, Personally Identifiable Information (PII), Protected Health Information (PHI), Controlled Unclassified Information (CUI), and even classified government data in a secure and compliant manner. Our platform's strong security enables regulatory requirements across industries and continents by aligning with frameworks like HIPAA, GDPR, and ITAR.

As our software powers mission-critical operations across major corporations and governments alike, our threat model focuses on defeating attacks by highly resourced, technical, and persistent adversaries. To defeat these adversaries, we take a highly opinionated stance and enforce a high minimum bar of security for all our customers. For example, multi-factor authentication has been mandatory for all our managed Software as a Service (SaaS) platform customers for years.

## Platform security

Palantir has security as a core development philosophy. Our platform security model enables strict enforcement of granular access controls with transparency and usability to build a collaborative and trusted ecosystem:

* **Strict enforcement:** Ensures users only have access to data that they have been authorized to interact with.
* **Granular controls:** Powerful enough to achieve flexible levels of access control granularity.
* **Transparency:** Enables users to reason about *who* has access to *what* resource and *why*.
* **Usability:** Empowers users to reason about and manage access controls with confidence.

Our platform security model encompasses both authentication and authorization. Authentication verifies the identity of a user, while authorization grants access based on a user’s attributes and permissions.

Data security in the Palantir platform is guaranteed through a combination of mandatory and discretionary controls. Mandatory controls propagate along with each unit of data or resource type, via our sophisticated provenance and lineage capabilities. Discretionary permissions are granted to users on individual resources, in the form of roles with different operations (for example, view or edit). In addition, granular row or column-level controls based on a user’s attributes can be put in place on resources too.

For highly sensitive data, markings are another form of mandatory controls that can be applied to data or resources that require special protection (for example, PII or financially sensitive data). Users must have special permission to discover or access such data.

## Enterprise security

We reject the notion of gating, pay-walling, or upselling core security controls like audit logging, single sign-on, and multi-factor authentication. Whether you’re a small business or a federal agency, you get access to every core enterprise security feature in our standard offering:

* Mandatory **encryption** of all data, both in transit and at rest, that uses robust, modern cryptography standards.
* Strong **authentication** and identity protection controls, including single sign-on and multi-factor authentication.
* Strong **authorization** controls, including mandatory and discretionary access controls.
* Robust **security audit logging** for detecting and investigating potential abuse.
* Highly extensible **information governance, management, and privacy controls** to meet the needs of any use case.

## Infrastructure security

If you are using our managed SaaS platform, Palantir’s hosted infrastructure has additional layers of security controls to help protect your data:

* Robust **security architecture** built around principles of zero trust, least privilege, and defense-in-depth.
* Enforced **security baseline configurations** with rigorous change management and security monitoring processes.
* Strong **network security** hardening and segmentation.
* Host-based and network-based **intrusion detection systems** to detect and defeat anomalous activity.
* Aggressive **infrastructure and application vulnerability management and patching**, with industry-leading SLAs.
* **Web application firewall** (WAF) inspection of incoming web requests to detect and block attacks.
* **Security monitoring** at every layer of the environment, including users, hosts, networks, and applications.

## Conclusion

Palantir cares deeply about the security outcomes of our customers, and we’re committed to transparency about our security practices and program. We stand resolute in continuously improving our security, data protection, and privacy controls to give you the most effective means of protecting your data possible.
