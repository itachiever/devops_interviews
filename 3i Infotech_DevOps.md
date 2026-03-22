# Job Description: 
### Role: Cloud & DevOps Engineer

### Position Overview 

We are seeking a highly skilled **Cloud & DevOps Engineer** with 4+ years of experience in designing, automating, and managing scalable cloud infrastructure and CI/CD pipelines using GitHub. The ideal candidate will have hands-on expertise in AWS and/or GCP, container orchestration (Kubernetes), Infrastructure as Code (Terraform/Ansible), and DevSecOps practices.

This role requires strong experience in building secure, high-availability systems, optimizing deployment processes, and improving operational efficiency through automation.


### Key Responsibilities

### CI/CD & Automation

* Design, implement, and maintain end-to-end CI/CD pipelines using Jenkins, GitLab CI/CD, or GitHub Actions.
* Automate build, test, and deployment workflows for containerized and non-containerized applications.
* Integrate security and quality scanning tools (SonarQube, Fortify, Trivy) within pipelines.
* Implement blue-green and canary deployment strategies in Kubernetes environments.

### Cloud Infrastructure (AWS / GCP)

* Provision and manage cloud infrastructure using Terraform, Ansible, and CloudFormation.
* Configure and manage services such as EC2, RDS, VPC, EKS, Lambda, S3, GKE, and Cloud Storage.
* Design secure networking architectures (VPC, subnets, security groups, NACLs, VPC peering).
* Implement cost optimization strategies and resource lifecycle management.


### Containerization & Orchestration

* Build and manage Docker images and container registries.
* Deploy and manage applications on Kubernetes (EKS/GKE).
* Implement Helm-based application deployments.
* Ensure high availability and scalability of containerized workloads.

### Monitoring & Observability

* Configure and maintain monitoring solutions using Prometheus and Grafana.
* Implement logging and alerting strategies for production systems.
* Ensure 99.9% uptime through proactive monitoring and performance optimization.

### Security & Compliance

* Implement IAM roles and access control policies.
* Manage secrets using AWS Secrets Manager, GCP Secrets Manager, or Vault.
* Ensure secure SSL/TLS configurations and vulnerability scanning.
* Follow DevSecOps best practices.


### System Administration & Scripting

* Manage Linux (Ubuntu) environments.
* Develop automation scripts using Python (Boto3), Bash, and Groovy.
* Optimize database queries and backup strategies.


### Required Skills & Qualifications

* 4+ years of experience in DevOps/Cloud Engineering.
* Strong hands-on experience with:

  * AWS and/or GCP
  * Jenkins or similar CI/CD tools
  * Docker and Kubernetes
  * Terraform and Ansible
* Experience with monitoring tools (Prometheus, Grafana).
* Strong understanding of networking, security, and cloud architecture.
* Proficiency in scripting (Python, Shell).
* Experience implementing blue-green and canary deployments.
* Knowledge of DevSecOps practices and security tools.

---

### Role: DevOps Engineer | Interview: 1st Round | Company: 3i Infotech | Client: ICICI | Experience: 4 Years

# Interview Questions:


1. **Tell me about yourself, your past experience, and your day-to-day activity in DevOps. What are your day-to-day activities?**

2. **You have worked on GitHub Actions, right?**

3. **Have you done multi-node deployment through GitHub Actions?**

4. **What is the flow and how would you perform the deployment from scratch?**

5. **In multi-node deployment, what approach would you use?**

6. **In security, what are the things that you are doing?**

7. **Which tools are you using for security?**

8. **If vulnerabilities are found in the scan, how do you identify them and handle them in the pipeline?**

9. **Is there any plugin used to generate vulnerability reports?**

10. **If a vulnerability is found, how do you notify the team or management and handle the pipeline failure?**

11. **Have you worked on Docker?**

12. **If you need to write a multi-stage Dockerfile, what is the best approach? Would you use multi-stage or single stage?**

13. **If a developer gives you a tar file, how would you load it into Docker using a command?**

14. **Have you worked on Kubernetes?**

15. **What does the Kubernetes `cordon` command do?**

16. **Have you worked on Ansible?**

17. **If you need to perform multi-server deployment using Ansible, what are the prerequisites and how would you write the pipeline and call the playbook?**

18. **Instead of SSH, can Ansible work using another port or approach (for example using AROS/port connectivity)?**

19. **In Linux servers, is SSH required for Ansible or can it work without SSH?**

20. **What are your day-to-day activities in your current organization and who is your client?**

21. **Is your client from the banking sector or a product-based company?**

22. **What exactly are you doing in that project?**

23. **When doing production deployment, is it done through CI/CD or manually?**

24. **For one application in production, how many servers are typically there?**

25. **How do you perform parallel deployment to 3-4 servers?**

26. **Do you have any questions for us?**

---
# Answers:

