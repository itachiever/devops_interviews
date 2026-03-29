 # Questions:

1. Can you explain your profile, your work, skill set, and projects?
2. Where are you currently based / which part of India are you from?
3. Why are you looking for a job change?
4. What have you done from scratch in your current project?
5. What is your team size?
6. Who do you report to?
7. Which client are you working for?
8. Can you explain your client architecture? How is it set up?
9. Is it monolithic or microservices? What kind of system is it?
10. How many services are there?
11. What is the reason for using Helm?
12. What monitoring tools are you using?
13. Are you using Azure only or a hybrid cloud?
14. Are you using VPN or a jump server? How does access work?
15. Where do you store your container images?
16. Have you heard about CrashLoopBackOff?
17. How do you debug a pod that is repeatedly restarting?
18. What is ClusterIP and NodePort? (difference)
19. What are Pods, Deployments, and Services?
20. How do you perform deployments? (initiation, process, closure)
21. What do you do if a deployment fails?
22. What is your rollback strategy? How do you revert to the previous deployment?
23. If deployment includes database changes (columns added/deleted), how do you roll it back?
24. You can use Liquibase or other tools — in your case, what process do you follow?
25. Which database are you using?
26. How are you using AI in your systems or day-to-day work?
27. What is your biggest achievement in your career?
28. If a server is going down intermittently and hanging, how will you handle it?
29. Do you have experience with APM tools like New Relic or Datadog?
30. How do you manage secrets?
31. Do you have any questions for me?


---

# 🧠 Interview Questions based on categories

### 🔹 Basic / Intro

1. **Can you explain your profile? What work have you done, your skill set, and projects?**
2. **Where are you currently based? / Which part of India are you from?**
3. **Why are you looking for a job change?**



### 🔹 Experience Depth

4. **What have you done from scratch in your current project?**
5. **What is your team size?**
6. **Who do you report to?**
7. **Which client are you working for?**


### 🔹 Architecture & System Design

8. **Can you explain your client architecture? How is it set up?**
9. **Is it monolithic or microservices? What kind of system is it?**
10. **How many services are there?**


## 🔹 Kubernetes / DevOps Concepts

11. **What is the reason for using Helm?**
12. **What monitoring tools are you using?**
13. **Are you using Azure only or hybrid cloud?**
14. **Are you using VPN or jump server? How does access work?**
15. **Where do you store container images?**

### 🔹 Kubernetes Troubleshooting

16. **Have you heard of CrashLoopBackOff?**
17. **How do you debug a pod that is repeatedly restarting?**


### 🔹 Kubernetes Basics

18. **What is ClusterIP and NodePort? (difference expected)**
19. **What are Pods, Deployments, and Services?**


### 🔹 CI/CD & Deployment

20. **How do you perform deployments? (process, initiation, closure)**
21. **What do you do if deployment fails?**
22. **What is your rollback strategy? How do you revert to previous deployment?**

### 🔹 Advanced Scenario (IMPORTANT)

23. **If deployment includes DB changes (columns added/deleted), how do you rollback?**
24. **You can use Liquibase, but in your case what process do you follow?**
25. **Which database are you using?**


### 🔹 AI Usage

26. **How are you using AI in your systems or day-to-day work?**


### 🔹 Behavioral

27. **What is your biggest achievement in your career?**


### 🔹 Troubleshooting Scenario

28. **If a server is going down intermittently and hanging, how will you handle it?**


### 🔹 Tools Exposure

29. **Do you have experience with APM tools like New Relic or Datadog?**


### 🔹 Security

30. **How do you manage secrets?**


### 🔹 Closing

31. **Do you have any questions for me?**


---

# Answers:

**1. Can you explain your profile, your work, skill set, and projects?**
*   **Role:** DevSecOps Engineer (4+ Years Exp).
*   **Key Skills:** CI/CD (Jenkins), Cloud (AWS/Azure), Containers (Kubernetes/Docker).
*   **Focus:** Automating SDLC & "Shift Left" Security.
*   **Current Project:** Built DevSecOps Platform from scratch (Hybrid Cloud).

**2. Where are you currently based / which part of India are you from?**
*   **Location:** Mumbai.
*   **Open to:** Relocation / Hybrid models.

**3. Why are you looking for a job change?**
*   **Current Status:** Successfully built stable infrastructure.
*   **Goal:** Seeking complex challenges at scale.
*   **Focus:** High-availability systems & Advanced Cloud Architecture.

**4. What have you done from scratch in your current project?**
*   **Achievement:** Built Organization's Internal DevSecOps Platform.
*   **Components:** Jenkins Setup, DMZ Gateway (NGINX), Kubernetes Deployments.
*   **Security:** Integrated SAST/DAST/SCA pipelines.
*   **Connectivity:** Established Secure VPN (On-prem to Cloud).

**5. What is your team size?**
*   **Core Team:** 3-4 Engineers.
*   **Support Scope:** Supporting ~20-30 Developers.

**6. Who do you report to?**
*   **Reporting Manager:** Engineering Manager.

**7. Which client are you working for?**
*   **Sector:** Enterprise [Banking/Financial/IT Services].
*   **Workload:** Critical internal apps (High Compliance).

**8. Can you explain your client architecture? How is it set up?**
*   **Architecture:** Hybrid Cloud.
*   **On-Prem:** DevSecOps Toolchain (Jenkins, Nexus).
*   **Cloud:** Application Workloads on Azure AKS & AWS EKS.
*   **Connection:** Site-to-Site VPN.

