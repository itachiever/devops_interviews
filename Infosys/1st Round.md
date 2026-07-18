# Interview Questions : 1st Round

1. Can you introduce yourself?

2. How many years of experience do you have?

3. Do you have experience working in the banking domain?

4. Are you comfortable relocating to Hyderabad and working from office?

5. What is the difference between Terraform Plan and Terraform Apply?

6. Are you aware of Ansible? How does Terraform differ from Ansible, Chef, or Puppet?

7. What is a Terraform Provider?

8. What is Terraform State File and why is it important?

9. What is Terraform Drift?

10. What is Terraform Validate and when do we use it?

11. What are Terraform Modules and why do we use them?

12. What are the best practices for handling secrets in Terraform?

13. Explain Terraform Architecture. What are the main components and how does Terraform work internally?

14. What does Terraform Init do?

15. What are Terraform Data Sources?

16. What is Terraform Taint?

17. What is Blue-Green Deployment?

18. In Kubernetes, what is a Pod?

19. What is the difference between Pod, Deployment, and Service in Kubernetes?

20. What is Kubelet and why do we use it?

21. What happens when a Kubernetes Pod goes into CrashLoopBackOff?

22. When a Pod continuously restarts in CrashLoopBackOff, what happens internally and which component is responsible for restarting it?

23. Are you familiar with Linux and Windows machines?

24. Have you worked on server packaging, image management, or server restoration activities?

25. What is an Ansible Playbook?

26. Explain the Ansible Playbook execution flow.

27. What is the difference between Terraform and Ansible?

28. Why do we use multiple tools like Terraform and Ansible? Why can't one tool handle both infrastructure provisioning and configuration management?

29. What is Idempotency?

30. What is the difference between Ansible Shell module and Command module?

31. What are Ansible Variables?

32. What is an Ansible Role?

33. What is the difference between Ansible Roles and Handlers?

34. How does Ansible execution work internally?

35. How do you implement zero downtime deployment?

36. An Ansible playbook is failing on one or two servers out of 100 servers. How do you troubleshoot?

37. An Ansible playbook normally completes quickly but suddenly takes more than 30 minutes. How do you troubleshoot?

38. A deployment is running on 50 servers and fails. What is your rollback strategy?

39. What is the difference between Git and GitHub?

40. What is a Git Branch?

41. What is the difference between Git Fetch and Git Pull?

42. What do you do when there is a Git Merge Conflict?

43. What is the difference between Git Merge and Git Rebase?

44. What is Git Fork?

45. What is Git Cherry-pick?

46. What are Git Hooks?

47. If you accidentally delete a Git branch, how do you restore it? What command will you use?

48. You pushed wrong code to the production branch. How do you resolve it?

49. For restoring wrong production code, would you use Git Reset or Git Revert? Why?

50. Explain your Linux knowledge. What activities have you performed in Linux?

51. When you receive an alert that resource utilization is high, what steps do you take to troubleshoot?

52. Do you have any questions for me?

53. What is your notice period?



# Answers


## 1. Can you introduce yourself?

**Answer:**

Thanks for the opportunity. My name is YOUR NAME. I am currently working as a **DevSecOps Engineer** with around **4.5 years of experience** in DevOps, DevSecOps, cloud infrastructure, and automation.

I started my career with **YOUR FIRST COMPANY NAME**, where I worked for around 2.5 years on DevOps activities. Currently, I am working with **CURRENT COMPANY NAME**, deployed at a client location **CLIENT NAME**, which is a fintech payment gateway solution provider.

In my current role, I am primarily responsible for **CI/CD automation, infrastructure provisioning, security integration, and deployment automation**. I work with tools like **Jenkins, GitLab, Terraform, Ansible, Docker, Kubernetes, and cloud platforms like AWS and Azure**.

I have hands-on experience in implementing security practices across the pipeline, including **SAST, SCA, SBOM generation, container image scanning, and secret detection** using tools like Fortify, Sonatype IQ, Trivy, and GitLeaks.

I have worked on both **VM-based and Kubernetes-based deployments**, including infrastructure automation using Terraform modules and container orchestration using Kubernetes.

