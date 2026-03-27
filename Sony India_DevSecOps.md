# Job Description
### Role: DevSecOps Engineer

### Experience: 4 - 6 Years

### Key Skills

* DevOps
* CI/CD Pipeline Development & Management
* AWS
* Kubernetes
* Docker

### Job Responsibilities

1. Design, implement, and maintain **secure CI/CD pipelines** for cloud-native workloads.
2. Embed **security controls into Infrastructure as Code (IaC)** and deployment workflows.
3. Integrate **security scanning, testing, and policy enforcement** into build pipelines.
4. Implement and manage **cloud security controls** across cloud environments.
5. Support **identity and access management (IAM), secrets management, and least-privilege models**.
6. Automate **compliance, monitoring, and vulnerability management** processes.
7. Work with engineering teams to **remediate security findings and reduce risks**.
8. Contribute to **cloud security standards, patterns, and best practices**.
9. Support **incident response and post-incident security improvements**.
10. Stay updated with **DevSecOps tools, cloud security trends, and threats**.
11. Identify opportunities to **improve delivery processes and cloud adoption strategies**.
12. Stay current with **AWS services and emerging cloud technologies**.

------

### Role: DevSecOps | Company: Curatal | Client: Sony India Software Centre Private Limited (SISCPL) | Interview: 1st Round (by Curatal) | Experience: 4 years

# Interview Question:

1. **Can you give a brief detail about yourself? What kind of roles and responsibilities do you do on a daily basis?**

2. **Which cloud platforms have you worked on, and can you explain all the services you have used in detail?**

3. **Could you explain in detail how you integrated all the security tools into your CI/CD?**

4. **What kind of work have you done with Python?**

5. **Can you write or demonstrate any Python automation script that you have implemented?**

6. **What kind of challenges have you seen in your career till date?**

7. **What kind of work have you done on infrastructure vulnerabilities?**

8. **Do you have anything you want to ask?**


### Questions I asked:

1. **Is this requirement for in-house or for Sony India? What kind of project or requirements are there?**

2. **What might be the further process if my profile gets forwarded?**

---

# Answers:

### **1. Can you give a brief detail about yourself? What kind of roles and responsibilities do you do on a daily basis?**

**Answer:**
"I am a DevSecOps Engineer with over 4 years of experience. I started my journey at Previous company name, focusing on AWS and Jenkins automation, and currently, I am working at Current company. Here, I am responsible for architecting a secure DevSecOps platform.

**My daily responsibilities include:**
1.  **Pipeline Management:** Designing and maintaining CI/CD pipelines in Jenkins and GitHub Actions.
2.  **Security Integration:** Embedding SAST, DAST, and SCA tools (like Fortify and SonarQube) into the development lifecycle.
3.  **Infrastructure Management:** Provisioning cloud resources using Terraform and managing Kubernetes clusters (AKS/EKS).
4.  **Troubleshooting:** Resolving deployment failures and automating operational tasks using Python scripts."

### **2. Which cloud platforms have you worked on, and can you explain all the services you have used in detail?**

**Answer:**
"I have worked extensively on **AWS** and **Azure**.

**On AWS:**
*   **Compute:** EC2 for hosting applications and Lambda for serverless functions.
*   **Containers:** EKS (Elastic Kubernetes Service) for orchestration and ECR for container registries.
*   **Storage:** S3 for object storage and EBS for block storage.
*   **Networking:** VPC configuration, Security Groups, Route 53 (DNS), and Load Balancers.
*   **Database:** RDS (PostgreSQL/MySQL).

**On Azure:**
*   **Containers:** AKS (Azure Kubernetes Service) with private clusters.
*   **Security:** Azure Key Vault for secrets management and Azure Active Directory (Entra ID) for IAM.
*   **Monitoring:** Azure Monitor and Log Analytics workspaces.
*   **Storage:** Blob Storage."

### **3. Could you explain in detail how you integrated all the security tools into your CI/CD?**

**Answer:**
"I follow a **'Shift Left'** approach to integrate security at every stage of the pipeline:

1.  **Commit Stage (Pre-build):** I use **GitLeaks** to scan for hardcoded secrets (API keys) before the code is even built.
2.  **Build Stage (SAST):** Once the code is compiled, I run **SonarQube** for code quality and **Fortify** for Static Application Security Testing to identify injection flaws.
3.  **Dependency Stage (SCA):** I integrate **OWASP Dependency-Check** or **Snyk** to scan the libraries for known vulnerabilities (CVEs).
4.  **Container Stage:** Before pushing the image, I use **Trivy** to scan the Docker image for OS-level vulnerabilities.
5.  **Quality Gates:** I configure the pipeline to **fail automatically** if 'Critical' or 'High' vulnerabilities are found, preventing the artifact from moving to the next stage."

