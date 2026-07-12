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

Actual Questions:

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

Answers:

1. **Tell me about your background and DevSecOps experience.**

   * “I have **4.5 years of experience** in **DevOps and DevSecOps**. I started my career at **TCS**, where I worked on CI/CD, containerization, Terraform-based infrastructure automation, and production support.
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

These are the kinds of structured, experience-backed answers a strong **4–5 YOE DevSecOps engineer** would typically give in an interview.
