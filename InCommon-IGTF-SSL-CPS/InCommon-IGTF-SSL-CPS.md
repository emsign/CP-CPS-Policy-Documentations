| Policy Document Description | Date of Publication | Version | CP/CPS OID |
|---|---|---|---|
|InCommon Certification Practices Statement for the InCommon IGTF Server Certification Authority | 21-Sep-2026 | 3.04 | 1.3.6.1.4.1.5923.1.4.3.4.3 |

# 1. INTRODUCTION

InCommon (“InCommon”) is an identity and trust community and services provider that offers optional subscription services for X.509 PKI certificates issued by an InCommon certification authority. CertiNext verifies the identity of each Subscriber and the Internet domains for which they are authoritative. InCommon outsources functions including protecting the CA private key, signing certificates, revoking certificates, publishing Certificate Revocation Lists (“CRLs”) and the operation of an Online Certificate Status Protocol (“OCSP”) responder to CertiNext Inc under the Master Services Agreement (“CertiNext Agreement”) between CertiNext Inc. (“CertiNext”) and University Corporation for Advanced Internet Development (d/b/a Internet2) and its single-member LLC, InCommon.

## 1.1 Overview

This InCommon Certification Practices Statement (CPS) outlines the legal, commercial, and technical principles and practices InCommon employs in managing the InCommon RSA IGTF Server CA 4. This CA signs SSL/TLS certificates as a result of Certificate Signing Requests (CSRs) approved by InCommon designated representatives (and their delegates) of research or educational institutions that are Subscribers to the InCommon Certificate Service. Certificates issued by the InCommon RSA IGTF Server CA 4 meet the requirements of the International Grid Trust Federation (IGTF) Classic CA Profile.

The InCommon RSA IGTF Server CA 4 intermediary CA certificate is signed by CertiNext’s emSign Root CA – G1 which in turn is signed by emSign Root CA - G1, so the InCommon RSA IGTF Server CA 4 and CPS are required to comply with applicable CertiNext policies, practices, CPS and agreements. In the event of a conflict between this CPS and IGTF requirements and CertiNext CPS and agreements, InCommon will promptly notify both IGTF and CertiNext and work with all parties to resolve the conflict.

The CPS is formatted and maintained in accordance with IETF PKIX RFC 3647. To preserve the format of RFC 3647, some section headings do not apply and will contain the text “Not applicable” ("n/a") or “No stipulation”. The RFC 3647 format is preserved to assist the reader in comparing and contrasting the various CPS documents provided by various CAs.

