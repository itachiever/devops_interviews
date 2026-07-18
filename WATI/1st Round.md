## Interview Questions:

1. **Let's start with a quick introduction. Are you working? State your expertise, current location, and job profile.**

2. **Do you have any experience with Snyk?**

3. **Can you explain what Policy as Code is?**

4. **What is the benefit of Policy as Code? When do we use it? Why do we need Policy as Code?**

5. **Let's say I am a developer, and you are managing my code repositories with Snyk, SAST, DAST, etc. If a High vulnerability is flagged, have you worked on security gating for such pipelines?**

6. **What is the logic? What is the main logic you use while creating security gating for any pipeline?**

7. **Let's say I don't want to spend extra hours fixing a vulnerability. I resist fixing it. How would you handle that situation through security gating?**

8. **When we focus too much on security and create very strict gates, developers may not like it because security is blocking their work. Have you worked on security gating? If yes, what was the main logic you used while designing those gates?**

9. **Have you worked on EKS? Can you explain how we can secure an EKS architecture?**

10. **Do you know anything about RBAC (Role-Based Access Control)?**

11. **How exactly do you manage RBAC? How do you implement it?**

12. **What about Secret Management?**

13. **Let's say we cannot use any third-party secret management tool because of budget constraints. What is the alternative approach?**

14. **Where are you working currently?**

15. **The position is in Bangalore. Are you okay with that?** *(Indirect location/relocation discussion)*

16. **What is your notice period?**

17. **How much is your current salary?**

18. **What are your salary expectations?**

19. **Do you have anything to ask me before I discuss internally with management and the CTO?**



### Core Technical Questions Asked

1. Tell me about yourself.
2. Experience with Snyk.
3. What is Policy as Code?
4. Why do we use Policy as Code?
5. Security Gating.
6. Logic behind Security Gating.
7. Managing developer resistance to security controls.
8. Balancing Security vs Developer Productivity.
9. EKS Security Architecture.
10. RBAC.
11. RBAC Implementation.
12. Secret Management.
13. Secret Management without third-party tools.


---

# Interview Answers


# 1. Tell me about yourself.

### Answer

"Thank you for the opportunity.

My name is YOUR NAME. I have over 4 years of experience in DevOps and DevSecOps. I started my career as a DevOps Engineer at PREVIOUS COMPANY, where I worked for around 2.5 years managing CI/CD pipelines, infrastructure automation, containerization, and cloud environments.

Currently, I am working as a DevSecOps Engineer at PRESENT COMPANY, supporting a fintech client that provides payment gateway solutions to banks. My responsibilities include integrating security controls into CI/CD pipelines, implementing SAST, SCA, container security, secret scanning, SBOM generation, vulnerability management, and ensuring compliance with PCI-DSS requirements.

My primary tools include Jenkins, GitLab, Kubernetes, Docker, Fortify, SonarQube, Snyk, Trivy, GitLeaks, Terraform, Ansible, and AWS."



# 2. Do you have experience with Snyk?

### Answer

"Yes, I have experience with Snyk.

I have used Snyk primarily for Software Composition Analysis (SCA), container image scanning, and infrastructure-as-code security scanning.

We integrated Snyk into CI/CD pipelines to automatically identify vulnerable open-source dependencies and container vulnerabilities. Based on organizational policies, critical and high-risk findings were either blocked through security gates or tracked through remediation workflows."



# 3. What is Policy as Code?

### Answer

"Policy as Code is the practice of defining security, compliance, and governance rules in code so that they can be automatically validated and enforced across systems and deployment pipelines.

Instead of manually reviewing configurations, policies are codified and executed automatically.

For example:

* Only approved container images can be deployed.
* Terraform resources must have encryption enabled.
* Kubernetes pods cannot run in privileged mode.

Common tools include OPA Gatekeeper, Kyverno, HashiCorp Sentinel, and AWS Organizations SCPs."



# 4. Why do we use Policy as Code?

### Answer

"We use Policy as Code to automate security and compliance enforcement consistently across environments.

Benefits include:

* Eliminates manual validation.
* Ensures consistent policy enforcement.
* Reduces human errors.
* Improves compliance adherence.
* Enables scalable governance.

It helps organizations implement security controls automatically during development, deployment, and runtime."



# 5. Have you worked on Security Gating?

### Answer

"Yes.

I have implemented security gates within CI/CD pipelines using tools such as Fortify, SonarQube, Snyk, Trivy, and GitLeaks.

