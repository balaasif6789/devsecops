11 Container Security Scanners to find Vulnerabilities

By Avi

Are your container and Docker image secure?

Let’s find out!

Hackers have gone very active in the past few years. Even big organizations like Facebook, Google, and Yahoo have been victims to attacks losing millions of dollars. That is why an application’s security is the utmost important thing in every organization today.

Many of these applications today run inside containers as they are easily scalable, cost-effective, faster deployable, take lesser storage, and use resources far better than virtual machines. So, the security factor of these containers is very crucial. A container image is made up of layers, and to get a real understanding of an image’s vulnerability stance, you need to access each layer. The smaller container images have a lesser chance to get exposed to potential vulnerabilities.

Containerization is one of the core stages in the DevOps process where security must be looked at on a serious note. A container image can have many bugs and security vulnerabilities, which gives a good opportunity for hackers to get access to the application or data present on the container costing millions to the company.

Hence, it is crucial to scan and audit the images and containers regularly. DevSecOps plays an important role in adding security to the DevOps processes, including scanning images and containers for bugs and vulnerabilities.

A container security scanner will help you find all the vulnerabilities inside your containers and monitor them regularly against any attack, issue, or a new bug.

Let’s explore the available options.

Clair
Clair is an open-source project which offers static security and vulnerability scanning for docker and application (appc) containers.

It is an API-driven analysis engine that checks for security flaws in the containers layer by layer. You can build services using Clair, which can monitor your containers continuously for any container vulnerabilities. It notifies you about a potential threat in the container. It notifies you about a potential threat in the container based on the Common Vulnerabilities and Exposures database (CVE) and similar databases.

If any threat or issue identifies which is already there in the National Vulnerability Database (NVD), it will retrieve the details and provide the details in the report.

clair dashboard
Clair features:

Scans for existing vulnerabilities and prevent them from being introduced in the future.
Provides REST API for integration with other tools
Sends a notification when it identifies any vulnerability
Provides report in HTML format with all the details of the scan
Updates metadata at regular intervals
Anchore
Anchore is an open-source project for deep analysis of docker images.

It also certifies a docker image telling whether it is secured or not. Anchore engine can run as on a standalone or on orchestration platforms such as Kubernetes, Rancher, Amazon ECS, Docker Swarm. Anchore is also available in Jenkins plugins to scan the CI/CD pipeline.

If you just need a Kubernetes scanner then check out these tools to find security flaws in Kubernetes.

You need to submit a docker image to anchore, which will analyze and provide you with the details if it has any vulnerabilities. You can use your custom security policy also to evaluate an image in anchore.

anchore dashboard
You can access anchore engine through CLI or REST APIs.

Anchore features:

Provides deep inspection of container images, OS packages, and software artifacts such as jar files
Integrates with your CI/CD pipeline seamlessly to find security breaches
Defines and applies policies to prevent building and deploying dangerous images
Check for only certified and secured images before deploying them on an orchestration platform.
Customize checks for vulnerabilities, configuration files, image secrets, exposed ports, etc.
Dagda
Dagda is an open-source tool for static analysis of known vulnerabilities such as trojans, malware, viruses, etc. in docker images and containers. It uses the ClamAV antivirus engine to detect such vulnerabilities.

It first imports all the known vulnerabilities from CVE, Red Hat Security Advisories (RHSA), Red Hat Bug Advisories (RHBA), Bugtraq IDs (BID), and Offensive Security database into a MongoDB. Then corresponding to the imported vulnerabilities, the images and containers are analyzed.


Dagda features:

Supports multiple Linux images (CentOS, Ubuntu, OpenSUSE, Alpine, etc.)
Analyses dependencies from java, python node js, javascript, ruby, PHP
Integrates with Falco for monitoring the running containers
Stores each analysis report in MongoDB to maintain the history of each docker image or container
Falco
Falco is an open-source project and a threat detection engine for Kubernetes. It is a runtime security tool to detect anomalous activity in hosts and containers running on Kubernetes. It detects any unexpected behaviors in your application and alerts you about the threats at runtime.

falco dashboard
It uses tcpdump like syntax to build the rules and leverages libraries such as libscap and libinsp which have the capability to go in and pull data from your Kubernetes API server or your container runtime environment.

Afterward, you can use that metadata to get about pods and labels and namespaces to actually go and create rules specific to a particular namespace or a particular container image. The rules focus on system calls and what system calls are allowed and disallowed on the system.

Aqua Security
Aqua Security protects applications that are built using cloud-native technologies like containers. It provides vulnerability scanning and management for orchestrators like Kubernetes.

It is a comprehensive security platform to ensure that those applications running on the containers are secure, and they’re running in a safe environment.

