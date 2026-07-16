## Questions: 1st Round

1. **Can you introduce yourself?**

2. **Can you walk me through a Jenkins CI/CD pipeline you built end-to-end for a product development?**

3. **Can you explain the stages, triggers, and how you handle secrets in the pipeline?**

4. **Why Jenkins and why not GitHub Actions?**

5. **When would you choose Jenkins, and when would you choose GitHub Actions?**

6. **Suppose a Kubernetes Pod is stuck in `CrashLoopBackOff`. How would you debug it in production?**

7. **How would you configure RBAC so that developers can deploy only to their own namespaces?**

8. **How do you manage Terraform state across multiple environments when multiple team members are working?**

9. **Should the Terraform state file be maintained per team, per environment, or per resource?**

10. **What do you mean by per environment versus per resource?**

11. **Can you explain the different security tools you have integrated into your CI/CD pipeline?**

12. **If a SAST scan reports 200 findings in a release, would you block the pipeline? Why or why not?**

13. **Who decides whether vulnerabilities can be skipped or whether the pipeline should be blocked?**

14. **Are those security decisions taken by you, or are they backed by management/security policies?**

15. **Suppose a developer accidentally commits an AWS Access Key to a Git repository. What would you do?**

16. **When such a secret is committed, do you only report it, or do you perform the remediation yourself?**

17. **If you had to remove the leaked secret yourself, do you know how to remove it properly so that it cannot be retrieved later?**

18. **Specifically, if it is an AWS Access Key, what should be your first action?**

19. **Deleting and recommitting is not enough because the key still exists in Git history. What else would you do to ensure it is completely secured?**

20. **Can you explain your experience working with a hybrid architecture?**

21. **Prometheus has alerted on high memory usage on a node. How would you triage and investigate the issue?**

22. **What if the high memory usage is caused by a sudden traffic spike or an attack?**

23. **Can you give an example of a Python or Bash script that you wrote to automate a real operational task (not CI/CD related)?**

24. **What other automation work have you done? What else would you like to add that demonstrates your scripting experience?**

25. **Do you have any questions for me?**





## Answers:





# 1. Tell me about yourself.

> **I have around 4.5 years of experience in DevOps and DevSecOps.**
>
> I started my career at **TCS**, where I worked primarily on **Jenkins, CI/CD pipeline management, and application deployments**. After around 2.5 years, I transitioned into a **DevSecOps Engineer** role.
>
> Currently, I work with **Talakunchi Networks**, deployed to **InSolutions Global (ISG)**, a fintech company providing payment gateway solutions for banking clients.
>
> My primary responsibilities include:
>
> * Designing and maintaining **Jenkins CI/CD pipelines**
> * Integrating security into CI/CD using **Fortify SAST/DAST, Sonatype Lifecycle & SBOM Manager, GitLeaks, Trivy and IaC scanning**
> * Managing **Docker** image creation and **Kubernetes** deployments using **Helm**
> * Provisioning infrastructure using **Terraform**
> * Working with **AWS/Azure** cloud environments
> * Monitoring applications using **Prometheus, Grafana and ELK**
> * Collaborating with Development, Operations and Security teams to implement **Shift-Left DevSecOps**

**Overall, my focus is to automate software delivery while embedding security throughout the SDLC.**



# 2. Walk me through a Jenkins CI/CD pipeline you built end-to-end.

Our source code is maintained in **GitLab**, and **Jenkins** acts as the orchestration platform.

### Pipeline Flow

### 1. Source Code Checkout

* Developer pushes code to GitLab.
* Jenkins pipeline is triggered automatically.
* Jenkins checks out the latest source code.



### 2. Secret Detection

* **GitLeaks** scans the repository.
* Detects API keys, passwords, tokens or hardcoded secrets.
* Pipeline stops if secrets are found.



### 3. Build Stage

* Build application using Maven/Gradle depending on project.
* Generate deployable artifacts.



### 4. Static Security Scan (SAST)

* **Fortify SAST**
* Detects source code vulnerabilities.
* Quality Gate is enforced.



### 5. Software Composition Analysis (SCA)

* **Sonatype Lifecycle**
* Detects vulnerable third-party libraries.
* Generates **SBOM**
* Pipeline fails if policy threshold is exceeded.



### 6. Docker Build

