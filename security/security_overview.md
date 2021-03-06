# Security Overview

Internet of Things (IoT) provides extensive connection over the world, helps traditional business make digital transition, creates value while reducing operation cost, and promotes production efficiency to increase business revenue.

On the other hand, however, security in the internet of things, privacy and ethics, and compliance is an ever huge challenge to businesses around the world. IoT solutions fuses the physical and digital worlds, which means potential attacks and risks can occur in both of them. IoT also brings more concerns about privacy and ethics. Companies are always cautious to their data, in regards to considerations about who has the right permissions to access what resources, who takes the privilege to manage the access control policies, and so on.

Therefore, comparing to cyber security requirements for traditional software development and implementation, a secure IoT solution requires protection, defense, and governance all through the data journey: secure provisioning of devices, secure communication between devices and cloud, secure data processing and storage in the cloud, secure application development, and so on.

This article introduces how EnOS provides a secure and private IoT solution. EnOS is a comprehensive IoT operation system with security built in every stage.

## A Glimpse of EnOS Security

EnOS manages over 100 Gigawatt of assets for our clients, among which most are giant energy company in the world. Solid security practices and principles are core to the design of EnOS to ensure that the security, privacy and ethics, and compliance of our clients’ systems and data are maintained at all times.

EnOS takes the advantages of secure infrastructure of leading IaaS vendors to maintain the cloud security, data privacy, such as guest operating system patching, firewall configuration, and disaster recovery. The network of EnOS is secured by world-class network infrastructure also provided by the IaaS vendors, including Virtual Private Cloud (VPC), limited access points, rule-based network traffic, IPsec VPN, etc. Considering secure transmission protection, applications connect to EnOS REST APIs MUST via HTTPS or Transport Layer Security(TLS), devices and EnOS edge can connect to cloud-based IoT Hub via TLS protected data tunnel.

EnOS offers secure edge, secure connectivity, secure data storage and processing, and so on. The rest of this article breaks down the EnOS into four primary security areas.

## Secure Edge

Each EnOS edge has a unique identity key which can be used by the IoT Hub to communicate with the edge while it is in operation. The key with a user-defined edge ID forms the basis of a token and a signature used in communication between the edge and the IoT Hub. These edge IDs can use an existing fixed identity such as serial number, network MAC address which is not simple to be changed. The edge IDs are managed by _edge device provisioner_ in the IoT Hub via EnOS console or APIs. The IoT Hub provides secure storage of edge identities and secret keys.

EnOS edge has built-in firmware/software upgrade feature to ensure that critical patches against security vulnerabilities can be applied manually or automatically. Any changes or firmware/software upgrades applied to edges will be logged at the cloud side for auditing.

Unused USB ports are disabled by default to prevent malicious access. Only network ports used by necessary applications and services are enabled by network policies explicitly.

Some type of EnOS edges are manufactured with TPM chips. EnOS may utilize this hardware feature to store the client certificate securely.

## Secure Connectivity

EnOS edge and other compatible edge devices communicate with EnOS cloud via TLS protected data tunnel. X.509 certificate based bi-directional authentication is enforced for each session. To ensure that each edge has its exclusive client certificate, the certificate request exchange is performed by edge during its first power-on procedure. Edge device generates public certificate request containing unique device identifier (e.g., serial number, network MAC address) and corresponding private key according to PKI standard. Certificate request will be forwarded to EnOS certification service or public-trusted CA for sign. Later, issued public certificate will be sent back to edge device, to be stored together with private key locally.

To ensure secure connections from the devices and end users to the EnOS portal, HTTP over TLS is applied for data transmissions, which uses public-key cryptography to prevent eavesdropping, tampering, and forgery.

Devices and end users can establish secure communication sessions to API endpoints that EnOS services provide. HTTPS is used for accessing the REST APIs. For the TLS protected data channel between the devices and EnOS cloud, X.509 certification based bidirectional authentication is adopted, all data is encrypted during transmission.

## Secure Cloud and Data

EnOS takes famous IaaS vendors as its cloud infrastructure providers. The IaaS vendor is responsible for protecting the global infrastructure that hosts all services provisioned in the cloud. The infrastructure is comprised of the hardware, software, networking, and facilities that run the cloud services. For these managed cloud services, the IaaS vendor manages basic security operations such as guest operating system patching, firewall configuration, and disaster recovery.

