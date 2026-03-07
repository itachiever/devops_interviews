Role: Sr. DevOps Engineer - AWS

About the job
XenonStack is looking for Sr. DevOps engineers to join our team to help manage and Deploy Workload for AWS Cloud infrastructure with OpenStack and Kubernetes.

Job Responsibilities

 Design, develop, and test features/functions delivered via applications and services
 Hands-on software development for infrastructure that will perform at scale
 Write Infrastructure as a code that is tested, readable, and maintainable
 Perform reviews, evaluate implementations, and provide feedback for tool improvements
 Lead technical and architectural discussions and decision-making.
 Collaborate with stakeholders to understand requirements, understand use cases and build towards a cohesive technical strategy
 Automate processes where possible and propose new tools when needed
 Participate in on-call rotations to support production :

Technical Requirements

 3+ years Linux/Unix Administration monitoring, reliability and security of Linux-based, online, high traffic services and Web/eCommerce properties
 2+ years of production experience in large-scale AWS cloud-based Infrastructure, Customer-facing and service-oriented person
 Working with software development team and basic exposure to at least one programming language i.e. Python, NodeJS or Java
 Understanding & curiosity of DevOps best practices, architectures, and methods
 Strong experience with Log Analysis and Monitoring tools such as CloudWatch, Splunk, Dynatrace, Nagios, etc.
 Hands-on network configuration involving load balancers, firewalls, ACLs and TCP/IP core components (http, DNS, routing, etc)
 Strong sysadmin background, proven knowledge of working and managing Linux systems such as RedHat or CentOS
 Strong with Docker and Kubernetes/ECS environments
 Expert Experience with infrastructure-as-code tools such as Terraform or CloudFormation
 Expert experience with CI/CD tools, such as Jenkins, Artifactory, GIT, etc.
 Knowledge of best practices and IT operations in an always-up, always-available service
 Good self management skills and ability to track and prioritise multiple tasks coming in simultaneously.

Professional Attributes

 Excellent communication skills & Attention to detail.
 Analytical mind and problem-solving Aptitude with Strong Organisational skills & Visual Thinking
 Experience : 2+ years
 Education : Technical Graduates Bachelors/Masters.

##
Role : DevOps Engineer 

Interview : 2nd Round 

Experience : 2.3 Years

# Questions :


1. Introduce Yourself


2. Have you created a cluster or managed a Kubernetes cluster? Can you explain the work you have done regarding it?


3. Suppose there is a Pod in a cluster that is repeatedly restarting and the status shows CrashLoopBackOff. How will you handle this scenario, and what are the causes of Pod failure?


4. Suppose a worker node in a cluster has become unstable and you are seeing the Pods are getting evicted with the message "rejected due to more pressure." How will you handle this critical situation, and what are the causes of more pressure?


5. Suppose you have a task to migrate a large-scale stateful application from an on-premises data center to a managed Kubernetes service in the cloud. The app relies heavily on local storage for known details/data in the source. What steps would you take to ensure successful migration of both stateful and stateless components with minimum downtime in the database?


6. Suppose you have some Docker images that are being used by a Kubernetes application and you discovered some vulnerabilities in those applications. How will you handle this situation and resolve them?


7. Tell me the scripting you have used in your projects. What input did it take and what did it do?


8. What AWS services have you used?


9. What are the different types of scaling policies we have in AWS? Are you using any of them?


# Answers:

---

### **1. Introduce Yourself**

**Sample Answer:**
"I am a DevOps/DevSecOps Engineer with **[X]** years of experience primarily focused on AWS and Kubernetes. I started my career in system administration, which gave me a strong foundation in Linux and networking, and then transitioned into Cloud Engineering.

In my most recent role at **[Company Name]**, I was responsible for managing our AWS infrastructure and Kubernetes clusters. I specialized in building secure CI/CD pipelines using GitLab and implementing Infrastructure as Code using Terraform and CloudFormation.

I am very passionate about **Security by Design**—integrating vulnerability scanning and compliance checks early in the development lifecycle. I am looking for a role where I can combine my cloud architecture skills with security to help build scalable, resilient platforms."

---

### **2. Have you created a cluster or managed a Kubernetes cluster? Can you explain the work you have done regarding it?**

**Sample Answer:**
"Yes, I have extensive experience managing Kubernetes clusters. In my previous role, I was responsible for managing a production **EKS (Elastic Kubernetes Service)** cluster on AWS hosting about 30 microservices.