* Build Docker image.
* Tag image with **Git Commit Hash**.
* Push to registry after successful validation.



### 7. Container Security

* **Trivy**
* Scan Docker image for OS and package vulnerabilities.



### 8. Infrastructure Security

* Scan Terraform code using **Checkov/tfsec** (or project-specific IaC scanner).
* Detect misconfigurations before provisioning.



### 9. Deployment

* Deploy to Kubernetes using **Helm Charts**
* Verify deployment health.



### 10. Manual Approval

* Production deployment requires approval.
* Only after approval does deployment continue.



### 11. Notifications

* Email/Teams notification sent.
* Build reports published.



**This pipeline implements Shift-Left Security by integrating security checks before deployment.**



# 3. Explain stages, triggers and how you handle secrets.

## Trigger

* Git Push
* Merge Request
* Manual Production Trigger



## Main Stages

* Source Checkout
* Secret Detection
* Build
* Fortify SAST
* Sonatype SCA
* Docker Build
* Trivy Scan
* Terraform IaC Scan
* Kubernetes Deployment
* Smoke Validation
* Notification



## Secret Management

We never hardcode secrets.

We use **HashiCorp Vault** as our centralized secret management solution.

* Vault stores

  * API Keys
  * Database Passwords
  * Tokens
  * Cloud Credentials

* Jenkins retrieves secrets dynamically during runtime.

* Secrets are never stored inside:

  * Git Repository
  * Jenkinsfile
  * Terraform Code

* Credentials are masked in Jenkins logs.

This ensures secure secret management throughout the pipeline.



# 4. Why Jenkins and not GitHub Actions?

It depends on the organization's ecosystem.

We use **GitLab** as our source code repository, so Jenkins integrates well with our environment.

Reasons for Jenkins:

* Mature enterprise solution
* Large plugin ecosystem (1800+ plugins)
* Highly customizable
* Easy integration with Fortify, Sonatype, Trivy, Vault, Kubernetes etc.
* Better suited for large enterprise CI/CD pipelines
* Supports distributed builds through agents

GitHub Actions is also a very good solution.

If the organization hosts code in GitHub and requires cloud-native CI/CD, GitHub Actions becomes a good choice because it has native integration with GitHub repositories.



# 5. When would you choose Jenkins and when GitHub Actions?

### Jenkins

Choose Jenkins when:

* Enterprise environments
* Complex multi-stage pipelines
* Multiple integrations
* Hybrid infrastructure
* Heavy customization required



### GitHub Actions

Choose GitHub Actions when:

* Source code is hosted on GitHub
* Simpler CI/CD workflows
* Cloud-native development
* Faster setup
* Smaller maintenance effort

**So the choice depends on the existing ecosystem and business requirements.**



# 6. Kubernetes Pod is in CrashLoopBackOff. How do you debug?

My approach is always systematic.

### Step 1

Check pod status

```bash
kubectl get pods -n <namespace>
```



### Step 2

Describe the pod

```bash
kubectl describe pod <pod>
```

Look for:

* OOMKilled
* ImagePullBackOff
* Failed Mount
* Probe failures
* Scheduling issues



### Step 3

Check Logs

```bash
kubectl logs <pod>
```

If restarted

```bash
kubectl logs <pod> --previous
```



### Step 4

Validate

* ConfigMaps
* Secrets
* Environment Variables



### Step 5

Check Resource Usage

```bash
kubectl top pod
```

Verify CPU/Memory utilization.



### Step 6

Check Health Probes

* Liveness
* Readiness
* Startup Probe



### Step 7

Verify

* Recent deployment
* Image version
* Application configuration

Finally fix the root cause, redeploy and monitor until the pod becomes healthy.



# 7. How would you configure RBAC for the Dev team?

RBAC follows the **Least Privilege Principle**.

For developers:

* Create a **Role** in the **Dev Namespace**
* Grant only required permissions:

  * get
  * list
  * watch
  * create/update deployments (if needed)
  * view pods and logs
* Avoid permissions on:

  * ClusterRoles
  * Nodes
  * Production namespaces
* Bind the Role using **RoleBinding** to users or groups.

This ensures developers can work only within their own namespace without affecting cluster-wide resources.



# 8. How do you manage Terraform state across multiple environments?

We use a **Remote Backend**.