### **4. What kind of work have you done with Python?**

**Answer:**
"I use Python primarily for **Automation** and **Cloud Operations**.
1.  **Boto3 Automation:** I write scripts to interact with AWS services—for example, automating the cleanup of unused EC2 instances or S3 buckets to save costs.
2.  **Custom Scripts:** I have written scripts to parse log files from Kubernetes and send alert summaries to Teams/Slack.
3.  **API Interactions:** I use Python to fetch reports from security tools (like Fortify) via their APIs and generate consolidated compliance reports."

### **5. Can you write or demonstrate any Python automation script that you have implemented?**

**Answer:**
"Certainly. Let me explain a script I wrote to **automate the cleanup of idle EC2 instances**.

**Logic:**
1.  Import `boto3` library.
2.  Initialize the EC2 client.
3.  Fetch all instances with a specific tag (e.g., `Environment: Dev`).
4.  Check the CPU utilization via CloudWatch metrics.
5.  If CPU is < 5% for 1 hour, stop the instance.
6.  Log the output.

**Pseudocode:**
```python
import boto3

def cleanup_idle_instances():
    client = boto3.client('ec2')
    # Describe instances
    instances = client.describe_instances(Filters=[{'Name': 'tag:Env', 'Values': ['Dev']}])
    
    for instance in instances:
        # Check metrics logic here
        if is_idle(instance.id):
            client.stop_instances(InstanceIds=[instance.id])
            print(f"Stopped instance: {instance.id}")
```

### **6. What kind of challenges have you seen in your career till date?**

**Answer:**
"One major challenge I faced was **resistance from developers** when we initially enforced strict security gates (SAST/DAST) in the pipeline. They felt it slowed down their release velocity.

**How I solved it:**
1.  I integrated the security scans to run in parallel with the build process to save time.
2.  I implemented **Quality Gates** that only failed on Critical issues, allowing 'Medium/Low' warnings to proceed (initially) to avoid blocking every release.
3.  I automated the reporting so developers received clear emails on how to fix the issues, rather than just a generic failure message. This improved the culture significantly."

### **7. What kind of work have you done on infrastructure vulnerabilities?**

**Answer:**
"I focus on securing the infrastructure layer:
1.  **Image Hardening:** I ensure the base Docker images are minimal (Distroless/Alpine) and scanned for CVEs before deployment.
2.  **IaC Scanning:** I use tools like **Checkov** or **Terraform Scan** to detect misconfigurations in Terraform code (e.g., open Security Groups or unencrypted S3 buckets) before applying them.
3.  **Cluster Hardening:** I implement **RBAC** strictly in Kubernetes to ensure least privilege access and use **Network Policies** to restrict pod-to-pod communication."

### **8. Do you have anything you want to ask?**

**Answer:**
"Yes, I have two questions based on the requirement:
1.  Is this requirement for an in-house project at Sony India, or for a specific client requirement?
2.  What might be the further process if my profile gets forwarded? Will there be a technical deep-dive round next?"

---

### Short Q&A:

**1. Brief detail about yourself & daily activities?**
*   **Intro:** 4+ Years Exp.
*   **Daily:** CI/CD Pipelines, Security Integration (Fortify/Sonar), K8s Management, Automation.

**2. Which cloud platforms & services used?**
*   **AWS:** EC2, EKS, S3, VPC, RDS, Lambda.
*   **Azure:** AKS (Private), KeyVault, Monitor, Blob Storage.

**3. How integrated security tools into CI/CD?**
*   **Commit:** GitLeaks (Secrets Scan).
*   **Build:** SonarQube & Fortify (SAST).
*   **Dependency:** OWASP/Snyk (SCA).
*   **Container:** Trivy (Image Scan).
*   **Gate:** Fail pipeline on Critical/High vulnerabilities.

**4. Work done with Python?**
*   **Automation:** Boto3 scripts for AWS resource mgmt.
*   **Ops:** Log parsing, API integration for reports, Custom alerts.

**5. Demonstrate Python automation script?**
*   **Use Case:** Cleanup Idle EC2 instances (Cost Optimization).
*   **Logic:** `Boto3` -> Filter Instances -> Check CPU -> Stop if Idle.

**6. Challenges seen in career?**
*   **Challenge:** Developer resistance to Security Gates slowing releases.
*   **Solution:** Parallel scanning, Quality Gates for Critical only, Automated Fix Reports.

**7. Work on infrastructure vulnerabilities?**
*   **IaC Scanning:** Checkov/Terrascan for Terraform misconfigurations.
*   **Image Hardening:** Minimal base images (Alpine).
*   **Access:** Strict RBAC & K8s Network Policies.

**8. Questions to ask?**
*   Is this for Sony India in-house or a specific client?
*   What is the further interview process?

