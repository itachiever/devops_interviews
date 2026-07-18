## Interview Questions: 2nd Round

1. Could you please walk me through your resume and overall experience?
2. Explain your end-to-end Jenkins CI/CD pipeline, including where each security scan runs and which scans block the build.
3. What is the difference between **SAST, DAST, SCA, and SBOM**, and why do we need all of them instead of just one?
4. Which **secret detection** and **secret management** tools have you worked with?
5. If GitLeaks detects an **AWS Access Key** that has already been committed and pushed to the repository, what actions will you take?
6. How does **Azure Key Vault** integrate with **AKS** at runtime?
7. How do you **harden a Docker image**?
8. Explain **Kubernetes RBAC** and how it is implemented.
9. Before using **RBAC/IAM Roles**, applications used AWS Access Key and Secret Key. After implementing IAM Roles, why are access keys no longer required?
10. Explain **Network Policies, Ingress, Egress, and Security Groups**.
11. How do you keep the **Terraform state file secure**?
12. How do you scan **Terraform code for misconfigurations before applying** the infrastructure changes?
13. If production is breached due to a **vulnerable dependency**, how would you handle the incident?
14. What is the difference between **Authentication and Authorization**?
15. What are the **security trade-offs of TLS termination at a Load Balancer**? 

---

# Answers





# 1. Could you please walk me through your resume and overall experience?

### Answer

My name is **YOUR NAME**, and I have **4.5 years of IT experience**, with over **2 years of experience in DevSecOps**.

Currently, I am working as a **DevSecOps Engineer** at **CURRENT COMPANY NAME**, where I am deployed to the client **CLIENT NAME**, a fintech payment gateway service provider.

My primary responsibility is securing the Software Development Life Cycle by integrating security controls throughout the CI/CD pipeline. I work with tools such as **Fortify SAST/DAST, Sonatype IQ Server for SCA and SBOM, GitLeaks for secret scanning, Trivy for container image scanning, Docker, Kubernetes, Jenkins, GitLab, Nexus, AWS, Azure, and Terraform**.

Our environment includes both **containerized applications running on Kubernetes** and **traditional VM-based deployments**. Since we operate in the payment domain, we follow **PCI DSS**, **RBI**, and internal security compliance standards.

Recently, I received the **Employee of the Quarter** award for standardizing and strengthening DevSecOps security practices across multiple projects.



# 2. Explain your end-to-end Jenkins CI/CD pipeline, including where each security scan runs and which scans block the build.

### Answer

Our CI/CD pipeline is orchestrated using **Jenkins**, while **GitLab** is used as the source code repository.

The pipeline flow is:

1. Developers commit code and raise a Pull Request in GitLab.
2. **GitLeaks** performs secret scanning during the Pull Request stage to detect hardcoded credentials.
3. After approval, Jenkins automatically triggers the pipeline.
4. The application is compiled and built using the appropriate build tool.
5. **Fortify SAST** scans the source code for security vulnerabilities.
6. **Sonatype IQ Server** performs **Software Composition Analysis (SCA)** and generates the **SBOM** by identifying vulnerable third-party dependencies.
7. If quality gates or security thresholds are violated, the pipeline is blocked.
8. Docker images are built.
9. **Trivy** scans the container images for operating system and package vulnerabilities.
10. If all scans pass successfully, artifacts are pushed to **Nexus Repository Manager**.
11. The application is deployed to Kubernetes using Helm.
12. After deployment, monitoring and validation are performed.

The scans that typically block the pipeline include:

* GitLeaks (hardcoded secrets)
* Fortify SAST (critical vulnerabilities)
* Sonatype IQ Server (policy violations)
* Trivy (critical container vulnerabilities)

This ensures security is enforced throughout the CI/CD pipeline using a shift-left DevSecOps approach.



# 3. What is the difference between SAST, DAST, SCA, and SBOM, and why do we need all of them instead of just one?

### Answer