**1. Tell me about yourself, your past experience, and your day-to-day activity in DevOps.**
*   **Answer:** 4+ Years Exp. Started at 1st company name (AWS/K8s), currently at current company (DevSecOps Lead).
*   **Day-to-Day:** Building CI/CD pipelines, managing K8s clusters (AKS/EKS), automating security scans (Fortify/SonarQube), and troubleshooting infra issues.

**2. You have worked on GitHub Actions, right?**
*   **Answer:** Yes. Experienced in writing workflow YAMLs, configuring self-hosted runners, and integrating security steps.

**3. Have you done multi-node deployment through GitHub Actions?**
*   **Answer:** Yes. Used self-hosted runners to trigger deployments across multiple K8s nodes for high availability.

**4. What is the flow and how would you perform the deployment from scratch?**
*   **Answer:** Code Checkout -> Build/Test -> Security Scan (SAST) -> Docker Build -> Push to Registry -> Deploy to K8s (Helm/Kubectl).

**5. In multi-node deployment, what approach would you use?**
*   **Answer:** **Rolling Update** strategy. Updates pods incrementally to ensure zero downtime. For VMs, use Ansible with `serial` batches.

**6. In security, what are the things that you are doing?**
*   **Answer:** DevSecOps implementation: SAST (SonarQube), SCA (OWASP/Snyk), Container Scanning (Trivy), and managing Secrets (Vault).

**7. Which tools are you using for security?**
*   **Answer:** Fortify (SAST/DAST), SonarQube, Snyk, OWASP Dependency-Check, Trivy, and GitLeaks.

**8. If vulnerabilities are found in the scan, how do you identify them and handle them in the pipeline?**
*   **Answer:** Implement **Quality Gates**. Critical/High severity = Fail Pipeline. Block artifact promotion until fixed.

**9. Is there any plugin used to generate vulnerability reports?**
*   **Answer:** Yes. **Fortify Plugin** and **SonarQube Scanner** in Jenkins. In GitHub Actions, generate SARIF reports for the Security tab.

**10. If a vulnerability is found, how do you notify the team?**
*   **Answer:** Automated alerts via **Slack/Teams** to the dev channel. Detailed email report sent. Pipeline stops to prevent bad code from reaching Prod.

**11. Have you worked on Docker?**
*   **Answer:** Yes, 3+ years. Writing Dockerfiles, optimizing images, and managing registries (Nexus/Docker Hub).

**12. If you need to write a multi-stage Dockerfile, what is the best approach?**
*   **Answer:** **Multi-stage is best.** Use a heavy 'Build Image' for compiling, then copy artifacts to a lightweight 'Runtime Image' (Alpine). Reduces size and attack surface.

**13. If a developer gives you a tar file, how would you load it into Docker?**
*   **Answer:** Command: `docker load -i filename.tar`

**14. Have you worked on Kubernetes?**
*   **Answer:** Yes. Managed AWS EKS and Azure AKS. Experience with Helm, Ingress, RBAC, and HPA.

**15. What does the Kubernetes `cordon` command do?**
*   **Answer:** Marks a node as **Unschedulable**. New pods won't start on it, but existing pods keep running. Used for maintenance.

**16. Have you worked on Ansible?**
*   **Answer:** Yes. Used for config management, patching, and application deployment across VMs.

**17. How to perform multi-server deployment using Ansible?**
*   **Prereqs:** Inventory file, SSH keys.
*   **Execution:** `ansible-playbook -i inventory playbook.yml`

**18. Instead of SSH, can Ansible work using another port?**
*   **Answer:** Yes. Specify `ansible_port` in inventory for custom SSH ports. For Windows, use **WinRM**.

**19. In Linux servers, is SSH required for Ansible?**
*   **Answer:** Yes. SSH is the standard connection for Ansible on Linux nodes.

**20. What are your day-to-day activities and who is your client?**
*   **Answer:** Maintaining CI/CD and Infra. Client: Current company (Product), previously in previous company.

**21. Is your client from the banking sector or a product-based company?**
*   **Answer:** Previous work (at previous company) involved banking-grade security for Govt sector. Current role is Product-based.

**22. What exactly are you doing in that project?**
*   **Answer:** Architecting secure Jenkins pipelines with DMZ setup, integrating Fortify scans, and automating deployments to Azure AKS.

**23. When doing production deployment, is it done through CI/CD or manually?**
*   **Answer:** Strictly **Automated CI/CD**. Manual deployments are prohibited to ensure audit trails and consistency.

**24. For one application in production, how many servers are typically there?**
*   **Answer:** K8s environment. Typically 3-5 Worker Nodes (HA setup). Pods distributed across nodes.

**25. How do you perform parallel deployment to 3-4 servers?**
*   **Answer:** K8s handles this via **Rolling Updates**. For VMs, use Ansible `strategy: free` or increase `forks` count.

**26. Do you have any questions for us?**
*   **Answer:**
    1. What is the current maturity of Security integration in your pipelines?
    2. How is the DevOps team structured with Devs and Security?
 
