# Interview Questions: 3rd Round (1st Client Round)

### 1. Give a brief introduction about yourself and explain your current project.



### 2. Explain your complete CI/CD pipeline and deployment workflow integrated with Jenkins and GitLab.



### 3. Which cloud platform are you more confident in—AWS or Azure?



### 4. What is your Kubernetes experience? Which areas have you worked on?



### 5. Why did you configure a secure VPN tunnel between on-premises infrastructure and Azure AKS?



### 6. How do you establish a Site-to-Site VPN connection between an on-premises network and Azure? Explain the configuration steps.



### 7. Which VPN tunneling mechanism did you use (Full Tunnel vs Split Tunnel)? Did you configure it yourself?



### 8. What is the difference between SAST and DAST?



### 9. How do you handle vulnerable package/library updates? How do you report them to developers and ensure remediation?



### 10. Assume a Microsoft account is compromised and login attempts are coming continuously from Europe while the actual user is in India. As a Security Engineer, how would you handle this incident?

*(Follow-up discussion included password reset, MFA, firewall policies, IP restrictions, and Geo-location restrictions.)*



### 11. What is the Kubernetes Control Plane?



### 12. What is etcd in Kubernetes?



### 13. Have you worked with Kong Ingress Controller?



### 14. How do you collect Azure audit logs and security logs from Azure resources into Microsoft Sentinel?

*(Expected discussion included Diagnostic Settings, Log Analytics Workspace, and Microsoft Sentinel.)*



### 15. Have you set up an open-source Kubernetes monitoring stack yourself? Explain your experience.



### 16. Where have you implemented Quality Gates? Have you configured Quality Gates or security policies at the GitHub repository level?



### 17. What is GitHub Advanced Security? Which security features are available?



### 18. How would you integrate SonarQube analysis into GitHub Pull Requests?



### 19. What are the best practices for designing reusable Terraform modules?



### 20. How do you version Terraform modules?



### 21. How do you safely release a new version of a Terraform module that contains breaking changes?



### 22. How do you deprecate older Terraform modules without affecting existing consumers?



### 23. Have you implemented Terraform security policies? Which IaC security scanning tools have you used?



### 24. Explain how you integrated security tools like Fortify, SonarQube, Trivy, Sonatype, etc., into Jenkins CI/CD pipelines.



### 25. What is the difference between `count` and `for_each` in Terraform?



### 26. How do you securely manage secrets in Terraform?



### 27. Which Terraform modules have you created? Give examples.



### 28. What variable types are available in Terraform?



### 29. Explain the standard Terraform project/file structure.



### 30. Which Terraform variable type is used for key-value data?



### 31. How have you used Python for automation? Give real project examples.



### 32. When calling REST APIs using Python, which library did you use? Which HTTP status codes are commonly returned?



### 33. How do you manage Terraform state files?



### 34. What happens if the Terraform state file is accidentally deleted?



### 35. How do you organize Terraform code for multiple environments? Explain your Git branching strategy.



### 36. What GitHub security policies or branch protection rules have you implemented?



### 37. What is GitHub Branch Protection? Why is it important?



### 38. Have you worked with JFrog Artifactory?



### 39. Are you currently working? What is your notice period? Are you willing to relocate to Hyderabad?



## This interview was **heavily focused on:**

* Terraform (≈40% of the interview)
* Azure (VPN, Sentinel, Monitoring)
* Kubernetes
* DevSecOps Security
* Jenkins CI/CD
* GitHub Security
* Python Automation
* Terraform State & Module Management
* Basic HR (Notice Period & Relocation)

Several questions included follow-ups, but I've consolidated them into their main question to avoid duplication.


----

# Answers:




# 1. Give a brief introduction about yourself and explain your current project.

### Answer:

Hi, I'm **NAME**, a **DevSecOps Engineer with around 4 years of experience** in DevOps and DevSecOps.

