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

### Question 1: Introduce yourself and explain your current roles and responsibilities.

Answer:

I’m a DevSecOps Engineer with around 4.5 years of experience in DevOps, CI/CD automation, cloud infrastructure, and application security.

Currently, I’m working with CURRENT COMPANY, deployed to In-Solutions Global, a fintech and payment gateway organization supporting banking clients.

My primary responsibility is integrating and managing security practices within CI/CD pipelines. I work with tools such as Fortify for SAST/DAST, Sonatype Lifecycle for SCA, Sonatype SBOM Manager, Trivy for container scanning, SonarQube, and secret-scanning tools.

We use GitLab for source-code management and Jenkins for pipeline orchestration. I support security-tool onboarding, pipeline integration, scan execution, quality gates, vulnerability analysis, and remediation coordination with development teams.

I’m also involved in security-platform administration, access management through RBAC and SSO, reporting, and automation using Python and Shell scripting.

Previously, I worked at TCS on an e-governance project, where I gained experience with Jenkins, Docker, Kubernetes, AWS services, Terraform, Ansible, and monitoring tools such as Prometheus and Grafana.

My strongest areas are DevSecOps, CI/CD security integration, vulnerability management, and automation, and I’m looking to expand further into cloud and platform security engineering.

### Question 2: How many years of overall experience do you have, and how many years of experience do you have with Azure?

Answer:

I have around 4.5 years of overall IT experience, primarily in DevOps and DevSecOps engineering.

My experience is mainly across AWS and hybrid cloud environments, with exposure to Azure as well. In my current project, I work with cloud and on-premises infrastructure, including Azure-related environments, access controls, networking concepts, and security integrations.

My strongest hands-on cloud experience is with AWS, while I have practical exposure to Azure services and cloud-security concepts. I’m comfortable working in multi-cloud environments and adapting to the specific services and processes used by the organization.

### Question 3: Have you worked on Terraform, or is infrastructure provisioning handled by a separate team?

Answer:

I have worked with Terraform, mainly in infrastructure provisioning activities and supporting infrastructure automation.

In my previous project at TCS, I had exposure to Terraform for provisioning AWS resources, including VPC-related infrastructure and virtual machines.

However, infrastructure provisioning was not my only responsibility. Some of the more extensive infrastructure activities were handled in coordination with the dedicated cloud or infrastructure team.

My involvement included understanding Terraform configurations, reviewing resource definitions, working with variables and outputs, and supporting the provisioning workflow.

My primary focus has been DevOps and DevSecOps, but I understand how Terraform fits into infrastructure automation and how infrastructure changes are managed through Git-based workflows and CI/CD pipelines.

### Question 4: Which Terraform modules have you created or worked on?

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

### Question 5: How do you ensure that VPC/VNet, subnet, and VM resources are created in the correct dependency order when provisioning everything in a single Terraform apply?

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

### Question 6: Have you developed CI/CD pipelines for infrastructure or application development? Which tools have you used?

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

### Question 7: Can you explain the infrastructure development pipeline end-to-end, including the type of application and the security steps involved?

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

### Question 8: What is a quality gate, and what criteria do you consider when configuring it?

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

### Question 9: Have you worked with AKS or EKS? Can you explain the application deployment architecture?

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

### Question 10: What scanning stages do you include in a CI/CD pipeline after source-code checkout and build?

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

### Question 11: How do you configure and execute Fortify SAST in a CI/CD pipeline? Explain the CLI or plugin integration, YAML configuration, prerequisites, and how scan results are generated and reviewed.

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


### Question 12: Have you worked with Azure Policies and Initiatives? Have you created custom policies or initiatives and assigned them at the Management Group or Subscription level?

Answer:

I have worked with Azure security and access-control concepts and have an understanding of Azure Policy and Initiatives.

Azure Policy helps organizations enforce governance and compliance requirements across their Azure resources. An initiative is a collection of multiple policy definitions grouped together to achieve a broader compliance objective.

For example, an organization can define policies to:

- Restrict resource deployment to approved Azure regions.
- Ensure storage accounts do not allow public access.
- Enforce encryption for supported resources.
- Require specific resource tags.
- Enable diagnostic logging.
- Restrict the creation of certain resource types.

Policies can be assigned at different scopes, such as a Management Group, Subscription, Resource Group, or individual resource, depending on governance requirements.

In an enterprise environment, centrally managed policies are commonly assigned at the Management Group level to maintain consistency across subscriptions.

My hands-on experience is stronger in DevSecOps security integration, access management, and security governance. I understand Azure Policy concepts and their role in enforcing cloud security standards, but I have not independently owned a large-scale custom policy framework.

