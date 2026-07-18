## Interview Questions: 1st Round

1. Tell me about yourself, focusing on your **DevSecOps, Platform Engineering, and AgentOps/AI experience**.
2. What is your experience with **AI Ops / LLMs / AgentOps**?
3. Which **cloud platform** are you most comfortable with?
4. Which **AWS services** have you worked on?
5. Explain your **end-to-end CI/CD pipeline** in your current project.
6. How and where is **GitLeaks** integrated into your CI/CD pipeline?
7. What is your experience with **Kubernetes**?
8. Which **automation/scripting tools or languages** are you comfortable with?
9. Explain the **Terraform project/repository structure** you are using in your current project.
10. What are the **Terraform best practices** you follow?
11. How do you handle **outbound (egress) connections** in Kubernetes?
12. What **DevSecOps metrics** do you follow, and what metrics do you monitor in the **SonarQube dashboard**?
13. What is the difference between **SCA, SAST, and DAST**? Explain with an example.
14. Which **location** are you currently working from?
15. Will you be able to **travel to the Hyderabad office** for the next technical/hands-on interview? 

---

# Answers


# 1. Tell me about yourself, focusing on your DevSecOps, Platform Engineering, and AgentOps/AI experience.

### Answer

My name is **YOUR NAME**, and I have **4.3 years of IT experience**, with a strong focus on **DevSecOps, DevOps, and Cloud Platform Engineering**.

Currently, I am working as a **DevSecOps Engineer** for **CLIENT NAME**, a fintech organization where we build and secure payment applications that comply with **PCI DSS** and **RBI security guidelines**.

My primary responsibilities include designing and implementing security controls throughout the CI/CD pipeline. I integrate **SAST, DAST, SCA, container image scanning, secret scanning, and SBOM generation** to ensure vulnerabilities are identified and remediated early in the SDLC.

Our technology stack includes **GitLab, Jenkins, Docker, Kubernetes, Nexus, Fortify, Sonatype IQ Server, Trivy, GitLeaks, AWS, Azure, and Terraform**. I also work on Kubernetes deployments, infrastructure automation, security hardening, and implementing observability solutions.

Regarding **AI/AgentOps**, I have not yet worked on production AI workloads. However, I have been actively learning concepts such as **LLMs, AWS Bedrock, LangChain, LangGraph, MCP, AgentOps, and MLOps**, and I have built hands-on practice projects to understand AI application deployment, monitoring, and security. My objective is to leverage my strong DevSecOps background while expanding into AI platform operations.



# 2. What is your experience with AI Ops / LLMs / AgentOps?

### Answer

I have not yet worked on **production AI or LLM workloads**, but I have been actively learning and gaining hands-on experience in this area.

My learning includes:

* Understanding **Large Language Models (LLMs)** and Agentic AI concepts.
* Working with **AWS Bedrock**, **LangChain**, **LangGraph**, and **Model Context Protocol (MCP)**.
* Learning how AI agents interact with enterprise applications through APIs and external tools.
* Understanding **prompt engineering, AI observability, guardrails, model evaluation, and AgentOps concepts**.
* Exploring secure deployment practices for AI workloads using DevSecOps principles.

Since my background is primarily in DevSecOps, I can contribute effectively in securing AI workloads, automating deployments, implementing CI/CD, infrastructure provisioning, secrets management, monitoring, and cloud security while continuously expanding my AI expertise.



# 3. Which cloud platform are you most comfortable with?

### Answer

I am most comfortable working with **AWS**, as it is the primary cloud platform used in my current project. I also have exposure to **Microsoft Azure** because our environment follows a hybrid-cloud architecture.

In AWS, I have worked with services such as:

* EC2
* EKS
* ECS
* Lambda
* VPC
* IAM
* CloudWatch
* CloudTrail
* Security Groups
* NAT Gateway
* Application Load Balancer
* KMS
* Secrets Manager
* S3

On Azure, I have worked with services including:

* AKS
* Azure Key Vault
* Azure Monitor
* Azure DevOps

Although AWS is my primary expertise, I am comfortable working in hybrid cloud environments.



# 4. Which AWS services have you worked on?

### Answer

In my current project, I have worked with several AWS services, including:

* **EC2** for hosting virtual machines.
* **EKS** for deploying and managing Kubernetes workloads.
* **ECS** for containerized applications where Kubernetes was not required.
* **Lambda** for serverless automation tasks.
* **VPC**, **Subnets**, **Route Tables**, **Internet Gateway**, and **NAT Gateway** for networking.
* **Application Load Balancer (ALB)** for traffic distribution.
* **IAM** for identity and access management.
* **CloudWatch** for monitoring and alerting.
* **CloudTrail** for auditing API activities.
* **Secrets Manager** and **AWS KMS** for secure secrets and key management.
* **Security Groups** and **Network ACLs** for network security.
* **S3** for artifact storage, backups, and logs.

