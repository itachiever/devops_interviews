## Questions: 1st Round

1. Difference between **Declarative** and **Scripted Jenkins Pipelines**? Which Jenkins Pipeline are you currently using?
2. How are you handling **zero downtime deployments** in Kubernetes?
3. Can you explain **Rolling Updates**?
4. Can you explain **Readiness Probe**?
5. Can you explain **Liveness Probe**?
6. Have you solved any production problem related to rolling updates or probes?
7. What is your approach towards **Resource Requests** and **Resource Limits**?
8. What is your approach towards **Horizontal Pod Autoscaler (HPA)**?
9. What is your approach towards **Vertical Pod Autoscaler (VPA)**?
10. When do you use **HPA** and when do you use **VPA**?
11. What exactly is **Configuration Drift**?
12. How did **Terraform** help you in fixing Configuration Drift?
13. Do you have experience writing **Terraform Modules**?
14. If you want to create an **AWS VPC using Terraform**, what are the key things you will mention in that module?
15. What exactly is **Ingress**?
16. What exactly is a **Load Balancer**?
17. What is the difference between **Ingress** and **Load Balancer**?
18. You mentioned **Trivy**, **Snyk**, and **GitLeaks**. What exactly do they detect?
19. What is your approach towards **Cloud Cost Optimization**?
20. You know about the **ELK Stack**, right?
21. How are you handling **log retention** at a large scale?
22. How do you handle **large log volumes**?
23. What is **Kafka**?
24. What is **RabbitMQ**?
25. What is the difference between **Kafka** and **RabbitMQ**?
26. How good are you in **Linux troubleshooting**?
27. Suppose an application is not accessible via the browser and only a few users are affected. How will you investigate it?
28. Which **Linux commands** will you use for troubleshooting?
29. Can you explain one **Linux troubleshooting task** you handled?
30. Were you involved in finding the **root cause** of production issues? What **production issue** did you handle recently?
31. Which **programming language** are you good at?
32. You said you're good at **Python**. Can you explain one Python script you wrote?
33. Instead of hardcoding server names, they're stored in a **text file**. How do you import/read that file in Python?
34. Will you write a **function** for that?
35. How will you **call/execute** that function in Python?

    

1. Difference between **Declarative** and **Scripted Jenkins Pipelines**.
2. Which Jenkins Pipeline are you currently using?
3. How are you handling **zero downtime deployments** in Kubernetes?
4. Can you explain **Rolling Updates**?
5. Can you explain **Readiness Probe**?
6. Can you explain **Liveness Probe**?
7. Have you solved any production problem related to rolling updates or probes?
8. What is your approach towards **Resource Requests** and **Resource Limits**?
9. What is your approach towards **Horizontal Pod Autoscaler (HPA)**?
10. What is your approach towards **Vertical Pod Autoscaler (VPA)**?
11. When do you use **HPA** and when do you use **VPA**?
12. What exactly is **Configuration Drift**?
13. How did **Terraform** help you in fixing Configuration Drift?
14. Do you have experience writing **Terraform Modules**?
15. If you want to create an **AWS VPC using Terraform**, what are the key things you will mention in that module?
16. What exactly is **Ingress**?
17. What exactly is a **Load Balancer**?
18. What is the difference between **Ingress** and **Load Balancer**?
19. You mentioned **Trivy**, **Snyk**, and **GitLeaks**. What exactly do they detect?
20. What is your approach towards **Cloud Cost Optimization**?
21. You know about the **ELK Stack**, right?
22. How are you handling **log retention** at a large scale?
23. How do you handle **large log volumes**?
24. What is **Kafka**?
25. What is **RabbitMQ**?
26. What is the difference between **Kafka** and **RabbitMQ**?
27. How good are you in **Linux troubleshooting**?
28. Suppose an application is not accessible via the browser and only a few users are affected. How will you investigate it?
29. Which **Linux commands** will you use for troubleshooting?
30. Can you explain one **Linux troubleshooting task** you handled?
31. Were you involved in finding the **root cause** of production issues?
32. What **production issue** did you handle recently?
33. Which **programming language** are you good at?
34. You said you're good at **Python**. Can you explain one Python script you wrote?
35. Instead of hardcoding server names, they're stored in a **text file**. How do you import/read that file in Python?
36. Will you write a **function** for that?
37. How will you **call/execute** that function in Python?


## Answers


---

