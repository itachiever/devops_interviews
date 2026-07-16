## Questions: 1st Round

1. Did you receive the Job Description (JD)?
2. How many years of experience do you have?
3. How would you rate your Python coding/scripting skills out of 5?
4. Are you more inclined towards DevSecOps or software tooling engineering?
5. Tell me about your DevSecOps experience in brief.
6. How do you design a secure CI/CD pipeline?
7. What security controls would you implement in Jenkins or GitHub Actions?
8. What is the difference between SAST, DAST, and SCA?
9. What is Shift Left Security?
10. How do you secure Docker containers?
11. How do you secure Kubernetes?
12. How do you secure an Azure environment?
13. What is Azure Key Vault?
14. What is Managed Identity?
15. What is Infrastructure as Code (IaC)?
16. Why do we use Infrastructure as Code?
17. How do you secure Terraform deployments?
18. How do you scan Terraform code?
19. What is the difference between Terraform and Helm?
20. How do you monitor a production environment?
21. What are SLA, SLO, and SLI?
22. Describe a major production incident you handled using the STAR method.
23. Have you used Python in DevSecOps?
24. In what scenarios have you used Python?
25. Have you worked with Microsoft Fabric or Power BI?
26. What is the Secure Software Development Life Cycle (SSDLC)?
27. What are the phases of the Secure SDLC?
28. How would you improve Secure SDLC adoption across your engineering team?
29. What is Threat Modeling?
30. Which threat modeling framework have you used?
31. What Python libraries have you used?
32. Do you have any questions for me?

### Questions the interviewer specifically recommended preparing for the client interview

33. How would you handle a false positive reported by a security scanner?
34. Explain your experience using real-world, scenario-based DevSecOps examples.

---

### Interview Areas Covered

* General Experience
* DevSecOps
* Python

  * Python Use Cases
  * Python Libraries
* CI/CD Security
* Jenkins / GitHub Actions Security
* Application Security Testing

  * SAST
  * DAST
  * SCA
  * Secret Scanning
  * Container Scanning
  * IaC Scanning
* Shift Left Security
* Docker Security
* Kubernetes Security
* Azure Security

  * Azure Key Vault
  * Managed Identity
* Infrastructure as Code (IaC)

  * Terraform
  * Helm
* Production Monitoring & Observability
* SRE Concepts

  * SLA
  * SLO
  * SLI
* Incident Management (STAR Method)
* Secure SDLC
* Threat Modeling
* Power BI / Microsoft Fabric
* Scenario-Based DevSecOps
* False Positive Handling

---

## Actual Questions: Removed small/Follow-up questions

1. Tell me about your background and DevSecOps experience. 
2. How do you design a secure CI/CD pipeline? 
3. What security controls would you implement in Jenkins/GitHub Actions? 
4. What is the difference between SAST, DAST, and SCA? 
5. What is Shift-Left Security? 
6. How do you secure Docker containers? 
7. How do you secure Kubernetes? 
8. How do you secure an Azure environment? 
9. What is Azure Key Vault? 
10. What is a Managed Identity? 
11. What is Infrastructure as Code, and why is it used? 
12. How do you secure Terraform deployments? How do you scan IaC? 
13. What is the difference between Terraform and Helm? 
14. How do you monitor a production environment? 
15. What are SLA, SLO, and SLI? 
16. Describe a major production incident you handled using the STAR method. 
17. Where have you used Python in DevSecOps? 
18. Do you have experience with Microsoft Fabric or Power BI? 
19. What is the Secure SDLC and its phases? 
20. How would you improve Secure SDLC adoption across engineering teams? 
21. What is threat modeling? 
22. Which threat-modeling frameworks have you used? 
23. Which Python libraries have you used? 
How would you handle false positives from a security scanner? (suggested preparation topic for the next round)

## Answers: 

