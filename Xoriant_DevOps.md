# Role: DevOps
# Experience: 3.9 YOE
# 1st Round Interview Questions:
---

→ what are your job responsibilities? How are you managing things? How are you doing collaborative work? What kind of projects are you supporting? How do you handle day-to-day activities?

→ For CI/CD are you using Jenkins? Let’s say I have Kubernetes environment might be I am going with DEV, UAT, and Production. How are you handling the pipelines? Are you having multiple Jenkins jobs triggered per environment, or is it a single job triggering from development to production? How is it happening?

→ In your Kubernetes environment, how many services and pods are running? How many applications are actually deployed?

→ How are you managing deployments? Do you have a single pipeline or multiple pipelines per branch?

→ Let’s say I am moving services to production—6 out of 10 services—from dev to production. How are you managing this workflow?

→ How do you come to know about the requirements? How do you move the code and understand how your Jenkins pipelines run? Once a Jenkins job is finished—let’s say it builds and releases to Kubernetes—how do you know things are working fine in production after deployment?

→ For DEV, UAT, and Production, are you using separate Git branches? Why do you need separate branches?

→ Let’s say you are moving code from development to pre-prod. Once pre-prod is fine, you move the code to the main/master branch for release. If something goes wrong in production and a hotfix/bugfix is needed—and rollback is not possible due to database or backend changes—what strategy do you follow to fix bugs in production?

→ Let’s say you created a hotfix branch from master. After fixing the issue, do you merge it back to master and also into the development branch?

→ How do you manage release versioning?

→ Are you creating a single Docker image for all environments, or are you creating images separately for each environment?

→ Can we use one image for the entire environment?

→ When pushing images to Artifactory/Nexus, how are you managing the lifecycle of those images?

→ Let’s say developers are creating multiple images. By the end of the month, there are many images in Nexus. How do you manage the image lifecycle? How do you decide which images need to be purged and which need to be kept? Does the same strategy apply for pre-prod and prod?

→ How do you create a Dockerfile for Node.js? Which version do you use, what base image, and what is the final image size? How do you manage node_modules? Do you install node modules every time, or do you copy them from somewhere? How do you handle these things?

→ If the image size becomes very large, how do you handle that?

→ What are the things you do using Terraform?

→ Can you give a recent example where you worked with Terraform, and what tasks you performed?

→ Have you used Terraform workspaces?

→ How do you differentiate environments within Terraform?

→ How do you manage multiple environments using Terraform?

→ Are you responsible for writing Terraform modules? For example, if you want to write a module for EC2, what best practices do you follow? How do you write reusable modules for different Terraform scripts, and what kind of standardization have you implemented?

→ You also work with Python, right? How do you handle exceptions in Python? Can you give a simple example of an exception—where and why we use it, and where we should not use exceptions?

→ How do you read a file in Python line by line?

→ Have you worked with Lambdas?

→ Do you know Lambda handlers? How do they work?

---

## Answers

---

## 1️⃣ Job Responsibilities, Collaboration & Day-to-Day Work

**Answer:**

My primary responsibility as a DevOps/DevSecOps engineer is to **build, maintain, and improve CI/CD pipelines**, manage **cloud and Kubernetes infrastructure**, and ensure **secure, reliable, and scalable deployments**.

On a day-to-day basis:

* I work closely with **developers** to understand application changes, build issues, and deployment needs.
* I collaborate with **QA/UAT teams** to support environment stability and release readiness.
* I coordinate with **security teams** for vulnerability scanning, compliance checks, and incident handling.
* I support **production systems**, monitor alerts, and handle incidents or performance issues.

Typical daily activities include:

* Monitoring Jenkins pipelines, Kubernetes clusters, and cloud resources
* Supporting deployments or hotfixes
* Debugging build or deployment failures
* Writing or improving automation using **Jenkins, Terraform, Ansible, or Python**
* Participating in **standups, release calls, and post-incident reviews**

The projects I support are mostly **microservices-based applications** running on Kubernetes with cloud infrastructure provisioned using Terraform.

---

## 2️⃣ CI/CD with Jenkins for DEV, UAT, PROD (Pipeline Design)

**Answer:**

