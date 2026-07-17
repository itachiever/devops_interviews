# Interview Questions: 4th Round (Client(Deutsche Börse) 2nd Round)


### 1. Introduce yourself and explain your DevSecOps experience.

### 2. How many Jenkins pipelines are you currently responsible for?

* How many applications are onboarded?
* Are they CI pipelines or complete CI/CD pipelines?

### 3. Tell us about your current team structure.

* How many people are in your team?
* What technologies do you use?
* What environments do you manage?
* How are applications deployed?

### 4. What exactly is your role in the team?

* Do you build pipelines from scratch?
* Do you improve existing pipelines?
* Are you responsible for security integration?
* Are you more of an architect or an implementation engineer?

### 5. If you were asked to build a secure CI/CD pipeline from scratch, what are the mandatory components and security controls you would implement?

### 6. Why did your organization choose a Hybrid Cloud architecture (On-Prem + Cloud) instead of a fully cloud-native architecture?

### 7. What were the key business and security drivers behind selecting this hybrid architecture?

### 8. You mentioned using an NGINX Gateway in the DMZ. What security threats does this architecture mitigate?

### 9. Imagine developers complain that integrating SAST, SCA, and Secret Scanning introduces many false positives and significantly increases build time. How would you balance security with developer productivity and pipeline performance?

### 10. What ticketing or incident management tool are you currently using?

### 11. Suppose a major production/security incident occurs. Walk us through your complete incident handling process.

* Initial response
* Impact analysis
* Stakeholder communication
* Root Cause Analysis (RCA)
* Resolution
* Documentation
* Postmortem
* Preventive actions

### 12. Can you explain a real production incident that happened in your current company?

* What was the issue?
* How did you investigate it?
* What actions did you take?
* What was the final outcome?

### 13. Why didn't you consider parallel execution of security scans from the beginning?

### 14. Are you and your team responsible for the infrastructure, CI/CD pipelines, security scanners, and their configurations?

### 15. Since you have control over scanner configurations, how do you ensure PCI-DSS compliance while modifying or disabling certain scans?

* What can be bypassed?
* What cannot be bypassed?
* How do business exceptions work?

### 16. What security and compliance requirements must be implemented in a Source Code Repository like GitLab?

### 17. How would you technically implement those security controls in GitLab?

* RBAC
* MFA/SSO
* Branch Protection
* Merge Request approvals
* Quality Gates
* Secret Management
* Audit Logging
* Pipeline enforcement

### 18. Do you have any questions for us?

# Core Technical Areas They Evaluated

* DevSecOps Platform Engineering
* Secure CI/CD Pipeline Design
* Jenkins Pipeline Architecture
* Hybrid Cloud Architecture
* PCI-DSS Compliance
* Security Governance
* Secure SDLC
* SAST / SCA / Secret Scanning Integration
* NGINX DMZ Architecture
* GitLab Security Controls
* Incident Management
* Root Cause Analysis
* Security vs Developer Productivity Trade-offs
* Platform Ownership
* Architecture Decision Making

---

# Answers

# **1. Introduce yourself and explain your DevSecOps experience.**

### Answer:

Hello, I'm **YOUR NAME**. I have **4.5 years of IT experience**, primarily working as a **DevSecOps Engineer** in the fintech domain.

Currently, I work with **CURRENT COMPANY NAME** for the **CLINET NAME** client, which provides payment solutions to banking customers. Since the organization follows **PCI-DSS, RBI, and SEBI compliance**, security is integrated throughout the SDLC.

My responsibilities include designing and maintaining secure CI/CD pipelines using **Jenkins**, integrating security tools such as **OpenText Fortify SAST, WebInspect DAST, Sonatype IQ Server for SCA/SBOM, Trivy, and GitLeaks**, managing infrastructure using **Terraform**, containerized deployments on **Docker and Kubernetes**, and implementing monitoring with **Prometheus and Grafana**.

I also work on governance, quality gates, developer onboarding, pipeline optimization, vulnerability management, and security compliance. Recently, I received the **Employee of the Quarter** award for my contribution toward improving the organization's PCI-DSS compliance.



# **2. How many Jenkins pipelines are you currently responsible for? How many applications are onboarded? Are they CI or complete CI/CD pipelines?**