My work involved:
1.  **Cluster Setup & Upgrades:** I provisioned the cluster using Terraform and managed version upgrades, ensuring zero downtime by draining nodes gracefully.
2.  **Application Deployment:** I managed deployments using **Helm Charts**. I created a standard Helm chart template that our development teams would reuse to ensure consistency.
3.  **Ingress & Networking:** I configured **NGINX Ingress Controller** to manage routing and SSL/TLS termination using Let's Encrypt and AWS Certificate Manager.
4.  **Monitoring:** I integrated Prometheus and Grafana to monitor the health of the cluster and set up alerts for high CPU or memory usage.

So, I handled the full lifecycle—from provisioning the infrastructure to ensuring the applications running inside were healthy."

---

### **3. Suppose there is a Pod in a cluster that is repeatedly restarting and the status shows CrashLoopBackOff. How will you handle this scenario, and what are the causes of Pod failure?**

**Sample Answer:**
"First, I wouldn't panic. CrashLoopBackOff means the container is starting, crashing, and Kubernetes is trying to restart it, but it keeps failing.

My troubleshooting steps would be:
1.  **Describe the Pod:** I would run `kubectl describe pod <pod-name>`. I would look at the **"Events"** section at the bottom. It usually tells me exactly why it crashed (e.g., "Liveness probe failed" or "OOMKilled").
2.  **Check the Logs:** I would run `kubectl logs <pod-name>` to see the application error logs. If the container has already restarted, I would use the `--previous` flag to see the logs from the *previous* crash.

**Common Causes I would look for:**
*   **Application Error:** A bug in the code causing an unhandled exception.
*   **Missing Config/Secrets:** The app is trying to read an environment variable or a file that doesn't exist (e.g., a database password missing).
*   **Liveness Probe Failure:** The app is running, but Kubernetes thinks it's dead because the health check endpoint is misconfigured or the app is too slow to respond.
*   **Resource Limits:** The container is running out of memory and getting OOMKilled (Out Of Memory)."

---

### **4. Suppose a worker node in a cluster has become unstable and you are seeing the Pods are getting evicted with the message "rejected due to more pressure." How will you handle this critical situation, and what are the causes of more pressure?**

**Sample Answer:**
"This situation is called **Node Pressure Eviction**. The Kubelet (the agent on the node) is proactively kicking out Pods to save the node from crashing.

**How I would handle it:**
1.  **Identify the Pressure:** I would run `kubectl describe node <node-name>` to see the "Conditions." It will show if the pressure is **Memory**, **Disk**, or **PID**.
2.  **Investigate:**
    *   If **Memory Pressure:** I would check which Pods are consuming the most RAM using `kubectl top pods`. Is there a memory leak?
    *   If **Disk Pressure:** I would SSH into the node and check `df -h`. Usually, the disk is full because of old container logs or Docker images filling up the space.
3.  **Remediation:** I would clean up unused Docker images (`docker system prune`) or rotate logs. If the node is just too small, I would scale up the node group or add a new node to the cluster.

**Causes of Pressure:**
*   **Resource Exhaustion:** An application is using more RAM or CPU than allocated.
*   **No Resource Limits:** If Pods don't have limits, one "noisy neighbor" can eat up all the node's resources.
*   **Disk Full:** Logs are not being rotated, filling up the node's hard drive."

---

### **5. Suppose you have a task to migrate a large-scale stateful application... (On-Prem to Cloud K8s with minimum downtime).**

**Sample Answer:**
"Migrating a stateful app with local storage is tricky because you can't just 'copy-paste' the storage easily. Here is my strategy:

**1. The Stateless Components (Microservices):**
I would containerize the application, push images to ECR/GCR, and deploy them to the cloud Kubernetes cluster. This is straightforward.

**2. The Stateful Components (Database & Local Data):**
Since the app relies on local storage on-prem, I would move it to **StatefulSets** and **Persistent Volumes (PVC)** in the cloud.
*   **Data Migration:** I would set up a hybrid connection (VPN/Direct Connect) between On-Prem and Cloud. I would use tools like **Rsync** or **Velero** (backup/restore tool) to copy the data from the on-prem local disks to a cloud storage class (like AWS EBS volumes).