Each security scan addresses a different area of application security.

**SAST (Static Application Security Testing)**

* Scans the application source code without executing it.
* Detects coding vulnerabilities such as SQL Injection, XSS, hardcoded credentials, and insecure coding practices.
* Performed during the build phase.

**DAST (Dynamic Application Security Testing)**

* Scans a running application.
* Identifies runtime vulnerabilities such as authentication issues, session management flaws, security misconfigurations, and exposed APIs.
* Performed after deployment to a test or staging environment.

**SCA (Software Composition Analysis)**

* Scans third-party and open-source libraries.
* Detects known vulnerabilities in dependencies.
* Suggests secure versions for remediation.

**SBOM (Software Bill of Materials)**

* Generates an inventory of all software components, libraries, versions, and licenses used in the application.
* Improves visibility, compliance, and vulnerability management.

### Why do we need all four?

Because each addresses a different security layer:

* **SAST** secures our source code.
* **SCA** secures third-party dependencies.
* **SBOM** provides complete component visibility and traceability.
* **DAST** validates the application's runtime security.

Using all of them together provides comprehensive application security coverage throughout the SDLC.



# 4. Which secret detection and secret management tools have you worked with?

### Answer

For **secret detection**, I have worked with:

* GitLeaks
* GitGuardian

These tools detect hardcoded credentials such as:

* API Keys
* AWS Access Keys
* Passwords
* Tokens
* Private Keys

For **secret management**, we primarily use:

* HashiCorp Vault

Sensitive information such as database credentials, API keys, certificates, and tokens are securely stored in Vault instead of being hardcoded into source code or configuration files.

Applications retrieve secrets securely at runtime, reducing the risk of credential exposure.



# 5. If GitLeaks detects an AWS Access Key that has already been committed and pushed to the repository, what actions will you take?

### Answer

If an AWS Access Key has already been committed and pushed, I would immediately follow the incident response process:

1. Confirm the exposed credential and assess its impact.
2. Immediately **rotate or revoke the compromised AWS Access Key** using IAM.
3. Replace the application with the newly generated credentials or migrate to IAM Roles if applicable.
4. Inform the development and security teams.
5. Remove the exposed secret from the source code and update the repository.
6. If required, clean the Git history using approved procedures.
7. Re-run GitLeaks to verify that no secrets remain.
8. Prevent the deployment until the issue is fully remediated.
9. Review AWS CloudTrail logs to identify whether the exposed key was misused.
10. Strengthen preventive controls such as mandatory GitLeaks scanning and developer awareness.

This approach ensures both immediate containment and long-term prevention of similar incidents.






# 6. How does Azure Key Vault integrate with AKS at runtime?

### Answer

Azure Key Vault integrates with AKS using the **Secrets Store CSI Driver** along with **Managed Identity** or **Workload Identity**.

The process is as follows:

1. Secrets such as passwords, certificates, and API keys are stored in Azure Key Vault.
2. AKS is configured with a Managed Identity or Workload Identity.
3. The identity is granted permission to access secrets in Azure Key Vault.
4. A **SecretProviderClass** is created in Kubernetes to define which secrets should be retrieved.
5. When the pod starts, the CSI Driver securely fetches the required secrets from Azure Key Vault.
6. The secrets are mounted into the pod as files or synchronized as Kubernetes Secrets.
7. If secrets are rotated in Key Vault, the application can consume the updated values without hardcoding credentials.

This approach eliminates hardcoded secrets and provides centralized, secure secret management.



# 7. How do you harden a Docker image?

### Answer

I follow several best practices to harden Docker images:

* Use **minimal base images** such as Alpine or Distroless wherever applicable.
* Use only trusted and verified base images from official repositories.
* Remove unnecessary packages and tools.
* Run containers as a **non-root user**.
* Avoid embedding secrets or credentials inside the image.
* Scan images using **Trivy** before deployment.
* Keep base images updated with the latest security patches.
* Use multi-stage builds to reduce image size.
* Set file and directory permissions appropriately.
* Store application configuration externally using Kubernetes Secrets or ConfigMaps.
* Regularly rebuild images to include security updates.

