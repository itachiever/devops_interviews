# Role: DevOps (Jenkins)

The candidate should have experience in DevOps engineering with strong expertise in Jenkins.

## Required Skill Set

### Must Have Skills
- Expertise in **Jenkins**, including pipeline scripting and plugin management
- Experience with **Grafana** and **SonarQube**
- Proficient in **Python scripting**
- Proficient in **Shell scripting**
- Experience running automated or scripted test cases in CI/CD pipelines and implementing gating
- Experience with **Ansible** or **Salt** for configuration management and deployment automation
- Experience with **Infrastructure as Code (IaC)** tools and principles
- Experience using **Terraform** for infrastructure provisioning and management
- Familiarity with containerization technologies such as **Docker**
- Experience with monitoring tools such as **Prometheus**, **Grafana**, or the **ELK Stack** (a plus)
- Strong understanding of **version control systems**, particularly **Git**
- Strong understanding of modern **SDLC best practices and workflows**
- Proven experience designing, implementing, and managing **CI/CD pipelines using Jenkins** to automate build, test, and deployment processes

---

# 1st Round

1. Day-to-day activities?


2. Explain the various stages of a CI/CD pipeline.


3. Can you describe the project you worked on?


4. How did you work with SonarQube and handle the issues reported?


5. What automation scripts have you written or used?


6. Are you familiar with core Python programming concepts?


7. Write a Python program to: Create a dictionary, Insert key-value pairs, Print dictionary keys and values


8. Have you worked with Python? a) Explain Object-Oriented Programming (OOP) concepts.


9. What exactly is meant by containerization?


10. How do you check build failures? Is there a dedicated team for handling them?


11. Do you have any questions for me?

---
# 1st Round Answers:
---

### **1. Day-to-day activities?**
*   **Monitoring:** Checking server health & dashboards.
*   **CI/CD:** Managing Jenkins/GitLab pipelines and deployments.
*   **Maintenance:** Patching servers and rotating secrets.
*   **Collaboration:** Meeting with developers for requirements and troubleshooting.
*   **Automation:** Writing scripts to automate manual tasks.

### **2. Stages of a CI/CD Pipeline**
1.  **Source/Checkout:** Pull code from repo (GitHub/Bitbucket).
2.  **Build:** Compile code (Maven/npm).
3.  **Test:** Run automated tests (Unit/Integration).
4.  **Deploy (Staging):** Deploy to test environment.
5.  **Deploy (Production):** Deploy to live environment for users.

### **3. Project Description**
*   **Project:** E-commerce Application (Microservices).
*   **Architecture:** Hosted on AWS (EC2).
*   **Role:** CI/CD & IaC (Jenkins, Docker, Ansible).
*   **Outcome:** Reduced deployment time; enabled zero-downtime releases.

### **4. SonarQube & Issue Handling**
*   **Integration:** Scanned code automatically in Jenkins pipeline.
*   **Quality Gate:** Blocked deployment if critical bugs found.
*   **Handling:** Checked dashboard daily; worked with devs to fix vulnerabilities and code smells.

### **5. Automation Scripts**
*   **Bash:** Log cleanup (deletes logs older than 30 days).
*   **Python:** Backup script (uploads to AWS S3).
*   **Script:** Auto-restart service if it stops responding.

### **6. Core Python Concepts**
*   **Basics:** Variables, Data Types, Loops, Functions.
*   **File Handling:** Reading/Writing files.
*   **OOP:** Classes, Objects, Encapsulation.
*   **Libraries:** Used `Boto3` for AWS automation.

### **7. Python Program (Dictionary)**
```python
# Create Dict
my_dict = {}

# Insert Pairs
my_dict['name'] = 'Sai'
my_dict['role'] = 'DevOps'

# Print Keys
for key in my_dict.keys():
    print(key)

# Print Values
for value in my_dict.values():
    print(value)
```

### **8. OOP Concepts (Object-Oriented Programming)**
*   **Class:** Blueprint/Template (e.g., Car).
*   **Object:** Instance of the class (e.g., Red Ferrari).
*   **Encapsulation:** Hiding internal details.
*   **Inheritance:** Creating new class from existing one (e.g., Sports Car extends Car).

### **9. Containerization**
*   **Definition:** Packaging app + dependencies into a single "Container."
*   **Benefit:** Runs exactly the same on Laptop, Test Server, and Cloud.
*   **Tool:** Docker.

### **10. Checking Build Failures**
*   **Method:** Check Console Output/Logs.
*   **Responsibility:**
    *   **Code Error:** Developer fixes it.
    *   **Infra Error:** DevOps Engineer fixes it.

### **11. Questions for Interviewer**
1.  Team size and current tools used?
2.  Upcoming projects/technologies?
3.  Learning and certification support?