1. **Tell me about your background and DevSecOps experience.**

   * “I have **4.5 years of experience** in **DevOps and DevSecOps**. I started my career at **FIRST COMPANY NAME**, where I worked on CI/CD, containerization, Terraform-based infrastructure automation, and production support.
   * In my current role, I work for a **fintech client** in the payment domain. My primary responsibility is to **embed security throughout the SDLC**.
   * I have designed and maintained **Jenkins pipelines**, integrated **Fortify, Snyk, Dependency-Check, and GitLeaks**, and automated deployments to **AKS** using **Terraform** and **Helm**.
   * I also work closely with developers to **triage vulnerabilities, drive remediation, and improve secure development practices**.”

2. **How do you design a secure CI/CD pipeline?**

   * Start with a secure **source-code repository** with branch protection and reviews.
   * Run **secret scanning**, **SAST**, and **SCA** immediately after code check-in.
   * Build the artifact and perform **container image scanning** and **IaC scanning**.
   * Enforce **quality gates** so critical findings block the pipeline.
   * Deploy first to lower environments, run **DAST** and automated tests, and then promote to production through **approval workflows**.
   * Sign artifacts/images and continuously monitor the application after deployment.

3. **What security controls would you implement in Jenkins/GitHub Actions?**

   * Enforce **RBAC** and integrate with **SSO/MFA**.
   * Store secrets in a **vault** instead of in pipelines.
   * Keep plugins/actions updated and use only **trusted, pinned versions**.
   * Enable **audit logging** and protect the build agents.
   * Use **signed artifacts** and implement mandatory **security gates**.

4. **What is the difference between SAST, DAST, and SCA?**

   * **SAST** analyzes the **source code** without executing it.
   * **DAST** tests the **running application** from the outside.
   * **SCA** examines **third-party dependencies** for vulnerabilities and license issues.
   * Together, they provide coverage across **custom code, runtime behavior, and open-source components**.

5. **What is Shift-Left Security?**

   * Shift-left means integrating security **as early as possible** in the SDLC.
   * In practice, this includes **threat modeling**, secure coding, and automated security scans in CI.
   * The goal is to **find issues when they are cheaper and easier to fix**.

6. **How do you secure Docker containers?**

   * Use **minimal, trusted base images** and patch them regularly.
   * Run containers as a **non-root user** and drop unnecessary capabilities.
   * Scan images before deployment and sign approved images.
   * Keep secrets out of the image and inject them securely at runtime.

7. **How do you secure Kubernetes?**

   * Apply **RBAC** with least privilege.
   * Use **Network Policies** and **Pod Security Standards**.
   * Manage secrets through **Key Vault** or a similar solution.
   * Enable **audit logging**, monitor the cluster, and keep it patched.

8. **How do you secure an Azure environment?**

   * Secure identities with **Entra ID**, **MFA**, and **RBAC**.
   * Use **VNets**, **NSGs**, **private endpoints**, and **Azure Firewall**.
   * Store secrets in **Key Vault** and enable encryption at rest and in transit.
   * Continuously assess the environment with **Defender for Cloud** and **Azure Monitor**.

9. **What is Azure Key Vault?**

   * “Azure Key Vault is a managed service for securely storing and controlling access to **secrets, certificates, and cryptographic keys**.
   * In our pipelines, we use it to fetch credentials dynamically, eliminating the need for hard-coded secrets.”

10. **What is a Managed Identity?**

    * “A Managed Identity is an Azure-provided identity for a resource.
    * It allows services such as AKS or VMs to access Azure resources securely **without storing credentials**, with permissions governed through **RBAC**.”

11. **What is Infrastructure as Code, and why is it used?**

    * “Infrastructure as Code means defining infrastructure in **version-controlled code**.
    * It provides **consistency, repeatability, auditability, and faster recovery**, while reducing manual errors and configuration drift.”

12. **How do you secure Terraform deployments? How do you scan IaC?**

    * Store Terraform code in Git with **peer reviews** and protected branches.
    * Run **`terraform fmt`**, **`validate`**, and review the **execution plan**.
    * Scan the code using tools such as **Snyk IaC**, **Checkov**, or **tfsec** before `apply`.
    * Use a **remote, encrypted backend** with state locking and restrict access to the state file.
    * Only approved, scanned changes are allowed to reach production.

13. **What is the difference between Terraform and Helm?**