These practices reduce the attack surface and improve container security.



# 8. Explain Kubernetes RBAC and how it is implemented.

### Answer

**RBAC (Role-Based Access Control)** is Kubernetes' authorization mechanism used to control access to cluster resources based on the principle of least privilege.

RBAC is implemented using four main components:

* **Role** – Defines permissions within a specific namespace.
* **ClusterRole** – Defines permissions across the entire cluster.
* **RoleBinding** – Assigns a Role to a user, group, or Service Account within a namespace.
* **ClusterRoleBinding** – Assigns a ClusterRole across the cluster.

The implementation process is:

1. Create a Role or ClusterRole with the required permissions.
2. Create a RoleBinding or ClusterRoleBinding.
3. Bind the permissions to a User, Group, or Service Account.
4. Kubernetes Authorizer validates every request against the assigned RBAC permissions.

This ensures users and applications receive only the permissions required to perform their tasks.



# 9. Before using RBAC/IAM Roles, applications used AWS Access Key and Secret Key. After implementing IAM Roles, why are access keys no longer required?

### Answer

Previously, applications authenticated to AWS using long-lived **Access Keys** and **Secret Keys**, which had to be stored securely and rotated periodically.

After implementing **IAM Roles**, static credentials are no longer required because:

* The workload assumes an IAM Role.
* AWS automatically provides **temporary security credentials**.
* Credentials are rotated automatically by AWS.
* Applications retrieve credentials dynamically instead of storing them.
* This significantly reduces the risk of credential leakage.

For Kubernetes on Amazon EKS, this is implemented using **IAM Roles for Service Accounts (IRSA)**, where a Kubernetes Service Account is associated with an IAM Role. Pods automatically obtain temporary credentials to access AWS services securely.

This approach improves security while simplifying credential management.



# 10. Explain Network Policies, Ingress, Egress, and Security Groups.

### Answer

These components provide security at different layers of the networking stack.

### Network Policies

* Kubernetes resource used to control **pod-to-pod communication**.
* Defines both **Ingress** and **Egress** rules.
* Restricts traffic based on namespaces, pods, or IP blocks.
* Implements micro-segmentation within the cluster.

### Ingress

* Manages **incoming traffic** from external users to Kubernetes services.
* Uses an Ingress Controller such as **NGINX** or **AWS ALB Ingress Controller**.
* Supports host-based and path-based routing.
* Can terminate TLS for HTTPS traffic.

### Egress

* Controls **outbound traffic** from pods to external services.
* Restricts which external endpoints or networks pods can access.
* Helps prevent unauthorized external communication.

### Security Groups

* AWS virtual firewalls attached to EC2 instances or Elastic Network Interfaces (ENIs).
* Control inbound and outbound traffic at the infrastructure level.
* Allow only required ports and protocols.
* Provide an additional security layer beyond Kubernetes networking.

Together, Network Policies secure communication within the Kubernetes cluster, Ingress and Egress control application traffic, and Security Groups secure the underlying AWS infrastructure.




# 11. How do you keep the Terraform state file secure?

### Answer

Terraform state files often contain infrastructure metadata and may include sensitive information, so securing them is very important.

The best practices I follow are:

* Store the Terraform state remotely in an **Amazon S3 bucket**.
* Enable **server-side encryption (SSE-KMS)** for the S3 bucket.
* Restrict access using **IAM policies** based on the principle of least privilege.
* Enable **DynamoDB state locking** to prevent concurrent modifications.
* Enable **S3 versioning** to maintain state history and support recovery.
* Avoid storing secrets directly in Terraform code or state whenever possible.
* Use **AWS Secrets Manager** or **Azure Key Vault** for sensitive credentials.
* Limit access to the backend only to authorized DevOps engineers and CI/CD pipelines.
* Regularly back up and audit access to the state file.