# 1. Difference between Declarative and Scripted Jenkins Pipelines. Which Jenkins Pipeline are you currently using?

## Answer

> **In our project, we primarily use the *Declarative Pipeline* because it is structured, easy to maintain, and recommended by Jenkins for most CI/CD implementations. For a few advanced use cases, we use the `script {}` block within the declarative pipeline whenever custom Groovy logic is required.**

### Declarative Pipeline

* Uses a **structured syntax** (`pipeline {}`).
* Easier to read and maintain.
* Supports built-in sections like **agent, stages, environment, post**.
* Best suited for standard enterprise CI/CD pipelines.

### Scripted Pipeline

* Uses **Groovy scripting** (`node {}`).
* More flexible for complex workflows.
* Requires more coding and is comparatively harder to maintain.

### Key Difference

| Declarative                   | Scripted                       |
| ----------------------------- | ------------------------------ |
| Structured syntax             | Groovy scripting               |
| Easy to maintain              | More flexible                  |
| Less coding                   | More coding                    |
| Recommended for most projects | Used for advanced/custom logic |

### Where I Used It

> "In our Jenkins pipeline, we automated **Build → Code Quality Scan → Security Scans → Docker Build → Image Push → Kubernetes Deployment** using a Declarative Pipeline."

---

# 2. How are you handling zero downtime deployments in Kubernetes?

## Answer

> **We achieve zero or minimal downtime deployments by using Rolling Updates, Readiness Probes, multiple Pod replicas, and Kubernetes Services.**

### Our Approach

* Use **Rolling Update** deployment strategy.
* Configure **multiple Pod replicas**.
* Configure **Readiness Probes** to send traffic only after the Pod becomes healthy.
* Configure **Liveness Probes** to automatically restart unhealthy containers.
* Deploy applications using **Helm** through the Jenkins pipeline.

### Production Example

> "During one deployment, the application required additional time to initialize because it established database connections during startup. The readiness probe timeout was too low, causing traffic to reach the Pod before it was ready, resulting in HTTP 503 errors."

### Resolution

* Increased **initialDelaySeconds**.
* Tuned readiness probe parameters.
* Redeployed through Helm.
* Verified all Pods reached **Ready** state before accepting traffic.

Result:

* No downtime.
* Stable deployments.

---

# 3. Can you explain Rolling Updates?

## Answer

> **Rolling Update is the default deployment strategy in Kubernetes where new Pods are created gradually while old Pods are terminated only after the new Pods become healthy. This ensures application availability during deployments.**

### How it Works

1. New Pod is created.
2. Kubernetes waits until it passes the Readiness Probe.
3. Traffic is redirected to the new Pod.
4. One old Pod is terminated.
5. Process repeats until all Pods are updated.

### Benefits

* Zero or minimal downtime.
* Easy rollback.
* Continuous availability.

### Production Usage

> "We use Rolling Updates for all application deployments through Jenkins and Helm."

---

# 4. Can you explain Readiness Probe?

## Answer

> **A Readiness Probe checks whether a container is ready to accept user traffic. Until the probe succeeds, Kubernetes does not send requests to that Pod.**

### Why It Is Used

* Prevents traffic from reaching Pods that are still starting.
* Avoids user-facing errors during deployments.
* Supports zero-downtime deployments.

### Production Example

> "Our application required around 30 seconds to initialize database connections. We increased the readiness probe delay so Kubernetes started routing traffic only after the application was fully ready."

---

# 5. Can you explain Liveness Probe?

## Answer

> **A Liveness Probe checks whether the application is still running correctly. If the probe fails continuously, Kubernetes automatically restarts the container.**

### Why It Is Used

* Detects hung or unresponsive applications.
* Automatically recovers failed containers.
* Improves application availability.

### Production Example

> "If a Java application becomes unresponsive due to memory issues or deadlocks, Kubernetes detects the failed liveness probe and restarts the container automatically."

---

# 6. Have you solved any production problem related to Rolling Updates or Probes?

## Answer

> **Yes. During one deployment, users started receiving intermittent HTTP 503 errors immediately after the release.**

### Investigation

* Checked Pod status.
* Reviewed application logs.
* Verified deployment events.
* Examined readiness probe configuration.

### Root Cause

The application startup time was longer than the configured readiness probe delay.

### Resolution

* Increased **initialDelaySeconds**.
* Adjusted **failureThreshold**.
* Redeployed using Helm.
* Verified successful rollout.

### Result