Sections of this CPS refer to services or practices provided by CertiNext under the CertiNext Agreement and in accord with provisions with the CertiNext Public Trust TLS (emSign hierarchy) “Certification Practice Statement” (<https://repository.emsign.com/>). The applicable CertiNext CPCPS is identified by the policy identifier 1.3.6.1.4.1.5923.1.4.3.1.2 latest version as of this publishing.

Such sections will contain the text “Provided by CertiNext as stated in the CertiNext CPS and binding upon the Subscriber.” The phrase “issued by InCommon” is to be interpreted as “issued by the corresponding CertiNext CA under the CertiNext Agreement.”

This CPS specifies the principles, procedures, and practices that the InCommon RSA IGTF Server CA 4 intermediary CA certificate follows to conform to the following standards, guidelines, and root program requirements:

1. RFC 3647 of the Internet Engineering Task Force (IETF):
   - Framework for Certificate Policy and Certification Practice Statement structure.
2. The latest versions (as on date of this CPS) of the CA/Browser Forum Requirements (Ref: <https://cabforum.org/>):
   - Baseline Requirements for the Issuance and Management of Publicly-Trusted Certificates (TLS BR)
   - Baseline Requirements for the Issuance and Management of Extended Validation (EV) Certificates
   - Network and Certificate System Security Requirements
   - *(Note: While other CA/B Forum Baseline Requirements such as for S/MIME and Code Signing exist, they are out of scope for this SSL/TLS CP/CPS and are included here only for completeness and alignment of terminology)*
3. WebTrust: Principles and Criteria for Certification Authorities, including:
   - WebTrust: Principles and Criteria for Certification Authorities – Network Security
   - WebTrust: Principles and Criteria for Certification Authorities - TLS Baseline
   - WebTrust: Principles and Criteria for Certification Authorities – Extended Validation TLS (where applicable)
4. Adherence to the latest published version Root Program Requirements and CCADB policy of major relying party software providers:
   - Google Chrome Root Program Policy
   - Mozilla Root Store Policy
   - Apple Root Certificate Program
   - Microsoft Root Certificate Program

If any inconsistency exists between this CP/CPS and aforesaid requirements, then the aforesaid Requirements take precedence over this CP/CPS.

## 1.2 Document Name and Identification

This document is the InCommon IGTF Server CPS version 3.04, which was approved for publication on 2026 by InCommon's certification Policy Authority. There is no separate Certification Policy document; policy is incorporated within this document.

The object identifier (cpOID) for this CPS is identified in Appendix B and will be included in end-entity certificates issued by InCommon. The current version of the CPS is made available to the public through InCommon's repository as described in Section 2 below.

Each new version of this CPS will result in assignment of a new cp OID to this document. Only significant changes that affect the trustworthiness of certificates require a newCPS to be produced.

Revisions to this document have been made as follows:

| Date | Changes | Version |
|---|---|---|
| August 2013 | Initial version for IGTF Server CA. | 1.0 |
| November 2013 | Reference CPS documents explicitly in Section 1.1. | 1.1 |
| May 2023 | Update references from Comodo to Sectigo, update hierarchy | 2.0 |
| April 2026 | InCommon CA platform provider transitioned to CertiNext Inc | 3.0 |
| July 2026 | Section 4.9.10 updated in accordance with the CA/Browser Forum TLS Baseline Requirements. | 3.02 |
| July 2026 | Reference to updated CAA validation procedures and Domain Component validation procedures in accordance the CA/Browser Forum TLS Baseline Requirements and referenced in the corresponding CertiNext CP/CPS | 3.03 |
| Sept 2026 | Updated the CPS in Alignment to latest approved TLS BR | 3.04 |

## 1.3 PKI Participants

### 1.3.1 Certification Authorities

Certification Authorities (CAs) issue public key certificates to subscribers. InCommon contracts a CA platform provider to operate and manage CAs on it’s behalf. A certification authority:

- Conforms its operations to this CPS as amended, and any additional underlying CP/CPS identified by this CPS
- Revokes certificates upon request by an authorized person,
- Maintains and updates its OCSP services on a regular basis,
- Publishes CRLs on a regular basis,
- Distributes issued certificates, and
- Notifies subscribers via email of expiring certificates that it has issued to them.

### 1.3.2 Registration Authorities

InCommon manages its own internal Registration Authority (RA) for IGTF purposes. Each Subscriber organization also manages and operates a delegated RA – comprising its Subscriber Registrars and any Delegated Subscriber Registrars – that is responsible for activities under its own management control for its own organization in respect to IGTF-specific requirements. InCommon relies upon the CA platform provider RAs to meet the latest requirements of CA/B Forum Baseline Requirements. InCommon RAs may act as trusted agents in assisting the CA platform RAs in their responsibilities.

### 1.3.3 Subscribers

Subscribers are research and education institutions, organizations, or other entities that use InCommon's PKI services to acquire certificates that support transactions and communications.

Subjects are identified in an issued certificate. The Requester controls the private key corresponding to the public key listed in an issued certificate.

Regardless of the Subject listed in the Certificate, the Subscriber always has the responsibility of ensuring that the Certificate is only used appropriately.

### 1.3.4 Relying Parties

Relying parties use InCommon's PKI service certificates to perform transactions, communications, or other functions at their own discretion.

Digital certificates do not guarantee that a certificate holder has good intentions or that the certificate holder will be an ethical business operation. It is the Relying Party’s responsibility to independently examine each certificate holder to determine whether the certificate owner is ethical and trustworthy.

### 1.3.5 Other participants

Other Participants are defined in their respective InCommon practices, guidelines, and by contract with CERTINext

## 1.4 Certificate Usage

A digital certificate is formatted data that cryptographically binds an identified Subject to a public key. A digital certificate allows an entity taking part in an electronic transaction to assert its identity to the other participants in such a transaction.

### 1.4.1 Appropriate Certificate Uses

Certificates issued under this CP/CPS are intended solely for use in TLS Server Authentication (idkpserverAuth, OID 1.3.6.1.5.5.7.3.1), as indicated by the Key Usage and Extended Key Usage (EKU) extensions included in the certificate.

These certificates enable secure communication by authenticating the identity of a server and establishing encrypted TLS sessions with client systems, such as web browsers or applications. Subscribers are responsible for selecting the appropriate certificate type based on the intended usage and assurance level required for their deployment environment.

IGTF CA issues the following SSL/TLS certificate profiles:

- Organization Validated (OV) Certificates: Intended for use where moderate assurance of the server operator’s identity is needed. OV certificates include verified organization information in the certificate subject.
- Wildcard Certificates: Enable encryption for all first-level subdomains under a single domain (e.g., \*.example.com). Wildcard certificates are available OV certificates only. Wildcard domain names SHALL NOT be included in EV Certificates, in accordance with CA/B Forum requirements.

The Subscriber must ensure that each certificate is used solely for its intended purpose and in accordance with this CPS, applicable agreements, and published certificate profiles.

This section defines the intended technical usage of certificates as governed by their certificate profile and extensions. It does not constitute a representation or guarantee of fitness for a particular purpose. Assurance levels vary based on certificate type and are subject to applicable validation procedures and the Subscriber Agreement.

### 1.4.2 Prohibited Certificate Uses

Certificates may only be used in accordance with their intended purpose and in compliance with all applicable laws and regulations including export laws as described in the Subscriber Addendum.

Certificates may not be used to complete or assist in performing any transaction that is prohibited by law. Digital certificates do not guarantee that a certificate holder has good intentions or that the certificate holder will be an ethical business operation.

Certificates may not be used for any application requiring fail-safe performance systems such as the operation of nuclear power facilities, air traffic control systems, weapon control systems, or any other system where a failure of the system could cause loss of life or property.

## 1.5 Policy Administration

### 1.5.1 Organization Administering the Document

This CPS is administered by the InCommon Policy Authority (PA). The InCommon PA is described in a document available in the InCommon CA repository as described in Section 2.

### 1.5.2 Contact Person

InCommon:

InCommon Certificate Service c/o Internet2

3520 Green Court, Suite 200 Ann Arbor, MI 48105

Email: [help@incommon.org](mailto:help@incommon.org) Phone: 1-734-913-4250

#### 1.5.2.1 Certificate Problem Reporting

To report problems with a certificate issued by us or request revocation, parties may contact us or use one of the supported automated mechanisms.

##### 1.5.2.1.1 Email Contact

Certificate-related issues such as key compromise, certificate misuse, or suspected fraudulent issuance may be reported via email:

- Attn: Revocation Support
- Email: <problem-reporting@emsign.com>

##### 1.5.2.1.2 CERTInext Portal

Subscribers, partners, and authorized users may initiate certificate revocation requests through the CERTInext Portal using the certificate management dashboard that is available via Login using: URL: <https://www.certinext.io>

##### 1.5.2.1.3 Enterprise API / Partner Integrations

Enterprise customers and authorized partners integrated with our platforms via secure APIs may submit certificate revocation requests programmatically. API access must be pre-authorized and authenticated in accordance with the API Specifications.

##### 1.5.2.1.4 ACME revokeCert Endpoint

For ACME-enabled accounts, certificate revocation may also be requested using the ACME revokeCert method if the Subscriber is in possession of the corresponding private key.

- ACME Directory: <https://acme.emsign.com/v1/directory>
- revokeCert Endpoint: <https://acme.emsign.com/v1/acme/revokeCert>

We authenticate all revocation requests based on the requester’s identity and relationship to the certificate. Requests submitted through trusted channels by Subscribers or Subject Organizations are verified using registered credentials or account-based validation. Requests from third parties may undergo additional investigation or corroboration prior to revocation. All revocation requests and corresponding actions are logged and processed in accordance with this CP/CPS.

### 1.5.3 Person Determining CPS Suitability for the Policy

There is no separate Certificate Policy document. The CPS combines both policy and practices.

### 1.5.4 CPS Approval Procedures

InCommon's CPS (and any amendments made to it) are reviewed and approved by InCommon's Policy Authority and approved by TAGPMA before signing any certificates under the new CP/CPS. Amendments to the CPS may be made by reviewing and updating the entire CPS or by publishing an addendum.

## 1.6 Definitions & Acronyms

### 1.6.1 Definitions

Affiliate: A corporation, partnership, joint venture or other entity controlling, controlled by, or under common control with another entity, or an agency, department, political subdivision, or any entity operating under the direct control of a Government Entity.

Applicant Representative: A natural person or human sponsor who is either the Applicant, employed by the Applicant, or an authorized agent who has express authority to represent the Applicant: (i) who signs and submits, or approves a certificate request on behalf of the Applicant; and/or (ii) who signs and submits a Subscriber Agreement on behalf of the Applicant; and/or (iii) who acknowledges the Terms of Use on behalf of the Applicant when the Applicant is an Affiliate of the CA or is the CA.

Applicant: The natural person or Legal Entity that applies for (or seeks renewal of) a Certificate. Once the Certificate issues, the Applicant is referred to as the Subscriber. For Certificates issued to devices, the Applicant is the entity that controls or operates the device named in the Certificate, even if the device is sending the actual certificate request.

Application Software Supplier: A supplier of Internet browser software or other relying-party application software that displays or uses Certificates and incorporates Root Certificates.

Attestation Letter: A letter attesting that Subject Information is correct written by an accountant, lawyer, government official, or other reliable third party customarily relied upon for such information.

Audit Period: In a period-of-time audit, the period between the first day (start) and the last day of operations (end) covered by the auditors in their engagement. (This is not the same as the period of time when the auditors are on-site at the CA.) The coverage rules and maximum length of audit periods are defined in this CP/CPS.

Audit Report: A report from a Qualified Auditor stating the Qualified Auditor’s opinion on whether an entity’s processes and controls comply with the mandatory provisions of these Requirements.

Authorization Domain Name: The Domain Name used to obtain authorization for certificate issuance for a given FQDN. The CA may use the FQDN returned from a DNS CNAME lookup as the FQDN for the purposes of domain validation. If the FQDN contains a wildcard character, then the CA MUST remove all wildcard labels from the left most portion of requested FQDN. The CA may prune zero or more labels from left to right until encountering a Base Domain Name and may use any one of the intermediate values for the purpose of domain validation.

Authorized Port: One of the following ports: 80 (http), 443 (http), 115 (sftp), 25 (smtp), 22 (ssh).

Authorization Domain Name (ADN): The Fully-Qualified Domain Name used to perform validation of domain authorization or control for a given Fully-Qualified Domain Name or Wildcard Domain Name. CERTINext derives the Authorization Domain Name in accordance with the process specified in Section 3.2.2.4 of the CA/Browser Forum TLS Baseline Requirements, under which the permissibility of CNAME substitution, label pruning, wildcard use and Onion Domain Names is determined by the validation method selected.

Base Domain Name: The portion of an applied for FQDN that is the first domain name node left of a registry controlled or public suffix plus the registry controlled or public suffix (e.g. "example.co.uk" or "example.com"). For FQDNs where the right most domain name node is a gTLD having ICANN Specification 13 in its registry agreement, the gTLD itself may be used as the Base Domain Name.

Baseline Requirements (BR): Means the CA/Browser Forum Baseline Requirements for the Issuance and Management of Publicly-Trusted Certificates, published at <https://www.cabforum.org/>

Basic Constraints: Means an extension that specifies whether the subject of the Certificate may act as a CA or only as an end-entity

CA Key Pair: A Key Pair where the Public Key appears as the Subject Public Key Info in one or more Root CA Certificate(s) and/or Subordinate CA Certificate(s)

CAA: The Certification Authority Authorization (CAA) DNS Resource Record allows a DNS domain name holder to specify the Certification Authorities (CAs) authorized to issue certificates for that domain.

Publication of CAA Resource Records allows a public Certification Authority to implement additional controls to reduce the risk of unintended certificate misuse.

Certificate Data: Certificate requests and data related thereto (whether obtained from the Applicant or otherwise) in the CA’s possession or control or to which the CA has access.

Certificate Management Process: Processes, practices, and procedures associated with the use of keys, software, and hardware, by which the CA verifies Certificate Data, issues Certificates, maintains a Repository, and revokes Certificates.

Certificate Policy: A set of rules that indicates the applicability of a named Certificate to a particular community and/or PKI implementation with common security requirements.

Certificate Problem Report: Complaint of suspected Key Compromise, Certificate misuse, or other types of fraud, compromise, misuse, or inappropriate conduct related to Certificates.

Certificate Profile: A set of documents or files that defines requirements for Certificate content and Certificate extensions in accordance with Section 7, e.g. a Section in a CA’s CPS or a certificate template file used by CA software.

Certificate Revocation List: A regularly updated time-stamped list of revoked Certificates that is created and digitally signed by the CA that issued the Certificates.

Certificate System: Means the system used by CERTInext or a delegated third party in providing identity verification, registration and enrollment, Certificate approval, issuance, validity status, support, and other PKI-related services

Certificate Transparency: Means the protocol described in RFC 6962 for publicly logging the existence of Transport Layer Security (TLS) certificates as they are issued or observed.

Certificate: An electronic document that uses a digital signature to bind a public key and an identity.

Certificate Data: Certificate requests and data related thereto (whether obtained from the Applicant or otherwise) in the CA’s possession or control or to which the CA has access.

Certification Authority Authorization (CAA): Means a DNS domain holder specify one or more CAs authorized to issue certificates for that domain name. This is described in RFC 8659

Certification Authority: An organization that is responsible for the creation, issuance, revocation, and management of Certificates. The term applies equally to both Roots CAs and Subordinate CAs.

Certification Practice Statement: One of several documents forming the governance framework in which Certificates are created, issued, managed, and used.

Common Criteria: Is a framework in which computer system users can specify their security functional and assurance requirements (SFRs and SARs respectively) in a Security Target (ST), and may be taken from Protection Profiles (PPs). It is an international standard (ISO/IEC 15408) for computer security certification

Control: “Control” (and its correlative meanings, “controlled by” and “under common control with”) means possession, directly or indirectly, of the power to: (1) direct the management, personnel, finances, or plans of such entity; (2) control the election of a majority of the directors; or (3) vote that portion of voting shares required for “control” under the law of the entity’s Jurisdiction of Incorporation or Registration but in no case less than 10%.

Country: Either a member of the United Nations OR a geographic region recognized as a Sovereign State by at least two UN member nations.

Critical Vulnerability: A system vulnerability that has a CVSS v2.0 score of 7.0 or higher according to the NVD or an equivalent to such CVSS rating (see http://nvd.nist.gov/home.cfm https://nvd.nist.gov/vuln-metrics/cvss), or as otherwise designated as a Critical Vulnerability by the CA or the CA/Browser Forum

Cross Certificate: A certificate that is used to establish a trust relationship between two Root CAs.

CSPRNG: A random number generator intended for use in cryptographic system.

Delegated Third Party: A natural person or Legal Entity that is not the CA but is authorized by the CA to assist in the Certificate Management Process by performing or fulfilling one or more of the CA requirements found herein.

Domain Authorization Document: Documentation provided by, or a CA’s documentation of a communication with, a Domain Name Registrar, the Domain Name Registrant, or the person or entity listed in WHOIS as the Domain Name Registrant (including any private, anonymous, or proxy registration service) attesting to the authority of an Applicant to request a Certificate for a specific Domain Namespace.

Domain Contact: The Domain Name Registrant, technical contact, or administrative contract (or the equivalent under a ccTLD) as listed in the WHOIS record of the Base Domain Name or in a DNS SOA record.

Domain Label: From RFC 8499 (http://tools.ietf.org/html/rfc8499): “An ordered list of zero or more octets that makes up a portion of a domain name. Using graph theory, a label identifies one node in a portion of the graph of all possible domain names.”

Domain Name Registrant: Sometimes referred to as the “owner” of a Domain Name, but more properly the person(s) or entity(ies) registered with a Domain Name Registrar as having the right to control how a Domain Name is used, such as the natural person or Legal Entity that is listed as the “Registrant” by WHOIS or the Domain Name Registrar.

Domain Name Registrar: A person or entity that registers Domain Names under the auspices of or by agreement with: (i) the Internet Corporation for Assigned Names and Numbers (ICANN); (ii) a national Domain Name authority/registry; or (iii) a Network Information Center (including their affiliates, contractors, delegates, successors, or assigns).

Domain Name: The label assigned to a node in the Domain Name System.

Domain Namespace: The set of all possible Domain Names that are subordinate to a single node in the Domain Name System.

Enterprise RA: An employee or agent of an organization unaffiliated with the CA who authorizes issuance of Certificates to that organization.

EV Code Signing Certificate: CA/Browser Forum Guidelines for the Issuance and Management of Extended Validation Certificates published at <https://www.cabforum.org/>

EV Guidelines (EVG): CA/Browser Forum Guidelines for the Issuance and Management of Extended Validation Certificates published at <https://www.cabforum.org/>

Expiry Date: The “Not After” date in a Certificate that defines the end of a Certificate’s validity period.

Fully-Qualified Domain Name: A Domain Name that includes the labels of all superior nodes in the Internet Domain Name System.

Government Entity: A government-operated legal entity, agency, department, ministry, branch, or similar element of the government of a country, or political subdivision within such country (such as a state, province, city, county, etc.).

Grace Period: Means the period during which the Subscriber must make a revocation request.

High Risk Certificate Request: A Request that the CA flags for additional scrutiny by reference to internal criteria and databases maintained by the CA, which may include names at higher risk for phishing or other fraudulent usage, names contained in previously rejected certificate requests or revoked Certificates, names listed on the Miller Smiles phishing list or the Google Safe Browsing list, or names that the CA identifies using its own risk-mitigation criteria.

Internal Name: A string of characters (not an IP address) in a Common Name or Subject Alternative Name field of a Certificate that cannot be verified as globally unique within the public DNS at the time of certificate issuance because it does not end with a Top Level Domain registered in IANA’s Root Zone Database.

IP Address: A 32-bit or 128-bit number assigned to a device that uses the Internet Protocol for communication.

Issuing CA: In relation to a particular Certificate, the CA that issued the Certificate. This could be either a Root CA or a Subordinate CA.

Key Compromise: A Private Key is said to be compromised if its value has been disclosed to an unauthorized person, an unauthorized person has had access to it, or there exists a practical technique by which an unauthorized person may discover its value. A Private Key is also considered compromised if methods have been developed that can easily calculate it based on the Public Key (such as a Debian weak key, see http://wiki.debian.org/SSLkeys) or if there is clear evidence that the specific method used to generate the Private Key was flawed.

Key Generation Script: A documented plan of procedures for the generation of a CA Key Pair.

Key Pair: The Private Key and its associated Public Key.

Legal Entity: An association, corporation, partnership, proprietorship, trust, government entity or other entity with legal standing in a country’s legal system.

Multi-Perspective Issuance Corroboration: A process in which the results of domain validation and CAA checking performed by the Primary Network Perspective are confirmed by additional Network Perspectives prior to issuing a certificate.

Network Perspective: Related to Multi-Perspective Issuance Corroboration. A Network Perspective refers to a system (such as a cloud-hosted server) or a group of network elements (like a VPN and its supporting infrastructure) used to send outbound Internet traffic during domain control validation and/or CAA checking. The location of a Network Perspective is defined as the point where outbound Internet traffic before any encapsulation is initially passed to the Internet service provider or network infrastructure responsible for connectivity.

Object Identifier: A unique alphanumeric or numeric identifier registered under the International Organization for Standardization’s applicable standard for a specific object or object class.

OCSP Responder: An online server operated under the authority of the CA and connected to its Repository for processing Certificate status requests.

Online Certificate Status Protocol: An online Certificate-checking protocol that enables relying party application software to determine the status of an identified Certificate.

Online Channel: Refers to emSign's online platforms such as CERTInext, ACME, API, and any other internet-based interfaces or services that enable Subscribers or Relying Parties to access CERTInext services through automated or self-service mechanisms.

Parent Company: A company that Controls a Subsidiary Company.

Private Key: The key of a Key Pair that is kept secret by the holder of the Key Pair, and that is used to create Digital Signatures and/or to decrypt electronic records or files that were encrypted with the corresponding Public Key.

Public Key Infrastructure: A set of hardware, software, people, procedures, rules, policies, and obligations used to facilitate the trustworthy creation, issuance, management, and use of Certificates and keys based on Public Key Cryptography.

Public Key: The key of a Key Pair that may be publicly disclosed by the holder of the corresponding Private Key and that is used by a Relying Party to verify Digital Signatures created with the holder's corresponding Private Key and/or to encrypt messages so that they can be decrypted only with the holder's corresponding Private Key.

Publicly-Trusted Certificate: A Certificate that is trusted by virtue of the fact that its corresponding Root Certificate is distributed as a trust anchor in widely-available application software.

Qualified Auditor: A natural person or Legal Entity that meets the requirements of this CP/CPS.

Random Value: A value specified by a CA to the Applicant that exhibits at least 112 bits of entropy.

Registered Domain Name: A Domain Name that has been registered with a Domain Name Registrar.

Registration Authority (RA): Any Legal Entity that is responsible for identification and authentication of subjects of Certificates, but is not a CA, and hence does not sign or issue Certificates. An RA may assist in the certificate application process or revocation process or both. When “RA” is used as an adjective to describe a role or function, it does not necessarily imply a separate body, but can be part of the CA.

Reliable Data Source: An identification document or source of data used to verify Subject Identity Information that is generally recognized among commercial enterprises and governments as reliable, and which was created by a third party for a purpose other than the Applicant obtaining a Certificate. The accuracy of the Reliable Data Source is evaluated for the source for its reliability, accuracy, and resistance to alteration or falsification. Such evaluation considers the age of the information, update frequency by such source, the data provider and the purpose of data collection, the accessibility of such data to public, the relative difficulty in falsifying or altering the data. The database maintained by CERTInext where it was primarily collected for fulfilling the validation is not qualified as the Reliable Data Source.

Reliable Method of Communication: A method of communication, such as a postal/courier delivery address, telephone number, or email address, that was verified using a source other than the Applicant Representative.

Relying Party Agreement: means an agreement between CERTInext and a Relying Party that must be read and accepted by a Relying Party prior to validating, relying on or using a Certificate and is available for reference in the Repository.

Relying Party: Any natural person or Legal Entity that relies on a Valid Certificate. An Application Software Supplier is not considered a Relying Party when software distributed by such Supplier merely displays information relating to a Certificate.

Repository: An online database containing publicly-disclosed PKI governance documents (such as Certificate Policies and Certification Practice Statements) and Certificate status information, either in the form of a CRL or an OCSP response.

Request Token: A value derived in a method specified by the CA which binds this demonstration of control to the certificate request. The Request Token SHALL incorporate the key used in the certificate request. A Request Token MAY include a timestamp to indicate when it was created. A Request Token MAY include other information to ensure its uniqueness. A Request Token that includes a timestamp SHALL remain valid for no more than 30 days from the time of creation. A Request Token that includes a timestamp SHALL be treated as invalid if its timestamp is in the future. A Request Token that does not include a timestamp is valid for a single use and the CA SHALL NOT re-use it for a subsequent validation. The binding SHALL use a digital signature algorithm or a cryptographic hash algorithm at least as strong as that to be used in signing the certificate request.

Required Website Content: Either a Random Value or a Request Token, together with additional information that uniquely identifies the Subscriber, as specified by the CA.

Reserved IP Address: An IPv4 or IPv6 address that the IANA has marked as reserved:

- <http://www.iana.org/assignments/ipv4-address-space/ipv4-address-space.xml>
- <http://www.iana.org/assignments/ipv6-address-space/ipv6-address-space.xml>

Root CA System: Means a system used to create a Root Certificate or to generate, store, or sign with the Private Key associated with a Root Certificate.

Root CA: The top level Certification Authority whose Root Certificate is distributed by Application Software Suppliers and that issues Subordinate CA Certificates.

Root Certificate: The self-signed Certificate issued by the Root CA to identify itself and to facilitate verification of Certificates issued to its Subordinate CAs.

Sovereign State: A state or country that administers its own government, and is not dependent upon, or subject to, another power.

Subject Identity Information: Information that identifies the Certificate Subject. Subject Identity Information does not include a domain name listed in the subjectAltName extension or the Subject commonName field.

Subject: The Subject is either the Subscriber or a device under the control and operation of the Subscriber.

Subordinate CA: A Certification Authority whose Certificate is signed by the Root CA, or another Subordinate CA.

Subscriber Agreement: An agreement between the CA and the Applicant/Subscriber that specifies the rights and responsibilities of the parties.

Subscriber: A natural person or Legal Entity to whom a Certificate is issued and who is legally bound by a Subscriber Agreement or Terms of Use.

Subsidiary Company: A company that is controlled by a Parent Company.

Technically Constrained Subordinate CA Certificate: A Subordinate CA certificate which uses a combination of Extended Key Usage settings and Name Constraint settings to limit the scope within which the Subordinate CA Certificate may issue Subscriber or additional Subordinate CA Certificates.

Terms of Use: Provisions regarding the safekeeping and acceptable uses of a Certificate issued in accordance with these Requirements when the Applicant/Subscriber is an Affiliate of the CA or is the CA.

Test Certificate: A Certificate with a maximum validity period of 30 days and which: (i) includes a critical extension with the specified Test Certificate CABF OID, or (ii) is issued under a CA where there are no certificate paths/chains to a root certificate subject to these Requirements.

Trustworthy System: Computer hardware, software, and procedures that are: reasonably secure from intrusion and misuse; provide a reasonable level of availability, reliability, and correct operation; are reasonably suited to performing their intended functions; and enforce the applicable security policy.

Unregistered Domain Name: A Domain Name that is not a Registered Domain Name.

Valid Certificate: A Certificate that passes the validation procedure specified in RFC 5280.

Validation Specialists: Someone who performs the information verification duties specified in this CP/CPS . This includes the RA / Trusted Personnel of CA.

Validity Period: The period of time measured from the date when the Certificate is issued until the Expiry Date.

Verified Method of Communication: Method of communication as defined and verified in conformance with Section 11.5 of the EVG

WebTrust for Certification Authorities: Means the current program for CAs located at CPA Canada Webtrust Principles and Criteria.

WHOIS: Information retrieved directly from the Domain Name Registrar or registry operator via the protocol defined in RFC 3912, the Registry Data Access Protocol defined in RFC 7482, or an HTTPS website

Wildcard Certificate: A Certificate containing an asterisk (\*) in the left-most position of any of the Subject Fully-Qualified Domain Names contained in the Certificate.

Wildcard Domain Name: A Domain Name consisting of a single asterisk character followed by a single full stop character (\*.) followed by a FQDN

X.509: Means the ITU-T standard for Certificates and their corresponding authentication framework

### 1.6.2 Acronyms

| # | Acronyms | Meaning |
|---|---|---|
| 1 | ACME | Automated Certificate Management Environment |
| 2 | AICPA | American Institute of Certified Public Accountants |
| 3 | API | Application Programming Interface |
| 4 | CA | Certification Authority |
| 5 | CAA | Certification Authority Authorization |
| 6 | CABF | CA/Browser Forum |
| 7 | ccTLD | Country Code Top-Level Domain |
| 8 | CICA | Canadian Institute of Chartered Accountants |
| 9 | CP | Certificate Policy |
| 10 | CPS | Certification Practice Statement |
| 11 | CRL | Certificate Revocation List |
| 12 | CSR | Certificate Signing Request |
| 13 | DBA | Doing Business As |
| 14 | DBA | Database Administrator |
| 15 | DN | Distinguished Names |
| 16 | DNS | Domain Name System |
| 17 | DSA | Digital Signature Algorithm |
| 18 | DV | Domain Validated |
| 19 | ECDSA | Elliptic Curve Digital Signature Algorithm |
| 20 | EKU | Extended Key Usage |
| 21 | EV | Extended Validation |
| 22 | FIPS | (US Government) Federal Information Processing Standard |
| 23 | FQDN | Fully-Qualified Domain Name |
| 24 | GET | Get Everything Transmitted |
| 25 | HTTP | Hypertext Transfer Protocol |
| 26 | IANA | Internet Assigned Numbers Authority |
| 27 | ICANN | Internet Corporation for Assigned Names and Numbers |
| 28 | IDN | Internationalized domain names |
| 29 | IDS | Intrusion Detection System |
| 30 | IETF | Internet Engineering Task Force |
| 31 | IPS | Intrusion Prevention System |
| 32 | ISO | International Organization for Standardization |
| 33 | MITM | Man-in-the-middle |
| 34 | MPIC | Multi-Perspective Issuance Corroboration |
| 35 | NIST | National Institute of Standards and Technology (USA) |
| 36 | NTP | Network Time Protocol |
| 37 | OCSP | Online Certificate Status Protocol |
| 38 | OID | Object Identifier |
| 39 | OV | Organization Validated |
| 40 | PKI | Public Key Infrastructure |
| 41 | POST | Power-On Self-Test |
| 42 | PQC | Post Quantum Cryptography |
| 43 | PSL | public suffix list |
| 44 | RA | Registration Authority |
| 45 | RSA | Rivest Shamir Adleman |
| 46 | SMIME | Secure MIME (Multipurpose Internet Mail Extensions) |
| 47 | SAN | Subject Alternative Name |
| 48 | SOA | Statement of Applicability |
| 49 | SSL | Secure Sockets Layer |
| 50 | TLS | Transport Layer Security |
| 51 | TSA | Time Stamp Authority |
| 52 | URL | Uniform Resource Locator |
| 53 | UTC | Coordinated Universal Time |
| 54 | VESDA | Very Early Smoke Detection Appliance |

# 2. PUBLICATION AND REPOSITORY RESPONSIBILITIES

This CPS is only one of a set of documents relevant to the InCommon RSA IGTF Server CA 4. The list of documents below is a non-exhaustive list of other relevant documents. The document name, location of, and status, whether public or private, are detailed below.

| Document Status Location | Status | Location |
|---|---|---|
| "InCommon Certification Practices Statement for the InCommon IGTF Server Certification Authority (This document) | Public | InCommon Repository |
| SSL Subscriber Agreement (i.e., “InCommon Certificate Service Subscription Addendum to the InCommon Federation Participation Agreement”) | Public | InCommon Repository |
| InCommon Certificate Service Relying Party Agreement | Public | InCommon Repository |
| InCommon Certificate Service Policy Authority | Public | InCommon Repository |

## 2.1 Repositories

InCommon publishes this CPS, related documents and certificates in its PKI services repository at <https://www.incommon.org/certificates/repository/>. The InCommon Operations group maintains the repository. InCommon makes reasonable efforts to ensure that the information in its repository is accurate, updated, and correct. However, in no event shall InCommon be liable for any amounts beyond the limits set forth in this CPS.

Parties accessing the repository agree to the terms posted in the repository in regard to its use of the documents and information on the repository. InCommon may revoke repository privileges for any party failing to comply with the terms on InCommon's website.

## 2.2 Publication of Certification Information

Certificate information is published in accordance with the provisions of the CPS relevant to such a certificate. Certificate content is published by issuing the certificate. Revoked certificate information is published in CRLs by InCommon’s CA service provider and is available also by OCSP. Users and relying parties should consult the CRLs or OCSP server prior to relying on information featured in a certificate.

## 2.3 Time or Frequency of Publication

Updates to the CPS are published in accordance with Section 9.12. Updates to the Subscriber Agreement, Relying Party Agreements, and other agreements posted in the repository are published as often as necessary. Certificates are published upon issuance.

## 2.4 Access Controls on Repositories

The information published in the InCommon repository (refer to section 2.1) is public information and may be accessed and redistributed freely by anyone visiting the site, provided they agree to the site’s terms and conditions as posted thereon. Read-only access to the information is unrestricted except as stated in section 2.1 above. InCommon has implemented logical and physical security measures to prevent unauthorized additions, modification, or deletions of repository entries.

# 3. IDENTIFICATION AND AUTHENTICATION

## 3.1 Naming

### 3.1.1 Types of Names

InCommon Certificates are issued with conform to X.500 and X.501 compliant non-null Distinguished Name (DN) in the Issuer and Subject Fields. Issuer Distinguished Names will identify Internet2 (InCommon's parent organization) as the primary organization and InCommon RSA IGTF Server CA 4 as the common name. Certificate Subject Distinguished Names will identify the Subscriber as the primary organization. The Subject will be in a name space owned by or under the administrative control of the Subscriber for which the TLS/SSL certificate will be used. Subject Alternate Name(s) must be included. Details of certificate profiles for TLS/SSL certificates may be found in the InCommon PKI repository as stated in Section 2.

InCommon certificates may include a brief statement describing limitations of liability, limitations in the value of transactions to be accomplished, validation period, and intended purpose of the certificate and any disclaimers of warranty that may apply. The lack of such information does not mean it does not apply to that certificate.

To communicate information InCommon may define:

- An InCommon standard resource qualifier to a certificate policy.
- Proprietary or other vendors’ extensions.

### 3.1.2 Need for Names to be Meaningful

InCommon uses non-ambiguous designations and commonly used semantics to identify both the Issuer of the Certificate and the Subject of the Certificate.

### 3.1.3 Anonymity or Pseudonymity of Subscribers

Does not apply to SSL/TLS certificates.

### 3.1.4 Rules for Interpreting Various name Forms

Distinguished Names in Certificates are interpreted using X.500 standards and ASN.1 syntax. For URIs and HTTP References, refer RFC 2253 and 2616 for further information on how X.500 distinguished names in certificates are interpreted.

### 3.1.5 Uniqueness of Names

The Distinguished Name in the Subject field of an InCommon RSA IGTF Server CA 4 issued Certificate is unique for each named Subject. Also, the CA assigns certificate serial numbers that appear in issued certificates. Assigned serial numbers are unique across all certificates issued by the CA.

The Distinguished Name in the Subject field of each Certificate issued by InCommon RSA IGTF Server CA 4 will contain a unique prefix of “/DC=org/DC=incommon/C=*Subscriber Country*/ST=*Subscriber State*/O=*Subscriber Name*” to avoid overlap with certificates issued by other CAs and other Subscribers. InCommon will assign a unique “Subscriber Name” to each subscriber during authentication of organization identity (see Section 3.2.2 and Section 4.2.1). InCommon will ensure through its internal procedures that a unique Subscriber Name once assigned is never re-assigned. An example Distinguished name is “/DC=org/DC=incommon/C=US/ST=Michigan/O=Example University/CN=server.example.edu”.

The Distinguished Name in the Issuer field of each Certificate issued by the InCommon IGTF Server CA will be “/C=US/O=Internet2/CN=InCommon RSA IGTF Server CA 4”.

Certificates must apply to unique resources/servers. Every subject distinguished name must be linked to one and only one end entity throughout the entire lifetime of the InCommon RSA IGTF Server CA 4. Certificates must not be shared among multiple resources/servers, except in the case of certificates issued with a wildcard in the Subject CommonName.

Each certificate issued under this CPS includes a unique serial number generated using a cryptographically secure random process. While the Subject Distinguished Name (DN) may be reused across multiple certificates for the same Subscriber, the domain names listed in the subjectAlternativeName extension are validated for control by the Subscriber. Domain name uniqueness is inherently managed by ICANN as part of the global DNS infrastructure.

### 3.1.6 Recognition, Authentication, and Role of Trademarks

InCommon does not permit the use of a name or symbol that infringes upon the intellectual property rights of another as stated in its subscriber agreements. However, InCommon does not verify nor check the name appearing in a certificate for non-infringement. Subscribers are solely responsible for ensuring the legality of any information presented for use in an InCommon CA issued certificate. When submitting a CSR, InCommon subscribers represent that they are not interfering with or infringing upon the rights of any third parties.

InCommon does not arbitrate, mediate, or otherwise resolve any dispute concerning the ownership of any intellectual property or a domain’s use of any infringing material. InCommon’s CA may reject a CSR or revoke a certificate if it believes that any information in the certificate may be subject to infringement claims or ownership disputes.

## 3.2 Initial Identity Validation

InCommon validates the identity of each new Subscriber and its officially designated officers, while the Certificate Manager validates domain names. For SSL/TLS certificates, InCommon validates only that the Subscriber has ownership of or administrative control for the Internet domain names(s) identified in its Subscriber Addendum or in later requests from Subscriber Registrars. Subsequently, subscriber Registrars are responsible to ensure the validity of any Subject information provided in a CSR. The InCommon CA will reject any CSR that includes a fully qualified domain name for which the Subscriber cannot be verified. All communications between the CA and RAs are conducted through a secure, authenticated web service that records all transactions. Subscribers are required to sign and comply with a certificate service agreement including identity validation processes. This agreement can be found in the “InCommon Certificate Service Subscription **Addendum to the InCommon Federation Participation Agreement**” (found in the document repository mentioned above).

### 3.2.1 Method to Prove Possession of Private Key

For SSL/TLS certificates, the Applicant must demonstrate control of the private key corresponding to the public key in the certificate request. This is typically done by submitting a PKCS#10 Certificate Signing Request (CSR) that is signed using the private key. Other industry-approved methods may be used, subject to **CERTInext** validation and approval.

InCommon does not generate key pairs for end-entity IGTF certificates that include the idkpserverAuth or anyExtendedKeyUsage EKU values. The Subscriber is responsible for secure key generation and protection. This ensures the Subscriber maintains sole control over the private key, as required by the CA/Browser Forum Baseline Requirements.

### 3.2.2 Authentication of Organization Identity

InCommon may accept at its discretion any official organizational documentation supporting an application to become a Subscriber. InCommon may also use the services of a third party to validate and confirm information. Sources include:

- official organizational documentation, such as business licenses, articles of incorporation, sales license or other relevant documents.
- Third-party services or records such as bank statements, records of accreditation status, or other relevant documents.

Verification can occur though an automated process or a manual review.

InCommon also verifies the identity of Subscriber's designated officers – an official executive and Subscriber Registrars designated by the executive – using out-of-band means to verify contact information and to make contact with each officer for credentialing and Subscriber Registrar's subsequent authentication to the certificate management UI.

### 3.2.3 Authentication of Individual Identity

Section 3.2.2 describes the identity vetting of Subscriber Registrars.

### 3.2.4 Non-Verified Subscriber Information

InCommon verifies only the information listed as validated in section 4.2. Any other information provided by Subscriber Registrars is not verified by InCommon.

### 3.2.5 Validation of Authority

The authority of a Subscriber to be issued a certificate is confirmed by a practical demonstration of the Subscriber Registrar's authority to act on behalf of the domain owner by means in accordance with acceptable practices as determined by the CA Browser Forum and specified at <https://cabforum.org/baseline-requirements-documents/>. Subscribers must notify InCommon if any Subscriber Registrar misrepresents his or her affiliation with or authority regarding Subscriber and Subscriber's domains.

### 3.2.6 Criteria for Interoperation

No stipulation.

## 3.3 Identification and Authentication for Re-key Requests

### 3.3.1 Identification and Authentication for Routine Re-key

Any Registrar or Requester can request a re-key by submitting an appropriate CSR.

Re-keying is a process where new private key / key pair is generated by the subscriber and a request is made to provide certificate, with information similar to a previous certificate.

Subscribers may request Re-key any number of times during the validity period of the certificate. Rekeyed Certificate has a ‘Valid Till’ date which equals the ‘Valid Till’ date of the certificate that is being re-issued.

Where the initial Subscriber identification & authentication process as per this CPS will be been performed as below:

| Validation Type | Certificate Issued On or After | Certificate Issued Before | Maximum Data Reuse Period | Re-Key Authentication Condition |
|---|---|---|---|---|
| Domain Name and IP Address Validation | April 20, 2026 | March 15, 2027 | 200 days | Must be validated within this period prior to certificate issuance. |
| Domain Name and IP Address Validation | March 15, 2027 | March 15, 2029 | 100 days | Must be validated within this period prior to certificate issuance. |
| Domain Name and IP Address Validation | March 15, 2029 | – | 10 days | Must be validated within this period prior to certificate issuance. |

### 3.3.2 Identification and Authentication for Re-key After Revocation

Not applicable to InCommon SSL/TLS certificates.

## 3.4 Identification and Authentication for Revocation Request

Prior to revoking a certificate, the InCommon CA verifies that the revocation was requested by the certificate Requester or an authorized Registrar associated with the Subscriber. InCommon may, if necessary, also request that the revocation request be made by the Subscriber's Executive contact. Upon receipt of an unconfirmed revocation request, the InCommon CA may request out-of-band confirmation from a known Subscriber Registrar or Executive.

# 4. CERTIFICATE LIFE-CYCLE OPERATIONAL REQUIREMENTS

## 4.1 Certificate Application

InCommon certificates are issued to authorized organizations and individuals who submit a certificate signing request and successfully complete the required validation procedures described herein. Prior to the issuance of a certificate, the InCommon RSA IGTF Server CA 4 will validate a request in accordance with this CPS. Validation of the request will involve the information provided by the Subscriber upon completion of their subscription contract and verified by InCommon prior to accepting the certificate request.

IGTF certificate requests may be submitted through authorized online channel including the CERTInext portal, enterprise integrations using our APIs, or automated systems such as ACME. Each application must include sufficient information to allow our platforms to confirm the identity of the requesting entity, validate control over the domain names to be certified, and verify that the individual submitting the request is authorized to act on behalf of the applicant organization, where applicable. Additionally, the application must enable validation that the public key submitted corresponds to a private key legitimately held by the applicant.

All applications are subject to verification procedures appropriate to the certificate type requested. Issuance proceeds only after successful completion of identity and domain validation steps by authorized Registration Authorities or us. Applicants must review the issued certificate for accuracy and promptly report any errors or inconsistencies.

### 4.1.1 Who Can Submit a Certificate Application

SSL/TLS certificate requests may be submitted by an authorized Registrar or an authorized Subscriber Requester.

### 4.1.2 Enrollment Process and Responsibilities

InCommon operates the Registration Authority, leveraging its current processes for verifying organizations and identity proofing officials authorized to act on behalf of an institution for certificate issuance. It is expected that at each institution a small number of Subscriber Registrars (typically two or three) will be authorized to manage the overall institutional certificate program.

Applicants seeking SSL/TLS Certificates shall complete an enrollment process designed to ensure the integrity, authenticity, and accountability of all issued certificates. While Issuing CAs may define specific implementation workflows, the enrollment process shall include the following minimum steps:

- The Applicant’s identity whether representing an organization or an individual shall be verified in accordance with the procedures outlined in Appendix A.
- The Applicant shall generate a secure cryptographic key pair and demonstrate possession of the private key, typically through submission of a digitally signed Certificate Signing Request (CSR).
- The verified identity shall be bound to the public key in accordance with this CP/CPS.
- The Applicant must enter into a binding Subscriber Agreement. The Issuing CA shall operate under a formal agreement with us.
- All communications supporting the application and issuance process whether electronic or out-of-band shall maintain the confidentiality and integrity of transmitted data using cryptographic methods appropriate to the key size and security profile.

Applicants are responsible for submitting accurate and complete information, responding to validation requests in a timely manner, and protecting the confidentiality of their private keys. Certificates shall only be issued once all validation requirements have been fulfilled and applicable agreements accepted.

## 4.2 Certificate Application Processing

### 4.2.1 Performing Identification and Authentication Functions

The InCommon Registration Authority validates the following required information in any SSL/TLS certificate. Other optional certificate subject information is considered under the purview of Subscriber Registrars and is detailed in the certificate profile found in the InCommon Repository.

- O (Organization): Legal Name of the Organization or a commonly understood and unique variant of Legal Name
- Common Name (CN): Fully Qualified Domain Name or publicly routable organizational IP address

InCommon Grid Host certificates are subject to CAA, DNSSEC, and MPIC validation requirements as outlined in the corresponding CertiNext CP/CPS.

### 4.2.2 Approval or Rejection of Certificate Applications

Subscriber Registrars are responsible for the approval of individual CSRs, the sub-domains represented in CSRs, and generally for the management of Subscriber certificates beyond the approvals of the Master Registrar stated in section 4.2.1.

The Issuing CA shall reject any application that fails validation or where the submitted information cannot be verified. Additionally, we reserve the right to reject a certificate application at its discretion, including but not limited to cases where:

- The Applicant or request is associated with high-risk domains, prohibited geographies, or restricted entities;
- Issuance may compromise the trustworthiness, security, or reputation of our PKI;
- The domain is a newly delegated gTLD that is not yet approved for public issuance;
- There is suspected misuse, fraud, or conflict with applicable laws or industry standards.

We are not obligated to provide specific reasons for the rejection of an application. Applicants whose requests have been denied may submit a new application following corrective action.

Subscribers are responsible for ensuring the ongoing accuracy of the information provided in their certificate applications. Failure to notify us of changes that affect certificate validity may result in certificate revocation in accordance with Section 4.9 and the terms of the Subscriber Agreement.

### 4.2.3 Time to Process Certificate Applications

Registration Authorities and Issuing CAs are under no obligation to process Digital Certificate Applications other than within a commercially reasonable time.

### 4.2.4 Certificate Authority Authorization (CAA)

For any certificate application involving domain names intended for server authentication, **CERTInext** shall perform Certification Authority Authorization (CAA) checks in accordance with RFC 8659 and Section 3.2.2.8 of the CA/Browser Forum TLS Baseline Requirements.

As part of the issuance process, **CERTInext** checks for CAA records for each dNSName in the subjectAltName extension of the certificate to be issued and processes the records found in accordance with RFC 8659. When processing CAA records, **CERTInext** processes the issue or issuewild. A certificate is not issued if an unrecognized property is encountered with the critical flag set.

If a CAA Resource Record is present for the domain, **CERTInext** shall verify whether the record authorizes certificate issuance by **CERTInext**. If the domain's CAA record does not include emsign.com for the relevant issue or issuewild property tags, as applicable, the certificate application shall be rejected.

If the Relevant RRset for a domain contains no restrictive tags then CAA does not restrict issuance. If no CAA record exists for the domain, issuance may proceed.

If **CERTInext** issues a certificate after performing a CAA check, issuance shall occur within the Time-To-Live (TTL) of the CAA record, or 8 hours, whichever is greater.

**CERTInext** does not treat a CAA record lookup failure as permission to issue, except under the limited circumstances permitted by the Baseline Requirements. **CERTInext** may treat a record lookup failure as permission to issue only if all of the following conditions are met: (i) the failure is outside the CA's infrastructure; (ii) the lookup has been retried at least once; and (iii) the domain's zone does not have a DNSSEC validation chain to the ICANN root. Where these conditions are not met, **CERTInext** fails closed and does not issue the certificate.

In accordance with Section 3.2.2.8 of the Baseline Requirements, **CERTInext** may rely on the following exceptions where applicable:

1. CAA checking is optional for certificates for which a Certificate Transparency precertificate was created and logged in at least two public logs, and for which CAA was checked at the time of precertificate issuance.
2. CAA checking is optional for certificates issued by a Technically Constrained Subordinate CA Certificate as set out in the Baseline Requirements, where the lack of CAA checking is an explicit contractual provision in the contract with the Applicant

**CERTInext** documents all actions taken based on CAA records. Potential issuance that was prevented by a CAA record is documented in sufficient detail to provide feedback to the CA/Browser Forum on the circumstances, where relevant.

**CERTInext** recognizes the following domain name values in CAA records as granting authorization for issuance by **CERTInext**:

- emsign.com

If no CAA record exists for the domain, issuance may proceed. The results of all CAA checks are logged for audit purposes.

Where applicable, **CERTInext** applies Multi-Perspective Issuance Corroboration (MPIC) to CAA checking, corroborating results using at least two independent Network Perspectives.

**Issuer Domain Names for DNS TXT Record with Persistent Value Validation**

For the DNS TXT Record with Persistent Value domain control validation method described in Section 3.2.2.4.22 of the Baseline Requirements and Sections 10.1, 10.2, and 10.3 of this CP/CPS, **CERTInext** recognizes the following as valid issuer-domain-name values in the Persistent DCV TXT Record’s RDATA:

- emsign.com
- certinext.io

## 4.3 Certificate Issuance

InCommon may refuse to issue a certificate to any party as InCommon sees fit. InCommon is not obligated to disclose the reasons for such a refusal.

### 4.3.1 CA Actions During Certificate Issuance

Upon approval of a certificate application, the CA signs an X.509 certificate containing the subscriber’s public key and subject distinguished name.

### 4.3.2 Notification to Subscriber by the CA of Issuance of Certificate

Each subscribing organization manages the notifications for its members. The InCommon Certificate Manager supports customizable email notification capabilities.

## 4.4 Certificate Acceptance

### 4.4.1 Conduct Constituting Certificate Acceptance

No stipulation.

### 4.4.2 Publication of the Certificate by the CA

No stipulation.

### 4.4.3 Notification of Certificate Issuance by the CA to Other Entities

No stipulation.

## 4.5 Key Pair and Certificate Usage

### 4.5.1 Subscriber Private Key and Certificate Usage

Use of the Private Key in conjunction with a certificate issued by this CA is prohibited until the Subscriber has agreed to a Subscriber agreement. Certificates may only be used for lawful and appropriate purposes as set forth in this CPS. Subscribers are responsible for protecting their private keys from unauthorized use and agree to immediately cease using the private key in conjunction with a Certificate following the expiration or revocation of the Certificate.

### 4.5.2 Relying Party Public Key and Certificate Usage

The final decision concerning whether or not to rely on a verified digital signature is exclusively that of the relying party.

## 4.6 Certificate Renewal

Renewal request requirements and procedures are treated as new certificate requests.

### 4.6.1 Circumstance for Certificate Renewal

An Issuing CA may process a renewal request if all of the following conditions are met:

- The public key remains valid and suitable for continued use.
- The associated private key has not been compromised.
- The certificate subject information and Subscriber attributes remain unchanged.
- No additional validation is required under the applicable certificate type.

Renewal may be permitted even after certificate expiration, provided the above conditions are met. However, the original certificate shall not be further renewed, rekeyed, or modified once expired.

### 4.6.2 Who May Request Renewal

Renewal may be requested by the original Subscriber or by a Registration Authority acting on their behalf. All renewal requests must be authenticated using approved subscriber authentication methods, such as passphrases, shared secrets, or account-based authentication. Submission of a CSR is optional, but if used, it must contain the same public key.

### 4.6.3 Processing Certificate Renewal Requests

We reserve the right to request re-authentication or updated information prior to processing a renewal request. In such cases, the same validation procedures applicable to new issuance may be applied. The original certificate may remain valid or may be revoked at our discretion.

### 4.6.4 Notification of New Certificate Issuance to Subscriber

Notification of the renewed certificate shall follow the same process as for new certificate issuance, as defined in Section 4.3.2 of this CPS. Subscribers may also receive email reminders about impending certificate expiration as a courtesy, typically within 60 days prior to expiry.

### 4.6.5 Conduct Constituting Acceptance of a Renewal Certificate

Subscriber conduct constituting acceptance of a renewed certificate shall be the same as defined under Section 4.4.1. This includes usage, installation, or download of the certificate.

### 4.6.6 Publication of the Renewal Certificate by the CA

Renewed certificates shall be published using the same mechanisms as those for new certificate issuance, including delivery to the Subscriber and publication in the certificate repository and CT logs, if applicable.

### 4.6.7 Notification of Certificate Issuance by the CA to other Entities

The CA may notify relevant Registration Authorities involved in the renewal process. No additional notifications are sent to external entities unless specifically required under applicable practices or agreements.

## 4.7 Certificate Re-key

Certificate rekey is the issuance of a new certificate that certifies a new public key for the same Subject. Rekey request requirements and procedures are treated as new certificate requests.

### 4.7.1 Circumstance for Certificate Re-Key

n/a.

### 4.7.2 Who May Request Certification of a New Public Key

n/a.

### 4.7.3 Processing Certificate Re-keying Requests

n/a.

### 4.7.4 Notification of New Certificate Issuance to Subscriber

n/a.

### 4.7.5 Conduct Constituting Acceptance of a Re-keyed Certificate

n/a.

### 4.7.6 Publication of the Re-keyed Certificate by the CA

n/a.

### 4.7.7 Notification of Certificate Issuance by the CA to Other Entities

n/a.

## 4.8 Certificate Modification

Certificate information may change during the life of the certificate. In this case, the InCommon RSA IGTF Server CA 4 will issue a new certificate based on the new information rather than modifying an existing certificate. Modification request requirements and procedures are treated as new certificate requests.

### 4.8.1 Circumstance for Certificate Modification

n/a.

### 4.8.2 Who May Request Certificate Modification

n/a.

### 4.8.3 Processing Certificate Modification Requests

n/a.

### 4.8.4 Notification of New Certificate Issuance to Subscriber

n/a.

### 4.8.5 Conduct Constituting Acceptance of Modified Certificate

n/a.

### 4.8.6 Publication of the Modified Certificate by the CA

n/a.

### 4.8.7 Notification of Certificate Issuance by the CA to Other Entities

n/a.

## 4.9 Certificate Revocation and Suspension

Upon revocation of a certificate, the operational period of that certificate is immediately considered terminated. The serial number of the revoked certificate will be placed within the CRL and available to the OCSP server and will remain available in those locations until the end of the certificate’s validity period.

InCommon does not make use of certificate suspension.

### 4.9.1 Circumstances for Revocation

Issuing CAs shall revoke Digital Certificates when the private key associated with the Digital Certificate is compromised or suspected to be compromised or when any of the information on a Digital Certificate change or becomes obsolete.

Issuing CA SHALL revoke a Digital Certificate of Subscriber within 24 hours when any of the following conditions are met:

- The Subscriber requests revocation of the Certificate.
- The original certificate request was not authorized by the Subscriber and retroactive authorization is not granted.
- The Private Key associated with or used to sign the Certificate has been compromised or misused.
- The Issuing CA becomes aware of a demonstrated or proven method (e.g., Debian weak keys) that exposes the Subscriber’s Private Key to compromise or makes it computable based on the Public Key.
- The Certificate was used to sign, publish, or distribute malware or other harmful content.
- The Issuing CA obtains evidence that the validation of domain authorization or control for any Fully-Qualified Domain Name or IP address in the Certificate should not be relied upon.
- The Certificate was used to authenticate a misleading or fraudulent subordinate domain name.

Issuing CA SHOULD revoke a Digital Certificate of Subscriber within 24 hours but MUST revoke within 5 days when any of the following conditions are met:

- Any information appearing in the Certificate was or became inaccurate or misleading.
- The Certificate was not issued in accordance with this CP/CPS or applicable industry standards.
- The Applicant has lost its rights to a trademark or the domain name listed in the Certificate.
- The Subscriber breached a material obligation under this CP/CPS or the Subscriber Agreement.
- InCommon notifies CertiNext that the InCommon Subscriber Agreement has been terminated or has lapsed.
- A government or regulatory order is received by the Issuing CA to revoke the Certificate.
- The Subscriber was added to a denied party or prohibited persons list (e.g., export control or sanctions list).
- The binding between the subject and the subject’s Public Key in the Certificate is no longer valid.
- For Certificates that have organizational affiliation, the Issuer CA or the RA shall require the Affiliated Organization to inform it if the subscriber affiliation changes. If the Affiliated Organization no longer authorizes the affiliation of a Subscriber, then the Issuer CA shall revoke any Certificates issued to that Subscriber containing the organizational affiliation. If an Affiliated Organization terminates its relationship with the Issuer CA or RA such that it no longer provides affiliation information, the Issuer CA shall revoke all Certificates affiliated with that Affiliated Organization.
- The Issuing CA ceases operations or its right to manage Certificates is revoked, and it has not arranged another CA for revocation support.
- The Issuing CA is compromised.
- The Certificate Holder is subject to bankruptcy or liquidation.
- The Certificate Holder is deceased.
- If not revoking the Certificate would compromise the trust status of the Issuing CA or affiliated systems.

The Issuing CA SHALL revoke a Subordinate CA Certificate within seven (7) days if one or more of the following occurs:

- The Subordinate CA requests revocation in writing;
- The Subordinate CA notifies the Issuing CA that the original certificate request was not authorized and does not retroactively grant authorization;
- If the Certificate no longer complies with the requirements specified in Sections 6.1.5 and 6.1.6 of the TLS Baseline Requirements.
- The Issuing CA obtains evidence that the Subordinate CA’s Private Key corresponding to the Public Key in the Certificate suffered a Key Compromise or no longer complies with the requirements of this CP/CPS.
- The Issuing CA obtains evidence that the Certificate was misused;
- The Issuing CA is made aware that the Certificate was not issued in accordance with or that Subordinate CA has not complied with this CP or the applicable Certificate Policy or Certification Practice Statement;
- The Issuing CA determines that any of the information appearing in the Certificate is inaccurate or misleading;
- The Issuing CA or Subordinate CA ceases operations for any reason and has not made arrangements for another CA to provide revocation support for the Certificate;
- The Issuing CA’s or Subordinate CA's right to issue Certificates under these Requirements expires or is revoked or terminated, unless the Issuing CA has made arrangements to continue maintaining the CRL/OCSP Repository;
- Revocation is required by the Issuing CA’s Certificate Policy and/or Certification Practice Statement;
- The technical content or format of the Certificate presents an unacceptable risk to Application Software Suppliers or Relying Parties (e.g. the CA/Browser Forum might determine that a deprecated cryptographic/signature algorithm or key size presents an unacceptable.)

**Revocation Reason Options:**

- keyCompromise (1): The certificate subscriber must choose the "keyCompromise" revocation reason when they have reason to believe that the private key of their certificate has been compromised, e.g. an unauthorized person has had access to the private key of their certificate.
- affiliationChanged (3): The certificate subscriber should choose the "affiliationChanged" revocation reason when their organization's name or other organizational information in the certificate has changed.
- Superseded (4): The certificate subscriber should choose the "superseded" revocation reason when they request a new certificate to replace their existing certificate.
- cessationOfOperation (5): The certificate subscriber should choose the "cessationOfOperation" revocation reason when they no longer own all of the domain names in the certificate or when they will no longer be using the certificate because they are discontinuing their website.
- privilegeWithdrawn (9): The certificate subscriber should choose the “privilegeWithdrawn“ revocation reason when the original Certificate request was not authorized and does not retroactively grant authorization.

### 4.9.2 Who can Request Revocation

The Subscriber, the Requester, or other appropriately authorized parties can request revocation of a certificate.

### 4.9.3 Procedure for Revocation Request

Issuing CAs and RAs will revoke a Digital Certificate upon receipt of a valid request and may provide automated mechanisms for requesting and authenticating revocation requests. A revocation request may be sent by the Certificate Holder or Affiliated Organization through any one or many of the following modes, as may be provided by Issuing CA:

- Submit the revocation request via the CERTInext platform
- Submit the revocation request via the Issuing CA Support Line
- Issuing CA website
- Contact administrators of Issuing CA or Registration Authority directly

Certificate Holders or Affiliated Organization may use a passphrase or any kind of shared secret or any other form of subscriber authentication mechanism, that will be used to activate the revocation process.

If revocation is requested by someone other than an authorized representative of the Subscriber or Affiliated Organization, the Issuer CA or RA shall investigate the alleged basis for the revocation request and take appropriate action.

The InCommon RSA IGTF Server CA 4 can revoke certificates without authentication upon proof of key compromise or violation of the CP/CPS rules and user obligations by the certificate holder.

### 4.9.4 Revocation Request Grace Period

The InCommon RSA IGTF Server CA 4 can revoke certificates without authentication upon proof of key compromise or violation of the CP/CPS rules and user obligations by the certificate holder.

The revocation request grace period is the time available to the subscriber within which the subscriber must make a revocation request after reasons for revocation have been identified. Subscribers shall request revocation as soon as possible if the Private Key corresponding to the Certificate is lost or compromised or if the certificate data is no longer valid. Issuing CAs will revoke Digital Certificates as soon as reasonably practical following verification of a revocation request.

### 4.9.5 Time Within Which CA Must Process the Revocation Request

The Issuer CA shall revoke Digital Certificates within such time, as reasonably practical, after validating the revocation request within timelines as mentioned in section 4.9 of this CPS.

### 4.9.6 Revocation Checking Requirement for Relying Parties

Relying Parties must always check the status of the Certificate on which they are relying. Relying Parties may check the OCSP and/or CRL to confirm that the certificate has not been revoked.

### 4.9.7 CRL Issuance Frequency (if applicable)

An updated CRL is published every 24 hours and remains valid for 7 days. Under special circumstances the CRL may be published more frequently. After any revocation a new CRL will be issued immediately.

### 4.9.8 Maximum Latency for CRLs (if applicable)

No stipulation.

### 4.9.9 On-line Revocation and Status Checking Availability

The InCommon RSA IGTF Server CA 4 manages and makes publicly available information about revoked certificates using Certificate Revocation Lists (CRLs). All CRLs issued by the InCommon CA are X.509v2 CRLs as profiled in RFC5280. Users and relying parties are strongly urged to check the status of certificates at all times prior to relying on information featured in a certificate. The CRL and OCSP locations are specified in Section 7.

### 4.9.10 On-line Revocation Checking Requirements

Relying Parties shall verify the revocation status of a Certificate through either the Certificate Revocation List (CRL) or the Online Certificate Status Protocol (OCSP) before relying upon the Certificate. Failure to perform such verification may limit the Relying Party's ability to demonstrate reasonable reliance on the Certificate.

The OCSP service provided by eMudhra enables Relying Parties to determine the current revocation status of Subscriber Certificates, Subordinate CA Certificates, and corresponding Precertificates. The OCSP service is implemented in accordance with RFC 6960 (Online Certificate Status Protocol), RFC 5019 (Lightweight OCSP Profile), and the applicable CA/Browser Forum TLS Baseline Requirements.

The OCSP responder URL is included in the Certificate, where applicable. The OCSP responder supports both HTTP GET and HTTP POST methods. The OCSP responder shall not return a "good" status for a certificate serial number that is unassigned, as defined in the applicable CA/Browser Forum TLS Baseline Requirements.

Where a Precertificate has been generated but the associated Certificate issuance transaction is not completed due to validation failure, operational cancellation, or system error, eMudhra shall ensure that the corresponding OCSP status information is provisioned and maintained in accordance with the applicable CA/Browser Forum TLS Baseline Requirements.

An authoritative OCSP response for a Subscriber Certificate or its corresponding Precertificate shall be made available within fifteen (15) minutes after the Certificate or Precertificate is first published or otherwise made available.

### 4.9.11 Other Forms of Revocation Advertisements available

n/a.

### 4.9.12 Special Requirements Re-key Compromise

No stipulation.

### 4.9.13 Circumstances for Suspension

The InCommon RSA IGTF Server CA 4 does not utilize certificate suspension.

### 4.9.14 Who can Request Suspension

n/a.

### 4.9.15 Procedure for Suspension Request

n/a.

### 4.9.16 Limits on Suspension Period

n/a.

## 4.10 Certificate Status Services

### 4.10.1 Operational Characteristics

Each CRL and the OCSP server contains information for all of the InCommon RSA IGTF Server CA 4's revoked certificates until they expire.

All expired CRLs are archived.

Individual entries into the OCSP can be requested using the InCommon RSA IGTF Server CA 4 OCSP server. Revoked certificates are identified in the OCSP server immediately after their revocation.

### 4.10.2 Service Availability

The OCSP server provides access to certificate status information 24x7. CRLs are open to public inspection 24x7. This is non-inclusive of scheduled maintenance and SLA downtime allowances of 99.9% availability.

### 4.10.3 Optional Features

n/a.

## 4.11 End of Subscription

Withdrawal and termination are described in the Subscriber Addendum.

## 4.12 Key Escrow and Recovery

The InCommon RSA IGTF Server CA 4 does not escrow Subscriber private keys.

# 5. FACILITY, MANAGEMENT, AND OPERATIONAL CONTROLS

## 5.1 Physical Controls

**All Issuing CAs shall implement appropriate physical controls for the following:**

1. Physical access control to the hardware used in connection with CA operations.
2. Physical access control over the relevant software.
3. Fire safety protection
4. Protection against failure of supporting utilities like power, telecommunications, etc.
5. Protection against theft.
6. Disaster recovery procedures.

### 5.1.1 Site Location and Construction

All Issuing CAs shall perform their CA operations from a secure datacenter with the following features:

1. The datacenter shall be equipped with physical and logical controls that makes the CA operations inaccessible to unauthorized persons.
2. The datacenter shall be a facility made of concrete and steel construction.
3. The datacenter shall have security protection mechanisms such as guards, door locks.
4. The datacenter shall be with raised floor construction and an array of resilient security and environmental systems.

For SSL/TLS Issuing CAs operated in colocation environments, physical access to the racks, HSMs, and related CA infrastructure is fully controlled and managed exclusively by trusted personnel. These systems are physically isolated and are not accessible to the datacenter provider or other tenants.

### 5.1.2 Physical Access

All Issuing CAs systems are located in a secure datacenter. Entry into this secure facility is allowed only to security-cleared and authorized personnel, whose movements within the facility are logged and audited. Physical access to this facility is also video recorded on a 24/7 basis. Further physical access to this facility is monitored 24/7 by onsite security personnel.

### 5.1.3 Power and Air Conditioning

No stipulation

### 5.1.4 Water exposures

No stipulation

### 5.1.5 Fire prevention and protection

No stipulation

### 5.1.6 Media storage

No stipulation

### 5.1.7 Waste disposal

No stipulation

### 5.1.8 Off-site backup

No stipulation

## 5.2 Procedural Controls

### 5.2.1 Trusted Roles

Trusted roles for the InCommon RSA IGTF Server CA 4 are defined as the RA personnel who verify the Subscriber organization status and the identity proofing of Subscriber Registrars and the assignment of Subscriber Registrar credentials to the management interface.

Trusted roles for the physical operation of the InCommon RSA IGTF Server CA 4 and certificate request and revocation servers are managed under subcontract to meet or exceed WebTrust for Certification Authorities Criteria as detailed at <https://www.cpacanada.ca/en/business-and-accounting-resources/audit-and-assurance/overview-of-webtrust-services/principles-and-criteria>.

### 5.2.2 Number of Persons Required Per Task

No stipulation.

### 5.2.3 Identification and Authentication for Each Role

No stipulation.

### 5.2.4 Roles Requiring Separation of Duties

No stipulation.

## 5.3 Personnel Controls

### 5.3.1 Qualifications, Experience, and Clearance Requirements

InCommon follows personnel and management practices that provide reasonable assurance of the trustworthiness and competence of their employees and of the satisfactory performance of their duties. All InCommon trusted personnel must have the necessary qualifications, experience, or training to fulfill their job descriptions. InCommon requires CA operators under subcontract to follow comparable personnel and management practices. The list of InCommon CA and RA personnel is maintained and verified at least once per year.

### 5.3.2 Background Check Procedures

Background checks are performed on all trusted InCommon personnel before access is granted to InCommon's systems. These checks include, but are not limited to, criminal history and employment history (for references). InCommon requires CA operators under subcontract to perform comparable background checks on subcontract personnel.

### 5.3.3 Training Requirements

Personnel training occurs via a mentoring process involving senior members of the team to which the employee is attached. The training program is periodically reviewed and enhanced as necessary.

Training programs are tailored toward each individual’s job responsibilities and, as appropriate, may include training on PKI concepts, job responsibilities, operational policies and procedures, incident handling and reporting, and disaster recovery procedures.

### 5.3.4 Retraining Frequency and Requirements

Personnel are required to attend refresher training to ensure that they can competently and satisfactorily perform their job responsibilities.

### 5.3.5 Job Rotation Frequency and Sequence

No Stipulation

### 5.3.6 Sanctions for Unauthorized Actions

Personnel violating a policy or procedure are subject to disciplinary action. The action taken depends on the circumstances surrounding the action, the severity of the violation, and the personnel’s past performance. In some cases, disciplinary action may include the personnel’s termination of employment.

### 5.3.7 Independent Contractor Requirements

If an independent contractor or consultant is used, InCommon will first ensure that each such contractor or consultant is first obligated to abide by the same functional and security criteria that are set forth herein. Contractors and consultants are subject to the same sanctions as other personnel as set forth in Section 5.3.6.

### 5.3.8 Documentation Supplied to Personnel

No stipulation.

## 5.4 Audit Logging Procedures

### 5.4.1 Types of Events Recorded

The InCommon RSA IGTF Server CA 4 logs and archives the following items:

- Certificate requests
- Certificate issuance
- Certificate revocations
- Issued CRLs
- Attempted and successful accesses to CA systems and reboots of those systems

### 5.4.2 Frequency of Processing Log

Audit logs shall be verified at least monthly to see for any evidence of malicious activity.

### 5.4.3 Retention Period for Audit Log

The retention period for audit logs, as mentioned in Section 5.4.1, and applicable to all Issuing CAs of, shall be as follows:

1. Logs of CA key management activity minimum 2 years
2. CA system logs of certificate management activity minimum 2 years
3. Operating system logs minimum 2 years
4. Physical access system logs minimum 2 years
5. Manual logs of physical access minimum 2 years
6. Video recording of CA facility accesses 90 days

### 5.4.4 Protection of Audit Log

Access to CA audit logs is restricted to CA operators.

### 5.4.5 Audit Log Backup Procedures

All Issuing CAs shall do onsite back up of the system generated audit logs on a daily basis.

At least on a monthly basis all audit logs and audit summaries shall be backed-up in a secure off site location. These shall be under the control of an authorized trusted role. Audit log backup should be protected to the same degree as originals

### 5.4.6 Audit Collection System (internal vs. external)

The security audit process of each Issuing CA must be initiated at system start up and may finish only at system shutdown. The audit collection system should ensure the integrity and availability of the data collected. If necessary, the audit collection system should protect the data confidentiality. In the case of a problem occurring during the process of the audit collection the Issuing CAs must determine whether to suspend Issuing CA operations until the problem is remedied.

Automated audit data is generated and recorded at the application, network, and operating system level. Manually generated audit data is recorded by the trusted-personnel.

### 5.4.7 Notification to Event-Causing Subject

No Stipulation

### 5.4.8 Vulnerability Assessments

All Issuing CAs shall perform regular vulnerability assessments. Such vulnerability assessments should focus on internal and external threats that could result in unauthorized access, tampering, modification, alteration or destruction of the Certificate issuance process.

The Vulnerability Assessments shall also include application scanning, as well as Penetration Testing. Any negative results out of such reports shall be put under corrective actions for such negative result. No common security vulnerabilities shall exist on public facing websites, hosted in the network.

The results of such vulnerability assessment tests shall be used to enhance the security of the environment.

## 5.5 Records archival

### 5.5.1 Types of records archived

The InCommon RSA IGTF Server CA 4 archives all audit data (see Section 5.4.1).

### 5.5.2 Retention period for archive

The InCommon RSA IGTF Server CA 4 maintains archives as per the defined in this CPS.

### 5.5.3 Protection of Archive

No stipulation.

### 5.5.4 Archive Backup Procedures

No stipulation.

### 5.5.5 Requirements for Time-Stamping of Records

No stipulation.

### 5.5.6 Archive Collection System

No stipulation.

### 5.5.7 Procedures to obtain and verify archive information

No stipulation.

## 5.6 Key changeover

Towards the end of each private key’s lifetime, a new CA signing key pair is commissioned and all subsequently issued certificates are signed with the new private signing key. Both the old and new keys will be concurrently active until all end-entity certificates issued under the old key expire. The older but still valid certificate will be available to verify old signatures and to sign CRLs until all the certificates signed using the associated private key have also expired.

The corresponding new CA public key certificate is provided to subscribers and relying parties through the delivery methods detailed in section 6.1 of this CPS.

## 5.7 Compromise and disaster recovery

### 5.7.1 Incident and compromise handling procedures

The CA Operations Disaster & Recovery Plan is in place with all CAs, in the form of a Business Continuity Plan. This plan fulfils the purpose towards restoring the core business operations when operations and/or systems have been adversely and significantly impacted. This restoration shall be made as quickly as practicable. Such plan shall provide immediate resumption of revocation services in the event of an unexpected emergency.

The disaster recovery and business resumption plan is proprietary, security-sensitive, and confidential. Accordingly, it is not intended to be made publicly available.

All Issuing CAs under our trust hierarchy have in place an appropriate Key compromise plan detailing the activities taken in the event of a compromise of an Issuing CA Private Key. Such plans include procedures for:

- Revoking all Digital Certificates signed with that Issuing CA’s Private Key;
- Notifying Issuing CA and all of the Holders of Digital Certificates issued by that Issuing CA.

#### 5.7.1.1 Mass Revocation Plan

We maintain a documented Mass Revocation Plan to manage large-scale certificate revocation events, such as widespread mis issuance or compromise. This plan is reviewed, tested, and updated at least annually and is integrated into our overall business continuity and incident response frameworks. It outlines clear roles and responsibilities for executing revocation actions, including notification to affected Subscribers, revocation timelines, and post-revocation validation.

The plan ensures rapid response while minimizing disruption to relying parties. Revocation actions are initiated in accordance with our incident handling procedures and under the supervision of the Policy Authority. Communication protocols include timely updates through appropriate channels and coordination with root programs and ecosystem stakeholders as required.

### 5.7.2 Computing resources, software, and/or data are corrupted

Any compromise detected on our computing resources, software, or data operations, it shall be investigated to the extent of the compromise and the risk presented to affected parties. Depending on the extent of the compromise, if it is determined that a continued operation could pose a significant risk to Relying Parties or Subscribers, such operation shall be suspended until it is ensured that the risk is mitigated.

### 5.7.3 Entity Private Key Compromise Procedures

Any private key compromise will result in revocation of the associated certificate(s) and issuance of an updated CRL as described in section 4.9.

### 5.7.4 Business continuity capabilities after a disaster

Provided by CertiNext as stated in the CertiNext CPS and binding upon the Subscriber.

## 5.8 CA or RA termination

If the InCommon RSA IGTF Server CA 4 must cease operation, InCommon will make a commercially reasonable effort to notify all participants in advance of the effective date of the termination as described in the Subscriber Addendum.

# 6. TECHNICAL SECURITY CONTROLS

The CA Private Keys are classified as highly critical to the business operations and continuity. If any of the CA’s private signing keys were compromised or were suspected of having been compromised, an assessment shall be made to determine the nature and extent of the compromise. In the most severe circumstances, all Certificates ever issued by the use of those keys shall be revoked and a notification shall be sent to all owners of Certificates of that revocation, and offer to re-issue the Certificates to the customers with an alternative /new key.

## 6.1 Key pair generation and installation

### 6.1.1 Key pair generation

InCommon RSA IGTF Server CA 4‘s private keys are generated in a physically secured environment by personnel in trusted roles within cryptographic modules.

Issuing CA key pairs are generated in a secure manner as part of a key ceremony in a physically trusted environment by trusted personnel. Issuing CA key generation is carried out in a secure device that is at least FIPS 140-2 Level 3 compliant. Key generation ceremonies are conducted with appropriate witness controls and documented in a Key Ceremony Report.

Subscriber key pairs:

1. Subscriber key pairs are generally generated by the Subscriber using secure methods (software or hardware) prior to submitting a Certificate Signing Request (CSR).
2. For SSL/TLS certificates, key generation typically occurs within the Subscriber's server or secure cryptographic device.

Issuing CA SHALL reject a certificate request if one or more of the following conditions are met:

1. The Key Pair does not meet the requirements set forth in Section 6.1.5 and/or Section 6.1.6;
2. There is clear evidence that the specific method used to generate the Private Key was flawed;
3. Issuing CA is aware of a demonstrated or proven method that exposes the Applicant’s Private Key to compromise;
4. Issuing CA has previously been made aware that the Applicant’s Private Key has suffered a Key Compromise, such as through the provisions of Section 4.9.1;
5. In the case of Debian weak keys vulnerability (https://wiki.debian.org/SSLkeys), the Issuer CA shall reject all keys found at https://github.com/cabforum/Debianweakkeys/ for each key type (e.g. RSA, ECDSA).
6. In the case of ROCA vulnerability, the Issuer CA shall reject keys identified by the tools available at https://github.com/crocs-muni/roca or equivalent.
7. In the case of Close Primes vulnerability (https://fermatattack.secvuln.info/), the Issuer CA shall reject weak keys which can be factored within 100 rounds using Fermat’s factorization method.

### 6.1.2 Private key delivery to subscriber

For TLS certificates, we do not generate or deliver private keys. The Subscriber is solely responsible for generating the key pair and ensuring the private key remains confidential and protected at all times. We do not retain, archive, or transmit private keys for TLS certificate Subscribers, except for the limited use case when automation services are contracted, as per Section 4.12.

### 6.1.3 Public key delivery to certificate issuer

Certificate requests are generated using Subscriber’s software, and the request is submitted to the InCommon RSA IGTF Server CA 4's approval workflow in the form of a PKCS #10 Certificate Signing Request (CSR).

### 6.1.4 CA public key delivery to relying parties

InCommon RSA IGTF Server CA 4 public keys are published in the CA repository (section 2.2) and are provided to the International Grid Trust Federation (IGTF) for inclusion in the IGTF Trust Anchor Distribution.

### 6.1.5 Key sizes

InCommon RSA IGTF Server CA 4 keys use a 4096 bit RSA modulus.

For IGTF end entity Certificates:

- RSA keys MUST have a minimum key length of 2048 bits.
- Elliptic Curve Cryptography (ECC) keys MUST use curves with a strength of at least NIST P-256 (also known as secp256r1).

### 6.1.6 Public key parameters generation and quality checking

No stipulation.

### 6.1.7 Key usage purposes (as per X.509 v3 key usage field)

The key usage field extension in InCommon Certificates specifies the purpose for which the Certificate and key pair may be used. Enforcement of the limitations of use found in this field is beyond InCommon's control as correct use is highly dependent on having the correct software.

## 6.2 Private Key Protection and Cryptographic Module Engineering Controls

### 6.2.1 Cryptographic module standards and controls

InCommon RSA IGTF Server CA 4 cryptographic key pairs are protected by cryptographic hardware security modules certified at FIPS 140 level 3 (or higher) and operated in FIPS 140 level 3 mode (or higher).

CertiNext ensures the protection of its Root signing key pair and the InCommon RSA IGTF Server CA 4 signing key pairs in accordance with its AICPA/CICA WebTrust program compliant infrastructure and CPS. Details of CertiNext's WebTrust compliancy are available at its official repository (<https://repository.emsign.com/>).

### 6.2.2 Private key (n out of m) multi-person control

For InCommon RSA IGTF Server CA 4 key recovery purposes, the InCommon RSA IGTF Server CA 4 signing keys will be encrypted and stored within a secure environment.

### 6.2.3 Private key escrow

InCommon RSA IGTF Server CA 4 does not escrow end-entity private keys.

### 6.2.4 Private key backup

See Section 6.2.2.

### 6.2.5 Private key archival

Not applicable.

### 6.2.6 Private key transfer into or from a cryptographic module

Where InCommon RSA IGTF Server CA 4 signing keys are backed up to another cryptographic hardware security module, such keys are transferred between devices in encrypted format only.

### 6.2.7 Private key storage on cryptographic module

The InCommon RSA IGTF Server CA 4 stores its private keys on cryptographic modules in nonexportable form.

### 6.2.8 Method of activating private key

The InCommon RSA IGTF Server CA 4 activates private keys according to the procedures of the hardware security modules which are run in FIPS 140-2 Level 3 mode.

### 6.2.9 Method of deactivating private key

The InCommon RSA IGTF Server CA 4 deactivates private keys according to the procedures of the hardware security modules which are run in FIPS 140-2 Level 3 mode.

### 6.2.10 Method of destroying private key

InCommon RSA IGTF Server CA 4 operators can destroy the private key in the cryptographic module by reinitializing the device (i.e., restoring it to factory default settings) or using the operator interface to securely delete the key.

### 6.2.11 Cryptographic Module Rating

See Section 6.2.1.

## 6.3 Other aspects of key pair management

No stipulation.

### 6.3.1 Public key archival

All issued certificates (which contain public keys) are archived for at least three years.

### 6.3.2 Certificate operational periods and key pair usage periods

The maximum validity periods for Digital Certificates issued within our default trust hierarchy are:

| Type | Private Key Use (signing the certificates) | Private Key Use (signing the CRL) | Certificate Term |
|---|---|---|---|
| Root CA Certificate | 20 years | 25 years | 25 years |
| All Subordinate CAs of Root CA e.g. InCommon Intermediate CAs | 3 years | 10 years | 10 years |
| Subscriber Certificates with Server Authentication EKU | Not Applicable | Not Applicable | 200 Days |

All certificates including subscriber certificates or any subordinate CA certificate end date shall not exceed the end date of its signing certificate (issuer).

## 6.4 Activation data

### 6.4.1 Activation data generation and installation

As per the CERTInext CPS

### 6.4.2 Activation data protection

As per the CERTInext CPS

### 6.4.3 Other aspects of activation data

As per the CERTInext CPS

## 6.5 Computer security controls

### 6.5.1 Specific computer security technical requirements

InCommon computer systems are set up and maintained in a secure manner that prevents unauthorized access. The InCommon RSA IGTF Server CA 4 computers are provided by CertiNext as stated in the CertiNext CPS and binding upon the Subscriber.

### 6.5.2 Computer security rating

No Stipulation.

## 6.6 Life cycle technical controls

### 6.6.1 System development controls

No stipulation.

### 6.6.2 Security management controls

No stipulation.

### 6.6.3 Life cycle security controls

No stipulation.

## 6.7 Network security controls

All InCommon RSA IGTF Server CA 4 systems employ operating system firewalls allowing inbound connections only for required CA services. InCommon RSA IGTF Server CA 4systems are connected to highly protected networks that are actively monitored for intrusions.

Issuing CA shall ensure that the network in which the CA system is hosted is protected by network firewalls and other systems that to the extent possible prevent unauthorized access by parties. Other measures include:

- Turning off any unused network ports or services.
- Firewalls and filtering routers used for CA equipment limits services to and from the CA equipment to those required to perform CA functions.
- Maintain network security controls that at minimum meet the Network and Certificate System Security Requirements.
- Check for mis-issuance of certificates, especially for high-profile domains.
- Shut down certificate issuance quickly if we are alerted of intrusion.
- Review network infrastructure, monitoring, passwords, etc. for signs of intrusion or weakness.
- Ensure IDS (Intrusion Detection System) and IPS (Intrusion Prevention System) systems, and other monitoring software are in place and are up-to-date.
- Segmentation of key certificate issuance systems from non-related servers and systems such as marketing websites, etc.

**Timeframe for Responding to and Remediating Vulnerabilities**

eMudhra shall maintain a documented process for the identification, assessment, prioritization, and remediation of vulnerabilities affecting systems, applications, and infrastructure supporting Certification Authority operations. Risk assessment for each identified vulnerability shall be completed within 48 working hours of identification. Vulnerabilities shall be remediated within the following timeframes based on their severity classification:

| Severity Level | Remediation Timeline |
|---|---|
| Critical | Within 96 Working Hours |
| High | Within 14 Working Days |
| Medium | Within 30 Working Days |
| Low | Within 60 Working Days |

## 6.8 Time-stamping

InCommon RSA IGTF Server CA 4 servers maintain accurate system clocks via trusted NTP servers or GPS devices.

# 7. CERTIFICATE, CRL, AND OCSP PROFILES

This CPS covers only InCommon RSA IGTF Server CA 4 certificates.

InCommon may update or extend its list of products, including the types of certificates it issues, as it sees fit. The publication or updating of the list of InCommon products creates no claims by any third party. If necessary, InCommon will amend this CPS or create a separate CPS upon the inclusion of a new certificate product in the InCommon hierarchy. The CPS will usually be made public on the official InCommon websites at least seven (7) days prior to the offering such new product.

Revoked certificates are appropriately referenced in the CRL and/or OCSP.

## 7.1 Certificate profile

In order to use and rely on an InCommon RSA IGTF Server CA 4 certificate, the relying party must use X.509v3 compliant software. Supported certificate profiles are listed in the InCommon Repository.

### 7.1.1 Version number(s)

The X.509 certificate version number is 2 indicating a Version 3 certificate.

### 7.1.2 Certificate extensions

The InCommon RSA IGTF Server CA 4 uses the standard X.509, version 3, to construct digital certificates for use within the InCommon PKI. X.509v3 allows a CA to add certain certificate extensions to the basic certificate structure. InCommon RSA IGTF Server CA 4 uses a number of certificate extensions for the purposes intended by X.509v3 as per Amendment 1 to ISO/IEC 9594-8, 1995.

The CA certificate contains the following extensions:

- X509v3 Basic Constraints: critical CA:TRUE
- X509v3 Key Usage: critical Certificate Sign, CRL Sign
- X509v3 Subject Key Identifier
- X509v3 Authority Key Identifier
- X509v3 CRL Distribution Points: URI: <http://crl.emsign.com/?roottlscag1.crl>
- X509v3 Certificate Authority Information Access: OCSP: URI: <http://ocsp-c.emsign.com/> and CRL: <http://crl.emsign.com/?roottlscag1.crl>

End entity certificates contain the following extensions:

- X509v3 Basic Constraints: critical CA:FALSE
- X509v3 Key Usage: critical Key Encipherment, Digital Signature
- X509v3 Extended Key Usage: TLS Web Server Authentication
- X509v3 Certificate Policies: Policy 1.3.6.1.4.1.50977.1.0.1.1, Policy: 1.3.6.1.4.1.5923.1.4.3.4.3, Policy: 1.2.840.113612.5.2.2.1 Policy: 2.23.140.1.2.2
- X509v3 CRL Distribution Points: URI: <https://crl.emsign.com/?EEEMIncommonIGTFOVG2C.crl>
- X509v3 Certificate Authority Information Access: OCSP: URI: <http://ocsp-c.emsign.com/>
- SubjectAltName: dnsName:FQDN

Reference for maximum Validity Periods of Subscriber Certificates

| Certificate Issued On or After | Certificate Issued Before | Maximum Validity Period |
|---|---|---|
| April 20, 2026 | March 15, 2027 | 200 days |
| March 15, 2027 | March 15, 2029 | 100 days |
| March 15, 2029 | – | 47 days |

### 7.1.3 Algorithm object identifiers

- Hash Functions: sha256 2.16.840.1.101.3.4.2.1, sha384 2.16.840.1.101.3.4.2.2
- RSA Encryption: rsaEncryption 1.2.840.113549.1.1.1
- Signature Algorithms: sha256WithRSAEncryption 1.2.840.113549.1.1.11, sha384WithRSAEncryption 1.2.840.113549.1.1.12

### 7.1.4 Name forms

See Section 3.1.5

### 7.1.5 Name constraints

All end entity subject distinguished names have the “/DC=org/DC=incommon” per Section 3.1.5.

### 7.1.6 Certificate policy object identifier

A Certificate Policy (CP) is a statement of the issuer that corresponds to the prescribed usage of a digital certificate within an issuance context. A policy object identifier (OID) is a number unique within a specific domain that allows for the unambiguous identification of a policy, including a certificate policy or a certificate practices statement (CPS).

Specific InCommon certificate profiles are found in the InCommon Repository, and any relevant OIDs are provided in Appendix B.

### 7.1.7 Usage of Policy Constraints extension

No Stipulation

### 7.1.8 Policy qualifiers syntax and semantics

The InCommon RSA IGTF Server CA 4 includes information in the Policy Qualifier field of the Certificate Policy extension that puts Relying Parties on notice as to the location of its CPS. This field usually includes a URL that points the Relying Party to the Relying Party Agreement, the CPS, and other documents in the repository where they can find out more about the limitations on liability and other terms and conditions governing the use of the Certificate.

### 7.1.9 Processing semantics for the critical Certificate Policies extension

No Stipulation.

## 7.2 CRL profile

CRLs comply with RFC 5280.

### 7.2.1 Version number(s)

The CRL version number is 1 indicating a Version 2 CRL.

### 7.2.2 CRL and CRL entry extensions

No Stipulation.

## 7.3 OCSP profile

OCSP is a way for users to obtain information about the revocation status of an InCommon RSA IGTF Server CA 4 issued Certificate. The InCommon RSA IGTF Server CA 4 uses OCSP to provide information about any of its revoked certificates that are unexpired. OCSP responders conform to RFC 8960.

### 7.3.1 Version Number(s)

No stipulation.

### 7.3.2 OCSP Extensions

No stipulation.

# 8. COMPLIANCE AUDIT AND OTHER ASSESSMENTS

The practices specified in this CPS have been designed to meet or exceed the requirements of generally accepted and developing industry standards, including the AICPA/CICA WebTrust Program for Certification Authorities, ANS X9.79:2001 PKI Practices and Policy Framework, and other industry standards related to the operation of CAs.

## 8.1 Frequency or Circumstances of Assessment

The InCommon RSA IGTF Server CA 4 performs internal operational audits at least once per year to verify compliance with the rules and procedures specified in this document.

All Issuing Certification Authorities are subject to an annual compliance audit. These audits are conducted by qualified independent auditors and are designed to confirm conformance with the latest versions of AICPA/CICA:

- WebTrust: for Certification Authorities
- WebTrust: Principles and Criteria for Certification Authorities – Network Security
- WebTrust: for Certification Authorities – Baseline Requirements for TLS
- WebTrust: for Extended Validation SSL, where applicable

These assessments ensure that our practices align with the CA/Browser Forum’s Baseline Requirements and applicable browser root program policies. Additional assessments may be performed in response to significant changes in CA operations, incidents, or at the discretion of the Policy Authority.

## 8.2 Identity/Qualifications of Assessor

As per the CERTInext CPS

## 8.3 Assessor’s Relationship to Assessed Entity

As per the CERTInext CPS

## 8.4 Topics Covered by Assessment

As per the CERTInext CPS.

## 8.5 Actions Taken as a Result of Deficiency

As per the CERTInext CPS

## 8.6 Communication of Results

InCommon RSA IGTF Server CA 4 audit result summaries are made available to TAGPMA upon request.

# 9. OTHER BUSINESS AND LEGAL MATTERS

While the structure of this CPS has been left intact as a matter of RFC form, the representations, warranties and limitations associated with this service are described in detail and governed by the provisions in the InCommon Participation Agreement and the Certificate Service Addendum.

## 9.1 Fees

### 9.1.1 Certificate Issuance or Renewal Fees

Fees are detailed on the official InCommon website (<https://www.incommon.org/certificates/>). InCommon may change these fees pursuant to its rights under the Subscriber Addendum.

### 9.1.2 Certificate Access Fees

Currently, InCommon does not charge a fee for Certificate access but may in the future. Charges may be incurred for extensive or time-consuming searches. Fees for such extensive use are negotiated on an individual basis.

### 9.1.3 Revocation or Status Information Access Fees

InCommon does not charge fees for the revocation of a certificate or for a Relying Party to check the validity status of an InCommon-issued certificate using its CRLs or OCSP.

### 9.1.4 Fees for Other Services

Fees for other services offered by InCommon are set either within the individual agreements with the parties or are detailed on the official InCommon website, depending on the services required.

### 9.1.5 Refund Policy

Subscriber refunds are described in the Subscriber Addendum.

## 9.2 Financial Responsibility

InCommon accepts no financial responsibility.

### 9.2.1 Insurance Coverage

Refer to the Subscriber Addendum and Relying Party Agreement.

### 9.2.2 Other Assets

InCommon accepts no financial responsibility.

### 9.2.3 Insurance or Warranty Coverage for End-Entities

InCommon provides no warranty as further described in the Subscriber Addendum and Relying Party Agreement.

## 9.3 Confidentiality of Business Information

InCommon observes the following rules on the protection of business information:

### 9.3.1 Scope of Confidential Information

InCommon keeps the following types of information confidential and maintains reasonable controls to prevent the exposure of such records to non-trusted personnel.

- Executed Subscriber agreements when not in violation with applicable state, federal, or other law (for example, state "sunshine" laws).
- Financial transaction records and financial audit records.
- External or internal audit trail records and reports.
- Certain portions of its contingency plans and disaster recovery plans.
- Internal tracking and records on the operations of the PKI infrastructure, certificate management and enrollment services and data.
- Subscriber Registrar email address and telephone if requested by Subscriber Registrar
- Proof of existence and organizational status of the Organization if marked Confidential by Subscriber

### 9.3.2 Information Not Within the Scope of Confidential Information

Subscribers acknowledge that revocation data of all certificates issued by the InCommon RSA IGTF Server CA 4is public information. Subscriber data marked as “Public” or submitted as part of a certificate request is not confidential and is published within an issued digital certificate in accordance with this CPS.

### 9.3.3 Responsibility to Protect Confidential Information

All personnel in trusted positions handle all confidential information in strict confidence. InCommon is not required to and does not release any confidential information, unless otherwise required by law or by obtaining consent from the party to whom the confidential information belongs, without an authenticated, reasonably specific request by an authorized party specifying:

- The consent of the party to whom InCommon owes a duty to keep information confidential.
- The name of the party requesting such information.
- A court order, if any.

## 9.4 Privacy of Personal Information

### 9.4.1 Privacy Plan

InCommon has implemented a privacy policy, which complies with this CPS. The InCommon privacy policy is published in the InCommon repository described in section 2.

### 9.4.2 Information Treated as Private

Any information about the designated officers of Subscriber organizations that is not publicly accessible or available through the content of the issued certificate, a CRL, or the OCSP is treated as private information. Subscriber organizations are responsible for the personal information of their delegated officers and constituents.

### 9.4.3 Information Not Deemed Private

Certificates, CRLs, the OCSP, and the information appearing in them are not considered private. Information about Subscribers available in public directories or databases is also not considered private.

### 9.4.4 Responsibility to Protect Private Information

All InCommon personnel receiving private information are responsible for protecting such information from compromise and disclosure to third parties. Each party will use the same degree of care that it exercises with respect to its own information of like importance, but in no event will the degree of care be less than a reasonable degree of care.

### 9.4.5 Notice and Consent to Use Private Information

Unless otherwise stated in this CPS, the applicable privacy policy, or by agreement, InCommon will use private information only for its own business purposes related to the services it provides to Subscriber and will not share that information with external parties except as required for by law or with the permission of the subject.

### 9.4.6 Disclosure Pursuant to Judicial or Administrative Process

InCommon is entitled to disclose any confidential or private information, if InCommon believes, in good faith, that the disclosure is necessary in response to subpoenas and search warrants or if disclosure is necessary in response to a pending legal proceeding or a state's mandated sunshine laws.

### 9.4.7 Other Information Disclosure Circumstances

No Stipulation.

## 9.5 Intellectual Property Rights

InCommon or its partners or associates own all intellectual property rights associated with its databases, websites, InCommon digital certificates and any other publication originating from InCommon, including this CPS.

### 9.5.1 Certificates

Certificates are the property of InCommon’s provider. InCommon gives permission to reproduce and distribute certificates on a nonexclusive, royalty-free basis, provided that they are reproduced and distributed in full. InCommon reserves the right to revoke the certificate pursuant to revocation terms in the Subscriber Addendum. Private and public keys are the property of the subscriber’s Subjects who rightfully generate and hold them.

Subscribers represent that their use of the certificate does not interfere with or infringe on any rights of third parties. The Subscriber represents that it is not seeking to use the issued certificate's domain and distinguished names for any unlawful purpose, including tortious interference with contract or prospective business advantage, unfair competition, injuring the reputation of another, and confusing or misleading a person, whether natural or incorporated.

### 9.5.2 Copyright

Copyright © 2010-2023 by Internet2. Permission to make digital or hard copies of part or all of this work for personal or classroom use is granted without fee provided that copies are not made or distributed for commercial advantage and that copies bear this notice. Abstracting or creation of derivative works with credit is permitted. To copy otherwise, to republish, to post on servers, or to redistribute to lists, requires prior specific permission.

### 9.5.3 Trademarks

See Subscriber Addendum.

### 9.5.4 Infringement

InCommon does not provide infringement resolution services. Subscribers are responsible for their own use of certificates. See the Subscriber Addendum for legal protections, rights and responsibilities.

## 9.6 Representations and Warranties

Subscribers, Subjects, relying parties and any other parties must not interfere with or reverse engineer the technical implementation of InCommon PKI services, including, but not limited to, the key generation process, the public website, and the InCommon repositories except as explicitly permitted by this CPS or upon prior written approval of InCommon. Results of failure to comply with this as a subscriber is described in the Subscriber Addendum. Failure to comply with this as a Relying Party will result in the termination of the agreement with the Relying Party, the removal of permission to use or access the InCommon repository and any Digital Certificate or Service provided by InCommon.

All parties – subscribers, certificate subjects, relying parties, and any others – are solely responsible for having exercised independent judgment and employed adequate training in choosing security software, hardware, and encryption/digital signature algorithms, including their respective parameters, procedures, and techniques as well as in using PKI as a solution to their security requirements.

### 9.6.1 CA Representations and Warranties

Other than the representations and warranties already detailed in this CPS, see Subscriber Addendum and InCommon Participation Agreement.

### 9.6.2 RA Representations and Warranties

Other than the representations and warranties already detailed in this CPS, see Subscriber Addendum and InCommon Participation Agreement.

### 9.6.3 Subscriber Representations and Warranties

Other than the representations and warranties already detailed in this CPS, see Subscriber Addendum and InCommon Participation Agreement

### 9.6.4 Relying Party Representations and Warranties

See the Relying Party Agreement in the InCommon Repository.

### 9.6.5 Representations and Warranties of Other Participants

No stipulation.

## 9.7 Disclaimers of Warranties

InCommon disclaims all warranties and obligations of any type, including any warranty of fitness for a particular purpose. See the Subscriber Addendum and InCommon Participation Agreement (found in the InCommon Repository) for further information.

## 9.8 Limitations of Liability

See the Subscriber Addendum and InCommon Participation Agreement (found in the InCommon Repository) for further information.

## 9.9 Indemnities

### 9.9.1 Subscriber Indemnity to InCommon

Indemnification by Subscriber to InCommon, if any, is described in the InCommon Subscriber Addendum.

### 9.9.2 Subscriber Indemnity to Relying Parties

No stipulation.

## 9.10 Term and Termination

### 9.10.1 Term

This CPS and any amendments are effective seven days after being published to the Repository and remain effective until replaced with a newer version.

### 9.10.2 Termination

In case of termination of InCommon RSA IGTF Server CA 4operations for any reason whatsoever except in the case of force majeure, InCommon will provide timely notice and transfer of responsibilities to succeeding entities, maintenance of records, and remedies. Details are provided in the Subscriber Addendum, available in the repository.

### 9.10.3 Effect of Termination and Survival

Details are provided in the Subscriber Addendum, available in the repository.

## 9.11 Individual notices and communications with Participants

InCommon accepts notices related to this CPS by means of email messages or in paper form to the InCommon point of contact listed in section 1.5.2. For communication issues related to the performance of certificates or the designation of Subscriber Executives and Registrars, secure communication will be required, either through out-of-band means such as telephone, through authorized web-based transactions or email secured by digital signature.

## 9.12 Amendments

The InCommon Policy Authority (PA) is also responsible for determining the suitability of proposed changes to the CPS prior to the publication of an amended edition. Amendments to this CPS may be made from time to time as approved by the InCommon PA. Amendments may be in the form of either an amended form of the CPS or made available as a supplemental document in InCommon's repository.

### 9.12.1 Procedure for Amendment

Updates supersede any designated or conflicting provisions of the referenced version of the CPS and are indicated through appropriate revision numbers and publication dates. Revisions that are not deemed significant by InCommon (those amendments or additions that have minimal or no impact on Subscribers or Relying Parties), are made without notice and without changing the version number of this CPS.

### 9.12.2 Notification Mechanism and Period

Upon the PAs listed in Section 1.5.4 approving such changes deemed to have significant impact on the users of this CPS, an updated edition of the CPS will be published in the InCommon repository, with seven (7) days’ notice given to Subscribers via email of upcoming changes. Suitable incremental version numbering will identify new editions.

### 9.12.3 Circumstances Under Which OID Must be Changed

If InCommon decides that a material change in InCommon's certificate policy warrants a change in the currently specified OID for a particular certificate type, then the revised CPS or amendment thereto will contain a revised OID for that type of certificate.

## 9.13 Dispute Resolution Provisions

Before resorting to any dispute resolution mechanism including adjudication or any type of alternative dispute resolution, a party must notify InCommon of the dispute with a view to seek a resolution. Parties must work with InCommon in good faith to resolve issues in a reasonable manner prior to third party involvement.

## 9.14 Governing Law

Details are provided in the InCommon Certificate Service Subscriber Addendum, available in the repository. This choice of law is made to provide uniform interpretation of this CPS, regardless of the place of residence or place of use of InCommon RSA IGTF Server CA 4’s certificates.

## 9.15 Compliance with Applicable Law

All parties agree to abide by all applicable laws when validating, issuing, or using certificates.

## 9.16 Miscellaneous Provisions

### 9.16.1 Entire Agreement

This CPS is not the entire agreement between any parties. All parties must accept additional agreements prior to receiving, using, or relying on a digital certificate. Section headings are for reference and convenience only and are not part of the interpretation of the CPS.

### 9.16.2 Assignment

This CPS is binding upon all successors and representatives of any party. The rights in this CPS are assignable.

### 9.16.3 Severability

Any provision held invalid or unenforceable will be reformed to the minimum extent necessary to make the provision valid and enforceable. If reformation is not possible, the provision is deemed omitted and the balance of the CPS remains valid and enforceable.

### 9.16.4 Enforcement

InCommon's failure to enforce any provision of this CPS does not wave its right to enforce the same provision later or right to enforce any other provision of this CPS. To be effective, all waivers must be both in writing and signed by InCommon. Agreements between InCommon and various parties control in the event of a conflict between this CPS and the Subscriber Addendum.

Except where an express time frame is set forth in this CPS, any delay or omission by any party will not impair or be construed as a waiver of such right, remedy or power.

### 9.16.5 Force Majeure

InCommon is not liable for a delay or failure to perform an obligation to the extent that the delay or failure is caused by an occurrence beyond the party's reasonable control. The operation of the Internet is beyond InCommon's reasonable control, and InCommon is not responsible for a delay or failure caused by an interruption or failure of telecommunication or digital transmission links, Internet slow-downs or failures, or other such transmission failure.

## 9.17 Other Provisions

No Stipulation

# Acknowledgments

The InCommon Policy Authority acknowledges the considerable efforts of the research and education community in the development of this CPS.

# APPENDIX A: PKI HIERARCHY

- emSign Root TLS CA - G1
   - InCommon RSA IGTF Server CA 4
      - Subscriber Server Certificates

# APPENDIX B: CERTIFICATE OBJECT IDENTIFIERS

| Entity / Certificate Policy/ Type of Certificate | OID |
|---|---|
| InCommon IGTF CPS | 1.3.6.1.4.1.5923.1.4.3.4.3 |
| CertiNext TLS CPS OID | 1.3.6.1.4.1.50977.1.0.1.1 |
| IGTF Classic Profile OID | 1.2.840.113612.5.2.2.1 |
| SSL/TLS - Organization Validation | 2.23.140.1.2.2, 1.3.6.1.4.1.50977.1.2.110 |
