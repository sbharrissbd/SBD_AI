1	In a single GitHub project repository, provide a README.md, discuss the size, scope and complexity of IT projects developed using DevSecOps CI/CD model in an Agile environment and projects developed using the tech stack in Appendix A and below:

1.1	Where the contractor acted as the prime or subcontractor but must have directly performed the work
SBD was the prime vendor on three efforts discussed in this response, HIOS, PECOS 2.0, and IMPACT Act. In all efforts discussed, SBD was involved in the development and management of every solution presented in this artifact. 
HIOS: Health Insurance Oversight System is a federal system of record for the Center for Medicare and Medicaid Services that provides a centralized, multi-user interface for insurance issuers and regulators to submit and store information on individual and small group major medical insurance. This system was recently migrated to and AWS solution and is currently undergoing incremental modernization efforts.HIOS is comprised of comprised of 17 enterprise-level systems and over 75 web services, involving over 22,085 active users, data from 6,090 issuers and 11,064 Health Plan Identifiers. 

PECOS 2.0: Provider Enrollment, Chain, and Ownership System (PECOS) is a CMS system in which providers of medical services and products that require Medicare Medicaid reimbursement are enrolled. PECOS 2.0 was a system modernization project by SBD in which the legacy system was completely reinvented utilizing modern technologies and approaches to development. The PECOS dataset is approximately 10 TB consisting, processing approximately 1.2 million transactions per year with approximately 1,800 enrollment analysts supporting all Medicare and Medicaid service and product providers nationwide. 
IMPACT Act: Improving Medicare Post-Acute Care Transformation Act’ (IMPACT Act) is a data science and analytics study that examines the effect of socioeconomic status on PAC quality measures and other resource utilization. SBD compliments studies currently being performed to examine Social Determinants of Health (SDOH) factors that influence cost and quality outcomes and Administrative Claims-to-Assessment Integration.. This project includes multiple disparate data sources within the Department of Health and Human Services and develops models for trend and predictive analysis. 
1.2	Pure open source technology in Amazon Web Services (AWS) with AI implementation, for projects in production environments, not development or experimental, and for these projects provide an infographic, details/descriptions and or diagram of the CI/CD pipeline and DevSecOps and Artificial Intelligence/Machine Learning (AI/ML) technology areas:

1.2.1	Programming Languages
SBD has developed one solution in AWS and migrated another into AWS. In both instanced the applications were developed with Java. However, open source technologies were utilized in as much as possible to support them. For instance, while the code was Java, we relied heavily on React JS and Spring frameworks. This code was then pushed to open source platforms. Below is a list of the technologies utilized for our solutions. 
•	Java 8 / JDBC v 4.2
•	React JS 16.0.0 /Redux v3.6.0
•	Spring Boot 2.0.0 / Spring 5.0.2 /Spring Data JPA v 2.1.0
•	Open API 3.0
•	AMQP v0.9.1
•	Ansible Playbooks
•	CloudFormation Scripts
•	Jenkins Scripts
•	Liquibase Scripts
1.2.2	Microservices and Containerized Services Platforms
PECOS 2.0 is based on microservices architecture with Kong as the API gateway and discovery server. As microservice nodes are deployed by the PECOS 2.0 OpenShift service, they are registered with Kong which then routes requests to the appropriate nodes without their clients needing to know the microservice instance’s full address.  
SBD utilized a Domain-Driven Design (DDD) approach when decomposing the PECOS 2.0 microservices. In this instance, the domain is the problem space; for PECOS 2.0, the domain was the business. The domain consisted of multiple subdomains, each becoming its own entity. Each subdomain within this approach can be a core, supporting, or generic domain. 
Each microservice is completely independent of each other with its own User Interface and database schema. We used RabbitMQ for the messaging framework to publish and subscribe to individual domain or microservice. 
Each service is packaged as a Docker image and container using Docker clustering or a container orchestration tool call OpenShift. 
Below is a picture of application code and DevOps cluster managed by OpenShift that SBD implemented. 
 