* Application became stable.
* No downtime during future deployments.

---

# 7. What is your approach towards Resource Requests and Resource Limits?

## Answer

> **For every Kubernetes deployment, we configure both Resource Requests and Resource Limits to ensure efficient resource utilization and stable application performance.**

### Resource Requests

* Minimum CPU and Memory guaranteed to the Pod.
* Used by the Scheduler to place Pods.

### Resource Limits

* Maximum CPU and Memory a Pod can consume.
* Prevents one Pod from consuming excessive cluster resources.

### Production Approach

* Configure requests and limits in Deployment manifests.
* Monitor actual usage using **Prometheus** and **Grafana**.
* Fine-tune values based on production metrics.

---

# 8. What is your approach towards Horizontal Pod Autoscaler (HPA)?

## Answer

> **We use Horizontal Pod Autoscaler to automatically increase or decrease the number of Pods based on CPU utilization.**

### How It Works

* Define minimum and maximum Pod count.
* Configure CPU utilization threshold (for example, 70%).
* Kubernetes automatically creates additional Pods when the threshold is exceeded.
* Scales down Pods when traffic decreases.

### Production Example

> "During high transaction periods, HPA automatically increased the number of application Pods, ensuring consistent performance without manual intervention."

---

# 9. What is your approach towards Vertical Pod Autoscaler (VPA)?

## Answer

> **Vertical Pod Autoscaler automatically adjusts the CPU and Memory allocated to a Pod based on its actual usage.**

### My Experience

> "We evaluated VPA but did not use it in our production environment."

### Reason

* VPA may restart Pods while modifying resource allocations.
* Since our applications were stateless, **HPA** provided sufficient scaling with minimal impact.

---

# 10. When do you use HPA and when do you use VPA?

## Answer

> **The choice depends on the application architecture and scaling requirements.**

### Horizontal Pod Autoscaler (HPA)

Used when:

* Application is **stateless**.
* Traffic varies throughout the day.
* Need to increase or decrease the number of Pods.

Example:

* Payment APIs.
* REST microservices.

### Vertical Pod Autoscaler (VPA)

Used when:

* Application cannot scale horizontally.
* Resource requirements change over time.
* Need to increase CPU or Memory assigned to individual Pods.

Example:

* Stateful workloads.
* Legacy applications.

### Our Project

> **We primarily used HPA because our microservices were stateless and could scale horizontally. We did not use VPA in production, as HPA was sufficient for our workload and avoided Pod restarts.**

Continuing from **Question 11**.

---

# 11. What exactly is Configuration Drift?

## Answer

> **Configuration Drift occurs when the actual infrastructure differs from the Infrastructure as Code (Terraform code). This usually happens when someone makes manual changes directly in the cloud console instead of updating the Terraform code.**

### Example

* Terraform defines an EC2 instance as **t3.medium**.
* Someone manually changes it to **t3.large** in the AWS Console.
* Now, the actual infrastructure and Terraform code are different. This is called **Configuration Drift**.

### Why is it a Problem?

* Infrastructure becomes inconsistent.
* Future deployments may fail or overwrite manual changes.
* Difficult to track and audit changes.

### Production Approach

> "To avoid configuration drift, we managed infrastructure changes through Terraform only and restricted manual changes using IAM permissions."

---

# 12. How did Terraform help you in fixing Configuration Drift?

## Answer

> **Terraform compares the desired infrastructure state (code) with the current infrastructure state and identifies any differences.**

### Our Approach

* Store Terraform state in **S3**.
* Use **DynamoDB** for state locking.
* Execute **terraform plan** before every deployment.
* Review the proposed changes.
* Apply only approved changes using **terraform apply**.

### Production Example

> "On one occasion, a Security Group rule was modified manually in AWS. During the next deployment, `terraform plan` detected the difference. After validating the change, we executed `terraform apply`, which restored the infrastructure to the desired state."

---

# 13. Do you have experience writing Terraform Modules?

## Answer

> **Yes. I have worked on creating reusable Terraform modules as well as enhancing existing modules based on project requirements. Modules helped us standardize infrastructure provisioning across multiple environments.**

### My Responsibilities

* Create reusable modules.
* Modify existing modules.
* Pass environment-specific variables.
* Consume modules across Dev, QA, and Production environments.

### Why Modules?

* Reusability
* Easy maintenance
* Consistency
* Reduced code duplication

---

# 14. If you want to create an AWS VPC using Terraform, what are the key things you will mention in that module?