### Answer:

Our organization has **80+ applications**, out of which **around 50 applications are currently onboarded to Jenkins**. The onboarding is happening in phases as part of the DevSecOps maturity journey.

The pipelines are **end-to-end CI/CD pipelines**, including:

* Source code checkout
* Build
* Unit testing
* SAST
* SCA
* Secret scanning
* Artifact publishing
* Container image creation
* Image scanning
* Deployment
* Post-deployment validation

I was responsible for designing, enhancing, and maintaining these pipelines while integrating security controls and compliance requirements.



# **3. Tell us about your current team structure.**

### Answer:

Our DevSecOps team consists of **13 members**, including DevSecOps engineers, platform engineers, and security engineers.

We support **80+ enterprise applications** deployed across a **hybrid infrastructure** consisting of:

* On-premises servers
* AWS
* Azure
* Kubernetes clusters
* Traditional VM-based applications

Our primary technology stack includes:

* GitLab (Source Code Management)
* Jenkins (CI/CD)
* Nexus Repository
* Terraform
* Docker
* Kubernetes
* Fortify
* Sonatype IQ
* Prometheus
* Grafana

The team is responsible for DevSecOps platform engineering, pipeline management, security tool integration, governance, vulnerability management, and supporting development teams.



# **4. What exactly is your role in the team?**

### Answer:

My role is primarily a **DevSecOps Engineer** responsible for building and maintaining secure CI/CD platforms.

My responsibilities include:

* Designing Jenkins pipelines from scratch.
* Enhancing existing CI/CD pipelines.
* Integrating security tools into the SDLC.
* Implementing quality gates.
* Automating security scans.
* Managing Terraform-based infrastructure.
* Supporting Kubernetes deployments.
* Optimizing pipeline performance.
* Assisting development teams with secure onboarding.
* Ensuring PCI-DSS compliance across the DevSecOps platform.

Although architecture decisions are taken collaboratively, I actively contribute to platform design discussions and implementation.



# **5. If you were asked to build a secure CI/CD pipeline from scratch, what are the mandatory components and security controls you would implement?**

### Answer:

A secure CI/CD pipeline should include the following stages:

1. **Source Code Management**

   * GitLab/GitHub
   * RBAC
   * MFA/SSO
   * Branch protection
   * Pull request approvals

2. **Pipeline Orchestration**

   * Jenkins or GitLab CI

3. **Build Stage**

   * Maven, Gradle, npm, Python, etc.

4. **Static Application Security Testing (SAST)**

5. **Software Composition Analysis (SCA)**

6. **Secret Scanning**

7. **Quality Gates**

   * Block builds for Critical and High vulnerabilities.

8. **Artifact Management**

   * Nexus or Artifactory

9. **Container Image Build**

10. **Container Image Scanning**

11. **Infrastructure as Code Scanning**

12. **Deployment**

* Kubernetes or VM

13. **Post-deployment Validation**

14. **Monitoring and Logging**

15. **Audit Logging**

The pipeline should be fully automated, secure by default, and compliant with organizational governance policies.



# **6. Why did your organization choose a Hybrid Cloud architecture instead of a fully cloud-native architecture?**

### Answer:

The primary reason was **security and regulatory compliance**.

Since we work in the **payment domain**, we must comply with **PCI-DSS, RBI, and SEBI guidelines**.

Critical DevSecOps components such as:

* Jenkins
* Fortify
* Sonatype IQ
* Nexus
* Source code repositories

are hosted **on-premises** to maintain complete control over sensitive assets.

Application workloads and Kubernetes clusters are deployed on **AWS and Azure**, allowing us to leverage cloud scalability while keeping sensitive infrastructure within controlled environments.

This approach provides both security and operational flexibility.



# **7. What were the key business and security drivers behind selecting this hybrid architecture?**

### Answer:

The major drivers were:

* PCI-DSS compliance requirements.
* RBI and SEBI regulatory requirements.
* Better control over sensitive DevSecOps infrastructure.
* Secure storage of source code and security data.
* Reduced exposure of critical systems to the public internet.
* Stronger access controls.
* Easier audit readiness.
* Better governance over security tools.
* Improved risk management.
* Scalability by utilizing cloud resources for application deployments.