* Store Terraform state in **AWS S3**
* Enable **DynamoDB State Locking**
* Separate state files for

  * Dev
  * QA
  * UAT
  * Production
* Execute Terraform through Jenkins pipeline instead of manual execution.
* Restrict access using IAM permissions.

This avoids state conflicts and enables multiple team members to collaborate safely.



# 9. Should Terraform state be per team, per environment, or per resource?

Our preferred approach is **per environment**.

For example:

```
terraform-state/
   dev/terraform.tfstate
   qa/terraform.tfstate
   prod/terraform.tfstate
```

Each environment has:

* Independent state
* Separate lifecycle
* Independent deployments
* Easier rollback
* Better isolation

Developers working on the same environment share the same state with DynamoDB locking.



# 10. What is the difference between per environment and per resource?

**Per Environment**

One state file manages all related infrastructure within an environment.

Example:

**Dev**

* VPC
* EC2
* EKS
* IAM
* Security Groups
* Load Balancer

All maintained together.



**Per Resource (or Component)**

Large organizations sometimes split state files by infrastructure components.

Example:

* Network State
* Kubernetes State
* Database State
* Application State

This reduces blast radius, improves scalability, and allows independent updates.

> **In my project, we primarily maintained Terraform state per environment, while larger infrastructures may further split state by major infrastructure components when required.**



Great. Below are the **improved interview-ready answers** for **Questions 11–20**, based on your actual project experience, while correcting and enhancing the responses from your interview.



# 11. Can you explain the different security tools you have used in your CI/CD pipelines?

In our project, we implemented a **Shift-Left DevSecOps** approach by integrating multiple security tools into the Jenkins CI/CD pipeline.

### 1. GitLeaks (Secret Scanning)

* Runs before the build stage.
* Detects hardcoded secrets such as API keys, passwords, tokens, and certificates.
* Pipeline fails if secrets are detected.



### 2. Fortify SAST (Static Application Security Testing)

* Scans source code without executing it.
* Detects vulnerabilities like SQL Injection, XSS, Command Injection, etc.
* Enforces Quality Gates before proceeding.



### 3. Sonatype Lifecycle (SCA)

* Performs Software Composition Analysis.
* Identifies vulnerable third-party libraries.
* Generates SBOM.
* Blocks builds if policy thresholds are exceeded.



### 4. Trivy (Container Security)

* Scans Docker images.
* Detects OS package vulnerabilities.
* Identifies misconfigurations and vulnerable dependencies.



### 5. Terraform IaC Scanning

* Scan Terraform code before provisioning.
* Detects security misconfigurations.



### 6. Fortify WebInspect (DAST)

* Performs Dynamic Application Security Testing.
* Scans deployed web applications and APIs.
* Detects runtime vulnerabilities.

**Overall, security checks are integrated throughout the pipeline to ensure only secure applications are deployed.**



# 12. Suppose a SAST scan reports 200 findings. Would you block the pipeline?

**Not immediately.**

The decision depends on the organization's security policy rather than the number of findings.

### My approach

* Review findings by severity:

  * Critical
  * High
  * Medium
  * Low

* Validate whether findings are:

  * New vulnerabilities
  * Existing accepted risks
  * False positives

* If Critical or High vulnerabilities exceed the approved threshold,

  * Pipeline fails.

* Medium and Low vulnerabilities

  * Raise remediation tickets.
  * Can be fixed in subsequent releases if approved.

**The decision is based on severity and policy, not simply the count of vulnerabilities.**



# 13. Who approves whether vulnerabilities can be skipped?

The approval is **not handled by DevSecOps alone.**

Typically:

* Product Owner
* Application Owner
* Security Team
* Engineering Manager

review the findings.

If a vulnerability requires a business exception,

* Risk is evaluated.
* Formal approval is obtained.
* The exception is documented.
* Pipeline proceeds only after approval.

**DevSecOps implements and enforces the policy but does not approve exceptions independently.**



# 14. Are these decisions taken by you or backed by management?

They are always **management and security policy driven.**

My responsibilities are:

* Configure security tools.
* Enforce security policies.
* Generate scan reports.
* Communicate vulnerabilities.
* Block the pipeline if thresholds are exceeded.

The acceptance of security risk is decided by:

* Product Management
* Security Team
* Business Owners