**3. Ensuring Minimum Downtime (The Cutover):**
*   I would set up a **Blue-Green Deployment** in the cloud.
*   I would continuously sync the data (Replication) from On-Prem to Cloud until the cutover time.
*   During the cutover window, I would stop the on-prem app, run a final sync to ensure 0 data loss, switch the DNS/Load Balancer to point to the new Cloud Kubernetes service, and bring the app online.

This approach ensures we have a rollback plan and minimizes the downtime window to just the final sync and DNS switch."

---

### **6. Suppose you have some Docker images that are being used by a Kubernetes application and you discovered some vulnerabilities in those applications. How will you handle this situation and resolve them?**

**Sample Answer:**
"Vulnerabilities are a constant reality. Here is how I handle them:

1.  **Scan & Prioritize:** First, I would use a scanning tool like **Trivy** or **Clair** to get a detailed report. I wouldn't panic at every 'Low' severity issue. I would focus on **High/Critical** vulnerabilities that have a known exploit (CVE).
2.  **Identify the Source:**
    *   Is the vulnerability in the **Base OS** (e.g., Alpine Linux)? If so, I just need to update the `FROM` line in the Dockerfile to the latest patched version.
    *   Is it in the **Application Library** (e.g., a vulnerable `npm` or `pip` package)? I need to update the dependency in the code (`package.json`).
3.  **Fix & Rebuild:** I would update the Dockerfile or code, build a **new Docker image** with a new tag (e.g., `v1.0.2`), and push it to the registry.
4.  **Deploy:** I would update the Kubernetes Deployment to use the new image tag.
5.  **Prevention:** To prevent this in the future, I would integrate this scanner into the **CI/CD pipeline**. If a High/Critical vulnerability is found during the build, the pipeline should **fail** automatically, preventing the bad image from ever being deployed."

---

### **7. Tell me the scripting you have used in your projects. What input did it take and what did it do?**


**Sample Answer:**
"I primarily use **Python (Boto3)** and **Bash**.

**Example 1: Python (Boto3)**
I wrote a Python script to automate the cleanup of old AWS snapshots.
*   **Input:** It took arguments like the number of days to retain and the AWS region.
*   **Action:** It queried the AWS API for snapshots older than `X` days, deleted them to save storage costs, and sent a Slack notification with a summary of what was deleted.

**Example 2: Bash**
I wrote a Bash script for backing up Kubernetes secrets.
*   **Input:** It took the namespace name.
*   **Action:** It used `kubectl get secrets` and encoded them into a JSON file, then uploaded that file to an S3 bucket for daily backups.

These scripts saved the team hours of manual work and reduced human error."

---

### **8. What AWS services have you used?**


**Sample Answer:**
"I have worked with a wide range of AWS services:
*   **Compute:** **EC2** (for legacy apps), **Lambda** (for serverless tasks), and **EKS** (for container orchestration).
*   **Storage & Database:** **S3** (for object storage), **EBS** (for block storage), and **RDS** (for managed SQL databases).
*   **Networking:** **VPC**, **Route53** (for DNS), and **Application Load Balancer** (for distributing traffic).
*   **Security & IAM:** **IAM** (roles and policies), **KMS** (for encryption keys), and **Secrets Manager** (for storing passwords).
*   **Management:** **CloudWatch** (for monitoring), **CloudFormation** (for IaC), and **AWS Config** (for compliance).
I am most comfortable with EKS and the networking/security side of AWS."

---

### **9. What are the different types of scaling policies we have in AWS? Are you using any of them?**

**Sample Answer:**
"Generally, there are two main types of scaling policies in AWS:

1.  **Manual Scaling:** You log into the console and increase the instance count yourself. This is slow and not recommended for production.
2.  **Dynamic Scaling (Auto Scaling):** This is what I use. It automatically adjusts capacity based on demand. There are specific types:
    *   **Target Tracking Scaling:** This is what I prefer and use. You set a target (e.g., 'Keep CPU usage at 50%'), and AWS automatically adds or removes instances to maintain that target. It's the most stable.
    *   **Step Scaling:** You define rules (e.g., 'If CPU > 70%, add 2 instances'). It's more rigid but gives you precise control.
    *   **Scheduled Scaling:** You predict the load (e.g., 'Every Monday at 9 AM, traffic spikes'). You schedule the scale-out to happen ahead of time.

I use **Target Tracking** for our web servers because it reacts instantly to traffic spikes without needing complex rule tuning."
