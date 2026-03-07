# Role: DevOps Engineer


## Questions:

1. Can you briefly explain the technology stacks and skills you have worked on?

2. What is CI/CD? What do you know about it?

3. What tools come under CI, CD, and CM (Continuous Monitoring), CT (Continuous Testing) ?

4. What CI/CD tool have you worked on? What tools were used in the pipeline, and what was the sequence?

5. What is SonarQube?

6. What is the difference between Jenkins and GitLab?

7. If you get a chance to set up a production CI/CD environment, which tool would you prefer—GitLab or Jenkins—and why?

8. Can you list some commonly used Jenkins plugins?

9. Do you use Git on a daily basis?

10. Suppose you are pushing code to raise a Pull Request and encounter a merge conflict. How would you fix it? What commands would you use?

11. Let’s say you are currently at commit 20. How would you move back to commit 18 or 19?

12. What Git commands do you use on a daily basis?

13. What have you done using Ansible? Which platforms have you worked on?

14. How would you install the Apache server on Linux using Ansible?

15. What do you know about Kubernetes?

16. What is the difference between Docker and Kubernetes?

17. Explain the components of Kubernetes.

18. What is the difference between a Node and a Pod in Kubernetes?

19. What is the difference between Grafana and Prometheus?




# Answers:

---

### **1. Technology & Skills**

**Q1. Can you briefly explain the technology stacks and skills you have worked on?**

**Answer:**
A typical technology stack for a DevOps Engineer with 2.5 years of experience includes:
*   **Operating System:** Linux (RHEL, Ubuntu) for system administration.
*   **Version Control:** Git and GitHub/GitLab for source code management.
*   **CI/CD Tools:** Jenkins and GitLab CI for building and deploying applications.
*   **Containerization:** Docker for creating images and Kubernetes for orchestration.
*   **Configuration Management:** Ansible for automating server configuration.
*   **Cloud:** AWS or Azure for managing cloud infrastructure.
*   **Infrastructure as Code:** Terraform or CloudFormation.
*   **Monitoring:** Prometheus and Grafana for tracking system health.

---

### **2. CI/CD Concepts**

**Q2. What is CI/CD? What do you know about it?**

**Answer:**
**CI/CD** stands for **Continuous Integration** and **Continuous Deployment/Delivery**.
*   **Continuous Integration (CI):** Developers frequently merge their code changes into a central repository. Automated builds and tests are run every time code is merged to detect bugs early.
*   **Continuous Deployment (CD):** Code changes are automatically deployed to a testing or production environment after passing the CI stage. This ensures that the software is always in a deployable state and reduces the time to market.

**Q3. What tools come under CI, CD, and CM (Continuous Monitoring), CT (Continuous Testing)**

**Answer:**
*   **CI Tools:** Jenkins, GitLab CI/CD, CircleCI, Travis CI.
*   **CD Tools:** ArgoCD, Spinnaker, Flux (for Kubernetes), and the deployment features of Jenkins/GitLab.
*   **CM (Continuous Monitoring):** Grafana, Prometheous
*   **CT (Continuous Testing):** Fortify, SonarQube, Sonatype, Trivy, Snyk, GitLeaks
*   
**Q4. What CI/CD tool have you worked on? What tools were used in the pipeline, and what was the sequence?**

**Answer:**
Experience is typically with **Jenkins** or **GitLab CI**.
**Sequence of a Pipeline:**
1.  **Code Checkout:** Using Git plugin or `git clone`.
2.  **Build:** Using tools like Maven or `npm install` to compile the code.
3.  **Test:** Running Unit Tests (JUnit) and Integration Tests.
4.  **Code Quality:** Scanning code with **SonarQube**.
5.  **Build Image:** Using Docker to create a container image.
6.  **Push Image:** Pushing the image to Docker Hub or AWS ECR.
7.  **Deploy:** Using Kubernetes commands (`kubectl apply`) or Ansible to deploy the application.

---

### **3. SonarQube**

**Q5. What is SonarQube?**

**Answer:**
**SonarQube** is an open-source platform for **continuous inspection of code quality**. It performs static code analysis to detect bugs, code smells, and vulnerabilities.
It provides reports on:
*   **Code Duplicates:** Repeated code blocks.
*   **Code Coverage:** How much of the code is tested by unit tests.
*   **Security Vulnerabilities:** Potential security flaws (like SQL Injection risks).
It helps maintain technical debt and ensures the codebase remains clean and secure.

---

### **4. Jenkins & GitLab**

**Q6. What is the difference between Jenkins and GitLab?**

**Answer:**
*   **Jenkins:** It is a standalone, self-hosted automation server. It is highly flexible because it has a massive plugin ecosystem, but it requires maintenance (server updates, plugin management). It uses **Groovy** for pipeline logic.
*   **GitLab:** It is a complete DevOps platform (Git repository + CI/CD + Project Management). It is **integrated**, meaning you don't need to install extra plugins to connect it to your code. It uses **YAML** for pipelines, which is generally easier to read than Groovy.

**Q7. If you get a chance to set up a production CI/CD environment, which tool would you prefer—GitLab or Jenkins—and why?**

**Answer:**
**Preference is usually GitLab CI** for modern setups.
**Reason:** It provides an "All-in-One" experience. Since the code repository (Git), Issue Tracking, and CI/CD pipeline are in the same place, it reduces the complexity of integration and maintenance. The YAML pipelines are easier for developers to write and review compared to Jenkinsfiles. However, if the requirement involves complex legacy integrations or a very specific plugin not available in GitLab, Jenkins would be the choice.