Most of my work involves deploying secure applications on AWS, automating infrastructure, integrating security controls, and monitoring cloud resources.



# 5. Explain your end-to-end CI/CD pipeline in your current project.

### Answer

Our CI/CD pipeline is orchestrated using **Jenkins**, while **GitLab** serves as the source code repository.

The workflow is as follows:

1. Developers commit code and raise a Pull Request in GitLab.
2. **GitLeaks** performs secret scanning before the code is merged.
3. Once the Pull Request is approved, Jenkins automatically triggers the pipeline.
4. The application is built using the appropriate build tool such as **Maven, Gradle, npm, or Python**, depending on the technology stack.
5. **Fortify SAST** scans the source code for security vulnerabilities.
6. **Sonatype IQ Server** performs **Software Composition Analysis (SCA)** and generates the **SBOM** by identifying vulnerable third-party dependencies.
7. Quality gates verify that the application meets the required security and quality standards.
8. Docker images are built for containerized applications.
9. **Trivy** scans the Docker images for operating system and package vulnerabilities.
10. If all security and quality checks pass, the artifacts or container images are versioned and pushed to **Nexus Repository Manager**.
11. During the CD stage, deployment is performed to Kubernetes using **Helm charts**, which reference the newly approved image version.
12. After deployment, the application is continuously monitored using our observability stack to ensure application health, security, and performance.

This pipeline ensures that security is integrated throughout the SDLC using a **shift-left DevSecOps approach**, allowing vulnerabilities to be identified and remediated before deployment.

# Part 2 (Questions 6–10)



# 6. How and where is GitLeaks integrated into your CI/CD pipeline?

### Answer

GitLeaks is integrated at the **early stage of our CI/CD pipeline** to prevent secrets from entering the source code repository.

The workflow is as follows:

1. Developers commit code and create a Pull Request in GitLab.
2. GitLeaks scans the source code for hardcoded secrets such as API keys, passwords, tokens, AWS access keys, and private keys.
3. The scan is executed during the Pull Request validation stage before code is merged into the main branch.
4. If any secrets are detected, the pipeline fails and the Pull Request is blocked until the issue is resolved.
5. Only after the repository is free from exposed secrets does the pipeline proceed to build, security scanning, and deployment.

By integrating GitLeaks at the beginning of the pipeline, we prevent sensitive information from reaching later stages of the SDLC.



# 7. What is your experience with Kubernetes?

### Answer

I have around **two years of hands-on experience** working with Kubernetes in production environments.

My responsibilities include:

* Deploying containerized applications on Kubernetes.
* Managing Deployments, Services, ConfigMaps, Secrets, and Ingress resources.
* Performing rolling updates and rollbacks.
* Deploying applications using Helm Charts.
* Troubleshooting pod failures, image pull issues, CrashLoopBackOff errors, and networking problems.
* Managing resource requests and limits for better cluster utilization.
* Implementing Kubernetes security using RBAC, Network Policies, and Secrets management.
* Monitoring workloads using Prometheus and Grafana.
* Supporting Kubernetes deployments primarily on **Amazon EKS**, with exposure to **Azure AKS**.

Overall, my experience focuses on secure deployment, operations, troubleshooting, and maintaining Kubernetes-based applications.



# 8. Which automation/scripting tools or languages are you comfortable with?

### Answer

I primarily use **Python** and **Shell scripting (Bash)** for automation.

Some common use cases include:

* Automating repetitive operational tasks.
* Writing deployment and maintenance scripts.
* Integrating automation into Jenkins pipelines.
* Managing infrastructure provisioning workflows.
* Parsing logs and generating reports.
* Automating security scans and validation tasks.

Apart from scripting, I also use **Terraform** extensively for Infrastructure as Code (IaC), enabling automated and repeatable infrastructure provisioning.

Overall, Python, Shell scripting, and Terraform form the core of my automation toolkit.



# 9. Explain the Terraform project/repository structure you are using in your current project.

### Answer

Our Terraform repository follows a **modular and environment-specific structure**, which promotes reusability, maintainability, and scalability.

The structure consists of:

* A **modules** directory containing reusable modules such as VPC, EC2, EKS, IAM, Security Groups, and other infrastructure components.
* Separate folders for each environment, such as **Development**, **UAT**, and **Production**.
* Each environment contains its own:

  * `main.tf`
  * `variables.tf`
  * `outputs.tf`
  * `terraform.tfvars`
  * Backend configuration for remote state.
* Remote state is stored securely in an **S3 bucket** with **DynamoDB** used for state locking.
* Version control is managed through Git, and infrastructure changes are reviewed through Pull Requests before deployment.

This modular approach enables infrastructure reuse while allowing each environment to maintain its own configuration.



# 10. What are the Terraform best practices you follow?

### Answer

The Terraform best practices I follow include:

* Creating **reusable modules** instead of duplicating code.
* Maintaining separate configurations for **Development, UAT, and Production** environments.
* Storing Terraform state remotely in an **encrypted S3 bucket**.
* Enabling **DynamoDB state locking** to prevent concurrent modifications.
* Following Infrastructure as Code principles by keeping configurations version-controlled in Git.
* Performing **`terraform fmt`**, **`terraform validate`**, and **`terraform plan`** before applying any changes.
* Reviewing infrastructure changes through Pull Requests.
* Restricting access to Terraform state using IAM policies and least-privilege access.
* Avoiding hardcoded credentials by using **AWS Secrets Manager**, **KMS**, or environment variables.
* Implementing security scanning using tools such as **Checkov** or **tfsec** before deployment.
* Applying consistent naming conventions, tagging standards, and proper documentation.
* Building **immutable infrastructure**, where infrastructure changes are implemented by provisioning updated resources instead of modifying existing ones whenever applicable.

These practices help ensure that our infrastructure remains secure, scalable, maintainable, and consistent across environments.



# 11. How do you handle outbound (egress) connections in Kubernetes?

### Answer

In Kubernetes, outbound (egress) traffic refers to communication initiated by pods to external services such as APIs, databases, or internet endpoints.

The approach depends on the cluster setup:

* Pods initiate outbound connections through the cluster networking.
* In **Amazon EKS**, workloads running on private nodes typically access the internet through a **NAT Gateway**.
* **Network Policies** can be configured to restrict or allow egress traffic to specific destinations.
* **Security Groups** and **Network ACLs** provide additional network-level security.
* DNS resolution is handled by CoreDNS before external communication.
* Outbound access is restricted based on the principle of least privilege to minimize security risks.

This ensures secure and controlled communication between Kubernetes workloads and external systems.



# 12. What DevSecOps metrics do you follow, and what metrics do you monitor in the SonarQube dashboard?

### Answer

From a DevSecOps perspective, I primarily monitor metrics that measure code quality, security posture, and remediation effectiveness.

In **SonarQube**, I typically monitor:

* Number of **Security Vulnerabilities**.
* **Bug** count.
* **Code Smells**.
* **Code Coverage** from unit tests.
* **Duplicated Code Percentage**.
* **Maintainability Rating**.
* **Reliability Rating**.
* **Security Rating**.
* **Technical Debt**.
* **Quality Gate** status (Pass/Fail).

Apart from SonarQube, I also track:

* SAST findings.
* SCA vulnerability count.
* Critical and High severity vulnerabilities.
* Container image vulnerabilities.
* Secret scanning results.
* Vulnerability remediation time.
* Build success/failure rate.
* Deployment success rate.

These metrics help ensure both application quality and security throughout the software development lifecycle.



# 13. What is the difference between SCA, SAST, and DAST? Explain with an example.

### Answer

**Software Composition Analysis (SCA)**

SCA identifies vulnerabilities in **third-party or open-source libraries** used by the application.

For example, in a Java application, the tool scans the **pom.xml** file to identify vulnerable dependencies and recommends secure versions for remediation.

Common tools include:

* Sonatype IQ Server
* Snyk
* OWASP Dependency-Check



**Static Application Security Testing (SAST)**

SAST analyzes the **application source code** without executing it.

It detects coding vulnerabilities such as:

* SQL Injection
* Cross-Site Scripting (XSS)
* Hardcoded credentials
* Insecure coding practices

The scan is typically performed during the CI pipeline before deployment.

Common tools include:

* Fortify
* SonarQube
* Checkmarx



**Dynamic Application Security Testing (DAST)**

DAST scans a **running application** by interacting with its exposed endpoints.

It identifies runtime vulnerabilities such as:

* Authentication issues
* Session management flaws
* Security misconfigurations
* API vulnerabilities

DAST is usually executed in testing or staging environments after deployment.

Common tools include:

* OWASP ZAP
* Burp Suite
* Fortify DAST



### Summary

* **SCA** → Scans third-party dependencies.
* **SAST** → Scans source code without executing the application.
* **DAST** → Scans a running application from an attacker's perspective.

Using all three together provides comprehensive application security coverage.



# 14. Which location are you currently working from?

### Answer

I am currently working for a client based in **Mumbai**. At the time of the interview, I was temporarily in my hometown in **Andhra Pradesh** due to a family requirement. Once my planned leave was completed, I was expected to return to the Mumbai location and continue working from there.



# 15. Will you be able to travel to the Hyderabad or Coimbatore office for the next technical/hands-on interview?

### Answer

Yes, I can make the necessary travel arrangements. Initially, I checked whether a Bangalore interview location was available since it is closer to my hometown. However, once I understood that the interview would only be conducted in Hyderabad, I confirmed my willingness to attend.

I requested some time to verify my travel schedule and committed to sharing my availability with the HR team so the interview could be scheduled accordingly.



