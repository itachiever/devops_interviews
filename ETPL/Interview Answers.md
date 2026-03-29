
### **1. Can you explain your profile, your work, skill set, and projects?**
"Sure. I am a DevSecOps Engineer with over 4 years of active experience. My core expertise lies in building secure CI/CD pipelines, managing hybrid cloud infrastructure (AWS & Azure), and automating deployments using Kubernetes and Docker.

In my current role, I designed a complete DevSecOps platform from scratch. This involved setting up Jenkins for orchestration, integrating security tools like Fortify and SonarQube, and managing Kubernetes clusters (AKS and EKS). I have a strong grasp of IaC using Terraform and Ansible, and I focus heavily on 'Shift Left' security—embedding security controls early in the development lifecycle."

### **2. Where are you currently based / which part of India are you from?**
"I am currently based in Mumbai. However, I am open to relocation or hybrid models as required by the role."

### **3. Why are you looking for a job change?**
"I have been with my current organization for a while and have successfully built stable infrastructure and processes. Now, I am looking for a role that offers more complex challenges at scale—specifically in high-availability systems and advanced cloud architectures. I want to leverage my experience in a Senior Engineer capacity to drive larger automation initiatives, which aligns perfectly with what this role offers."

### **4. What have you done from scratch in your current project?**
"My biggest 'from scratch' achievement was setting up the organization’s internal DevSecOps platform. When I joined, the process was manual and lacked security integration. I architected the entire workflow:
1.  I set up the Jenkins infrastructure with a DMZ gateway using NGINX for secure external exposure.
2.  I containerized the applications and deployed them to Kubernetes.
3.  I integrated SAST, DAST, and SCA tools into the pipelines.
4.  I established a secure VPN tunnel between our on-prem infrastructure and the cloud, ensuring end-to-end automation for the first time in the organization."

### **5. What is your team size?**
"I work in a lean team structure. The core DevOps/Platform engineering team consists of about 3-4 members. However, we collaborate closely with development and security teams, effectively supporting an engineering organization of around 20-30 people."

### **6. Who do you report to?**
"I report directly to the Engineering Manager, who oversees the infrastructure and delivery verticals."