This architecture balances regulatory compliance with modern cloud capabilities.



# **8. You mentioned using an NGINX Gateway in the DMZ. What security threats does this architecture mitigate?**

### Answer:

The NGINX Gateway placed in the DMZ acts as a secure entry point between external users and internal applications.

It helps mitigate:

* Unauthorized direct access to backend services.
* Exposure of internal IP addresses.
* Malicious external traffic.
* Layer-7 attacks.
* SQL Injection.
* Cross-Site Scripting (XSS).
* Basic DDoS mitigation through traffic filtering and rate limiting.
* URL filtering.
* SSL/TLS termination.
* Reverse proxy security.
* Centralized request validation.

Overall, it improves security by ensuring backend services are never directly exposed to the internet.



# **9. Imagine developers complain that integrating SAST, SCA, and Secret Scanning introduces many false positives and significantly increases build time. How would you balance security with developer productivity?**

### Answer:

I would address both **pipeline performance** and **false positives** without compromising security.

For performance:

* Run SAST, SCA, and Secret Scanning in parallel wherever possible.
* Scan only changed code during pull requests when supported.
* Optimize scanner configurations.
* Schedule full scans during nightly builds where appropriate.

For false positives:

* Fine-tune scanner rules.
* Maintain approved false-positive suppressions.
* Review suppressions periodically.
* Customize policies based on project requirements.
* Train developers on secure coding practices.

For governance:

* Keep Critical and High vulnerabilities as mandatory quality gates.
* Allow approved business exceptions only through documented risk acceptance and proper approvals.
* Continuously monitor pipeline metrics and improve scan efficiency.

This approach maintains strong security while improving developer experience and delivery speed.



# **10. What ticketing or incident management tool are you currently using?**

### Answer:

Currently, we do not have a dedicated enterprise ticketing tool integrated into our DevSecOps workflow. The organization is planning to onboard **Jira** for centralized issue tracking.

For security vulnerabilities, we primarily use **OpenText Fortify SSC**, which maintains the complete vulnerability lifecycle, including findings, history, severity, status, assignments, and remediation tracking.

For major production issues, communication is coordinated through email, Microsoft Teams, and internal stakeholders until Jira is fully adopted.



# **11. Suppose a major production/security incident occurs. Walk us through your complete incident handling process.**

### Answer:

Whenever a major incident occurs, I follow a structured incident response process.

### 1. Identify the Incident

* Verify the alert.
* Determine affected applications, infrastructure, and users.
* Assess the blast radius.

### 2. Contain the Issue

* Prevent further impact.
* Isolate affected systems if required.
* Disable vulnerable services or deployments when necessary.

### 3. Notify Stakeholders

* Inform DevOps, Security, Application Owners, and Management.
* Start incident communication based on severity.

### 4. Investigate Root Cause

* Analyze logs, monitoring dashboards, and security events.
* Review deployment history and recent infrastructure changes.
* Identify the actual root cause.

### 5. Resolve the Issue

* Apply fixes or rollback if necessary.
* Validate service recovery.
* Ensure systems are functioning normally.

### 6. Monitor Recovery

* Verify application health.
* Monitor logs and alerts for recurring issues.

### 7. Post-Incident Activities

* Prepare RCA documentation.
* Conduct postmortem discussions.
* Implement preventive measures.
* Update documentation and runbooks.

This structured approach minimizes downtime and prevents recurrence.



# **12. Can you explain a real production incident that happened in your current company?**

### Answer (STAR Method):

**Situation:**

After integrating **Fortify SAST** and **Sonatype IQ Server** into several Jenkins pipelines, developers reported a significant increase in pipeline execution time, and many builds were failing because of false-positive findings.

**Task:**

Our objective was to improve developer productivity without compromising PCI-DSS security requirements.

**Action:**

* Analyzed pipeline execution stages.
* Identified that SAST and SCA scans were running sequentially.
* Modified the pipeline to execute security scans in parallel.
* Fine-tuned Fortify scan configurations.
* Reduced unnecessary scanning rules while keeping PCI-DSS mandatory checks.
* Configured approved false-positive suppressions.
* Optimized quality gate policies.