## Answer

> **I would create a reusable VPC module with configurable variables so it can be used across multiple environments.**

### Resources Included

* VPC
* Public Subnets
* Private Subnets
* Internet Gateway
* NAT Gateway
* Route Tables
* Route Table Associations
* Security Groups (if required)
* Network ACLs (if required)
* Tags

### Variables

* VPC CIDR
* Public Subnet CIDRs
* Private Subnet CIDRs
* Availability Zones
* Environment Name

### Outputs

* VPC ID
* Public Subnet IDs
* Private Subnet IDs
* NAT Gateway ID

### Production Approach

> "Instead of hardcoding values, we passed variables through `terraform.tfvars` so the same module could be reused for Dev, QA, and Production."

---

# 15. What exactly is Ingress?

## Answer

> **Ingress is a Kubernetes resource that manages external HTTP/HTTPS access to applications running inside the cluster. It routes incoming requests to the appropriate Kubernetes Service based on hostnames or URL paths.**

### Responsibilities

* HTTP/HTTPS routing
* Path-based routing
* Host-based routing
* SSL/TLS termination
* Centralized routing management

### Production Example

Suppose we have:

* **app.company.com** → Payment Service
* **admin.company.com** → Admin Service

The Ingress Controller routes each request to the appropriate Kubernetes Service based on the hostname.

---

# 16. What exactly is a Load Balancer?

## Answer

> **A Load Balancer distributes incoming client requests across multiple backend servers or Kubernetes nodes to ensure high availability and reliability.**

### Responsibilities

* Receives external traffic.
* Distributes requests across backend instances.
* Performs health checks.
* Prevents a single server from becoming overloaded.
* Improves application availability.

### Production Example

> "In AWS, we used an **Application Load Balancer (ALB)** to receive internet traffic and forward it to the Kubernetes Ingress Controller."

---

# 17. What is the difference between Ingress and Load Balancer?

## Answer

> **A Load Balancer brings external traffic into the Kubernetes cluster, while Ingress decides where that traffic should go inside the cluster.**

### Load Balancer

* Cloud resource.
* Receives internet traffic.
* Forwards requests into Kubernetes.

### Ingress

* Kubernetes resource.
* Routes traffic to the correct Service.
* Supports host-based and path-based routing.

### Request Flow

```text
User
   │
DNS
   │
AWS Load Balancer
   │
Ingress Controller
   │
Kubernetes Service
   │
Pods
```

### Production Example

> "We exposed our applications using an AWS Application Load Balancer, while the NGINX Ingress Controller routed requests to the appropriate microservices."

---

# 18. You mentioned Trivy, Snyk, and GitLeaks. What exactly do they detect?

## Answer

> **These tools are integrated into our CI/CD pipeline to identify security issues before deployment.**

### Trivy

Detects:

* Container image vulnerabilities
* OS package vulnerabilities
* Application dependency vulnerabilities
* Kubernetes misconfigurations
* Secrets (when enabled)

---

### Snyk

Detects:

* Vulnerable open-source dependencies
* Container image vulnerabilities
* License compliance issues

---

### GitLeaks

Detects:

* Hardcoded passwords
* API Keys
* AWS Access Keys
* Tokens
* Private Keys
* Secrets committed to Git repositories

### Production Approach

> "These scans were integrated into our Jenkins pipeline. If critical vulnerabilities or exposed secrets were detected, the pipeline failed, and developers were required to remediate the issues before deployment."

---

# 19. What is your approach towards Cloud Cost Optimization?

## Answer

> **My approach is to optimize cloud resources while maintaining application performance and availability.**

### Our Approach

* Configure appropriate CPU and Memory requests/limits.
* Use **Horizontal Pod Autoscaler (HPA)**.
* Monitor resource utilization using **Prometheus** and **Grafana**.
* Right-size over-provisioned resources.
* Remove unused cloud resources.
* Clean up unused Docker images and old artifacts.
* Manage infrastructure through Terraform to avoid unnecessary resources.

### Production Example

> "We analyzed resource utilization using Prometheus and Grafana, reduced over-provisioned CPU and Memory requests for several microservices, and enabled HPA. This improved resource utilization and reduced infrastructure costs."

---

# 20. You know about the ELK Stack, right?

## Answer

> **Yes. I have worked with the ELK Stack for centralized logging and troubleshooting in our Kubernetes environment.**

### ELK Components

