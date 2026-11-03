# Interview Questions: 1st Round

## 1. Introduction and experience

1\. Can you introduce yourself and explain your current roles and responsibilities?

2\. How many years of overall experience do you have, and how much experience do you have with Azure?

3\. Have you worked with Terraform, or is infrastructure provisioning handled by a separate team?

## 2. Terraform and Infrastructure as Code

4\. Which Terraform modules have you created or worked on? Explain your experience creating VPC, subnet and VM modules.

5\. If you provision a VPC/VNet, subnet and VM together in a single Terraform apply, how do you ensure that the subnet is created before the VM? How do you establish resource dependencies in Terraform?

## 3. CI/CD and DevSecOps

6\. Have you developed CI/CD pipelines for infrastructure deployment and application deployment? Which tools have you used?

7\. Walk me through your infrastructure development pipeline end to end. What type of application was involved, and at which stages did you implement security controls?

8\. What is a quality gate? How do you define quality gates, and what criteria do you use to allow or block a pipeline?

9\. Is your application deployed on AKS or EKS? Explain the application deployment architecture.

10\. After the code checkout and build stages, what security scanning stages do you execute in your CI/CD pipeline? Explain the different scans.

11\. How do you configure and execute Fortify SAST scanning in a CI/CD pipeline? Explain the CLI commands, plugins, YAML pipeline steps, prerequisites and result publishing process.

## 4. Azure Security and Governance

12\. Have you worked with Azure Policies and Initiatives? Can you explain any custom policy or initiative you have implemented at the management group or subscription level?

13\. Have you independently created and deployed any custom Azure Policy? If yes, explain the policy and its implementation.

14\. Have you worked on identifying and remediating non-compliant resources in Azure? Explain the remediation activities you performed.

15\. Have you executed any Azure remediation task? Explain a real-time scenario and the steps you followed.

16\. Have you worked with Azure Firewall or other firewall technologies? Who manages firewall configuration in your current project?

17\. Have you configured or worked with Microsoft Defender for Cloud? What security features or recommendations have you handled?

## 5. Git Security and Secrets Management

18\. As a security engineer, how would you proactively prevent developers from accidentally pushing secrets such as API keys, passwords or tokens into GitHub/GitLab repositories? What preventive scanning mechanisms would you implement?

19\. Have you worked with GitLeaks, TruffleHog or GitGuardian? Explain how you configure GitLeaks and integrate it into a CI/CD pipeline. At which stage would you execute the scan?

20\. Where would you securely store sensitive infrastructure information such as AWS Account IDs, Azure Tenant IDs, credentials and other configuration values used in GitHub/GitLab repositories?

21\. How would you integrate an external secret manager such as AWS Secrets Manager, Azure Key Vault or HashiCorp Vault with GitHub/GitLab pipelines?

## 6. Security Monitoring and Vulnerability Management

22\. Have you worked with Microsoft Sentinel and Qualys? Explain their purpose, how they are used and your level of hands-on experience.

## 7. Cloud Networking and Architecture

23\. Consider a VM deployed inside an Azure VNet or AWS VPC. Explain the ideal end-to-end inbound traffic flow, including DNS, routing, network security controls, firewalls and the destination VM.

24\. At which different network layers can you control or restrict traffic reaching a VM? Explain the role of NSGs, Security Groups, route tables, UDRs and firewalls.

## 8. Cloud Storage Security and Troubleshooting

25\. Suppose an Azure Storage Account is configured as private, but an unauthorized external user is still able to access its Blob data. What could be the possible reasons, and how would you investigate and troubleshoot the issue?

## Additional questions from the interview closing discussion

These were not technical assessment questions, but were also asked:

1. Do you have any questions for the interview panel about the role, project or client?
2. What is your current notice period and expected last working date?
3. Do you currently have any other offer in hand?

----
# Answers: 1st Round

## Question 1

Question:

Introduce yourself and explain your current roles and responsibilities.

Answer:

Good morning. I’m a DevSecOps Engineer with around 4.5 years of experience in DevOps, CI/CD automation, cloud infrastructure, and application security.

Currently, I’m working with CURRENT COMPANY, deployed to In-Solutions Global, a fintech and payment gateway organization supporting banking clients.