**As a DevSecOps engineer, I enforce the policy rather than deciding the acceptable level of risk myself.**



# 15. A developer accidentally commits an AWS Access Key to Git. What would you do?

I would treat this as a **security incident.**

### Step 1

Immediately disable or rotate the exposed AWS Access Key.



### Step 2

Inform:

* Security Team
* Cloud Team
* Application Owner



### Step 3

Generate a new access key.

Update it securely in:

* HashiCorp Vault
* AWS Secrets Manager
* Jenkins Credentials



### Step 4

Remove the secret from Git history.



### Step 5

Review CloudTrail logs.

Verify whether the compromised key was used.



### Step 6

Run GitLeaks again.

Ensure no additional secrets exist.



### Step 7

Implement preventive controls:

* GitLeaks pre-commit hooks
* CI secret scanning
* Developer awareness

**The highest priority is rotating the exposed key immediately because it should be considered compromised.**



# 16. Do you perform remediation or just report it?

It depends on my level of access.

If I have IAM permissions:

* Disable the compromised key.
* Rotate credentials.
* Update secure secret storage.
* Verify application functionality.

If I don't have permissions:

* Raise a high-priority security incident.
* Coordinate with the Cloud/Security team.
* Track the issue until resolution.

**I don't simply report the issue; I take ownership of the incident response within my responsibilities and coordinate the remaining actions if administrative access is required.**



# 17. How do you remove the leaked secret so it cannot be recovered?

Deleting the file alone is **not sufficient** because the secret remains in Git history.

### Proper approach

* Rotate the exposed credential.
* Rewrite Git history using:

  * `git filter-repo` (preferred)
  * or BFG Repo-Cleaner
* Force push the cleaned repository.
* Ask developers to re-clone or reset their local repositories.
* Run GitLeaks to verify complete removal.
* Store new credentials securely.

**This permanently removes the secret from repository history while ensuring the leaked credential is no longer valid.**



# 18. If it's an AWS Access Key specifically, what is your first action?

The very first action is:

**Immediately rotate or deactivate the AWS Access Key in IAM.**

Reason:

Once the key is exposed,

* It must be considered compromised.
* Anyone with access to that key could potentially access AWS resources.

After rotation:

* Update the new key in Vault or Jenkins Credentials.
* Restart applications if necessary.
* Review CloudTrail for unauthorized usage.

**Rotating the key immediately eliminates the security risk, even if the old key still exists in Git history.**



# 19. Simply deleting and recommitting is not enough. What else would you do?

Correct.

Deleting the file only removes it from the latest commit.

The secret still exists in previous commits.

### Complete remediation

* Rotate the exposed key.
* Remove the secret from Git history using:

  * `git filter-repo`
  * or BFG Repo-Cleaner
* Force push the updated repository.
* Ask all developers to synchronize with the rewritten history.
* Run GitLeaks again.
* Store the new credential securely.
* Implement preventive controls.

**This ensures the leaked credential cannot be recovered from repository history and prevents similar incidents in the future.**



# 20. Explain your experience with a Hybrid Architecture.

In my current project, we work in a **Hybrid Cloud Architecture**, where some services run on the cloud while others remain on-premises due to security and compliance requirements.

### Architecture Overview

* Applications are deployed on **AWS EKS** (or Kubernetes in cloud).
* Critical internal services and some security tools remain on-premises.
* Secure communication is established through a **Site-to-Site VPN** between cloud and on-premises.

### CI/CD

* Source Code: GitLab
* CI/CD: Jenkins
* Security Tools:

  * Fortify
  * Sonatype
  * GitLeaks
  * Trivy

### Traffic Flow

* External traffic enters through:

  * Load Balancer
  * Kubernetes Ingress
* Internal traffic to on-premises systems is routed securely through the VPN.

### Monitoring

* Prometheus
* Grafana
* AWS CloudWatch
* Azure Monitor (where applicable)

**This architecture allowed us to leverage cloud scalability while keeping sensitive systems and enterprise services on-premises to satisfy security and regulatory requirements.**




> **Note:** In the previous list, **Question 20** was "Hybrid Architecture." So below I've continued from **Question 21 to Question 25**.



# 21. Prometheus is alerting on high memory usage on a node. How do you triage it?