* **Elasticsearch** – Stores and indexes logs.
* **Logstash** *(or Filebeat/Fluent Bit)* – Collects and forwards logs.
* **Kibana** – Visualizes and searches logs.

### How We Used It

* Collected application and container logs from Kubernetes.
* Centralized logs in Elasticsearch.
* Used Kibana to search logs, troubleshoot production issues, and analyze application errors.
* Configured log retention and index rotation to efficiently manage large log volumes.

### Production Example

> "When users reported application failures, we searched logs in Kibana using request IDs and timestamps, identified the root cause from the application logs, and worked with the development team to resolve the issue."


---

# 21. How are you handling log retention at a large scale?

## Answer

> **We handled log retention by configuring retention policies and index lifecycle management in Elasticsearch. This ensured logs were available for troubleshooting while preventing storage from growing indefinitely.**

### Our Approach

* Configure **retention policies** based on project requirements (e.g., 30–90 days).
* Use **Index Lifecycle Management (ILM)** or index rotation.
* Archive or delete old logs automatically.
* Retain only logs required for auditing and troubleshooting.

### Production Example

> "In production, application logs were generated continuously. We configured retention policies so older indices were automatically deleted after the defined retention period, helping us optimize storage without affecting troubleshooting."

---

# 22. How do you manage huge log volumes?

## Answer

> **We reduced unnecessary log storage by collecting only relevant logs, rotating indices, and avoiding excessive debug logging in production.**

### Our Approach

* Use **Filebeat/Fluent Bit** to collect logs.
* Rotate Elasticsearch indices (daily/weekly).
* Enable only required log levels (INFO, WARN, ERROR).
* Avoid DEBUG logging in production.
* Configure log retention policies.
* Monitor Elasticsearch storage utilization.

### Production Example

> "We observed rapid Elasticsearch storage growth due to verbose application logs. After reviewing the logging configuration, we disabled unnecessary DEBUG logs and optimized the retention policy, significantly reducing storage usage."

---

# 23. What is Kafka?

## Answer

> **Apache Kafka is a distributed event-streaming platform used for real-time data streaming and asynchronous communication between applications.**

### Features

* High throughput.
* Fault tolerant.
* Distributed architecture.
* Stores messages for a configurable retention period.
* Supports multiple consumers reading the same data.

### Common Use Cases

* Event-driven architectures.
* Log aggregation.
* Real-time analytics.
* Activity tracking.

### My Experience

> **I have knowledge of Kafka architecture and use cases, but I have not been directly responsible for configuring or administering Kafka clusters in production.**

---

# 24. What is RabbitMQ?

## Answer

> **RabbitMQ is a message broker that enables asynchronous communication between applications by sending messages through queues.**

### Features

* Reliable message delivery.
* Queue-based communication.
* Supports acknowledgements.
* Suitable for background task processing.

### Common Use Cases

* Order processing.
* Email notifications.
* Background jobs.
* Task scheduling.

### My Experience

> **I understand RabbitMQ concepts and architecture, but I have not worked directly on RabbitMQ administration in my project.**

---

# 25. What is the difference between Kafka and RabbitMQ?

## Answer

> **Both are messaging solutions, but they are designed for different use cases.**

| Kafka                                        | RabbitMQ                               |
| -------------------------------------------- | -------------------------------------- |
| Event streaming platform                     | Message broker                         |
| High throughput                              | Reliable task processing               |
| Stores messages for retention                | Removes messages after acknowledgement |
| Multiple consumers can read the same message | Message is usually consumed once       |
| Best for streaming events                    | Best for background jobs and queues    |

### Interview Closing Statement

> **Kafka is best suited for event streaming and large-scale distributed systems, whereas RabbitMQ is commonly used for reliable task processing and traditional message queuing.**

---

# 26. How good are you in Linux troubleshooting?

## Answer

> **I would rate myself around 4 out of 5. I work with Linux daily for application deployments, troubleshooting, log analysis, and automation.**

### Daily Activities

* Checking application logs.
* Monitoring system resources.
* Managing services.
* Verifying network connectivity.
* Troubleshooting deployment issues.
* Writing Shell and Python scripts.

### Common Commands

* `top`
* `free -h`
* `df -h`
* `ps -ef`
* `systemctl`
* `journalctl`
* `curl`
* `ss -tuln`

---

# 27. Suppose an application is not accessible via the browser and only a few users are affected. How will you investigate it?

## Answer