**Q8. Can you list some commonly used Jenkins plugins?**

**Answer:**
*   **Git Plugin:** To clone repositories from GitHub/GitLab.
*   **Pipeline Plugin:** To define build pipelines as code.
*   **Docker Plugin:** To build and use Docker containers within builds.
*   **Credentials Binding Plugin:** To securely use passwords/keys in builds.
*   **SonarQube Scanner:** To integrate code quality analysis.
*   **Blue Ocean:** To provide a modern, visual UI for pipelines.

---

### **5. Git**

**Q9. Do you use Git on a daily basis?**

**Answer:**
Yes, Git is used daily for version control, collaborating with team members, and managing code changes across branches.

**Q10. Suppose you are pushing code to raise a Pull Request and encounter a merge conflict. How would you fix it? What commands would you use?**

**Answer:**
To fix a merge conflict:
1.  **Pull the latest changes:** `git pull origin <branch-name>`
2.  **Identify conflicts:** Git will list the files with conflicts.
3.  **Open the files:** Look for markers like `<<<<<<<` and `>>>>>>>`.
4.  **Edit the files:** Manually decide which code to keep or merge both.
5.  **Stage the files:** `git add <resolved-file-name>`
6.  **Commit the resolution:** `git commit -m "Resolved merge conflict"`
7.  **Push the changes:** `git push origin <branch-name>`

**Q11. Let’s say you are currently at commit 20. How would you move back to commit 18 or 19?**

**Answer:**
This is done using the `git reset` command.
*   **To go back to Commit 18 but keep changes in staging area:** `git reset --soft HEAD~2`
*   **To go back to Commit 18 and discard changes in staging (but keep files):** `git reset --mixed HEAD~2`
*   **To go back to Commit 18 and discard ALL changes (Dangerous):** `git reset --hard HEAD~2`

**Q12. What Git commands do you use on a daily basis?**

**Answer:**
*   `git add`: To stage files.
*   `git commit`: To save changes.
*   `git push` / `git pull`: To sync with remote.
*   `git status`: To check the state of files.
*   `git log`: To see commit history.
*   `git checkout` / `git switch`: To switch branches.

---

### **6. Ansible**

**Q13. What have you done using Ansible? Which platforms have you worked on?**

**Answer:**
Ansible is used for **Configuration Management** and **Application Deployment**.
**Tasks include:**
*   Installing and configuring packages (like Nginx, Java).
*   Managing users and permissions.
*   Copying configuration files to servers.
*   Deploying applications.
**Platforms:** Typically worked on are **Linux** (RHEL, CentOS, Ubuntu) and **Windows** (using WinRM).

**Q14. How would you install the Apache server on Linux using Ansible?**

**Answer:**
We would write a **Playbook** (a YAML file).
We use the `yum` or `apt` module depending on the OS distribution.
**Example (for Ubuntu/Debian):**
```yaml
- name: Install Apache
  apt:
    name: apache2
    state: present
    update_cache: yes
```
Running this playbook (`ansible-playbook -i hosts install_apache.yml`) will ensure Apache is installed on the target servers.

---

### **7. Docker & Kubernetes**

**Q15. What do you know about Kubernetes?**

**Answer:**
**Kubernetes (K8s)** is an open-source **Container Orchestration Platform**. It automates the deployment, scaling, and management of containerized applications (like Docker containers).
It handles:
*   **Scaling:** Increasing/decreasing the number of application instances automatically.
*   **Self-healing:** Restarting containers that fail.
*   **Load Balancing:** Distributing network traffic across containers.

**Q16. What is the difference between Docker and Kubernetes?**

**Answer:**
*   **Docker:** is a platform used to **create** and **run** containers individually. It packages the application and its dependencies into an image. It runs on a single host.
*   **Kubernetes:** is a platform used to **manage** and **orchestrate** those Docker containers across a cluster of multiple machines (Nodes). It makes sure the containers are running, healthy, and connected to the network.

**Q17. Explain the components of Kubernetes.**

**Answer:**
Kubernetes has two main parts: the **Control Plane** and the **Worker Nodes**.
*   **Control Plane (Master):** The brain of the cluster.
    *   **API Server:** The front door for all commands.
    *   **etcd:** The key-value store that holds cluster data.
    *   **Scheduler:** Decides which Node runs a new Pod.
    *   **Controller Manager:** Ensures the desired state (e.g., 3 copies of an app).
*   **Worker Node:** Where applications run.
    *   **Kubelet:** The agent that talks to the Master.
    *   **Kube-proxy:** Manages network rules.
    *   **Container Runtime:** (e.g., Docker) that runs the containers.

**Q18. What is the difference between a Node and a Pod in Kubernetes?**

**Answer:**
*   **Node:** It is a physical or virtual machine (Worker). It is the hardware resource (CPU, RAM, Disk) where the Kubernetes cluster runs.
*   **Pod:** It is the smallest deployable unit in Kubernetes. A Pod wraps one or more containers. Containers inside a Pod share the same IP address and storage. A Pod runs *on* a Node.

---

### **8. Monitoring Tools**

**Q19. What is the difference between Grafana and Prometheus?**

**Answer:**
*   **Prometheus:** It is a **Time-Series Database** and a monitoring system. Its job is to **scrape (pull)** metrics from applications and store them. It has its own query language called **PromQL**.
*   **Grafana:** It is a **Visualization** tool. It connects to data sources like Prometheus and creates beautiful dashboards and graphs. It does not store data itself; it just visualizes the data stored in Prometheus.
*   **In short:** Prometheus collects the data, and Grafana shows the data.