I also have experience with monitoring and observability tools like **Prometheus and Grafana**, along with Linux administration, shell scripting, and automation using Python.

Overall, my experience is focused on building secure, scalable, and automated DevOps environments.



# 2. How many years of experience do you have?

**Answer:**

I have around **4.5 years of overall IT experience**, with hands-on experience primarily in **DevOps and DevSecOps engineering**.

My experience includes CI/CD automation, cloud infrastructure, Terraform-based IaC, Kubernetes, containerization, security automation, and production support activities.



# 3. Do you have experience working in the banking domain?

**Answer:**

Yes, I have experience working in the **banking and fintech domain**.

Currently, I am working with **CLIENT NAME**, which provides payment gateway solutions for banking clients. In this project, I am involved in DevSecOps activities such as CI/CD automation, security scanning, infrastructure automation, and deployment management.

Earlier, while working with PREVIOUS COMPOANY, I was involved in an **e-governance domain project**.



# 4. Are you comfortable relocating to Hyderabad and working from office?

**Answer:**

Yes, I am comfortable relocating to Hyderabad and working from office as per the organization's requirements.

I am currently looking for opportunities in the southern region, so Hyderabad would be a suitable location for me.



# 5. What is the difference between Terraform Plan and Terraform Apply?

**Answer:**

**Terraform Plan** and **Terraform Apply** are two important stages in the Terraform workflow.

* **Terraform Plan**:

  * It is a dry-run operation that shows what changes Terraform is going to make before actually applying them.
  * It compares the current infrastructure state with the desired configuration and provides an execution plan.
  * It helps us review changes before deployment.

Example:

```bash
terraform plan
```

* **Terraform Apply**:

  * It executes the planned changes and creates, updates, or deletes the infrastructure resources based on the Terraform configuration.

Example:

```bash
terraform apply
```

In short, **Terraform Plan is used for previewing changes, whereas Terraform Apply is used for executing those changes.**



# 6. Are you aware of Ansible? How does Terraform differ from Ansible, Chef, or Puppet?

**Answer:**

Yes, I have hands-on experience with Ansible as well.

The main difference is:

* **Terraform** is primarily an **Infrastructure as Code (IaC) tool** used for provisioning and managing infrastructure resources such as:

  * Virtual machines
  * Networks
  * Load balancers
  * Cloud resources

* **Ansible, Chef, and Puppet** are mainly **configuration management tools** used after infrastructure provisioning to configure systems.

For example:

* Terraform can create an AWS EC2 instance.
* Ansible can install required packages, configure applications, update configurations, and manage services on that EC2 instance.

Terraform follows a **declarative approach** where we define the desired infrastructure state, while Ansible is mainly used for configuration and automation tasks.



# 7. What is a Terraform Provider?

**Answer:**

A Terraform Provider is a plugin that allows Terraform to communicate with external platforms and APIs.

Providers are responsible for:

* Authenticating with the target platform.
* Understanding available resources.
* Creating, updating, and deleting resources.

For example:

* AWS Provider allows Terraform to manage AWS resources.
* Azure Provider allows Terraform to manage Azure resources.
* Kubernetes Provider allows Terraform to manage Kubernetes resources.

Terraform uses providers to interact with the required infrastructure platforms.



# 8. What is Terraform State File and why is it important?

**Answer:**

Terraform State File (`terraform.tfstate`) stores the current state information of the infrastructure managed by Terraform.

It maintains the mapping between:

* Terraform configuration files
* Actual infrastructure resources

It is important because Terraform uses the state file to:

* Track existing resources.
* Identify what changes need to be applied.
* Detect infrastructure drift.
* Maintain consistency between desired and actual state.

In production environments, we generally store the state file in a **remote backend** such as AWS S3 with a locking mechanism using DynamoDB to avoid conflicts when multiple engineers work simultaneously.



# 9. What is Terraform Drift?

**Answer:**

Terraform drift occurs when the actual infrastructure state becomes different from the desired state defined in Terraform configuration.

For example:

* Terraform created an AWS resource.
* Later, someone manually changes the configuration through the AWS Console.
* Now the actual infrastructure does not match Terraform state.

This difference is called **Terraform Drift**.

We can identify drift by running:

```bash
terraform plan
```