### Question 13: Have you independently created and deployed a custom Azure Policy?

Answer:

I have an understanding of how custom Azure Policies are defined and deployed, but I haven't independently owned a custom policy implementation in production.

A custom Azure Policy is generally created using a JSON policy definition. It contains the policy rule, parameters, and effect that determine how Azure evaluates a resource.

For example, if an organization wants to prevent storage accounts from allowing public network access, we can create a policy that checks the `publicNetworkAccess` property.

The policy can use the Deny effect to prevent non-compliant resources from being created or updated.

The general implementation process is:

1. Define the policy rule and parameters.
2. Validate the JSON definition.
3. Create the policy definition.
4. Assign it at the required scope.
5. Start with Audit mode where appropriate to understand the impact.
6. Move to enforcement using Deny after validating the results.
7. Monitor compliance and handle existing non-compliant resources.

For existing resources, remediation may be required. Depending on the policy effect, Azure Policy can also support remediation through effects such as DeployIfNotExists and Modify.

### Question 14: Have you worked on remediating non-compliant Azure resources?

Answer:

I understand the process of identifying and remediating non-compliant Azure resources through Azure Policy and Defender for Cloud recommendations.

The first step is to identify the non-compliant resource and understand which policy or security recommendation it has violated.

For example, if a storage account is reported as non-compliant because public network access is enabled, I would:

1. Review the policy definition and the compliance result.
2. Identify the affected storage account and understand its business purpose.
3. Verify whether public access is actually required.
4. Coordinate with the application or infrastructure owner.
5. Disable public network access or restrict it through the appropriate firewall and private endpoint configuration.
6. Validate that the application continues to work.
7. Re-evaluate the resource and confirm that it is compliant.

I would also document the remediation and ensure that similar configurations are prevented in future deployments through policy enforcement and infrastructure-as-code controls.

My experience is primarily around security findings, access governance, and vulnerability remediation coordination, rather than independently managing Azure Policy remediation across an entire enterprise environment.

### Question 15: Have you executed an Azure remediation task? Can you explain the scenario and the steps involved?

Answer:

I understand how Azure remediation tasks work, particularly for resources identified as non-compliant through Azure Policy.

For example, consider a storage account that does not have the required diagnostic settings configured.

If the assigned policy uses the DeployIfNotExists effect, Azure can identify the non-compliant resource and support a remediation task to deploy the required diagnostic settings.

The general process is:

1. Identify the non-compliant resource from the Azure Policy compliance dashboard.
2. Review the policy definition and understand the required configuration.
3. Confirm that the policy assignment has the required managed identity and permissions.
4. Create a remediation task for the affected resources.
5. Azure uses the managed identity to apply the required configuration.
6. Monitor the remediation task status.
7. Re-evaluate compliance to confirm that the resource is compliant.

For policies using the Modify effect, remediation can similarly apply supported property changes to existing resources.

One important consideration is that remediation tasks do not automatically fix every type of policy violation. The policy must support remediation, and the required permissions and configuration must be in place.

### Question 16: Have you worked with firewalls? What is your experience, and who manages the firewall in your project?

Answer:

Yes, I have worked in environments where network security is implemented through firewalls, security groups, network security groups, and controlled network access.

In my current project, we have a hybrid architecture involving cloud and on-premises environments. Applications are hosted in private networks, and access is controlled through network security rules, VPN connectivity, load balancers, and DMZ-level reverse proxies.

For example, incoming application traffic typically passes through a load balancer and NGINX reverse proxy before reaching the application ingress and Kubernetes services.

At the network level:

- AWS Security Groups control inbound and outbound traffic at the resource or network-interface level.
- Azure NSGs control traffic based on source, destination, port, and protocol.
- Cloud firewalls provide centralized network traffic inspection and filtering.
- Network firewalls can control traffic between network segments and external networks.

Firewall infrastructure and rule management are generally handled by the dedicated network or infrastructure security teams in coordination with application owners.

My responsibility is to understand the required connectivity from an application and security perspective, coordinate access requirements, and ensure that unnecessary or overly permissive access is avoided. I don't claim to be the primary owner of enterprise firewall administration.

## Question 17

Question:

Have you worked with Microsoft Defender for Cloud? What are its main features and how is it used?

Answer:

I am familiar with Microsoft Defender for Cloud and its role in cloud security posture management and workload protection.

Defender for Cloud helps organizations assess the security posture of their Azure and supported multi-cloud environments.

Its main capabilities include:

1. Secure Score: Provides an overall indication of the security posture and highlights areas that need improvement.
2. Security Recommendations: Identifies misconfigurations and security weaknesses in cloud resources.
3. Regulatory Compliance: Helps assess resources against supported compliance standards.
4. Vulnerability Assessment: Helps identify vulnerabilities in supported workloads and resources.
5. Threat Protection: Detects suspicious activities and potential threats.
6. Security Alerts: Generates alerts that security teams can investigate and respond to.
7. Attack Path Analysis: Helps identify potential paths an attacker could use to compromise important resources.

For example, if Defender for Cloud identifies a virtual machine with an unnecessarily exposed management port, we can review the recommendation, validate the access requirement, and restrict the NSG rules.

We can also use Just-in-Time VM access, where supported, to reduce continuous exposure of management ports.

My experience is more aligned with DevSecOps security tools and vulnerability management, but I understand how Defender for Cloud complements those controls by providing visibility into cloud infrastructure security.

### Question 18: How do you prevent secrets such as API keys, passwords, and access tokens from being pushed to GitHub or GitLab repositories?

Answer:

We follow a combination of preventive and detective controls to prevent secrets from being committed to source-code repositories.

The main controls include:

1. Secret scanning: Integrate tools such as GitLeaks into the CI/CD pipeline to identify credentials and sensitive information.
2. Pre-commit hooks: Scan files before developers commit changes locally.
3. Push protection: Where supported, use repository-level push protection to block known secret patterns before they enter the repository.
4. Branch protection: Enable protected branches and mandatory merge-request approvals.
5. Access control: Apply least-privilege permissions to repositories and CI/CD variables.
6. Centralized secrets management: Store sensitive credentials in Azure Key Vault, AWS Secrets Manager, or another approved vault.
7. Regular scanning: Scan repository contents and, where required, Git history to identify previously committed secrets.

For example, if a developer accidentally commits an API token, the secret-scanning tool should detect it and block the pipeline or merge request based on the configured policy.

If a real secret is exposed, simply deleting it from the latest commit is not sufficient. We must revoke or rotate the credential, investigate its exposure, remove it from the repository history where appropriate, and store the replacement securely.

In my current project, I work with secret-scanning integration and security checks as part of the DevSecOps pipeline.

### Question 19: Have you configured tools such as GitLeaks, TruffleHog, or GitGuardian? At which stage do you integrate secret scanning into the CI/CD pipeline?

Answer:

Yes, I have exposure to secret-scanning tools and their integration into DevSecOps workflows, including GitLeaks and similar solutions.

Secret scanning can be implemented at multiple stages:

- Pre-commit stage: Detect secrets before developers commit code.
- Pull request or merge request stage: Scan changes before they are merged.
- CI/CD pipeline stage: Scan the checked-out repository during pipeline execution.
- Periodic repository scanning: Scan existing repositories and Git history for previously committed secrets.

For example, GitLeaks can be executed from a Jenkins pipeline using its CLI.

A simple command is:

```
gitleaks detect --source . --redact --exit-code 1
```

Here:

- `detect` runs the secret-detection scan.
- `--source .` specifies the current repository.
- `--redact` masks detected secret values in the output.
- `--exit-code 1` returns a failure code when secrets are detected.

In Jenkins, we can execute this command as a pipeline stage. If a secret is detected, the pipeline can be failed or blocked based on the configured security policy.

The exact integration depends on the tool and CI/CD platform. For example, GitGuardian also provides repository and CI/CD integrations.

If a secret is detected, we should validate the finding, revoke or rotate the credential, investigate potential exposure, and ensure the replacement is stored in an approved secrets-management solution.

### Question 20: How do you securely store account IDs, tenant IDs, credentials, and application configuration?

Answer:

First, I differentiate between non-sensitive configuration and sensitive information.

Values such as AWS account IDs, Azure tenant IDs, subscription IDs, application names, and environment names are identifiers. They are not necessarily secrets by themselves, although they should still be handled according to organizational security policies.

However, passwords, access keys, client secrets, private keys, certificates, and access tokens must always be protected.

For sensitive information, I prefer centralized secrets-management solutions such as:

- Azure Key Vault for Azure environments.
- AWS Secrets Manager for AWS environments.
- HashiCorp Vault for centralized secrets management across environments.

In CI/CD pipelines, we should retrieve secrets dynamically at runtime rather than hardcoding them in source code or pipeline files.

We should also follow these practices:

1. Use managed identities or IAM roles where possible instead of long-lived credentials.
2. Apply least-privilege access.
3. Restrict access to secrets based on application and environment.
4. Enable secret rotation and expiration where supported.
5. Avoid printing secrets in pipeline logs.
6. Enable auditing and monitoring of secret access.