My primary responsibility is integrating and managing security practices within CI/CD pipelines. I work with tools such as Fortify for SAST/DAST, Sonatype Lifecycle for SCA, Sonatype SBOM Manager, Trivy for container scanning, SonarQube, and secret-scanning tools.

We use GitLab for source-code management and Jenkins for pipeline orchestration. I support security-tool onboarding, pipeline integration, scan execution, quality gates, vulnerability analysis, and remediation coordination with development teams.

I’m also involved in security-platform administration, access management through RBAC and SSO, reporting, and automation using Python and Shell scripting.

Previously, I worked at TCS on an e-governance project, where I gained experience with Jenkins, Docker, Kubernetes, AWS services, Terraform, Ansible, and monitoring tools such as Prometheus and Grafana.

My strongest areas are DevSecOps, CI/CD security integration, vulnerability management, and automation, and I’m looking to expand further into cloud and platform security engineering.

## Question 2

Question:

How many years of overall experience do you have, and how many years of experience do you have with Azure?

Answer:

I have around 4.5 years of overall IT experience, primarily in DevOps and DevSecOps engineering.

My experience is mainly across AWS and hybrid cloud environments, with exposure to Azure as well. In my current project, I work with cloud and on-premises infrastructure, including Azure-related environments, access controls, networking concepts, and security integrations.

My strongest hands-on cloud experience is with AWS, while I have practical exposure to Azure services and cloud-security concepts. I’m comfortable working in multi-cloud environments and adapting to the specific services and processes used by the organization.

## Question 3

Question:

Have you worked on Terraform, or is infrastructure provisioning handled by a separate team?

Answer:

I have worked with Terraform, mainly in infrastructure provisioning activities and supporting infrastructure automation.

In my previous project at TCS, I had exposure to Terraform for provisioning AWS resources, including VPC-related infrastructure and virtual machines.

However, infrastructure provisioning was not my only responsibility. Some of the more extensive infrastructure activities were handled in coordination with the dedicated cloud or infrastructure team.

My involvement included understanding Terraform configurations, reviewing resource definitions, working with variables and outputs, and supporting the provisioning workflow.

My primary focus has been DevOps and DevSecOps, but I understand how Terraform fits into infrastructure automation and how infrastructure changes are managed through Git-based workflows and CI/CD pipelines.

## Question 4

Question:

Which Terraform modules have you created or worked on?

Answer:

I have worked with Terraform configurations and reusable module structures, primarily around VPC and virtual machine provisioning.

For example, in AWS, the infrastructure configuration involved resources such as:

- VPC and subnets.
- Internet and NAT gateways.
- Route tables and associations.
- Security groups.
- EC2 instances and related networking components.

The idea behind using modules is to make infrastructure code reusable and consistent rather than defining the same resources repeatedly.

We can define inputs through variables, expose required values through outputs, and reuse the module across different environments by passing environment-specific configurations.

My experience is mainly with working on and understanding these module-based configurations rather than independently owning a large Terraform module framework in production.

## Question 5

Question:

How do you ensure that VPC/VNet, subnet, and VM resources are created in the correct dependency order when provisioning everything in a single Terraform apply?

Answer:

Terraform handles resource creation order through its dependency graph.

There are two main ways to define dependencies:

1. Implicit dependency: Terraform automatically identifies dependencies when one resource references another resource's attribute.
2. Explicit dependency: We use `depends_on` when a dependency exists but is not directly represented through a resource reference.

For example, when creating an EC2 instance, its network interface or instance configuration references the subnet ID. Terraform understands that the subnet must be created before the dependent resource.

Similarly, if a virtual machine depends on a network interface, Terraform creates the network interface first and then the VM.

For dependencies that Terraform cannot identify automatically, we can explicitly define `depends_on`.

Before applying the configuration, I use `terraform plan` to review the execution plan and verify the proposed changes and dependencies.

This helps ensure resources are provisioned in the correct order and reduces deployment failures caused by missing dependencies.

## Question 6

Question:

Have you developed CI/CD pipelines for infrastructure or application development? Which tools have you used?

Answer:

Yes. I have worked with CI/CD pipelines for application builds, security integration, and deployment workflows. I have also had exposure to infrastructure automation using Terraform.

In my current project, we primarily use GitLab for source-code management and Jenkins for CI/CD orchestration.