* **Terraform** is an **Infrastructure as Code** tool used to provision cloud resources such as VNets, AKS clusters, VMs, and databases.
* **Helm** is a **package manager for Kubernetes** used to deploy and manage applications within a cluster.
* In practice, I use **Terraform to build the platform** and **Helm to deploy workloads** on that platform.

14. **How do you monitor a production environment?**

* We collect **metrics** with **Prometheus** and visualize them in **Grafana**.
* Logs are centralized in **ELK** and **Azure Monitor** for troubleshooting and auditing.
* We configure alerts for **latency, error rates, resource usage, and pod restarts**.
* The key is to combine **metrics, logs, traces, and alerting** to achieve full observability.

15. **What are SLA, SLO, and SLI?**

* **SLI** is the actual measurement, such as API availability.
* **SLO** is the target, for example **99.9% uptime**.
* **SLA** is the contractual commitment to the customer, often including penalties if not met.
* In short: **SLIs are measured, SLOs are goals, and SLAs are promises**.

16. **Describe a major production incident you handled using the STAR method.**

* **Situation:** After a production deployment, users experienced intermittent **HTTP 500 errors**.
* **Task:** I was responsible for restoring service and identifying the root cause.
* **Action:** I analyzed **Grafana metrics** and **ELK logs**, identified an incorrect configuration affecting database connectivity, rolled back via the Jenkins pipeline, fixed the configuration, and added an automated validation step.
* **Result:** Service was restored within minutes, and the new validation check prevented recurrence.

17. **Where have you used Python in DevSecOps?**

* I have used Python for **vulnerability aggregation**, combining findings from multiple scanners into a single report.
* I have written scripts for **log parsing**, API integrations with Jenkins, and generating operational reports.
* These automations reduced manual effort and improved response times.

18. **Do you have experience with Microsoft Fabric or Power BI?**

* “I have not used them extensively in production. My experience has primarily been with **Grafana** for operational dashboards. However, I understand the concepts and am confident in learning them quickly because of my experience with observability and data visualization.”

Explanation:
* **Power BI** is a **business intelligence and data visualization platform**. It connects to various data sources, lets you transform and model the data, and create **interactive dashboards and reports** for business and operational insights.

* **Microsoft Fabric** is a **unified analytics platform** that brings together **data engineering, data integration, data warehousing, data science, real-time analytics, and Power BI** into a single SaaS offering. It is built around the concept of **OneLake**, a centralized data lake for the organization.

For an interview, you can summarize:

> “Power BI focuses on **visualization and reporting**, while Microsoft Fabric provides the **end-to-end data platform**—from data ingestion and processing to analytics and dashboards.”

19. **What is the Secure SDLC and its phases?**

* The phases are **Requirements**, **Design**, **Development**, **Testing**, **Deployment**, and **Operations/Maintenance**.
* Security activities such as **threat modeling, code reviews, and security testing** are embedded throughout the lifecycle.

20. **How would you improve Secure SDLC adoption across engineering teams?**

* Establish **security champions**.
* Provide **developer training** and clear **secure coding standards**.
* Automate security checks in CI/CD and enforce policies through pipelines.
* Use **dashboards and metrics** to track progress and conduct regular **threat-modeling workshops**.

21. **What is threat modeling?**

* Threat modeling is the structured process of identifying **assets, threats, attack paths, and mitigations** during the design phase.
* It helps us address risks before implementation begins.

22. **Which threat-modeling frameworks have you used?**

* I am familiar with **STRIDE**, which categorizes threats into **Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege**.
* I have used it during design discussions to ensure we systematically consider security risks.

23. **Which Python libraries have you used?**

* **`requests`** for REST APIs.
* **`json`** and **`PyYAML`** for configuration processing.
* **`logging`** for application logs.
* **`re`** for parsing logs and extracting patterns.
* **`subprocess`** for invoking CLI tools from scripts.

24. **How would you handle false positives from a security scanner?**

* First, I would **validate the finding manually** to confirm whether it is exploitable.
* If it is a false positive, I would document the analysis, suppress or tune the rule with proper approval, and track it in the vulnerability management process.
* The objective is to maintain **developer trust in the tools** while ensuring that genuine risks are never overlooked.