Security gates automatically evaluate scan results and determine whether the build should proceed or fail based on predefined organizational security policies."



# 6. What logic do you use while creating Security Gates?

### Answer

"The primary logic is risk-based decision making.

I evaluate:

* Vulnerability severity.
* Exploitability.
* Business impact.
* Availability of fixes.
* Regulatory requirements.

Typically:

* Critical vulnerabilities block deployments.
* High vulnerabilities may require remediation or exception approval.
* Medium and Low vulnerabilities are tracked through remediation SLAs.

The goal is to prevent significant security risks from reaching production while maintaining delivery velocity."



# 7. What if a developer resists fixing vulnerabilities?

### Answer

"Security should not become a bottleneck.

In such situations, I discuss the risk and explain the potential business impact.

If the issue is genuinely low risk, a formal risk acceptance process can be followed.

For high-risk vulnerabilities, we typically require remediation before deployment. For lower-risk findings, we may allow deployment with documented exceptions and defined remediation timelines."



# 8. How do you balance Security vs Developer Productivity?

### Answer

"My approach is to implement security progressively.

Initially, security tools operate in monitoring mode to establish baselines.

Once teams understand the findings and remediation process, enforcement is gradually introduced.

Typically:

* Secrets and Critical findings are blocked immediately.
* High findings may require approvals.
* Lower findings are tracked through SLAs.

This ensures security improves without negatively impacting delivery timelines."



# 9. How do you secure an EKS Architecture?

### Answer

"I secure EKS using a defense-in-depth approach.

Key controls include:

* IAM Roles for Service Accounts (IRSA)
* RBAC implementation
* Private worker nodes
* Network Policies
* Security Groups
* KMS encryption
* Secrets management
* Container image scanning
* Admission Controllers
* Audit logging
* Runtime monitoring

This ensures security across identity, networking, workloads, and data protection."



# 10. Do you know RBAC?

### Answer

"Yes.

RBAC stands for Role-Based Access Control.

It restricts access based on user roles and responsibilities.

Instead of granting permissions directly to users, permissions are assigned to roles, and users inherit permissions through role assignments."



# 11. How do you implement RBAC?

### Answer

"In Kubernetes, RBAC is implemented using:

* Roles
* ClusterRoles
* RoleBindings
* ClusterRoleBindings

Users authenticate through SSO or IAM integration and are granted only the permissions required for their responsibilities following the principle of least privilege."



# 12. What is Secret Management?

### Answer

"Secret Management is the secure storage, access, rotation, and monitoring of sensitive information such as:

* Passwords
* API keys
* Tokens
* Certificates
* Database credentials

The goal is to prevent exposure while ensuring authorized applications can securely retrieve required secrets."



# 13. How do you manage secrets without third-party tools?

### Answer

"If dedicated secret management tools are unavailable, I would use native platform capabilities.

Examples include:

* Jenkins encrypted credentials
* Kubernetes Secrets
* AWS IAM Roles
* Environment variable injection
* Encryption at rest
* RBAC restrictions
* Secret rotation policies

Additionally, secret scanning tools like GitLeaks can be integrated to prevent accidental credential exposure."



# 14. Where are you working currently?

### Answer

"Currently, I am working as a DevSecOps Engineer at PRESENT COMPANY in Mumbai, supporting a fintech client in the payment gateway domain."



# 15. Are you comfortable relocating to Bangalore?

### Answer

"Yes.

I previously worked in Bangalore during my tenure with LAST COMPANY and am comfortable relocating if required."



# 16. What is your Notice Period?

### Answer

"My official notice period is 90 days. However, based on previous discussions and organizational practices, early release may be possible depending on project transition requirements."



# 17. What is your Current Salary?

### Answer

"My current CTC is MENTION CURRENT CTC in LPA."



# 18. What are your Salary Expectations?

### Answer

"Based on my experience in DevOps, DevSecOps, cloud security, CI/CD security, Kubernetes security, and compliance-related implementations, I am expecting around EXPECTED CTC in LPA. However, I am open to discussing the overall compensation structure."



# 19. Do you have any questions for us?

### Answer

"Yes, I have a few questions.

1. Could you share more about the current DevSecOps maturity within the organization?
2. What are the primary security challenges the team is currently addressing?
3. How is the DevSecOps team structured, and what would be the key expectations for this role during the first six months?
4. What security tools and cloud platforms are currently being used?"

These questions demonstrate genuine interest in the role and a long-term mindset.