1.2.3	Message Streaming
For PECOS 2.0, SBD used RabbitMQ for asynchronous messaging for inter-service communication. The services communicated by exchanging messages over messaging channels called Topics. PECOS also implemented an architectural pattern called “Event Sourcing” in which sequence of events are recorded in an append-only Event Store using RabbitMQ. The RabbitMQ cluster was deployed and managed by OpenShift.
Our HIOS solution relied on Apache Camel for the inter-service communication.
1.2.4	CI/CD Pipeline Automation
The PECOS 2.0 DevSecOps team implemented full Continuous Integration/Continuous Deployment (CI/CD) automation pipeline to deliver multiple micro-services to OpenShift platform in containers. The platform was implemented as Infrastructure-as-Code (IAC) and configured purely through automation. Nexus was used for the container store. SonarQube, OWASP and Twistlock scans were used to create a centralized artifacts repository of hardened and authorized containers. Microservices were secured by leveraging both native AWS constructs and capabilities and the security and isolation mechanisms that are built into OpenShift. 
Below is a picture of CI/CD pipeline with corresponding tools. 

 
1.2.5	AI/ML platforms and integration
SBD’s IMPACT Act employs  SAS analytics on an AWS platform. We use IBM’s SPSS for statistical analysis, and DBeaver to interact with local databases. The system is supported with a Postgres database with plans to migrate to Amazon Redshift in the near future. Other tools and technologies, such as Python and Microsoft BI, are used as required. 
1.2.6	Alerting and Monitoring
SBD’s HIOS solution uses New Relic for application performance monitoring (APM). New relic has built-in  features to deliver real-time and trending data about the application's performance, CPU availability, database loads, or something else entirely unexpected. HIOS solution has customized and configured new relic to quickly identify potential problems before they affect the end users. 
SBD customized New Relic’s Alerts alerting solution with policies and conditions to be able to notify IT operations immediately when an incident occurs. 
SBD continues to develop automated solutions with New Relic that will enhance and automated its COTS AI capabilities. 
1.2.7	Implementation of Shift-Left strategy and up front threat assessment models
For PECOS 2.0, we implemented an eight-step strategy for shifting security to the Left these steps are listed below. 
1.	Define the guiding principles
2.	Document the AWS best practices and CIS benchmarks
3.	Build the security controls and configurations in the infrastructure code
4.	Leverage shared services, such as Nessus scans and Splunk
5.	Security code reposited in GitHub and protect via permissions and controls
6.	Implement through DevSecOps pipeline to discover and log vulnerabilities
7.	Build monitoring capabilities for infrastructure and applications
8.	Log all generated documents in the security repository 
 