Whenever I receive a **high memory usage alert**, I first verify whether it's a temporary spike or an actual resource issue before taking action.

### Step 1: Verify the Alert

* Check **Grafana dashboards**.
* Observe memory usage trends.
* Determine whether it is:

  * A temporary spike
  * A continuously increasing trend



### Step 2: Identify the Affected Workload

Run:

```bash
kubectl top nodes
kubectl top pods -A
```

Identify:

* Which node has high memory usage.
* Which pods are consuming the most memory.



### Step 3: Check Pod Health

Verify whether any pod is:

* OOMKilled
* Restarting repeatedly
* Consuming abnormal memory

Run:

```bash
kubectl describe pod <pod-name>
```



### Step 4: Review Logs

Check:

```bash
kubectl logs <pod-name>
```

Look for:

* Memory leaks
* Application exceptions
* Infinite loops
* Cache issues



### Step 5: Verify Recent Changes

Check if:

* A new deployment happened recently.
* Resource requests/limits changed.
* Configuration changes were introduced.



### Step 6: Consider Traffic Spikes

Sometimes high memory usage is expected due to:

* Sudden increase in user traffic
* Scheduled jobs
* Batch processing
* DDoS or abnormal traffic

Verify:

* Application metrics
* Load Balancer metrics
* CloudWatch/Azure Monitor
* Prometheus metrics



### Step 7: Take Corrective Action

Depending on the root cause:

* Restart the affected pod (if necessary)
* Increase resource limits
* Scale horizontally
* Roll back the deployment if required
* Fix application memory leaks

**My objective is not just to clear the alert but to identify and resolve the root cause while minimizing production impact.**



# 22. What if the high memory usage is caused by a sudden traffic spike?

The first step is to verify whether the spike is **legitimate traffic** or an **unexpected attack**.

### If it's legitimate traffic:

* Verify application response times.
* Check HPA (Horizontal Pod Autoscaler).
* Scale pods if necessary.
* Monitor resource utilization.



### If it's abnormal traffic or a possible attack:

* Verify ingress/load balancer metrics.
* Check WAF or firewall logs.
* Review application access logs.
* Block suspicious IPs if required.
* Coordinate with the Security team.



### Continue Monitoring

Ensure:

* Memory usage returns to normal.
* Alerts are cleared.
* Applications remain healthy.

**The key is to distinguish between expected business traffic and abnormal behavior before taking action.**



# 23. Give an example of a Python or Bash script you wrote to automate an operational task.

Yes.

I have written **Bash and Python scripts** for several operational tasks.

One example is **automating disk cleanup on Linux servers.**

### The Bash script performs:

* Checks disk utilization using:

```bash
df -h
```

* Identifies old log files.
* Removes temporary files.
* Deletes archived logs older than a configured retention period.
* Generates cleanup logs.
* Sends a summary notification after execution.

This script was scheduled using **Cron**, eliminating manual cleanup activities.



Another example is a **Python automation script**.

It:

* Reads vulnerability reports through APIs.
* Extracts Critical and High vulnerabilities.
* Generates summary reports.
* Publishes the results to Jenkins dashboards for easier visibility.

**These automations reduced manual effort, improved consistency, and saved operational time.**



# 24. What other automation work have you done?

Apart from cleanup scripts, I have worked on several operational automations.

Examples include:

* Log parsing and report generation.
* Automating vulnerability report extraction using APIs.
* Integrating security scan results into Jenkins dashboards.
* Automating disk utilization monitoring.
* Automating backup-related activities.
* Writing Bash scripts for routine Linux administration tasks.
* Developing Python utilities for processing security reports.

I have also written small utility scripts for:

* File management
* Log cleanup
* Data extraction
* API integration
* Operational health checks

**My objective while writing automation scripts is always to reduce repetitive manual work, improve consistency, and save operational time.**



# 25. Do you have any questions for me?

Yes, thank you.

I have a couple of questions.

### Question 1

**Could you please share a little about the current DevSecOps environment and the technology stack used by your team?**



### Question 2

**What would be the key expectations from the person joining this role during the first three to six months?**



### Question 3

**Could you also tell me how the DevSecOps team is structured, and how closely it collaborates with the Development and Security teams?**



### (Optional Final Question)

**Based on today's discussion, is there any area where you think I could improve or strengthen my skills for this role?**