As developers build images, they have a set of technologies and libraries to build their images. Aqua security allows them to scan those images to ensure that those images are clean, they don’t have any known vulnerabilities in them, they don’t have any known passwords or secrets, and no kind of security threat that could make that image vulnerable.

aqua security dashboard
If any vulnerability is found, aqua security reports them back to the developer and recommends what they need to do to fix those vulnerable images.

Aqua Security also has technologies to ensure that it doesn’t get attacked or penetrated with any security threat once the container runs on production.

Docker Bench
Docker Bench Security is a script with multiple automated tests to check for the best practices for deploying containers on production.

To run docker bench security, you need to have Docker 1.13.0 or later.

You need to run the below command to run docker bench security.

docker run -it --net host --pid host --userns host --cap-add audit_control \
-e DOCKER_CONTENT_TRUST=$DOCKER_CONTENT_TRUST \
-v /var/lib:/var/lib \
-v /var/run/docker.sock:/var/run/docker.sock \
-v /usr/lib/systemd:/usr/lib/systemd \
-v /etc:/etc --label docker_bench_security \
docker/docker-bench-security
After this, the script will run, and it will share details for INFO, WARN, PASS. After running the script, you can check at all the warning messages and make the corrections.

docker bench security
Harbor
Harbor is an open-source and trusted cloud native registry that provides security policies and role-based access control (RBAC). It stores, signs, and scans docker images for vulnerabilities. It can be installed on a Kubernetes cluster or any other system which supports Docker.

harbor dashboard
Harbor features:

Easily deployable using Docker Compose
Provides security and vulnerability analysis
Multi-tenant content signing and validation
Identity integration and role-based access control
Extensible API and User Interface
Image replication between instances
Supports LDAP/AD and OIDC for user management and user authentication
JFrog Xray
JFrog Xray is continuous open-source security and universal artifact analysis tool.

With JFrog Xray, you can continuously scan your artifacts and dependencies for security vulnerabilities and license compliance issues.

As a universal artifact analysis solution, Xray proactively identifies security vulnerabilities and license risks. Before manifesting in production, Xray natively integrates with JFrog Artifactory providing visibility in all the artifact metadata, including security status in a single screen.

jfrog xray
JFrog Xray database of new vulnerabilities and technologies is constantly expanding, enabling you to make better technical judgments with fewer trade-offs. It checks all your components against its growing database of new vulnerabilities and alerts you to new issues even after the release.

It supports all package types and uses deep recursive scanning to review all underlined layers and dependencies, even those packaged in Docker images and zip files. JFrog Xray also creates a graph of your artifacts and dependencies structure and impact analysis of the vulnerabilities and license issues discovered

Qualys
Qualys container security is a tool used to discover, track, and continuously protect container environments. It scans for vulnerabilities inside images or containers in the DevOps pipeline and deployments on cloud or on-premise environments.

qualys
Qualys provides a free version of the container security application to give users a glimpse of what it can offer. It gives you a view of images and containers running in the environment. If you want to scan them, you need to take their paid subscription.

It also provides runtime security for containers by giving function level firewall for containers. It gives in-depth visibility into container behavior and protects the image and running containers using Qualys CRS (container runtime security) layer.

Docker Scan
Still, in beta, Docker Scan leverages Synk engine and capable of scanning local Dockerfile, images, and its dependencies to find known vulnerabilities. You can run docker scan from Docker Desktop.

docker scan mydockerimage
Grype
These days, container security is a popular topic. The scanner to scan container security is one of many tools you can use to help secure your containers. Grype is a security scanner for containers used to identify vulnerabilities in containers operating on any platform.

It can be found on GitHub and is open source. Both a web application and a command-line tool are available for Grype.

grypevulnerabilitiesscanner
This open-source container vulnerability scanner tool aids DevOps teams in finding and resolving security flaws in their runtime environments and container images.

It checks running containers for potential security flaws and scans public and private Docker images for vulnerabilities. Grype can be used alone or as a plug-in for well-known DevOps instruments like Jenkins, CircleCI, and Travis CI.

Top Features

Support all popular operating systems, including Redhat, Oracle, Ubuntu, CentOS, etc.
Simple installation and compatibility with several other languages, including Java, Ruby, PHP, and DotNet
Accepts Syft, SPDX, and CycloneDX SBOM input formats
Its output format can be defined using Go templates
Supports several sources for building vulnerability databases to increase the reliability of vulnerability matching.
Grype is gaining popularity because it is simple to install and can be used on any platform that supports containers.

Since there are numerous ways to attack a container, having a solid security scanner is essential. Hence a new container security scanner, Grype, can be used to find vulnerabilities in containers and prevent attacks.