Yes, we use **Jenkins for CI/CD** with Kubernetes environments like **DEV, UAT, and Production**.

We generally follow a **single Jenkins pipeline with environment-specific stages**, not completely separate jobs for each environment.

How it works:

* **CI stages** (build, unit tests, security scans, Docker image build) are triggered automatically on **code commit**.
* The pipeline builds **one immutable Docker image** and pushes it to Nexus/Artifactory.
* **CD stages** deploy the same image to:

  * DEV automatically
  * UAT after approval
  * Production after final approval

Environment-specific behavior is handled using:

* Different **values files (Helm)** or **Kubernetes manifests**
* Environment variables
* Separate namespaces or clusters

This approach ensures **consistency across environments** and avoids “works in dev but not in prod” issues.

---

## 3️⃣ Kubernetes Environment – Services, Pods & Applications

**Answer:**

In a typical Kubernetes setup:

* We usually have **20–40 microservices** depending on the project
* Each service may run **2–5 pods per environment**
* So overall, we might see **100+ pods per environment**

Applications are usually:

* Independent microservices
* Exposed internally via ClusterIP
* Exposed externally via Ingress or LoadBalancer

We manage and monitor this using:

* `kubectl`
* Prometheus & Grafana
* Centralized logging (ELK or similar)

The exact numbers vary by environment:

* DEV has fewer replicas
* PROD has higher replicas for high availability

---

## 4️⃣ Deployment Strategy – Single or Multiple Pipelines

**Answer:**

We mostly use a **single pipeline**, but it is **branch-aware and environment-aware**.

Pipeline behavior changes based on:

* Git branch
* Environment
* Approval gates

Example:

* Feature branches → CI only
* Develop branch → CI + deploy to DEV
* Release branch → deploy to UAT
* Main/Master branch → deploy to Production

This keeps the pipeline **centralized, manageable, and auditable**, instead of maintaining multiple Jenkins jobs.

---

## 5️⃣ Deploying Partial Services (6 out of 10 to Production)

**Answer:**

In microservices architecture, we **deploy services independently**.

If only **6 out of 10 services** need to go to production:

* Only those services are built and deployed
* Other services remain untouched

This is handled by:

* Separate repositories per service **OR**
* Mono-repo with service-level pipeline triggers

Each service has:

* Its own Docker image
* Its own Helm chart or Kubernetes manifest
* Its own deployment pipeline

So production deployment is **service-specific**, not environment-wide.

---

## 6️⃣ Requirements Gathering & Post-Deployment Validation

**Answer:**

Requirements come from:

* Jira tickets
* Release notes
* Sprint planning discussions
* Direct communication with developers or product owners

Once Jenkins finishes:

* We verify deployment using:

  * `kubectl rollout status`
  * Health check endpoints
  * Application logs
* We monitor:

  * Error rates
  * Pod restarts
  * Latency and resource usage

For production:

* We rely on **monitoring dashboards**
* Alerts from Prometheus or cloud monitoring
* Sometimes smoke tests or sanity checks

If everything is green, the deployment is considered successful.

---

## 7️⃣ Git Branching for DEV, UAT & PROD

**Answer:**

Yes, we use **separate Git branches**.

Typical setup:

* `develop` → DEV
* `release` or `uat` → UAT
* `main/master` → Production

Why separate branches:

* Code stability increases as we move forward
* Production code remains protected
* Easier rollback and hotfix management
* Controlled release process

This avoids unstable code reaching production accidentally.

---

## 8️⃣ Production Bugfix When Rollback Is Not Possible

**Answer:**

If rollback is not possible due to:

* Database changes
* Backend API changes

We follow a **hotfix strategy**:

* Create a **hotfix branch from master**
* Apply minimal, targeted fix
* Test it quickly in a controlled environment
* Deploy directly to production

After production fix:

* The same fix is merged back into **develop**
* This ensures future releases include the fix

This is a very common real-world production scenario.

---

## 9️⃣ Hotfix Branch – Merge Strategy

**Answer:**

Yes, after fixing the issue:

* The hotfix branch is merged into **master**
* And also merged into **develop**

Why:

* Master gets the immediate fix
* Develop stays in sync
* Avoids reintroducing the same bug in future releases