From the security perspective, adopting an IaaS vendor brings the following benefits:

- Industry-standard security compliance.
- State-of-the-art physical and environmental security solutions.
- High availability, which promotes business continuity.
- World-class secure network infrastructure with focus on manageability and monitoring.
- Mature change management process.

The data centers where EnOS is hosted are state of the art, secured by innovative architectural and engineering approaches:  
- The data centers are housed in nondescript facilities.
- Physical access is strictly controlled at both the perimeter and the building ingress points by professional security staff who utilizes video surveillance, intrusion detection systems, and other electronic means to enforce security.
- An authorized staff must pass two-factor authentication for a minimum of two times to access the data center.

EnOS adopts a very strict mechanism for protecting data at rest. Sensitive data, defined by built-in and custom rules, is encrypted before putting into files or databases. Data is encrypted with keys exclusive to the customers that are generated by EnOS or provided by clients. Decryption happens automatically when data is retrieved through the EnOS API. Therefore, no intruders or platform operators will have access to the data even when they have access to the underlying file system or database systems.

Within EnOS, data (such as files, database) belonging to different clients (a.k.a. “OU”) are stored separately or segmentally. Logical data segmentation is established in all underlying components of EnOS. In the EnOS big data storage system, all files, tables, and other types of data are secured by access control, although data from different clients are stored physically in a single cluster. Only authorized user may access data with audit-enabled API calls or command tools. This mechanism not only promotes the security of data, but also makes it possible to share data among different clients without extra storage cost.

In addition, EnOS also has capability of providing dedicated storage for those clients with highly sensitive data, to meet the requirement of some special scenarios.

## Secure Application

While the underlying IaaS secures the physical venues, network, operating systems, and managed services. EnOS secures the applications that are hosted on the platform, including applications that manage massive IoT assets.

EnOS secures applications through the following means:

- Identity and Access Management
- Network protection
- Data encryption
- Logging and Monitoring
- Security Auditing

#### Identity and Access Management

Identity and Access Management (IAM) enables you to create and manage permissions for EnOS resources. IAM unifies access control for Cloud Platform services into a single system and presents a consistent set of operations. EnOS applies the IAM scheme to support multi-tenancy, where each tenant in EnOS is managed as an organizational unit. Data that belongs to different organizations are securely segregated and can only be accessed by users that are registered to the organization.

The built-in IAM of EnOS schemes provide capabilities of identity management, authentication, authorization, and auditing.

#### Network Protection

EnOS hosts several automated monitoring tools to detect abnormal and unauthorized activities and situations at ingress and egress points. These tools monitor the server and network usage, port scanning activities, application usage, and unauthorized intrusion attempts. The tools allow custom performance metric thresholds to be set for abnormal activities.

#### Data Encryption

Sensitive data, defined by built-in and custom rules, is encrypted before being put into files or databases. Decryption happens automatically when data is retrieved through the EnOS API.

#### Logging and Monitoring

Centralized logging service in EnOS is configured to aggregate activity logs and show security related metrics at the real-time.

EnOS logs all user activities to the portal and API invocations. The activity log contains details about each access request including the request type, requested resource, requestor’s IP, and the date and time of the request. Alerts are triggered when defined thresholds are exceeded.

#### Security Auditing

Accounts with proper privileges may access authorized resources via EnOS service APIs and portal. Access validation is performed for each access attempt. Success or failure attempts are recorded in IAM logs for auditing and abnormality detection purposes.

## Conclusion

Security is integrated into every aspect of EnOS. EnOS offers you unique security advantages derived from protect, governance and defense for the IoT Security, privacy and ethics, and compliance.

Modern applications are continuously moving to the cloud because the cloud not only provides scalability, high performance and reliability, but also provides very high security standard.

Compared to the traditional application hosted in the clients’ own data center, whose security completely relies on the clients, the security responsibilities of the cloud applications are shared across the cloud infrastructure provider, the cloud application platform and the clients.

The IaaS vendor is responsible for the industrial compliance, the physical and environmental security, the network security, the operating system security and the storage security. EnOS, as the IoT PaaS, is responsible for adopting the best security practices for authentication, access control, network protection, data encrypting, activity logging and auditing to secure clients’ data and applications.

EnOS has taken security seriously and carefully considers all security aspects with substantial web application security experience. EnOS will continue to help our clients make a sound decision on the IoT platform to protect the confidentiality, integrity, and availability of their devices and data.