Terraform compares the current infrastructure with the state file and highlights the differences.



# 10. What is Terraform Validate and when do we use it?

**Answer:**

Terraform Validate is a command used to check whether Terraform configuration files are syntactically correct and internally consistent.

It validates:

* Terraform syntax.
* Resource configuration.
* Required arguments.
* Configuration structure.

Example:

```bash
terraform validate
```

We usually run it during development or as part of CI/CD pipeline validation before deploying infrastructure changes.



# 11. What are Terraform Modules and why do we use them?

**Answer:**

Terraform Modules are reusable collections of Terraform configuration files that group multiple resources together.

We use modules to:

* Avoid writing duplicate Terraform code.
* Improve reusability.
* Maintain standard infrastructure patterns.
* Simplify infrastructure management across environments.

For example:

* Creating a reusable VPC module.
* Creating reusable Kubernetes cluster modules.
* Creating reusable application infrastructure modules.

Instead of creating the same resources repeatedly, we can call the module whenever required.



# 12. What are the best practices for handling secrets in Terraform?

**Answer:**

The best practices for managing secrets in Terraform are:

* Avoid storing secrets directly inside Terraform files or variable files.

* Use external secret management solutions such as:

  * HashiCorp Vault
  * AWS Secrets Manager
  * Azure Key Vault

* Use environment variables for sensitive values when required.

* Mark sensitive variables using Terraform sensitive attributes.

Example:

```hcl
variable "password" {
  sensitive = true
}
```

* Secure Terraform state files because they may contain sensitive information.
* Store state remotely with proper access control and encryption.



# 13. Explain Terraform Architecture. What are the main components and how does Terraform work internally?

**Answer:**

Terraform architecture mainly consists of the following components:

### 1. Terraform Core

* The Terraform engine responsible for:

  * Reading configuration files.
  * Creating execution plans.
  * Managing resource lifecycle.

### 2. Configuration Files

* Terraform configurations are written using **HCL (HashiCorp Configuration Language)**.
* These files define the desired infrastructure state.

### 3. Providers

* Providers act as plugins that allow Terraform to communicate with platforms like AWS, Azure, GCP, and Kubernetes.

### 4. State File

* Stores information about currently managed infrastructure.

### 5. Backend

* Defines where Terraform state is stored.
* Example: AWS S3 backend.

The workflow is:

1. Write Terraform configuration.
2. Run `terraform init` to initialize providers and backend.
3. Run `terraform plan` to preview changes.
4. Run `terraform apply` to provision or modify infrastructure.



# 14. What does Terraform do?

**Answer:**

Terraform is an **Infrastructure as Code (IaC) tool** used to automate infrastructure provisioning and management.

It allows us to define infrastructure using configuration files and automatically create, modify, or delete resources.

Terraform helps organizations achieve:

* Automation.
* Consistency.
* Version-controlled infrastructure.
* Repeatable deployments.
* Reduced manual errors.

It supports multiple platforms including AWS, Azure, GCP, Kubernetes, and many other providers.



# 15. What are Terraform Data Sources?

**Answer:**

Terraform Data Sources allow Terraform to retrieve information about existing resources that are not managed by Terraform.

They are used when we need to reference existing infrastructure details.

For example:

* Existing VPC ID.
* Existing AMI ID.
* Existing subnet information.

Example:

```hcl
data "aws_vpc" "existing" {
  default = true
}
```

Terraform reads the information from the external resource and allows us to use it in our configuration.



# 16. What is Terraform Taint?

**Answer:**

Terraform Taint is a mechanism used to mark a resource as requiring recreation during the next Terraform apply.

It is useful when:

* A resource is corrupted.
* A resource configuration is not working properly.
* We want Terraform to destroy and recreate a specific resource.

Example:

```bash
terraform taint aws_instance.example
```

During the next `terraform apply`, Terraform will recreate that resource.

*(Note: In newer Terraform versions, `terraform apply -replace` is preferred over taint.)*



# 17. What is Blue-Green Deployment?

**Answer:**

Blue-Green Deployment is a deployment strategy where we maintain two identical environments:

* **Blue Environment**

  * Current production environment.

* **Green Environment**

  * New version of the application.