> **I troubleshoot layer by layer to quickly isolate the root cause.**

### Step 1

Verify the issue.

* Is it affecting all users or only a few?
* Check the HTTP status code.

```bash
curl -I https://application-url
```

---

### Step 2

Check DNS resolution.

```bash
nslookup application-url
```

---

### Step 3

Verify network connectivity.

```bash
ping <server-ip>
```

---

### Step 4

Verify application process.

```bash
ps -ef | grep application
```

---

### Step 5

Check application logs.

```bash
journalctl -u application
```

or

```bash
tail -100 application.log
```

---

### Step 6

Check CPU, Memory and Disk.

```bash
top
free -h
df -h
```

---

### Step 7

Verify firewall and listening ports.

```bash
ss -tuln
```

### Production Approach

> **If only a few users are affected, I first suspect DNS, Load Balancer, routing, or client network issues before assuming an application failure.**

---

# 28. Which Linux commands will you use for troubleshooting?

## Answer

### Process

```bash
ps -ef
top
htop
```

---

### Memory

```bash
free -h
vmstat
```

---

### Disk

```bash
df -h
du -sh
```

---

### Logs

```bash
journalctl
tail -f
less
```

---

### Network

```bash
ping
curl
ss -tuln
netstat -tuln
nslookup
dig
traceroute
```

---

### Services

```bash
systemctl status
systemctl restart
```

---

### Kubernetes

```bash
kubectl logs
kubectl describe pod
kubectl get events
```

---

# 29. Can you explain one Linux troubleshooting task you handled?

## Answer

> **One production issue I handled involved intermittent HTTP 503 errors immediately after a Kubernetes deployment.**

### Investigation

* Checked Pod status.
* Verified application logs.
* Reviewed readiness probe.
* Verified deployment events.

### Root Cause

The application startup took longer than expected, but Kubernetes started routing traffic immediately.

### Resolution

* Increased **initialDelaySeconds**.
* Tuned readiness probe configuration.
* Redeployed using Helm.
* Verified successful rollout.

### Result

* 503 errors were eliminated.
* Future deployments were completed without downtime.

---

# 30. Were you involved in finding the root cause of production issues? What production issue did you handle recently?

## Answer

> **Yes. My responsibility was to investigate production issues, identify the root cause, coordinate with the development team when required, and ensure the issue was resolved with minimal business impact.**

### Recent Production Issue

**Problem**

* Users experienced intermittent **HTTP 503** errors after deployment.

**Investigation**

* Checked Kubernetes Pods.
* Reviewed application logs.
* Verified deployment events.
* Checked readiness probe configuration.

**Root Cause**

* Application initialization time exceeded the configured readiness probe delay.

**Resolution**

* Updated readiness probe parameters.
* Redeployed through Helm.
* Monitored rollout until all Pods became healthy.

**Result**

* Service was restored successfully.
* Standardized readiness probe configuration across similar applications.
* No recurrence of the issue during subsequent deployments.

> **Interview Tip:** This is a strong STAR-based answer because it demonstrates your troubleshooting methodology, Kubernetes knowledge, and production ownership without overstating your role.


Continuing from **Question 31**.

---

# 31. Which programming language are you good at?

## Answer

> **I am primarily comfortable with Python and Shell Scripting. Out of the two, Python is my strongest language because I use it regularly for automation and operational tasks in DevOps.**

### Where I Used Python

* Automation of repetitive tasks.
* Service health checks.
* Log parsing and analysis.
* Reading server inventories from files.
* Generating reports.
* Triggering API calls.
* CI/CD automation support.

### Where I Used Shell Scripting

* Linux administration tasks.
* Deployment automation.
* Log monitoring.
* Cron job automation.
* Service management.

### Interview Closing Statement

> **My day-to-day scripting is mostly Python for automation and Shell scripting for Linux operational activities.**

---

# 32. You said you're good at Python. Can you explain one Python script you wrote?

## Answer

> **One Python script I worked on was used to restart application services across multiple servers. Instead of hardcoding server names, the servers were maintained in a separate text file. The script would read the file and execute the required action on each server.**

### Why We Built It

* Eliminate repetitive manual work.
* Standardize operations.
* Reduce human errors.

### High-Level Flow

```text id="lkf12a"
Read Servers File
        ↓
Get Server List
        ↓
Loop Through Servers
        ↓
Connect to Server
        ↓
Check Service Status
        ↓
Restart Service
        ↓
Log Result
```