**9. Is it monolithic or microservices? What kind of system is it?**
*   **Architecture Type:** Microservices.
*   **Pattern:** Database per Service.
*   **Benefit:** Independent Scaling & Deployment.

**10. How many services are there?**
*   **Count:** 15-20 Microservices.
*   **Setup:** Independent Pipelines & Configs.

**11. What is the reason for using Helm?**
*   **Reusability:** Template YAMLs (Dev/Stage/Prod).
*   **Versioning:** Track releases via Helm Charts.
*   **Lifecycle:** Simplifies Upgrades & Rollbacks.

**12. What monitoring tools are you using?**
*   **Metrics:** Prometheus & Grafana.
*   **Logs:** ELK Stack (Elasticsearch, Logstash, Kibana).
*   **Cloud:** Azure Monitor / Container Insights.

**13. Are you using Azure only or a hybrid cloud?**
*   **Model:** Hybrid Cloud.
*   **Setup:** On-prem Build Servers + Cloud Compute (AKS/EKS).
*   **Benefit:** Data Control + Cloud Scalability.

**14. Are you using VPN or a jump server? How does access work?**
*   **Access:** No Public Exposure.
*   **Method:** VPN Client for internal network.
*   **K8s:** Private Clusters (API access via VPN only).

**15. Where do you store your container images?**
*   **Registry:** Sonatype Nexus Repository.
*   **Usage:** Proxy for public images + Internal app storage.

**16. Have you heard about CrashLoopBackOff?**
*   **Definition:** K8s error state.
*   **Meaning:** Container starts but crashes repeatedly.
*   **Action:** K8s backs off before restarting.

**17. How do you debug a pod that is repeatedly restarting?**
*   **Step 1:** `kubectl describe pod` (Check Events).
*   **Step 2:** `kubectl logs --previous` (See crashed logs).
*   **Common Issues:** Missing Env Vars, Probes, App Errors.

**18. What is ClusterIP and NodePort? (difference)**
*   **ClusterIP:** Internal IP only (Default). Use: Internal Services.
*   **NodePort:** Exposes port on Node IP. Use: Dev/Test or behind Load Balancer.

**19. What are Pods, Deployments, and Services?**
*   **Pod:** Smallest unit (Running process).
*   **Deployment:** Controller (Manages Replicas/State).
*   **Service:** Networking (Stable IP/Endpoint).

**20. How do you perform deployments? (initiation, process, closure)**
*   **Workflow:** GitOps.
*   **Start:** Merge Request (Update Helm values).
*   **Process:** Jenkins Build -> Helm Upgrade.
*   **End:** Health Check -> Slack Notification.

**21. What do you do if a deployment fails?**
*   **Investigate:** Jenkins logs & `kubectl describe`.
*   **Identify:** `ImagePullBackOff` or `CrashLoopBackOff`.
*   **Action:** Stop pipeline, fix issue, redeploy.

**22. What is your rollback strategy? How do you revert to the previous deployment?**
*   **Command:** `helm rollback <release> <revision>`.
*   **Auto-Heal:** Pipeline auto-triggers rollback if health checks fail.

**23. If deployment includes database changes (columns added/deleted), how do you roll it back?**
*   **Strategy:** Backward Compatibility.
*   **Step 1:** Deploy code supporting old & new schema.
*   **Step 2:** Run DB Migration.
*   **Rule:** Never automate DB rollbacks (Risk of data loss).

**24. You can use Liquibase or other tools — in your case, what process do you follow?**
*   **Tool:** Custom SQL scripts via Jenkins.
*   **Logic:** Python wrapper tracks executed scripts.
*   **Repo:** Migration scripts in separate Git repo.

**25. Which database are you using?**
*   **Relational:** PostgreSQL.
*   **Caching:** Redis.
*   **Messaging:** Kafka.

**26. How are you using AI in your systems or day-to-day work?**
*   **Scripting:** Generate logic for Python/Bash.
*   **Troubleshooting:** Analyze cryptic error logs.
*   **Docs:** Draft runbooks & diagrams.

**27. What is your biggest achievement in your career?**
*   **Achievement:** Built Hybrid DevSecOps Platform from scratch.
*   **Impact:** Moved team from Manual -> Fully Automated.
*   **Components:** Jenkins, Security Scanning, K8s, VPN.

**28. If a server is going down intermittently and hanging, how will you handle it?**
*   **Debug:** `top`, `htop` (CPU/Mem).
*   **Disk:** Check I/O (`iostat`) & Space (`df -h`).
*   **Logs:** `/var/log/syslog` & App Logs.
*   **Fix:** Kill memory leak process or Scale resources.

**29. Do you have experience with APM tools like New Relic or Datadog?**
*   **Stack:** Prometheus + Grafana + ELK.
*   **Concept:** Familiar with APM concepts (Tracing).
*   **Integration:** Using OpenTelemetry for deep tracing.

**30. How do you manage secrets?**
*   **Prevention:** GitLeaks (Scan code).
*   **Storage:** AWS Secrets Manager / Azure KeyVault.
*   **Injection:** External Secrets Operator (Sync to K8s).

**31. Do you have any questions for me?**
*   **Question 1:** Team structure & collaboration with Devs?
*   **Question 2:** Future roadmap (Migration to GitLab CI/Terraform)?