The new version is deployed and tested in the green environment. Once validation is successful, traffic is switched from blue to green.

Advantages:

* Zero downtime deployment.
* Easy rollback.
* Reduced deployment risk.

If issues occur after switching traffic, we can quickly route traffic back to the blue environment.



# 18. In Kubernetes, what is a Pod?

**Answer:**

A Pod is the smallest deployable unit in Kubernetes.

A Pod can contain:

* One or more containers.
* Shared network namespace.
* Shared storage volumes.

Usually, a Pod runs one application container, but multiple tightly coupled containers can run together inside the same Pod.

Pods are ephemeral in nature, meaning they can be created, destroyed, and recreated based on workload requirements.



# 19. What is the difference between Pod, Deployment, and Service in Kubernetes?

**Answer:**

### Pod:

* The smallest execution unit in Kubernetes.
* Runs one or more containers.
* Represents the running instance of an application.

### Deployment:

* Manages the lifecycle of Pods.
* Ensures the required number of replicas are running.
* Provides features like:

  * Scaling
  * Rolling updates
  * Rollbacks

### Service:

* Provides stable network access to Pods.
* Provides a stable IP address and DNS name.
* Routes traffic to the appropriate Pods.

In simple terms:

* **Pod runs the application.**
* **Deployment manages Pods.**
* **Service exposes Pods for communication.**



# 20. What is Kubelet and why do we use it?

**Answer:**

Kubelet is an agent that runs on every Kubernetes worker node.

Its responsibilities include:

* Communicating with the Kubernetes API Server.
* Ensuring containers described in Pod specifications are running.
* Monitoring container health.
* Working with the container runtime such as Docker/containerd to manage containers.

In simple terms, **Kubelet ensures that the desired state defined by Kubernetes is maintained on each worker node.**


# 21. What happens when a Kubernetes Pod goes into CrashLoopBackOff?

**Answer:**

CrashLoopBackOff means that a container inside a Pod is repeatedly starting and failing, and Kubernetes is temporarily delaying the restart attempts.

Common reasons for CrashLoopBackOff include:

* Application startup failures.
* Incorrect application configuration.
* Missing or incorrect environment variables.
* Secret or ConfigMap issues.
* Container image issues.
* Resource limitations such as Out Of Memory (OOM).
* Dependency failures.

When this happens, I troubleshoot by checking:

```bash
kubectl get pods
kubectl describe pod <pod-name>
kubectl logs <pod-name>
```

I check:

* Container logs.
* Pod events.
* Application errors.
* Resource utilization.
* Configuration issues.

After identifying the root cause, I fix the issue and redeploy the application.



# 22. When a Pod continuously restarts in CrashLoopBackOff, what happens internally and which component is responsible for restarting it?

**Answer:**

When a Pod enters CrashLoopBackOff, the restart process works as follows:

* The **kubelet**, which runs on the worker node, continuously monitors the containers running on that node.
* When a container exits unexpectedly, kubelet checks the Pod's **restart policy**.
* Based on the restart policy, kubelet instructs the container runtime, such as **containerd**, to restart the container.
* Kubernetes applies an increasing delay between restart attempts using a backoff mechanism to avoid continuous rapid restarts.

The main component responsible for monitoring and restarting containers at the node level is **kubelet**.



# 23. Are you familiar with Linux and Windows machines?

**Answer:**

Yes, I have worked with both Linux and Windows environments.

My primary experience is with Linux-based systems because most of my DevOps and DevSecOps activities involve Linux servers.

I have worked on:

* Linux server administration.
* Application deployment activities.
* Package installation and management.
* Log monitoring and troubleshooting.
* Shell scripting and automation.
* Service management.

I also have exposure to Windows environments based on application requirements and support activities.



# 24. Have you worked on server packaging, image management, or server restoration activities?

**Answer:**

Yes, I have experience with image management mainly at the container level.

My experience includes:

* Building Docker images using Dockerfiles.
* Managing container images.
* Tagging and pushing images to registries like Nexus and container registries.
* Scanning container images using security tools like Trivy.
* Maintaining image versions as part of CI/CD pipelines.

I also have exposure to server-level image management and restoration activities as part of infrastructure support.