For example, an application running in Azure can use a managed identity to retrieve a database password from Azure Key Vault without storing the credential directly in the application code.

### Question 21: How do you integrate AWS Secrets Manager, Azure Key Vault, or HashiCorp Vault with GitHub Actions or GitLab CI/CD?

Answer:

We can integrate secrets-management platforms with CI/CD pipelines using secure authentication mechanisms and runtime secret retrieval.

The preferred approach is to avoid storing long-lived credentials directly in pipeline variables wherever possible.

For example, in Azure, GitHub Actions or an Azure DevOps pipeline can authenticate using Workload Identity Federation, allowing the pipeline to obtain an identity-based token without maintaining a long-lived client secret.

Similarly, in AWS, GitHub Actions can use OIDC federation to assume an IAM role and retrieve secrets from AWS Secrets Manager.

The general workflow is:

1. Configure the CI/CD platform's identity with the cloud provider.
2. Establish a trusted relationship using OIDC or the supported authentication mechanism.
3. Assign the required permissions to access only the necessary secrets.
4. Authenticate during pipeline execution.
5. Retrieve the secret dynamically from the vault.
6. Pass it securely to the application or deployment process.
7. Ensure the secret is not exposed in logs or artifacts.

For HashiCorp Vault, we can use its authentication methods, such as JWT/OIDC or Kubernetes authentication, depending on the deployment environment.

For production environments, I would prefer short-lived credentials, least-privilege access, secret rotation, and audit logging.

The exact integration syntax depends on whether we are using GitHub Actions, GitLab CI, Jenkins, or Azure DevOps.

### Question 22: Have you worked with Microsoft Sentinel and Qualys? What are their purposes, and what is your level of experience with them?

Answer:

I am familiar with both tools and understand their roles in enterprise security operations, although my primary hands-on experience is with DevSecOps tools such as Fortify, Sonatype, Trivy, and SonarQube.

Microsoft Sentinel is a cloud-native SIEM and SOAR platform.

Its primary purpose is to collect and analyze security data from different sources, identify suspicious activities, generate security incidents, and support investigation and response.

Its major capabilities include:

- Log collection from cloud and on-premises sources.
- Analytics rules for threat detection.
- Incident creation and investigation.
- Threat intelligence integration.
- Workbooks and dashboards.
- Automation using playbooks.

For example, Sentinel can correlate multiple failed login attempts with unusual activity and generate an incident for the security team to investigate.

Qualys is a cloud-based security and vulnerability-management platform.

It helps organizations discover assets, identify vulnerabilities, assess security configurations, and prioritize remediation.

For example, a vulnerability scan can identify an outdated package or a known vulnerability on a virtual machine. The security team can then prioritize remediation based on severity and business risk.

My experience is primarily with application security scanning and vulnerability remediation workflows, but I understand how Sentinel and Qualys complement DevSecOps by extending security visibility into infrastructure monitoring and enterprise security operations.

### Question 23: If you deploy a virtual machine in an Azure VNet or AWS VPC, can you explain the ideal inbound traffic flow, including DNS, routing, network security, and firewalls?

Answer:

The inbound traffic flow depends on whether the application is publicly accessible or intended for private access. For a production application, I would prefer exposing it through a controlled entry point rather than directly exposing the virtual machine.

A typical public application architecture would look like:

User → DNS → WAF/Application Gateway or Load Balancer → Firewall/Network Controls → Private Subnet → Application VM → Database.

The main components are:

1. DNS: Resolves the application domain name to the appropriate public or private endpoint.
2. WAF/Application Gateway: For HTTP/HTTPS applications, a Web Application Firewall can inspect requests and help protect against common web attacks.
3. Load Balancer: Distributes incoming traffic across application instances.
4. Firewall: Applies centralized network-security rules and inspects traffic where required.
5. Route Tables: Determine the next hop for network traffic.
6. NSG/Security Groups: Restrict traffic based on source, destination, port, and protocol.
7. Private Subnet: Hosts application resources without direct public exposure.
8. Database Subnet: Keeps database resources private and allows only required application connectivity.

In Azure, we can use NSGs, Azure Firewall, Application Gateway, UDRs, and Private Endpoints depending on the architecture.

In AWS, equivalent services include Security Groups, Network ACLs, AWS Network Firewall, Application Load Balancer, route tables, and VPC endpoints.

For administrative access, I would prefer VPN, Azure Bastion, or AWS Systems Manager Session Manager rather than exposing RDP or SSH directly to the internet.

