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


---


## Answers:



---

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

---

# 2. Walk me through a Jenkins CI/CD pipeline you built end-to-end.

Our source code is maintained in **GitLab**, and **Jenkins** acts as the orchestration platform.

### Pipeline Flow

### 1. Source Code Checkout

* Developer pushes code to GitLab.
* Jenkins pipeline is triggered automatically.
* Jenkins checks out the latest source code.

---

### 2. Secret Detection

* **GitLeaks** scans the repository.
* Detects API keys, passwords, tokens or hardcoded secrets.
* Pipeline stops if secrets are found.

---

### 3. Build Stage

* Build application using Maven/Gradle depending on project.
* Generate deployable artifacts.

---

### 4. Static Security Scan (SAST)

* **Fortify SAST**
* Detects source code vulnerabilities.
* Quality Gate is enforced.

---

### 5. Software Composition Analysis (SCA)

* **Sonatype Lifecycle**
* Detects vulnerable third-party libraries.
* Generates **SBOM**
* Pipeline fails if policy threshold is exceeded.

---

### 6. Docker Build

* Build Docker image.
* Tag image with **Git Commit Hash**.
* Push to registry after successful validation.

---

### 7. Container Security

* **Trivy**
* Scan Docker image for OS and package vulnerabilities.

---

### 8. Infrastructure Security

* Scan Terraform code using **Checkov/tfsec** (or project-specific IaC scanner).
* Detect misconfigurations before provisioning.

---

### 9. Deployment

* Deploy to Kubernetes using **Helm Charts**
* Verify deployment health.

---

### 10. Manual Approval

* Production deployment requires approval.
* Only after approval does deployment continue.

---

### 11. Notifications

* Email/Teams notification sent.
* Build reports published.

---

**This pipeline implements Shift-Left Security by integrating security checks before deployment.**

---

# 3. Explain stages, triggers and how you handle secrets.

## Trigger

* Git Push
* Merge Request
* Manual Production Trigger

---

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

---

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

---

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

---

# 5. When would you choose Jenkins and when GitHub Actions?

### Jenkins

Choose Jenkins when:

* Enterprise environments
* Complex multi-stage pipelines
* Multiple integrations
* Hybrid infrastructure
* Heavy customization required

---

### GitHub Actions

Choose GitHub Actions when:

* Source code is hosted on GitHub
* Simpler CI/CD workflows
* Cloud-native development
* Faster setup
* Smaller maintenance effort

**So the choice depends on the existing ecosystem and business requirements.**

---

# 6. Kubernetes Pod is in CrashLoopBackOff. How do you debug?

My approach is always systematic.

### Step 1

Check pod status

```bash
kubectl get pods -n <namespace>
```

---

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

---

### Step 3

Check Logs

```bash
kubectl logs <pod>
```

If restarted

```bash
kubectl logs <pod> --previous
```

---

### Step 4

Validate

* ConfigMaps
* Secrets
* Environment Variables

---

### Step 5

Check Resource Usage

```bash
kubectl top pod
```

Verify CPU/Memory utilization.

---

### Step 6

Check Health Probes

* Liveness
* Readiness
* Startup Probe

---

### Step 7

Verify

* Recent deployment
* Image version
* Application configuration

Finally fix the root cause, redeploy and monitor until the pod becomes healthy.

---

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

---

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

---

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

---

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

---

**Per Resource (or Component)**

Large organizations sometimes split state files by infrastructure components.

Example:

* Network State
* Kubernetes State
* Database State
* Application State

This reduces blast radius, improves scalability, and allows independent updates.

> **In my project, we primarily maintained Terraform state per environment, while larger infrastructures may further split state by major infrastructure components when required.**