# 25. What is an Ansible Playbook?

**Answer:**

An Ansible Playbook is a YAML-based automation file that defines a sequence of tasks to be executed on target machines.

It describes:

* What actions need to be performed.
* Which hosts should execute those actions.
* Required variables and configurations.

For example, an Ansible Playbook can be used to:

* Install software packages.
* Configure applications.
* Update configurations.
* Manage services.

Example flow:

1. Connect to target servers.
2. Install required packages.
3. Update configuration files.
4. Restart services.

Playbooks are reusable and help automate configuration management activities.



# 26. Explain the Ansible Playbook execution flow.

**Answer:**

The Ansible Playbook execution flow is:

1. **Inventory**

   * Ansible reads the inventory file to identify target hosts.

2. **Playbook Parsing**

   * Ansible reads the YAML playbook and identifies the tasks to execute.

3. **Connection Establishment**

   * Ansible connects to target machines using SSH or WinRM.

4. **Task Execution**

   * Tasks are executed sequentially on target hosts.

5. **Module Execution**

   * Ansible uses modules such as package, service, copy, and command modules to perform actions.

6. **Result Collection**

   * Ansible collects execution results and reports success, failure, or changes.

Ansible follows an idempotent approach, meaning repeated execution should bring the system to the desired state without unnecessary changes.



# 27. What is the difference between Terraform and Ansible?

**Answer:**

Terraform and Ansible are both automation tools, but they solve different problems.

### Terraform:

* Primarily used for **Infrastructure as Code (IaC)**.
* Used to provision infrastructure resources.
* Examples:

  * Virtual machines.
  * Networks.
  * Load balancers.
  * Cloud resources.

### Ansible:

* Primarily used for **configuration management and automation**.
* Used after infrastructure provisioning.
* Examples:

  * Installing packages.
  * Managing configurations.
  * Deploying applications.
  * Managing services.

For example:

* Terraform creates an AWS EC2 instance.
* Ansible installs applications and configures that server.



# 28. Why do we use multiple tools like Terraform and Ansible? Why can't one tool handle both infrastructure provisioning and configuration management?

**Answer:**

We use multiple tools because each tool is designed for a specific purpose.

Terraform is strong in:

* Infrastructure provisioning.
* Resource lifecycle management.
* Cloud infrastructure automation.

Ansible is strong in:

* Configuration management.
* Application deployment.
* Server automation.
* Patch management.

Although Terraform has some configuration capabilities and Ansible can provision infrastructure, organizations usually separate responsibilities because:

* Terraform provides better infrastructure lifecycle management.
* Ansible provides better configuration and operational automation.

Using both tools together provides better flexibility and maintainability.



# 29. What is Idempotency?

**Answer:**

Idempotency means that executing the same operation multiple times produces the same final result without causing unwanted changes.

For example:

* If an Ansible playbook installs a package that is already installed, running the playbook again will not reinstall or create unnecessary changes.
* It checks the current state and only performs actions if required.

Idempotency helps achieve:

* Reliable automation.
* Consistent system configuration.
* Safe repeated executions.



# 30. What is the difference between Ansible Shell module and Command module?

**Answer:**

The main difference is how they execute commands.

### Command Module:

* Executes commands directly on the target system.
* Does not process commands through a shell.
* More secure because shell features are not available.

Example:

```yaml
- name: Check uptime
  command: uptime
```

### Shell Module:

* Executes commands through the system shell.
* Supports shell features like:

  * Pipes (`|`)
  * Redirection (`>`)
  * Environment variables.

Example:

```yaml
- name: Search logs
  shell: cat app.log | grep ERROR
```

Generally, we prefer the **command module** whenever possible and use the **shell module** only when shell-specific functionality is required.



# 31. What are Ansible Variables?

**Answer:**

Ansible Variables are used to store dynamic values that can be reused throughout playbooks.

They help avoid hardcoding values and make automation more flexible.

Variables can be defined in:

* Playbooks.
* Inventory files.
* Variable files.
* Roles.

Examples:

* Package names.
* Server configurations.
* Environment-specific values.

Example:

```yaml
app_port: 8080
```

Then we can reference this variable inside the playbook.