1.2.8	Perform Platform Level threat assessment
SBD implements a Multi-Layered Security approach across its applications to assess and maintain security across the applications. This approach includes the following: 
•	Physical isolation by using node labeling to deploy Pods on separate EC2 instances in different subnets
•	Network isolation via network policies and the software defined network.
•	Twistlock provides build time scanning of container images and run time scanning of Containers
•	Container images are secured and controlled with Center for Internet Security (CIS) benchmark and other controls:
a)	Least privileged
b)	Role based
c)	Minimal footprint with no commands to run
d)	SELinux 
e)	Control Groups (cgroups)
f)	Linux Capabilities restrictions
g)	Seccomp configuration
SBD’s multi-layers approach addresses security concerns across three major components: perimeter, containter, and platform. 
Perimeter Security. The PECOS architecture leveraged a tool called Sophos, from the AWS Market Place, which provides our perimeter security at the edge within the DMZ. This tool provides several security components to our infrastructure including a Web Application Firewall (WAF), Intrusion Detection System (IDS), Intrusion Prevention System (IPS), Traffic Inspection, and many other security controls and policies. 
Container Security. The PECOS Docker containers leverage a multi-layered approach to security, and implement many different mechanisms to scan, monitor, isolate, and restrict them to protect application processes and data. Docker containers run within the underlying Linux kernel on the isolated virtual host (EC2 instance), which is isolated from other virtual hosts which may be on the same physical server. Even within the isolated virtual host, there are several other Linux controls that are implemented to protect and isolate containers:
Platform Security. The OpenShift platform also has several security mechanisms built in, which have been implemented to further protect the application and its data. In addition, our supporting infrastructure that hosts OpenShift has been designed and implemented according to the CMS TRA, with several other implemented security controls: 
•	Software Defined Network (SDN) – This defines policies on the internal container overlay network, which defines explicit ingress and egress rules for container-to-container communication.
•	Node Labeling - Labels are applied to deployment configurations to ensure that specific pods and containers are only deployed to the appropriate EC2 instance types, in the correct zones, according to the CMS TRA.
•	Deployment configurations are created so that Containers will not run as root, so they won’t be able to access the Docker daemon, or modify SDN policies; Root access is also be protected on underlying hosts.
•	Every Pod gets a unique SELinux context on a host. It would be extremely difficult, but if you were to break out, SELinux would prevent you from being able to access anything on the host, besides what the pod already had access to; which is nothing since we have secured containers. For example, a microservice Pod only has access to files in the microservice folder, with a microservice user owner.
•	OpenShift's Security Enhanced Linux modifications protect Host from container breakout.
1.2.9	Areas of automating
SBD implements Continuous Integration/Continuous Delivery, Continout Delivery pipelines resulting in Release On Demand. This is proven through the DevSecOps approach provided for PECOS and the solution currently being developed and modernized for HIOS. Our solution provides complete automation from point of commit to point of delivery, automating fuctional testing, vulernability scanning, and production release, allowing on-demand deployments across multiple environments. The DevSecOps approach delivers early and often, providing solutions to your users faster while reducing risk and cost. 
1.2.10	Demonstration of analytics based on big data lakes
For the PAC GVO contract, SBD utilizes Internal and External data sources to CMS resources to inform CMS on the degree to which SDOH influences the amount paid and the quality outcomes Medicare beneficiaries experience. The team ingests four years of Medicare claims history for the entire Medicare population to account for every business case scenario, including dissemination of claims resource users without a follow-up PAC use. Rather than using a subset of beneficiaries as research sample, SBD is analyzing claims services for all beneficiaries having at least one PAC assessment within a three year period. This information provides overarching understandings associated with overall population health and quality and influencing factors. 
This project is segmented into the four phases shown below. The Data Analytics will be used to create a prototype to view the information in a meaningful way. 
1)	Environmental Scan – Research potential data sources for predictive modeling of SDOH. Review literature for studies related to this scope.
2)	Data Collection / Analysis – Establish integrated database of CMS and Non-CMS data to track quality, cost, and utilization. Migrate data from source systems to DB instance
3)	Data Analytics – After creating an integrated database among the critical source data, the study enters an advanced analytics phase to statistically measure relationships and associations among SDOH and quality variables using multivariate statistics, such as:
a.	Multiple Regression will calculate the statistical correlation between variables
b.	Factor Analysis will mine the hidden relationships within data by establishing matrices of variance
c.	Multivariate Analysis of Variances (MANOVA) will help isolate specific risk factors from their compounding effect on the dependent variables.
4)	Prototype Development – The prototype will assist users in determining best care options and view and download predictive models reflecting populations affected by potential policy changes. 
a.	Policy changes to reimbursement, quality measurement methods, data collection methods or other ways in which CMS influences provider/beneficiary behaviors.
b.	Effects of policy changes that reflect costs, outcomes or other quantifiable methods for determining the level of quality of care delivered.
c.	Populations defined into segments exhibiting SDOH.
1.2.11	Working with disparate data sources for a predictive analysis
SBD utilizes predictive tools for IMPACT Act across multiple databases within HHS to examine implications upon populations as a result of potential policy changes.
SBD’s work includes model design and business case development by conducting an exhaustive environmental scan of existing research pertaining to the study scope. This initiative enables the project team to configure the data requirements as well as aligning the study hypothesis to meeting the CCSQ goal of improving quality, while lowering cost, in the PAC setting.
SBD designs, implements, and evaluates data models from CMS source data, along with non-CMS derived source data, to measure the appropriateness to meeting the study objectives, and incorporates data strategy best practices for operationalizing the management and integration of disparate source data into a central data repository.
The project research team is comprised of data and research scientists to support the execution of the project statistical analysis to support the predictive model. The team is building an integrated clinical data repository to provide a platform for predictive analytics. The integration strategy is documented to be reproducible for expansion into new data sources. The team deploys Master Data Management and other data strategies including data integration to ensure integration occurs without manipulating the sample size.
1.2.12	Implementing cloud best practices using AI predictive analysis
While SBD has implemented cloud solutions, we have only planned AI solutions in cloud environments. Our planned work includes the following concepts:
1.	Manage cloud costs using AI predictive analysis through power cycling of solution instances. 
2.	Filter unnecessary alerts and automate actions for known events to enable IT specialists to focus on what’s important and not be distracted by false positives.
3.	Threat detection and analysis for compliance and risk reduction. 
4.	Monitor, manage, self-heal, and optimize applications through event analysis, trigger points, and other AIOps concepts. 
5.	Predictive scaling of solution environments to maintain optimal resource utilization. 
1.2.13	Formed a technical team as first point of contact to address and resolve tickets
The technical team and first point of contact are established in the DevSecOps model that was used in PECOS and HIOS. This establishes tier-level three support with microservice owners who are technical experts within their domains. They can receive tickets through the service desk system and notifications through New Relic. They then manage tickets through a Kanban solution as the front end component of DevSecOps, and released upon successful negotiation of the pipeline. 
1.2.14	Experience with DevOps Alerting and Monitoring
As with PECOS and HIOS, alerting and monitoring falls within the realm of Application Operations who works closely with DevSecOps to develop and implement plans and metrics for the performance and management of the solution. Our solutions integrate with systems like New Relic and Cloudwatch for application performance, Promethius for log aggregation and Splunk for log monitoring, Hygiea for code health, Twistlock security and vulnerabilities, and the OpenShift Cluster Console (OKD) for platform monitoring.
These systems integrate with the solution and with each other, and alert in multiple ways to include email. Automation is gained through use of webhooks, which we integrated in our DevSecOps pipeline. However, webhook can be used much more extensively in conjunction with an APIs to trigger remediations to attempt to return the system to full health. 
1.2.15	Demonstration of analytics based on service desk tickets
On HIOS, SBD utilizes analytics to create granular metrics that measure their performance against the requested work that establishes a baseline by which goals can be assigned. 
1.2.16	Working with disparate data sources for a predictive analysis 
Please refer to 1.2.11 of the same title. 
1.2.17	Implementing intelligent Tier 3 Ops routing system

SBD clients tend to control the service desk software that is implemented around our solutions. So we cannot control these environments. However, the routing system is based on the taxonomy associated with help desk categories and can automatically forward to the appropriate teams and persons based on the information provided. Newer systems have the ability to transcribe phone messages and sort requests based on content. Furthermore, these systems can sort requests and forward them according to the correct support team. Additionally, monitoring systems can be integrated with the service desk, either through an API or through a webhook which can trigger a ticket to be created and routed accordingly. 

Intelligent routing systems also route tickets to level resources to ensure tickets are resolved as efficiently as possible. AI in this sense reviews ticket queues and metrics like resolution times to determine who should receive the next ticket. 