**Result:**

* Pipeline execution time reduced significantly.
* Developer complaints decreased.
* Security coverage remained unchanged.
* PCI-DSS compliance was maintained.
* Overall CI/CD efficiency improved.



# **13. Why didn't you consider parallel execution of security scans from the beginning?**

### Answer:

Initially, our focus was on successfully integrating the security tools into the CI/CD pipeline and ensuring compliance.

As adoption increased and more applications were onboarded, developers started reporting longer pipeline execution times.

Based on this feedback and performance analysis, we optimized the pipeline by introducing **parallel execution** of independent scans such as SAST and SCA.

This iterative improvement allowed us to enhance pipeline performance without affecting security controls.



# **14. Are you and your team responsible for the infrastructure, CI/CD pipelines, security scanners, and their configurations?**

### Answer:

Yes.

Our team is responsible for:

* Jenkins pipeline development and maintenance.
* Security tool integration.
* Fortify configuration.
* Sonatype IQ configuration.
* Pipeline governance.
* Quality gates.
* Terraform modules for DevSecOps infrastructure.
* Kubernetes deployment support.
* Security policy implementation.
* Developer onboarding.
* Compliance implementation.

Infrastructure provisioning is shared with the infrastructure/platform team, while the DevSecOps team owns the security automation and pipeline configurations.



# **15. Since you have control over scanner configurations, how do you ensure PCI-DSS compliance while modifying or disabling certain scans?**

### Answer:

PCI-DSS mandatory security controls are **never disabled**.

Our approach is:

* Critical and High vulnerabilities always fail the build.
* Mandatory compliance scans always remain enabled.
* Low and Medium vulnerabilities may be tracked and resolved in later sprints based on organizational policy.
* Any temporary bypass requires a documented **business exception**, formal risk acceptance, and management approval.
* Every exception is tracked and reviewed during audits.

This ensures compliance is maintained while supporting business requirements in controlled scenarios.



# **16. What security and compliance requirements must be implemented in a Source Code Repository like GitLab?**

### Answer:

From a security perspective, GitLab should implement:

* Role-Based Access Control (RBAC).
* Multi-Factor Authentication (MFA).
* SSO integration.
* Branch protection.
* Mandatory Pull/Merge Request approvals.
* Code review policies.
* Signed commits (where applicable).
* Secret scanning.
* SAST integration.
* SCA integration.
* Protected tags and releases.
* Audit logging.
* Repository activity monitoring.
* Least privilege access.
* Pipeline quality gates.
* Secure credential management.
* Compliance reporting.

These controls help secure the SDLC and satisfy audit requirements.



# **17. How would you technically implement those security controls in GitLab?**

### Answer:

I would implement the following:

### Identity & Access

* Configure LDAP/SAML-based SSO.
* Enforce Multi-Factor Authentication.
* Assign RBAC roles (Guest, Developer, Maintainer, Owner).

### Repository Protection

* Protect main and release branches.
* Disable direct pushes.
* Allow merges only through Merge Requests.
* Require minimum two reviewers.

### CI/CD Security

* Trigger Jenkins/GitLab pipelines on Merge Requests.
* Execute:

  * SAST
  * SCA
  * Secret Scanning
  * Container Image Scanning
* Configure quality gates to block builds on Critical and High vulnerabilities.

### Secret Management

* Never store secrets in repositories.
* Retrieve secrets securely from **HashiCorp Vault** during runtime.

### Audit & Compliance

* Enable audit logging.
* Retain logs according to compliance requirements.
* Monitor repository activities.
* Generate compliance reports for audits.

This provides a secure, governed, and compliant GitLab environment.



# **18. Do you have any questions for us?**

### Answer:

Yes, I have a few questions.

**1.** Since this is a centralized DevSecOps Platform Engineering team, how much involvement will I have in defining platform architecture and security standards?

**2.** What are the major priorities for the team over the next 6–12 months?

**3.** Which technologies and security tools are currently part of your standardized DevSecOps platform, and are there any plans to introduce additional tools?

**4.** How do different product teams collaborate with the centralized DevSecOps Platform Engineering team?

**5.** What does success look like for this role during the first six months?