# 32. What is an Ansible Role?

**Answer:**

An Ansible Role is a reusable structure that organizes automation content into a standard directory format.

Roles help organize:

* Tasks.
* Variables.
* Templates.
* Handlers.
* Files.
* Defaults.

Instead of maintaining large playbooks, we can create reusable roles and use them across multiple projects.

For example:

* Web server installation role.
* Database configuration role.
* Application deployment role.



# 33. What is the difference between Ansible Roles and Handlers?

**Answer:**

### Ansible Role:

* A reusable collection of automation components.
* Used to organize and reuse playbook logic.
* Contains tasks, variables, templates, files, and handlers.

### Ansible Handler:

* A special task that runs only when triggered by another task.
* Usually used for actions like restarting services after configuration changes.

Example:

If an Nginx configuration file changes:

* The task updates the configuration.
* The handler restarts the Nginx service.

In simple terms:

* **Role = reusable automation structure.**
* **Handler = triggered action executed when changes occur.**



# 34. How does Ansible execution work internally?

**Answer:**

Ansible execution flow works as follows:

1. Ansible reads the inventory file to identify target hosts.
2. It loads the playbook and determines required tasks.
3. It establishes connection with remote machines using SSH/WinRM.
4. It transfers required modules to the target systems.
5. Modules execute the required actions.
6. Results are returned back to the Ansible controller.
7. Ansible displays execution status such as changed, successful, or failed.

Ansible follows an agentless architecture, meaning no Ansible agent needs to be installed on managed nodes.



# 35. How do you implement zero downtime deployment?

**Answer:**

Zero downtime deployment can be achieved using proper deployment strategies and high availability practices.

Approaches include:

### Rolling Deployment:

* Gradually replaces old application instances with new versions.
* Ensures some instances remain available during deployment.

### Blue-Green Deployment:

* Maintains two identical environments.
* Deploys the new version to the idle environment.
* Switches traffic after validation.

### Additional practices:

* Load balancing.
* Multiple application replicas.
* Health checks.
* Automated rollback mechanisms.

In Kubernetes, we can achieve this using Deployment strategies with rolling updates.



# 36. An Ansible playbook is failing on one or two servers out of 100 servers. How do you troubleshoot?

**Answer:**

I would troubleshoot it step-by-step:

1. Identify the failed servers from Ansible execution output.

2. Check the failed task and error message.

3. Verify connectivity:

```bash
ansible all -m ping
```

4. Check:

* SSH connectivity.
* Permissions.
* Required packages.
* Configuration differences.

5. Run the playbook only on the failed servers for debugging.

Example:

```bash
ansible-playbook playbook.yml --limit failed-server
```

6. Compare the failed servers with successful servers to identify configuration differences.

After identifying the root cause, I fix the issue and rerun the playbook.



# 37. An Ansible playbook normally completes quickly but suddenly takes more than 30 minutes. How do you troubleshoot?

**Answer:**

I would troubleshoot by checking:

1. Identify which task is taking more time from Ansible output.

2. Check connectivity issues between controller and target servers.

3. Verify:

* Network latency.
* SSH response time.
* Server resource utilization.

4. Check if any task is waiting due to:

* Package installation.
* External dependency.
* Long-running commands.

5. Enable detailed logging:

```bash
ansible-playbook playbook.yml -vvv
```

6. Optimize slow tasks by:

* Using parallel execution.
* Improving task logic.
* Removing unnecessary operations.



# 38. A deployment is running on 50 servers and fails. What is your rollback strategy?

**Answer:**

My rollback approach depends on the deployment method and application architecture.

Steps:

1. Identify the failure point and stop further deployment.

2. Roll back to the previous stable version.

Examples:

* Deploy previous application artifact.
* Restore previous Docker image version.
* Use Kubernetes rollback:

```bash
kubectl rollout undo deployment <deployment-name>
```

3. Validate application health after rollback.

4. Analyze the root cause and fix the issue before attempting redeployment.

The goal is to restore service availability first and then perform detailed RCA.



# 39. What is the difference between Git and GitHub?

**Answer:**

Git and GitHub are related but different.

### Git:

* A distributed version control system.
* Installed locally on developer machines.
* Used to track code changes, create branches, and manage commits.