### Production Benefit

> "This reduced manual effort and ensured consistent execution across all target servers."

---

# 33. Instead of hardcoding server names, they're stored in a text file. How do you read that file in Python?

## Answer

### Example

```python id="eqh28w"
with open("servers.txt", "r") as file:
    servers = file.readlines()

for server in servers:
    server = server.strip()
    print(server)
```

### Explanation

* `open()` → Opens the file.
* `"r"` → Read mode.
* `readlines()` → Reads all lines.
* `strip()` → Removes newline characters.
* `for` loop → Iterates through each server.

### Why Use a File?

> **Keeping server names in a file makes the script reusable and easier to maintain. If servers change, we only update the file instead of modifying the code.**

---

# 34. Will you write a function for that?

## Answer

> **Yes. In production, I would write a reusable function instead of repeating the same logic multiple times.**

### Example

```python id="40m4m8"
def read_servers(filename):
    with open(filename, "r") as file:
        return [line.strip() for line in file]
```

### Why Use a Function?

* Reusability.
* Cleaner code.
* Easier maintenance.
* Better readability.

### Interview Statement

> **Functions help us follow modular coding practices and avoid duplicate code.**

---

# 35. How will you call/execute that function in Python?

## Answer

### Example

```python id="hysdks"
servers = read_servers("servers.txt")

for server in servers:
    print(server)
```

### Explanation

* Function is called using:

```python id="gjstq8"
read_servers("servers.txt")
```

* The function returns a list of servers.
* The program then loops through the list and performs required actions.

### Interview Statement

> **The function executes when it is called. It returns the required data, which can then be processed by the main program.**

---

# 36. Were you involved in finding the root cause of production issues?

## Answer

> **Yes. One of my key responsibilities was supporting production deployments, monitoring applications, troubleshooting issues, identifying root causes, and coordinating with development teams whenever required.**

### My Approach

1. Understand the issue.
2. Verify impact.
3. Check logs and monitoring dashboards.
4. Analyze application behavior.
5. Identify root cause.
6. Implement fix.
7. Validate resolution.
8. Document findings.

### Tools Used

* Kubernetes
* Jenkins
* ELK
* Prometheus
* Grafana
* Linux logs

### Interview Statement

> **While development teams handled code fixes, I was actively involved in infrastructure, deployment, monitoring, and root cause analysis activities.**

---

# 37. What production issue did you handle recently?

## Answer

This is probably the **strongest answer from the entire interview**, so keep it polished.

### Situation

> **Recently, users started experiencing intermittent HTTP 503 errors immediately after a Kubernetes deployment.**

---

### Investigation

I performed the following checks:

* Verified Pod status.

```bash id="xhv6nd"
kubectl get pods
```

* Checked Pod logs.

```bash id="2dk5fc"
kubectl logs <pod-name>
```

* Reviewed deployment events.

```bash id="v2o8on"
kubectl describe pod <pod-name>
```

* Verified readiness probe configuration.

---

### Root Cause

> **The application startup time was longer than expected because it needed to establish database connections and load application configurations. However, Kubernetes started routing traffic before the application became fully ready.**

---

### Resolution

* Increased readiness probe delay.

```yaml id="4l0y8r"
initialDelaySeconds: 30
```

* Tuned probe thresholds.
* Redeployed through Helm.
* Monitored rollout.

```bash id="jspl4u"
kubectl rollout status deployment/app
```

---

### Result

* HTTP 503 errors were resolved.
* No downtime observed.
* Improved deployment stability.
* Applied the same readiness standards to similar services.

### Interview Closing Statement

> **The key lesson from this incident was that a healthy container is not always a ready application. Proper readiness probe configuration is critical for successful zero-downtime deployments.**

---

# Quick Revision of Questions 31–37

### Python

* Python and Shell are primary scripting languages.
* Python used for automation.
* Use `open()` to read files.
* Use functions for reusability.
* Functions execute when called.

### Production Support

* Follow a structured troubleshooting approach.
* Analyze logs first.
* Verify infrastructure and application health.
* Identify root cause before applying fixes.

### Production Issue

* HTTP 503 after deployment.
* Readiness probe misconfiguration.
* Increased startup delay.
* Redeployed successfully.
* Zero downtime achieved.

These answers now cover **all 37 questions** from the Xoriant interview in a polished, future-reference format aligned with your actual DevOps/DevSecOps experience.