I started my career at **PREVIOUS COMPANY NAME** as a DevOps Engineer, where I worked on CI/CD automation, infrastructure provisioning, and deployment activities. Later, I transitioned into **DevSecOps**, focusing on integrating security into the Software Development Lifecycle.

Currently, I'm working with **CURRENT COMPANY NAME** for a fintech client called **CLIENT NAME**, which provides payment gateway solutions to banking clients like SBI.

My primary responsibilities include:

* Designing and maintaining secure **Jenkins CI/CD pipelines**
* Integrating **Fortify (SAST)**, **Sonatype IQ (SCA & SBOM)**, **Trivy (Container Scanning)**, and secret scanning into the pipeline
* Managing artifact repositories using **Nexus**
* Supporting deployments on **VMs and Kubernetes**
* Performing Infrastructure as Code security scanning
* Working with **AWS and Azure** environments
* Implementing security controls to comply with **PCI-DSS** requirements
* Supporting monitoring using **Prometheus and Grafana**

Overall, my focus has been to automate software delivery while embedding security checks throughout the CI/CD pipeline.



# 2. Explain your complete CI/CD pipeline and deployment workflow integrated with Jenkins and GitLab.

### Answer:

Our CI/CD workflow follows these stages:

1. Developers commit code to **GitLab**.
2. A **GitLab Webhook** automatically triggers the Jenkins pipeline.
3. Jenkins checks out the latest source code.
4. The application is built using the appropriate build tool such as **Maven, Gradle, npm, or Python**.
5. **Fortify SAST** scans the source code for security vulnerabilities.
6. **Sonatype IQ** performs Software Composition Analysis (SCA) and generates an SBOM.
7. If any critical or high vulnerabilities are detected, the pipeline fails based on configured quality gates.
8. Successful artifacts are uploaded to **Nexus Repository**.
9. Docker images are built and pushed to the container registry.
10. **Trivy** scans the container images for OS and package vulnerabilities.
11. After all security gates pass, deployment is performed using **Helm charts** to Kubernetes or through VM deployment pipelines.
12. Once deployed, application health and infrastructure are monitored using **Prometheus and Grafana**.

This approach ensures that security validation happens before deployment into production.



# 3. Which cloud platform are you more confident in—AWS or Azure?

### Answer:

I have worked in a **hybrid cloud environment**, using both AWS and Azure.

If I compare both, I'm slightly more confident in **AWS**, where I've worked with services such as:

* EC2
* S3
* IAM
* VPC
* Security Groups
* CloudWatch
* EKS

On Azure, I've worked with:

* AKS
* Azure Virtual Networks
* Azure VPN Gateway
* Azure Monitor
* Log Analytics Workspace
* Key Vault

Overall, I'm comfortable working with both cloud platforms depending on project requirements.



# 4. What is your Kubernetes experience? Which areas have you worked on?

### Answer:

My experience with Kubernetes includes both deployment and security activities.

I have worked on:

* Deploying applications using **Helm charts**
* Managing Deployments, Services, ConfigMaps, and Secrets
* Working with Ingress Controllers
* Understanding Namespaces and RBAC
* Supporting AKS and Kubernetes-based deployments
* Troubleshooting Pods and Deployments
* Performing container image scanning using Trivy
* Following Kubernetes security best practices
* Monitoring Kubernetes clusters using Prometheus and Grafana

While a dedicated Kubernetes platform team managed the cluster infrastructure, I was responsible for deployment, security integration, and troubleshooting activities.



# 5. Why did you configure a secure VPN tunnel between on-premises infrastructure and Azure AKS?

### Answer:

The primary purpose was to establish a **secure private communication channel** between our on-premises DevSecOps infrastructure and Azure.

Our Jenkins server, GitLab, databases, and several security tools were hosted on-premises, while applications were deployed on Azure AKS.

The VPN tunnel allowed:

* Secure communication between Jenkins and AKS
* Secure deployment from on-premises CI/CD pipelines
* Secure access to Azure resources
* Protection of sensitive traffic over public networks
* Compliance with organizational security requirements

It eliminated the need to expose internal systems over the internet.