### GitHub:

* A cloud-based platform that hosts Git repositories.
* Provides collaboration features like:

  * Pull requests.
  * Code reviews.
  * Issue tracking.
  * Repository management.

In simple terms:

* **Git manages source code versions.**
* **GitHub provides a platform to collaborate and host Git repositories.**



# 40. What is a Git Branch?

**Answer:**

A Git Branch is an independent line of development that allows teams to work on changes without affecting the main codebase.

Branches are commonly used for:

* Feature development.
* Bug fixes.
* Hotfixes.
* Release management.

Example workflow:

* Developer creates a feature branch.
* Makes code changes.
* Commits and pushes changes.
* Raises a Pull Request.
* After review and validation, changes are merged into the main branch.

Branches help teams maintain clean and organized development workflows.



# 41. What is the difference between Git Fetch and Git Pull?

**Answer:**

The difference between `git fetch` and `git pull` is:

### Git Fetch:

* Downloads the latest changes, commits, and references from the remote repository.
* Does not modify the current working branch.
* Allows us to review changes before merging.

Example:

```bash
git fetch origin
```

### Git Pull:

* Downloads the latest changes from the remote repository and automatically merges them into the current branch.
* It is a combination of:

```bash
git fetch + git merge
```

Example:

```bash
git pull origin main
```

In simple terms:

* **Git fetch only downloads changes.**
* **Git pull downloads and applies changes to the current branch.**



# 42. What do you do when there is a Git Merge Conflict?

**Answer:**

A merge conflict occurs when Git cannot automatically merge changes because the same part of a file has been modified differently in two branches.

I handle merge conflicts by following these steps:

1. Identify the conflicting files:

```bash
git status
```

2. Open the files and review the conflict markers:

```text
<<<<<<<
=======
>>>>>>>
```

3. Manually resolve the required changes.

4. Add the resolved files:

```bash
git add <file-name>
```

5. Commit the merge:

```bash
git commit
```

6. Push the changes after validation.

Before merging, I also ensure I pull the latest code to minimize conflicts.



# 43. What is the difference between Git Merge and Git Rebase?

**Answer:**

Both Git Merge and Git Rebase are used to integrate changes from one branch into another, but they work differently.

### Git Merge:

* Combines two branches by creating a new merge commit.
* Maintains the complete branch history.
* Safer for shared branches.

Example:

```bash
git merge feature-branch
```

### Git Rebase:

* Moves or reapplies commits from one branch onto another branch.
* Creates a cleaner, linear commit history.
* Rewrites commit history.

Example:

```bash
git rebase main
```

In practice:

* I prefer **merge** for shared branches like main/master.
* I use **rebase** for cleaning up local feature branch history before creating a pull request.



# 44. What is a Git Fork?

**Answer:**

A Git Fork is a copy of an existing repository created under another user's or organization's account.

It allows users to:

* Make independent changes.
* Modify the code without affecting the original repository.
* Submit changes back using a Pull Request.

For example:

* I can fork an open-source repository.
* Make required changes in my forked repository.
* Raise a Pull Request to the original repository.

Forking is commonly used in open-source collaboration.



# 45. What is Git Cherry-Pick?

**Answer:**

Git Cherry-Pick is a command used to apply a specific commit from one branch into another branch without merging the complete branch.

Example:

```bash
git cherry-pick <commit-id>
```

Use cases:

* Moving a specific bug fix from one branch to another.
* Applying a hotfix commit to a production branch.

For example:

* A bug fix is committed in a development branch.
* Instead of merging the entire branch, we can cherry-pick only that required commit into the production branch.



# 46. What are Git Hooks?

**Answer:**

Git Hooks are scripts that automatically execute at specific points during Git operations.

They are used to automate tasks such as:

* Code validation.
* Running tests.
* Checking commit messages.
* Performing security checks.

Examples:

### Pre-commit Hook:

* Runs before creating a commit.
* Can be used for code formatting or static analysis.

### Post-commit Hook:

* Runs after a commit is created.

### Pre-push Hook:

* Runs before pushing code to a remote repository.

Git hooks help improve code quality and enforce development standards.