We should also enable TLS, logging, monitoring, and appropriate access controls.

The main objective is to follow defense in depth, minimize public exposure, and allow only the required traffic between network layers.

### Question 24: What are the different network layers or components used to control traffic, such as NSGs, Security Groups, Route Tables, UDRs, and Firewalls? Explain their differences.

Answer:

These components operate at different levels of network traffic control.

1\. Network Security Groups (NSGs) – Azure

NSGs control inbound and outbound traffic for Azure network interfaces and subnets.

They use rules based on source, destination, port, protocol, and priority.

For example, we can allow HTTPS traffic on port 443 from an approved source while denying unnecessary inbound access.

2\. Security Groups – AWS

AWS Security Groups act as virtual firewalls associated with network interfaces and supported resources.

They control inbound and outbound traffic and are stateful, meaning return traffic for an allowed connection is automatically permitted.

3\. Route Tables

Route tables determine where network traffic should be forwarded based on destination IP ranges.

For example, traffic destined for the internet may be routed through an Internet Gateway, NAT Gateway, or centralized firewall, depending on the architecture.

4\. User Defined Routes (UDRs) – Azure

UDRs allow us to customize Azure routing instead of relying only on system routes.

For example, we can configure a route that sends outbound traffic from a subnet through Azure Firewall for centralized inspection.

5\. Firewalls

Firewalls provide network traffic filtering and, depending on the product, additional inspection capabilities.

They can enforce centralized security policies between networks, subnets, and external destinations.

6\. Network ACLs – AWS

Network ACLs operate at the subnet level and are stateless. They can allow or deny inbound and outbound traffic using ordered rules.

The key difference is:

- NSGs and Security Groups control which traffic is allowed.
- Route Tables and UDRs determine where traffic goes.
- Firewalls provide centralized filtering and inspection.
- Network ACLs provide subnet-level stateless filtering in AWS.

In production, these controls work together. For example, an application subnet may have a route directing outbound traffic through a firewall, while an NSG or Security Group allows only the required application ports.

### Question 25: If an Azure Storage Account is configured as private but someone from an external network can still access its Blob Storage, what could be the possible reasons, and how would you troubleshoot the issue?

Answer:

First, I would verify what is meant by private because storage access can be controlled through multiple layers, including network configuration, authentication, authorization, and container-level permissions.

A storage account may still be accessible under certain conditions even when the intention is to restrict public access.

Some possible causes include:

1. Public Network Access: Public network access may still be enabled on the storage account.
2. Firewall Configuration: The storage firewall may allow all networks or include overly broad IP ranges.
3. Container Public Access: The Blob container may have anonymous public read access enabled, depending on the account configuration.
4. SAS Token Exposure: A Shared Access Signature token may have been leaked or configured with excessive permissions or validity.
5. Storage Account Keys: An account access key may have been exposed or compromised.
6. Excessive RBAC Permissions: A user, service principal, or managed identity may have been granted unnecessary data-plane permissions.
7. Application-Level Exposure: An application or API may be providing access to the storage account externally.
8. Private Endpoint or DNS Misconfiguration: Incorrect DNS resolution or network routing may cause traffic to use an unintended access path.

I would troubleshoot it systematically:

Step 1 – Verify network configuration

Check whether public network access is enabled and review the storage account firewall settings, allowed IP ranges, and virtual network rules.

Step 2 – Check Blob access configuration

Verify whether anonymous access is enabled at the storage-account level and whether individual containers have public access permissions.

Step 3 – Review authentication and authorization

Check Azure RBAC assignments, SAS tokens, storage account keys, and application identities to identify who can access the data and through which authentication method.

Step 4 – Review logs

Use Azure Monitor, diagnostic logs, and relevant activity records to investigate the access time, source IP, caller identity, operation, and authentication method.

Step 5 – Check Private Endpoint and DNS

Verify that the private endpoint is correctly configured, private DNS resolves the storage account to its private IP address, and the expected network path is being used.

Step 6 – Contain and remediate

If unauthorized access is confirmed, revoke exposed SAS tokens, rotate compromised storage account keys, remove unnecessary permissions, disable anonymous access, and restrict public network access where appropriate.

Step 7 – Validate

Retest access from both authorized and unauthorized networks to confirm that only approved identities and network paths can access the storage account.

Finally, I would document the root cause, preserve relevant logs, and implement preventive controls through Azure Policy and infrastructure-as-code validation.

The important point is that network restrictions and identity-based access controls must work together. A private endpoint alone does not replace proper authentication and authorization.