# 6. How do you establish a Site-to-Site VPN connection between an on-premises network and Azure? Explain the configuration steps.

### Answer:

The typical process is:

1. Create an **Azure Virtual Network (VNet)**.
2. Create the required application subnets.
3. Create a dedicated **GatewaySubnet**.
4. Deploy an **Azure Virtual Network Gateway** with VPN type as **Route-Based**.
5. Assign a Public IP to the VPN Gateway.
6. Create a **Local Network Gateway**, representing the on-premises network.
7. Configure the on-premises public IP address and local address space.
8. Create a **Site-to-Site VPN Connection** between both gateways.
9. Configure a shared key (Pre-Shared Key) on both sides.
10. Ensure that on-premises and Azure CIDR ranges do not overlap.
11. Validate routing and connectivity.

This establishes secure encrypted communication between the two environments.



# 7. Which VPN tunneling mechanism did you use (Full Tunnel vs Split Tunnel)? Did you configure it yourself?

### Answer:

I was aware of the VPN architecture and how it was used in our environment, but the actual VPN configuration was handled by the Networking team.

My responsibility was mainly integrating the DevSecOps platform with the cloud environment.

I understand the concepts:

* **Full Tunnel:** All traffic passes through the VPN.
* **Split Tunnel:** Only traffic destined for specific networks passes through the VPN, while internet traffic goes directly.

Our networking team managed the production VPN configuration.



# 8. What is the difference between SAST and DAST?

### Answer:

| SAST                                                                 | DAST                                                                                                  |
| -- | -- |
| Static Application Security Testing                                  | Dynamic Application Security Testing                                                                  |
| Scans source code without executing the application                  | Scans a running application                                                                           |
| Performed during development                                         | Performed after deployment                                                                            |
| Finds coding issues like SQL Injection, Hardcoded Secrets, XSS, etc. | Finds runtime issues like Authentication flaws, Session issues, Security headers, API vulnerabilities |
| White-box testing                                                    | Black-box testing                                                                                     |

We use **Fortify** for SAST, while DAST is typically performed using tools like OWASP ZAP against deployed applications.



# 9. How do you handle vulnerable package/library updates? How do you report them to developers and ensure remediation?

### Answer:

We use **Sonatype IQ Server** for Software Composition Analysis.

The process is:

1. Sonatype scans application dependencies during the CI/CD pipeline.
2. Vulnerable packages are identified along with their CVEs.
3. The tool recommends safer package versions.
4. If vulnerabilities exceed the defined policy threshold, the pipeline fails.
5. Reports are generated in the Sonatype dashboard.
6. Developers access the reports through SSO.
7. Developers upgrade the affected packages.
8. The application is rebuilt and rescanned.
9. Once vulnerabilities are resolved, the pipeline proceeds.

This ensures vulnerable libraries are remediated before deployment.



# 10. Assume a Microsoft account is compromised and login attempts are continuously coming from Europe while the actual user is in India. As a Security Engineer, how would you handle this incident?

### Answer:

I would take the following steps:

1. Verify the suspicious login activity.
2. Immediately reset the user's password.
3. Revoke all active user sessions.
4. Force re-authentication.
5. Enable or verify Multi-Factor Authentication.
6. Review Azure AD sign-in logs.
7. Block suspicious sessions using Conditional Access policies.
8. Configure **Geo-location restrictions** to allow logins only from approved countries such as India.
9. Investigate whether credentials were leaked.
10. Monitor the account for further suspicious activity.

Using Azure Conditional Access with geo-location policies is one of the most effective ways to mitigate this type of attack.



# 11. What is the Kubernetes Control Plane?

### Answer:

The **Control Plane** is the management layer of a Kubernetes cluster.

It is responsible for:

* Managing the overall cluster state
* Scheduling Pods onto worker nodes
* Exposing the Kubernetes API
* Maintaining cluster configuration
* Monitoring cluster health
* Handling authentication and authorization

Major Control Plane components include:

* kube-apiserver
* etcd
* kube-scheduler
* kube-controller-manager
* cloud-controller-manager (cloud environments)



# 12. What is etcd in Kubernetes?

### Answer:

**etcd** is Kubernetes' distributed key-value database.

It stores all cluster information such as:

* Nodes
* Pods
* Services
* ConfigMaps
* Secrets
* Cluster configuration
* Desired state

Whenever changes are made to the cluster, they are stored in etcd.

Because it stores the entire cluster state, regular backups of etcd are critical.



# 13. Have you worked with Kong Ingress Controller?

### Answer:

I have not worked with **Kong Ingress Controller** in production.

However, I understand that it is an API Gateway and Kubernetes Ingress Controller used for:

* API routing
* Authentication
* Rate limiting
* SSL termination
* Load balancing
* Traffic management

In my projects, I primarily worked with **NGINX Ingress Controller**.



# 14. How do you collect Azure audit logs and security logs from Azure resources into Microsoft Sentinel?

### Answer:

The standard approach is:

1. Enable **Diagnostic Settings** on Azure resources.
2. Select the required log categories such as Audit Logs, Activity Logs, or Security Logs.
3. Configure the destination as a **Log Analytics Workspace**.
4. Connect the Log Analytics Workspace to **Microsoft Sentinel**.
5. Sentinel collects, correlates, and analyzes the logs for threat detection and monitoring.

This enables centralized security monitoring across Azure resources.



# 15. Have you set up an open-source Kubernetes monitoring stack yourself? Explain your experience.

### Answer:

I have primarily worked with an existing monitoring stack rather than setting it up from scratch.

My responsibilities included:

* Monitoring application health using Prometheus and Grafana
* Creating dashboards
* Investigating alerts
* Troubleshooting application issues
* Monitoring Kubernetes resource utilization

I understand the setup process involving Prometheus, Grafana, Node Exporter, and kube-state-metrics, but my production experience has mainly been on the operational side.



# 16. Where have you implemented Quality Gates? Have you configured Quality Gates or security policies at the GitHub repository level?

### Answer:

Most of my Quality Gate implementation experience has been within the **Jenkins CI/CD pipeline**.

I configured quality gates for:

* Fortify SAST
* Sonatype IQ
* Trivy
* Secret Scanning

The pipeline automatically blocks deployments when vulnerabilities exceed the defined severity threshold.

At the Git repository level, I have experience with branch protection, pull request approvals, and integrating security scans as part of the CI/CD workflow.



# 17. What is GitHub Advanced Security? Which security features are available?

### Answer:

GitHub Advanced Security provides built-in security capabilities for repositories.

Major features include:

* Code Scanning
* Secret Scanning
* Dependabot Alerts
* Dependabot Security Updates
* Dependency Graph
* Security Overview
* Pull Request Security Checks

These features help identify vulnerabilities early during development.



# 18. How would you integrate SonarQube analysis into GitHub Pull Requests?

### Answer:

The integration process is:

1. Connect GitHub with SonarQube.
2. Configure SonarQube credentials in the CI/CD pipeline.
3. Trigger SonarQube analysis whenever a Pull Request is created.
4. SonarQube analyzes code quality and security.
5. Publish the Quality Gate result back to the Pull Request.
6. Configure branch protection rules so that PRs cannot be merged if the Quality Gate fails.

This ensures only quality-approved code is merged into the main branch.



# 19. What are the best practices for designing reusable Terraform modules?

### Answer:

Some key best practices are:

* Keep modules focused on a single responsibility.
* Parameterize values using input variables.
* Avoid hardcoding resource values.
* Use outputs for inter-module communication.
* Maintain a clear directory structure.
* Implement least-privilege IAM permissions.
* Validate variables where possible.
* Version modules properly.
* Document inputs, outputs, and usage examples.
* Ensure modules are reusable across environments.



# 20. How do you version Terraform modules?

### Answer:

We follow **Semantic Versioning (SemVer)** for Terraform modules:

* **MAJOR** version (e.g., v2.0.0): Breaking changes
* **MINOR** version (e.g., v1.2.0): New features without breaking compatibility
* **PATCH** version (e.g., v1.2.1): Bug fixes

The modules are stored in Git repositories and versioned using Git tags or release branches. Instead of modifying an existing stable module, we create a new version, validate it through testing, document the changes, and allow consuming teams to upgrade when they are ready. This minimizes disruption while maintaining backward compatibility wherever possible.




# 21. How do you deprecate an old Terraform module?

### Answer:

When deprecating a Terraform module, I follow a controlled process:

* First, identify which teams or projects are still consuming that module.
* Announce the deprecation well in advance with a recommended replacement module.
* Mark the module as deprecated in the documentation and README.
* Stop adding new features and provide only critical fixes.
* Publish migration guidelines for consumers.
* After all dependent teams migrate, archive or remove the old module following the organization's release policy.

This approach avoids breaking existing deployments while ensuring a smooth migration.



# 22. Have you used Terraform security policies (Sentinel/OPA)?

### Answer:

Personally, I haven't implemented **Sentinel or OPA policies** in production.

However, I have worked on securing Terraform code by integrating IaC security scanning tools such as:

* Trivy
* Checkov
* Snyk IaC

These tools scan Terraform files for:

* Misconfigured security groups
* Publicly exposed storage
* Open network ports
* Missing encryption
* IAM permission issues

The scans were integrated into Jenkins pipelines, and deployments were blocked if critical issues were found.



# 23. How did you integrate Fortify, SonarQube, Trivy and other security tools into Jenkins?

### Answer:

Our Jenkins pipeline included security scanning as mandatory stages.

The workflow was:

1. Developer commits code to GitLab.
2. Jenkins pipeline is triggered.
3. Build stage executes.
4. Fortify performs SAST scanning.
5. Sonatype IQ performs SCA and SBOM generation.
6. Trivy scans Docker images.
7. Secret scanning is performed.
8. Quality gates validate vulnerability thresholds.
9. If all scans pass, artifacts are uploaded to Nexus.
10. Deployment proceeds only after successful validation.

Developers receive scan reports directly from Jenkins, and detailed findings are available in each security tool's dashboard.



# 24. What is the difference between Terraform `count` and `for_each`?

### Answer:

**count**

* Creates resources based on an integer value.
* Resources are indexed numerically.
* Best suited when resources are identical.

Example:

```terraform
count = 3
```

Creates:

* VM[0]
* VM[1]
* VM[2]



**for_each**

* Creates resources from a map or set.
* Each resource has a meaningful key.
* Better when resources have different configurations.

Example:

```terraform
for_each = {
dev = "East US"
prod = "West US"
}
```

This creates separately named resources for dev and prod.

Generally, I prefer **for_each** because it's easier to manage and avoids unnecessary resource recreation.



# 25. How do you manage secrets in Terraform?

### Answer:

Secrets should never be hardcoded inside Terraform code.

In our environment:

* Jenkins credentials store was used for pipeline secrets.
* HashiCorp Vault was used for runtime secret retrieval.
* Sensitive values were stored as encrypted secrets.
* Terraform variables were marked as `sensitive`.
* Secrets were injected during runtime instead of storing them in Git.

This keeps credentials secure throughout the deployment process.



# 26. Which Terraform modules have you created?

### Answer:

I have worked on reusable modules for resources such as:

* Virtual Networks (VNet/VPC)
* Storage Accounts
* Security Groups
* IAM Roles
* AKS infrastructure
* Virtual Machines
* Resource Groups

Each module was parameterized using variables so it could be reused across multiple environments.



# 27. What variable types are available in Terraform?

### Answer:

Common Terraform variable types include:

* string
* number
* bool
* list
* map
* object
* tuple
* set

These are used depending on the type of configuration being passed into the module.



# 28. How do you structure Terraform code?

### Answer:

A typical Terraform project structure looks like this:

```
main.tf
variables.tf
outputs.tf
providers.tf
terraform.tfvars

modules/
   network/
   storage/
   aks/
```

Each reusable module also contains:

* main.tf
* variables.tf
* outputs.tf

This structure improves maintainability and reusability.



# 29. What is the key-value variable type in Terraform?

### Answer:

The key-value variable type is **map**.

Example:

```terraform
variable "tags" {
  type = map(string)
}
```

Example value:

```terraform
tags = {
Environment = "Prod"
Owner = "DevOps"
}
```

Maps are commonly used for tags and configuration settings.



# 30. Where do you specify variable values in Terraform?

### Answer:

Variable values are usually provided through:

* terraform.tfvars
* environment-specific `.tfvars` files
* command-line `-var`
* environment variables (`TF_VAR_*`)
* CI/CD pipeline variables

In our projects, environment-specific `.tfvars` files were primarily used.



# 31. Where have you used Python automation?

### Answer:

I have used Python primarily for automation tasks such as:

* Database backup automation
* Calling REST APIs
* Parsing security scan reports
* Generating vulnerability summaries
* Automating repetitive DevSecOps tasks
* File and log processing

Python helped reduce manual effort and improve operational efficiency.



# 32. Which Python library do you use for REST API calls?

### Answer:

The most common library is **requests**.

Typical workflow:

* Send GET/POST requests
* Pass authentication headers or tokens
* Receive JSON responses
* Parse response data
* Handle exceptions and HTTP status codes



# 33. Which HTTP status codes are commonly used?

### Answer:

Some commonly used HTTP status codes are:

* 200 — Success
* 201 — Resource Created
* 400 — Bad Request
* 401 — Unauthorized
* 403 — Forbidden
* 404 — Not Found
* 500 — Internal Server Error
* 502 — Bad Gateway
* 503 — Service Unavailable



# 34. How do you manage Terraform state files?

### Answer:

We stored Terraform state remotely using:

* AWS S3 as the backend
* DynamoDB for state locking

Benefits include:

* Shared state for teams
* Prevents simultaneous modifications
* Versioning support
* Recovery from accidental changes

This is the recommended approach for production environments.



# 35. What happens if the Terraform state file gets deleted?

### Answer:

If the state file is deleted, Terraform loses track of existing infrastructure.

As a result:

* `terraform plan` assumes the resources don't exist.
* It attempts to recreate them.
* During `terraform apply`, duplicate resource errors may occur because the infrastructure already exists.

Recovery typically involves:

* Restoring the state from S3 versioning or backup.
* Or importing existing resources using `terraform import`.

Deleting the state file should always be avoided.



# 36. What branching strategy do you follow?

### Answer:

We followed an environment-based Git branching strategy.

Typical branches included:

* feature/*
* develop
* UAT
* release
* main

Developers worked on feature branches, raised pull requests, and after approvals the code was promoted through higher environments until production.



# 37. What GitHub security policies have you used?

### Answer:

Some GitHub security best practices include:

* Pull Request approvals
* Branch protection rules
* Required status checks
* Secret scanning
* Code scanning
* Dependabot alerts
* Least privilege access
* MFA for users
* SSO integration

In our projects, these controls helped secure source code and prevent unauthorized changes.



# 38. What is Branch Protection in GitHub?

### Answer:

Branch Protection prevents direct changes to important branches such as `main`.

Typical rules include:

* No direct push to main
* Mandatory Pull Requests
* Required reviewer approvals
* Successful CI/CD checks before merge
* Passing security scans
* Restrict force push
* Restrict branch deletion

This ensures only validated code reaches production.



# 39. Have you worked with JFrog?

### Answer:

Yes, I have exposure to JFrog Artifactory.

Although our primary artifact repository was **Nexus**, the overall concepts are very similar.

Both are used for:

* Artifact storage
* Version management
* Docker image repositories
* Maven/npm repositories
* CI/CD integration
* Secure artifact distribution

So I can quickly adapt to JFrog environments because the workflow is largely the same.