# 47. If you accidentally delete a Git branch, how do you restore it? What command will you use?

**Answer:**

If I accidentally delete a Git branch, I will first try to identify the last commit reference of that deleted branch using Git reflog.

Steps:

1. Check the recent Git history:

```bash
git reflog
```

2. Identify the commit ID where the deleted branch was pointing.

3. Restore the branch using:

```bash
git checkout -b <branch-name> <commit-id>
```

or:

```bash
git branch <branch-name> <commit-id>
```

Example:

```bash
git branch feature-branch abc1234
```

If the branch was deleted only locally and the remote branch still exists, I can restore it by fetching from the remote repository:

```bash
git fetch origin
git checkout -b <branch-name> origin/<branch-name>
```



# 48. You pushed wrong code to the production branch. How do you resolve it?

**Answer:**

If wrong code is pushed to the production branch, my first priority is to restore the production environment quickly and safely.

Steps:

1. Identify the incorrect commit:

```bash
git log
```

2. Check the impact of the change.

3. For production branches, I will use **git revert** to create a new commit that safely reverses the incorrect changes.

```bash
git revert <commit-id>
```

4. Push the reverted changes:

```bash
git push origin main
```

5. Validate that the production application is working correctly.

6. Perform root cause analysis and implement preventive measures before the next deployment.

I avoid rewriting production history because production branches are usually shared by multiple teams.



# 49. For restoring wrong production code, would you use Git Reset or Git Revert? Why?

**Answer:**

For restoring wrong production code, I would use **Git Revert** instead of Git Reset.

### Git Revert:

* Creates a new commit that reverses the changes introduced by the previous commit.
* Maintains the complete Git history.
* Safer for shared branches like production.

Example:

```bash
git revert <commit-id>
```

### Git Reset:

* Moves the branch pointer back to an earlier commit.
* Removes commits from the branch history.
* Rewrites history, which can create issues for other team members.

Example:

```bash
git reset --hard <commit-id>
```

In production environments, I prefer **Git Revert** because it is safer, traceable, and follows good version control practices.



# 50. Explain your Linux knowledge. What activities have you performed in Linux?

**Answer:**

I have hands-on experience working with Linux environments as part of my DevOps and DevSecOps responsibilities.

My regular activities include:

* Working with Linux file and directory management commands.
* Managing files, permissions, and ownership.
* Installing and managing software packages.
* Performing application deployments on Linux servers.
* Managing services using system commands.
* Monitoring application and system logs.
* Troubleshooting application and server issues.
* Checking CPU, memory, disk, and network utilization.
* Writing shell scripts for automation tasks.
* Performing build and compilation activities whenever required.
* Supporting security scanning activities on Linux-based environments.

I use Linux extensively for deployment automation, troubleshooting, and operational activities.



# 51. When you receive an alert that resource utilization is high, what steps do you take to troubleshoot?

**Answer:**

When I receive a high resource utilization alert, I follow a structured troubleshooting approach.

First, I identify which resource is impacted:

* CPU utilization.
* Memory utilization.
* Disk usage.
* Disk I/O.
* Network utilization.

I check system-level metrics using commands like:

```bash
top
htop
free -m
df -h
iostat
```

Then I analyze:

* Which process is consuming high resources.
* Application logs for errors.
* Recent deployments or configuration changes.
* System performance metrics.

Based on the findings, I take appropriate action such as:

* Restarting unhealthy services if required.
* Optimizing resource-consuming processes.
* Scaling resources.
* Coordinating with application teams for application-level issues.

After resolving the issue, I perform root cause analysis and monitor the system to prevent recurrence.



# 52. Do you have any questions for me?

**Answer:**

Yes, I have a few questions:

1. Could you please share more details about the project and the team structure for this role?

2. I would like to understand the primary responsibilities and expectations from this role in the initial months.

3. Could you please explain the technology stack currently being used, especially around IaC, automation, and Nutanix-related technologies?

4. What are the next steps in the interview process?



# 53. What is your notice period?

**Answer:**

I am currently serving my notice period.

My official notice period is **90 days**, but I am actively working with my current organization regarding an early release.

I will try my best to align my availability with the organization's requirement and ensure a smooth transition before joining.