These practices ensure that the Terraform state remains secure, available, and protected from unauthorized access or accidental corruption.



# 12. How do you scan Terraform code for misconfigurations before applying the infrastructure changes?

### Answer

Before provisioning infrastructure, I validate both the syntax and the security of the Terraform code.

The typical process is:

1. Run **`terraform fmt`** to standardize formatting.
2. Run **`terraform validate`** to verify the configuration syntax.
3. Run **`terraform plan`** to review the proposed infrastructure changes.
4. Scan the Terraform code using tools such as **Checkov** or **tfsec** to detect security misconfigurations.
5. Review the Pull Request before merging.
6. Execute the pipeline only after all validation and security checks pass.

The security scans identify issues such as:

* Publicly exposed resources
* Unencrypted storage
* Overly permissive IAM policies
* Open Security Groups
* Missing logging or encryption
* Non-compliance with security best practices

This helps prevent insecure infrastructure from being deployed into production.



# 13. If production is breached due to a vulnerable dependency, how would you handle the incident?

### Answer

If a production environment is compromised due to a vulnerable dependency, my priority is to contain the incident and restore the environment securely.

The steps I would follow are:

1. Immediately isolate the affected application or workload to prevent further impact.
2. Notify the security team and initiate the incident response process.
3. Analyze logs, monitoring data, and alerts to identify the vulnerable dependency and determine the scope of the impact.
4. Revoke or rotate any compromised credentials, secrets, or tokens if required.
5. Upgrade the vulnerable dependency to a secure version.
6. Rebuild the application and perform **SCA**, **SAST**, and container image scans to verify that the vulnerability has been remediated.
7. Deploy the patched application through the standard CI/CD pipeline.
8. Monitor the application closely after deployment.
9. Perform a Root Cause Analysis (RCA) and implement preventive measures to avoid similar incidents in the future.

This approach ensures proper containment, remediation, recovery, and continuous improvement.



# 14. What is the difference between Authentication and Authorization?

### Answer

**Authentication** is the process of verifying **who the user or system is**, while **Authorization** determines **what the authenticated user is allowed to access or perform**.

For example:

* A user logs into an application using a username, password, or Multi-Factor Authentication (MFA). This is **Authentication**.
* Once authenticated, the application determines whether the user can create, modify, or delete resources based on assigned permissions. This is **Authorization**.

In Kubernetes:

* Authentication verifies the identity using certificates, tokens, or IAM.
* Authorization uses **RBAC** to determine what actions the authenticated user or Service Account is permitted to perform.

In short:

* **Authentication = Who are you?**
* **Authorization = What are you allowed to do?**



# 15. What are the security trade-offs of TLS termination at a Load Balancer?

### Answer

TLS termination at a Load Balancer means that the encrypted HTTPS traffic is decrypted at the Load Balancer before being forwarded to the backend application.

### Advantages

* Offloads SSL/TLS processing from backend servers, improving application performance.
* Simplifies certificate management by maintaining certificates at a central location.
* Enables advanced routing, inspection, and load-balancing features.

### Security Trade-offs

* Traffic between the Load Balancer and backend servers may be unencrypted if TLS is not re-established.
* The Load Balancer becomes a trusted security boundary and must be properly secured.
* If the internal network is compromised, decrypted traffic could potentially be intercepted.

### Best Practices

* Implement **end-to-end encryption** by enabling TLS between the Load Balancer and backend services.
* Use strong TLS versions and secure cipher suites.
* Store certificates securely using services such as **AWS Certificate Manager (ACM)** or **Azure Key Vault**.
* Restrict access to backend services using Security Groups, Network Policies, and firewall rules.
* Regularly rotate and renew TLS certificates.

Using TLS termination with backend re-encryption provides the operational benefits of centralized certificate management while maintaining end-to-end security.