### **7. Which client are you working for?**
*(Note: Since I don't know your specific client name, I will answer generically based on your resume sector)*
"I am currently working for an enterprise client in the [Banking/Financial/IT Services] sector. We manage their critical internal applications which require strict compliance and high availability due to the sensitive nature of the data."

### **8. Can you explain your client architecture? How is it set up?**
"It is a Hybrid Cloud architecture.
*   **On-Premise:** We have our core DevSecOps toolchain (Jenkins, Nexus, Fortify) hosted on-premise for security control.
*   **Cloud:** The application workloads run on Azure AKS and AWS EKS.
*   **Connectivity:** We use a Site-to-Site VPN to connect the on-prem CI/CD system to the cloud clusters.
*   **Flow:** Developers commit code -> Jenkins builds on-prem -> Security scans occur -> Docker images are pushed to Nexus -> Jenkins deploys to AKS/EKS via the VPN."

### **9. Is it monolithic or microservices? What kind of system is it?**
"It is purely a **Microservices architecture**. We broke down a legacy monolith into smaller, independent services to allow for independent scaling and deployment. Each service has its own database instance, following the 'Database per Service' pattern."

### **10. How many services are there?**
"Currently, we manage around **15 to 20 microservices** in the production environment. Each has its own pipeline and deployment configuration."

### **11. What is the reason for using Helm?**
"We use Helm primarily for **standardization and reusability**. Managing raw YAML files for 20 microservices is prone to human error and creates drift.
*   **Templating:** Helm allows us to create a standard chart template. We just pass different `values.yaml` files for DEV, UAT, and PROD.
*   **Versioning:** It allows us to version our releases, making it easy to track what is deployed.
*   **Lifecycle Management:** It handles upgrades and rollbacks efficiently, which `kubectl apply` doesn't manage natively."

### **12. What monitoring tools are you using?**
"We use a modern observability stack.
*   **Metrics:** Prometheus for scraping metrics and Grafana for visualization.
*   **Logs:** We use the ELK Stack (Elasticsearch, Logstash, Kibana) for centralized logging.
*   **Cloud Native:** For Azure workloads, we utilize Azure Monitor and Container Insights."

### **13. Are you using Azure only or a hybrid cloud?**
"As I mentioned, it is a **Hybrid Cloud** model. We leverage Azure AKS and AWS EKS for compute, but we maintain critical infrastructure components and build servers on-premise. This hybrid approach gives us better control over sensitive data while utilizing the cloud for scalability."

### **14. Are you using VPN or a jump server? How does access work?**
"For infrastructure access, we do **not** expose clusters to the public internet.
1.  **VPN:** Engineers connect via a VPN client to access the internal network.
2.  **Bastion/Jump Host:** For SSH access to VMs or legacy systems, we use a Bastion host.
3.  **Kubernetes Access:** We use private clusters, so kubectl access is only available via the VPN connection to the private API server endpoint."

### **15. Where do you store your container images?**
"We use **Sonatype Nexus Repository** as our primary Docker Registry. It acts as a proxy for public images (like Docker Hub) to cache them locally and speed up builds. We also use it to store our internal application images securely before they are deployed to the cluster."


### **16. Have you heard about CrashLoopBackOff?**
"Yes, definitely. **CrashLoopBackOff** is a common Kubernetes error state. It essentially means Kubernetes tried to start a container, but the container keeps crashing repeatedly. After it crashes, Kubernetes waits for a specific back-off period before trying to restart it again. It's a signal that the application inside the container is failing immediately upon startup."

### **17. How do you debug a pod that is repeatedly restarting?**
"My approach is systematic:
1.  **Check Status:** First, I run `kubectl describe pod <pod-name>` to see the events. This tells me if the issue is a resource constraint or a liveness probe failure.
2.  **Check Logs:** If the pod started but crashed, I run `kubectl logs <pod-name> --previous`. The `--previous` flag is crucial here; it fetches logs from the container instance that crashed before the restart, allowing me to see the actual error message.
3.  **Common Culprits:** I usually look for missing environment variables, missing secrets/configmaps, or application-level exceptions like database connection failures."

### **18. What is ClusterIP and NodePort? (difference)**
"Both are Kubernetes Service types, but they serve different purposes:
*   **ClusterIP:** This is the default type. It exposes the service on a stable internal IP address within the cluster. It makes the service reachable only from *inside* the cluster. We use this for internal microservices that don't need external traffic.
*   **NodePort:** This exposes the service on a specific port on *every* worker node in the cluster. It allows external traffic to access the service by hitting `NodeIP:Port`. It’s often used for development or quick testing, but in production, we usually put a Load Balancer or Ingress in front of it."

### **19. What are Pods, Deployments, and Services?**
"I like to think of it in layers:
*   **Pod:** The smallest deployable unit. It represents a running process and encapsulates one or more containers.
*   **Deployment:** This is the controller. It manages the Pods. It defines the desired state, like 'I want 3 replicas of this Pod.' It handles ReplicaSets, rolling updates, and self-healing if a pod dies.
*   **Service:** This is the networking layer. Since Pods have dynamic IPs, the Service provides a stable endpoint (a constant IP or DNS name) so other applications can talk to the pods managed by the Deployment."

### **20. How do you perform deployments? (initiation, process, closure)**
"We follow a strict GitOps workflow:
1.  **Initiation:** A developer creates a Merge Request (MR) and updates the version tag in the Helm values file.
2.  **Process:** Once approved and merged, Jenkins triggers the pipeline. It builds the Docker image, pushes it to Nexus, and then triggers the Helm upgrade command.
3.  **Closure:** Helm applies the changes to the cluster. We wait for the rollout to complete, verify the health status, and then send a notification to the team Slack channel confirming success."

### **21. What do you do if a deployment fails?**
"If a deployment fails:
1.  I check the Jenkins logs immediately to see which stage failed.
2.  If it failed during the deploy stage, I check the pod status in Kubernetes to see if it’s in `ImagePullBackOff` or `CrashLoopBackOff`.
3.  I analyze the logs using `kubectl logs`.
4.  Crucially, I ensure the pipeline stops automatically so it doesn't proceed to the next environment, preventing a bad build from reaching Production."

### **22. What is your rollback strategy? How do you revert to the previous deployment?**
"Since we use Helm, the rollback strategy is streamlined:
*   **Helm Rollback:** If a release is failing, I use the command `helm rollback <release-name> <revision-number>`. Helm keeps a history of releases, so reverting is instant.
*   **Automated Check:** In our pipelines, we have a 'Verify' stage. If the health check fails after deployment, the pipeline automatically triggers a rollback to the previous stable version."

### **23. If deployment includes database changes (columns added/deleted), how do you roll it back?**
"This is tricky. Rolling back code is easy, but rolling back a database schema is risky and can cause data loss. I follow the **Backward Compatibility** strategy:
1.  **Two-Phase Deployment:**
    *   *Phase 1:* I deploy a code version that supports *both* the old and new schema.
    *   *Phase 2:* I run the database migration to add the column.
2.  **Rollback:** If Phase 2 fails, I just roll back the code to the previous version. The database change (like adding a column) is usually safe to leave temporarily or revert manually with a script.
3.  **Golden Rule:** I never let automated pipelines drop columns or delete data. Those are manual, reviewed operations."

### **24. You can use Liquibase or other tools — in your case, what process do you follow?**
"We use a custom setup with Jenkins. We maintain SQL migration scripts in a separate Git repository. When the pipeline runs, a specific stage executes these scripts against the database using a Python wrapper that tracks which scripts have already run. It’s similar to Flyway or Liquibase but custom-built to fit our specific enterprise requirements."

### **25. Which database are you using?**
"For the microservices, we primarily use **PostgreSQL** for relational data and **Redis** for caching and session management. We also use **Kafka** for messaging between services."

### **26. How are you using AI in your systems or day-to-day work?**
"I actively use AI tools like ChatGPT or GitHub Copilot to boost productivity.
1.  **Scripting:** If I need a complex Python script for log parsing, I use AI to generate the base logic and then refine it.
2.  **Troubleshooting:** If I encounter a cryptic error in a log, I paste it into an LLM to quickly understand the root cause.
3.  **Documentation:** I use it to draft initial runbooks or documentation structures, which saves a significant amount of time."

### **27. What is your biggest achievement in your career?**
"My biggest achievement was building the **Hybrid DevSecOps Platform from scratch** in my current organization. Before I joined, there was no standardization. I single-handedly designed the architecture, set up the Jenkins CI/CD, integrated security scanners (Fortify/SonarQube), and established the Kubernetes deployment model. Seeing the entire engineering team move from manual deployments to a fully automated, secure 'one-click' deployment process gave me immense satisfaction."

### **28. If a server is going down intermittently and hanging, how will you handle it?**
"This requires a deep dive:
1.  **Immediate Check:** I check `top` or `htop` to see if CPU or Memory is maxed out.
2.  **Logs:** I check `/var/log/syslog` and application logs for errors.
3.  **Disk I/O:** Often, servers hang due to high disk I/O or full disk space. I check `df -h` and `iostat`.
4.  **Root Cause:** If it's a memory leak, I restart the service and plan a fix. If it's resource saturation, I scale vertically or horizontally.
5.  **Observability:** I verify if the alerts in Prometheus/Grafana fired correctly; if not, I tune the alerts."

### **29. Do you have experience with APM tools like New Relic or Datadog?**
"While I haven't used New Relic or Datadog extensively in production, I am very familiar with **APM concepts**. We use **Prometheus** and **Grafana** for metrics, and **ELK Stack** for logs. I understand that tools like New Relic provide deeper application-level tracing (like transaction traces), which we sometimes emulate using OpenTelemetry libraries feeding into our stack."

### **30. How do you manage secrets?**
"I adhere to the principle that **secrets should never be in code**.
1.  **In Code:** We use **GitLeaks** in pre-commit hooks to scan for accidental commits.
2.  **In Cloud:** We use **AWS Secrets Manager** and **Azure KeyVault**.
3.  **In Kubernetes:** We integrate with **External Secrets Operator**. This operator syncs secrets from the cloud vault (KeyVault) into Kubernetes Secrets. This way, developers don't need to define secrets in YAML files; they are injected automatically and securely."

### **31. Do you have any questions for me?**
"Yes, I do.
1.  Regarding the team structure, how large is the current DevOps team, and how closely do they work with the development teams on a daily basis?
2.  I see you are using Ansible and Jenkins. Are there any plans to migrate towards GitLab CI or Terraform in the near future, or is the current stack stable for the long term?"