The general workflow is:

1. Developers push code to GitLab.
2. Jenkins checks out the source code.
3. The application is built and unit tests are executed.
4. Security scans are performed using tools such as Fortify, Sonatype, Trivy, and secret scanners, depending on the application and pipeline.
5. Quality and security gates evaluate the scan results.
6. Approved artifacts are published to Nexus.
7. The deployment process proceeds through the relevant environment.

For infrastructure automation, Terraform can be integrated into a pipeline to validate configurations, generate a plan, review changes, and apply approved infrastructure updates.

I have also worked with Docker, Kubernetes, AWS, and Ansible as part of the broader DevOps workflow.

My primary hands-on responsibility has been CI/CD security integration and pipeline support, while infrastructure provisioning and some deployment activities are coordinated with the respective teams.

## Question 7

Question:

Can you explain the infrastructure development pipeline end-to-end, including the type of application and the security steps involved?

Answer:

In our project, we support multiple application types, mainly microservices and traditional applications deployed on virtual machines.

For the application CI/CD workflow, the process starts when a developer pushes code to GitLab.

The pipeline is orchestrated through Jenkins and generally follows these stages:

1. Source checkout: Jenkins retrieves the source code from GitLab.
2. Build and testing: The application is compiled or packaged, and unit tests are executed.
3. Code quality: SonarQube performs static code-quality analysis.
4. SAST: Fortify scans the source code for security vulnerabilities.
5. SCA and SBOM: Sonatype Lifecycle analyzes open-source dependencies and identifies vulnerable components. SBOM information is generated and managed through the relevant SBOM tooling.
6. Secret scanning: Tools such as GitLeaks or other secret-scanning solutions identify exposed credentials and sensitive information.
7. Container scanning: For containerized applications, Trivy scans the container image for vulnerabilities and misconfigurations.
8. Quality gates: The pipeline evaluates the scan results against defined security and quality thresholds.
9. Artifact publishing: Approved build artifacts or container images are published to Nexus or the configured registry.
10. Deployment: The application is deployed to the relevant environment through the deployment workflow.

For Kubernetes-based applications, the container image is deployed through Kubernetes resources such as Deployments and Services, with Ingress or NGINX handling incoming application traffic.

For traditional applications, packaged JAR or WAR artifacts can be deployed to virtual machines.

From the infrastructure perspective, Terraform can be used to provision the required cloud resources, while Ansible can support configuration management and server setup.

My primary responsibility in this workflow is the security integration, scan execution, quality gates, vulnerability management, and coordination with development teams.

## Question 8

Question:

What is a quality gate, and what criteria do you consider when configuring it?

Answer:

A quality gate is a set of predefined conditions that an application or build must satisfy before it can proceed to the next stage of the CI/CD pipeline.

In DevSecOps, we use quality gates to ensure that security and code-quality requirements are met before an artifact is released.

Some important criteria include:

- SAST: No unaccepted critical or high-severity security vulnerabilities.
- SCA: No prohibited vulnerable open-source dependencies based on the organization's policy.
- Secret scanning: No exposed passwords, API keys, tokens, or private keys.
- Container scanning: No vulnerabilities above the configured severity threshold.
- Code quality: Compliance with agreed code-quality and test-coverage requirements.
- Build and testing: Successful build and required automated tests.

For example, if Fortify identifies a critical vulnerability or Sonatype reports a dependency that violates the organization's security policy, the pipeline can fail or block promotion.

The development team then investigates and remediates the finding. After the fix, the pipeline is executed again to verify that the issue is resolved.

In production environments, quality gates should be risk-based and aligned with security policies. We should also have a documented exception process for approved business cases, rather than bypassing security controls without review.

## Question 9

Question:

Have you worked with AKS or EKS? Can you explain the application deployment architecture?

Answer:

Yes. I have exposure to Kubernetes environments, including AWS EKS and Azure AKS, and have worked with Kubernetes-based application deployment workflows.

At a high level, the application is packaged as a Docker container image and pushed to a container registry.

The Kubernetes deployment process generally works as follows:

1. The container image is built and pushed to the configured registry.
2. Kubernetes Deployment manifests define the desired number of replicas and the container image.
3. The Kubernetes Deployment controller manages the ReplicaSets and Pods.
4. A Kubernetes Service provides stable internal connectivity to the application Pods.
5. Ingress or an NGINX Ingress Controller manages external HTTP/HTTPS access.
6. ConfigMaps and Secrets provide application configuration and sensitive values, with appropriate access controls.

For incoming traffic, the flow is generally:

DNS → Load Balancer → Ingress/NGINX → Kubernetes Service → Application Pod.

The application Pods communicate with databases or other microservices through the appropriate network paths.

From a security perspective, we need to consider RBAC, namespace isolation, network policies, secure container images, image vulnerability scanning, non-root containers, secrets management, and resource limits.

In my current project, I support the security and CI/CD aspects of these application workflows, including container image scanning and security checks. I work with the relevant teams for deployment and infrastructure activities.

## Question 10

Question:

What scanning stages do you include in a CI/CD pipeline after source-code checkout and build?

Answer:

After source-code checkout and build, we integrate multiple security and quality checks depending on the application type.

The main scanning stages are:

1. SAST – Static Application Security Testing: We use Fortify to identify security vulnerabilities in application source code without executing the application.
2. SCA – Software Composition Analysis: We use Sonatype Lifecycle to analyze third-party and open-source dependencies, identify vulnerable components, and evaluate policy violations.
3. SBOM generation: We generate a Software Bill of Materials to maintain visibility into the components and dependencies included in the application.
4. Secret scanning: Tools such as GitLeaks identify accidentally committed credentials, API keys, tokens, and other sensitive information.
5. Container image scanning: We use Trivy to identify vulnerabilities in container images, including operating-system packages and application dependencies.
6. DAST – Dynamic Application Security Testing: Where configured, tools such as Fortify WebInspect or OWASP ZAP test a running application for security vulnerabilities.
7. Code-quality analysis: SonarQube checks code quality, maintainability issues, and other configured quality metrics.

The scan results are evaluated against security policies and quality gates.

If a critical issue or a policy violation is identified, the pipeline can block the build or artifact promotion until the issue is remediated or an approved exception is granted.

The exact scanning stages depend on the application, technology stack, and security requirements.

## Question 11

Question:

How do you configure and execute Fortify SAST in a CI/CD pipeline? Explain the CLI or plugin integration, YAML configuration, prerequisites, and how scan results are generated and reviewed.

Answer:

Fortify SAST can be integrated into a CI/CD pipeline to perform static security analysis of application source code.

In our environment, we use Fortify as part of the Jenkins-based CI/CD workflow, with the integration orchestrated through shared pipeline logic.

At a high level, the process involves the following steps:

1. Prerequisites: We need access to the Fortify tools and server, the required application source code, appropriate scan configuration, and valid authentication or service-account permissions.
2. Source checkout: Jenkins checks out the application code from GitLab.
3. Build integration: The application is prepared for scanning. For compiled languages, the build process may need to be captured so Fortify can analyze the source and build information.
4. Translation and scanning: Fortify tools such as the ScanCentral SAST client or Fortify Static Code Analyzer are used to prepare and execute the scan, depending on the configured architecture.
5. Scan submission: The scan results are uploaded to Fortify Software Security Center, or SSC, for centralized management.
6. Results review: Security teams review vulnerabilities, severity, affected files, and remediation details through SSC.
7. Pipeline integration: The pipeline can use the scan status or configured security thresholds to determine whether the build should proceed.

For example, a Jenkins pipeline can invoke a shared library that handles the Fortify scan steps. In a YAML-based pipeline, the equivalent scan commands and configuration can be defined as pipeline stages, depending on the CI/CD platform.

A simplified conceptual workflow is:

```
Checkout Source Code
        |
Build / Prepare Source
        |
Fortify Translation
        |
Fortify SAST Scan
        |
Upload Results to SSC
        |
Review Vulnerabilities
        |
Apply Security Gate
```

The important production considerations are ensuring that the correct application version is scanned, scan credentials are securely managed, the required build settings are configured, and results are associated with the correct project and release in SSC.

We also need to manage false positives and approved vulnerability suppressions carefully, with appropriate justification and review.

In my current role, I work with Fortify integration and scan operations as part of the DevSecOps pipeline, including coordination around scan results, vulnerability triage, and remediation with development teams.