Skipping merge to develop can cause regression later.

---

## 🔟 Release Versioning Strategy

**Answer:**

We follow **semantic versioning**:

* `MAJOR.MINOR.PATCH`

Examples:

* `1.2.0` → new feature release
* `1.2.1` → bug fix
* `2.0.0` → breaking change

Versioning is applied to:

* Git tags
* Docker images
* Helm chart versions

This helps with:

* Traceability
* Rollbacks
* Audit and compliance

---

## 1️⃣1️⃣ Single Docker Image vs Separate Images per Environment

**Answer:**

We follow the principle of **“build once, deploy everywhere.”**
So we **create a single Docker image** and deploy the same image to **DEV, UAT, and Production**.

Why:

* Ensures **consistency across environments**
* Avoids environment-specific bugs
* Improves traceability and rollback
* Aligns with DevOps best practices

The image remains the same; only **configuration changes per environment**, like:

* Environment variables
* ConfigMaps
* Secrets
* Helm values

---

## 1️⃣2️⃣ Can One Image Be Used Across All Environments?

**Answer:**

Yes, **one Docker image should be used for all environments**.

We never bake environment-specific values into the image.
Instead, we externalize configuration using:

* Kubernetes ConfigMaps
* Secrets
* Helm values files
* Runtime environment variables

This ensures:

* No rebuilds per environment
* Faster deployments
* Better security and auditability

---

## 1️⃣3️⃣ Image Lifecycle Management in Nexus / Artifactory

**Answer:**

We manage image lifecycle using:

* **Retention policies**
* **Tagging strategies**
* **Automated cleanup jobs**

Typical approach:

* Keep:

  * Latest N images (for example, last 20)
  * All production-tagged images
* Purge:

  * Old snapshots
  * Untagged images
  * Failed or unused builds

This cleanup is usually automated using:

* Nexus lifecycle policies
* Scheduled cleanup scripts
* Jenkins cleanup jobs

---

## 1️⃣4️⃣ Handling Large Number of Images in Nexus

**Answer:**

At month-end, when many images accumulate:

* We rely on **image tagging**

  * `latest`
  * semantic versions
  * environment-specific tags (prod-release)
* Production images are **never auto-deleted**
* DEV and UAT images follow aggressive cleanup

Retention differs by environment:

* DEV → short retention
* UAT → medium retention
* PROD → long-term retention

This balances **storage cost and traceability**.

---

## 1️⃣5️⃣ Dockerfile for Node.js – Best Practices

**Answer:**

We use **multi-stage Docker builds** for Node.js.

Typical choices:

* Base image: `node:18-alpine`
* Reason:

  * Smaller size
  * Faster build
  * Security-friendly

Steps:

* First stage:

  * Install dependencies
  * Build application
* Second stage:

  * Copy only build artifacts
  * Exclude dev dependencies

Final image size is usually **under 150–200 MB**, sometimes even smaller.

---

## 1️⃣6️⃣ Managing `node_modules`

**Answer:**

We **do not copy `node_modules` from local machines**.

Best practice:

* Use `package-lock.json`
* Run `npm ci` during build
* Cache dependencies at Docker layer level

This ensures:

* Clean, reproducible builds
* No local dependency mismatch
* Faster rebuilds due to Docker layer caching

---

## 1️⃣7️⃣ Handling Large Docker Image Size

**Answer:**

If the image becomes large, we:

* Switch to `alpine` base images
* Use multi-stage builds
* Remove unnecessary tools and files
* Exclude dev dependencies
* Use `.dockerignore`

We also scan images using:

* Trivy
* Snyk

This improves **performance, security, and cost efficiency**.

---

## 1️⃣8️⃣ Terraform – What Do You Use It For?

**Answer:**

We use Terraform for:

* Provisioning cloud infrastructure
* Managing Kubernetes clusters
* Creating networking components
* IAM roles and policies
* Load balancers, databases, EC2 instances

Terraform allows us to manage infrastructure as **code**, ensuring:

* Consistency
* Version control
* Easy recreation

---

## 1️⃣9️⃣ Real Terraform Use Case

**Answer:**

Recently, I used Terraform to:

* Create EKS cluster
* Configure node groups
* Setup VPC, subnets, route tables
* Create IAM roles
* Integrate load balancers

We used:

* Remote backend (S3 + DynamoDB)
* Variables for environment-specific values
* Modules for reusability

---

## 2️⃣0️⃣ Terraform Workspaces

**Answer:**

Yes, I have used Terraform workspaces.

Workspaces help manage:

* DEV
* UAT
* PROD

Using the same codebase with:

* Different state files
* Different variable values

This avoids code duplication and keeps infrastructure consistent across environments.

---

## 2️⃣1️⃣ Differentiating Environments in Terraform

**Answer:**

We differentiate environments in Terraform using a combination of:

* **Variables**
* **Workspaces**
* **Separate state files**
* **Environment-specific tfvars**

Typical setup:

* `variables.tf` → common variables
* `dev.tfvars`, `uat.tfvars`, `prod.tfvars` → environment values
* Remote backend with separate state per environment

Example differences:

* Instance size
* Auto-scaling limits
* Number of replicas
* Network CIDR ranges

This ensures the **same Terraform code** works across environments while keeping configurations isolated.

---

## 2️⃣2️⃣ Multi-Environment Management Using Terraform

**Answer:**

Multi-environment management is done using:

* A **single Terraform codebase**
* Environment-specific inputs
* Separate backends or workspaces

Flow:

* Same modules reused
* Different variable values per environment
* Separate state to avoid conflicts

This avoids:

* Code duplication
* Configuration drift
* Manual infrastructure changes

Everything is controlled through **Git + Terraform plan/apply**.

---

## 2️⃣3️⃣ Writing Reusable Terraform Modules (Example: EC2)

**Answer:**

Yes, I am responsible for writing Terraform modules.

Best practices I follow:

* One resource type per module
* Clear input/output variables
* No hardcoded values
* Use defaults where possible
* Proper tagging standards
* Versioned modules

EC2 module structure:

* `main.tf` → EC2 resource
* `variables.tf` → configurable inputs
* `outputs.tf` → instance ID, IP, etc.

This allows the same module to be reused across:

* DEV
* UAT
* PROD
* Multiple projects

---

## 2️⃣4️⃣ Terraform Module Standardization

**Answer:**

We standardize modules by:

* Enforcing naming conventions
* Mandatory tagging (env, owner, cost-center)
* Version control for modules
* Documentation for usage
* Code reviews before changes

This helps:

* Reduce errors
* Improve reuse
* Maintain consistency across teams

---

## 2️⃣5️⃣ Python – Exception Handling

**Answer:**

In Python, exceptions are used to handle **unexpected runtime errors** gracefully.

Common examples:

* File not found
* Network failure
* Invalid input

We use:

* `try`, `except`, `finally`
* Custom exceptions when needed

Exceptions should be used for **exceptional cases**, not normal logic flow.

---

## 2️⃣6️⃣ Python Exception – Simple Example

**Answer:**

Example:

```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found")
finally:
    print("Execution completed")
```

Where to use exceptions:

* External dependencies
* I/O operations
* API calls

Where NOT to use exceptions:

* Normal conditional checks
* Business logic decisions

---

## 2️⃣7️⃣ Reading a File Line by Line in Python

**Answer:**

The best way is using a context manager:

```python
with open("abc.txt", "r") as file:
    for line in file:
        print(line.strip())
```

Why:

* Memory efficient
* Automatically closes file
* Clean and readable code

---

## 2️⃣8️⃣ Experience with AWS Lambda

**Answer:**

Yes, I have worked with **AWS Lambda functions**.

Use cases:

* Event-driven automation
* File processing in S3
* Scheduled jobs
* API backends
* CI/CD automation tasks

Lambda is serverless, so:

* No server management
* Auto scaling
* Pay only for execution time

---

## 2️⃣9️⃣ AWS Lambda Handlers – How They Work

**Answer:**

A Lambda handler is the **entry point** of the function.

Format:

```python
def lambda_handler(event, context):
    return "Hello World"
```

* `event` → input data (API, S3, SNS, etc.)
* `context` → runtime metadata

When an event occurs:

* AWS invokes the handler
* Code executes
* Output is returned or passed to the next service

---




