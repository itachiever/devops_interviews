# Job Description: 
Role: DevSecOps Engineer

### Mandatory Skills

* IAM
* Networking
* CI/CD pipelines in GitLab
* CloudFormation
* OpenTofu
* Docker
* Kubernetes
* EKS
* GitLab security scanning

### Requirements

* 2+ years of hands-on experience with cloud platforms (AWS preferred), including IAM, networking, compute, and storage.
* 2+ years of experience designing and maintaining CI/CD pipelines in GitLab, including integrating security scanning and pipeline controls.
* 2+ years of Infrastructure as Code (IaC) experience using CloudFormation, OpenTofu, or similar tools.
* Advanced understanding of cloud security principles, including least privilege, network segmentation, and encryption.
* 1+ year of experience integrating GitLab security scanning (SAST, DAST, SCA, container scanning, secrets detection) into CI/CD pipelines.
* 1+ year of experience with container platforms and tooling (Docker, Kubernetes, EKS).
* 1+ year of experience with identity and access management (AWS IAM, Identity Center, role-based access).
* 1+ year of experience implementing logging, monitoring, and alerting for cloud workloads.
* Understanding of SDLC, DevOps practices, and automated testing strategies.
* Experience implementing reusable pipeline templates and enforcing security guardrails at scale.
* Experience integrating CI/CD pipelines with cloud IAM and secrets management using short-lived credentials.
* Advanced problem-solving and analytical skills.
* Demonstrated ability to collaborate across development, security, and infrastructure teams.
* Demonstrated willingness to take accountability and ownership to solve problems.


### Nice to Have

* AWS Certified Solutions Architect, Security – Specialty, or Cloud Practitioner certification.
* Experience with compliance frameworks (SOC 2, ISO 27001, NIST, CIS Benchmarks).
* Experience with policy-as-code tools (OPA, Sentinel, AWS Config rules).
* Experience supporting production incident response and post-incident analysis.


### Roles & Responsibilities

This role combines strong cloud engineering, security, and automation skills to support modern application platforms. The DevSecOps Engineer partners closely with Cloud Engineering, Application Development, Security, and Architecture teams to enforce security-by-design principles while enabling developer velocity.

### Responsibilities

* Design, implement, and maintain secure CI/CD pipelines for cloud-native workloads.
* Embed security controls into Infrastructure as Code (IaC) and deployment workflows.
* Integrate security scanning, testing, and policy enforcement into build pipelines.
* Implement and manage cloud security controls across cloud environments.
* Support identity and access management, secrets management, and least-privilege models.
* Automate compliance, monitoring, and vulnerability management processes.
* Partner with engineering teams to remediate security findings and reduce risk.
* Contribute to cloud security standards, patterns, and best practices.
* Support incident response, post-incident reviews, and security improvements.
* Stay current with emerging DevSecOps tools, AWS services, cloud security trends, and threats.
* Identify opportunities to streamline delivery processes and improve cloud adoption strategies.

---

### Role: DevSecOps Engineer | Interview: 1st Round | Company: Sonata Software

# Interview Questions:


1. **Can you give a brief introduction about yourself?**

2. **Your company wants to move a batch data processing workflow from on-prem to AWS ensuring daily ingestion, processing, and full traceability. Which AWS services would you choose and how would you architect the solution for reliability and monitoring?**

3. **You need to migrate a legacy web application with a relational database to AWS ensuring high scalability, availability, and minimal downtime. What AWS services and architecture would you use, and how would you plan the migration?**

4. **You are responsible for maintaining multiple CloudFormation stacks with strict compliance and security requirements. How do you ensure that only approved resource configurations are deployed, both initially and during updates?**

5. **A critical production stack managed by CloudFormation contains sensitive resources and strict policies. How do you safely decommission this stack while ensuring compliance, retention requirements, and avoiding data loss or service disruption?**

6. **A development team wants to rapidly deploy new features but is concerned about security risks. As a DevSecOps expert, how would you balance speed with robust security?**

7. **How comfortable are you in Python (including writing scripts for automation)?**

8. **Write a Python script that automatically rotates and archives log files in a specified directory.**

---
# Answers:

### **1. Can you give a brief introduction about yourself?**

**Strategy:** Keep it concise. Map your experience directly to the JD. Highlight the transition from DevOps to DevSecOps to show career growth.

**Answer:**
"Hi, I’m a DevSecOps Engineer with over 4 years of hands-on experience in building secure CI/CD pipelines and managing hybrid cloud infrastructure. My core strength lies in 'Security by Design'—integrating security controls early in the SDLC.

In my current role, I architected a secure hybrid DevSecOps platform from scratch, utilizing Jenkins, Kubernetes, and Fortify scanners, while ensuring network security via DMZ architectures and VPNs. I have deep experience with IaC using Terraform and CloudFormation, and I’ve recently been focusing heavily on GitLab CI/CD and AWS EKS to automate deployments and enforce compliance.

I hold AWS and Azure certifications, which validate my understanding of cloud-native security principles like least privilege and IAM. I’m passionate about automating security guardrails to enable developer velocity without compromising compliance."

---

### **2. Batch Data Processing Workflow (On-prem to AWS)**

**Question:** *Move batch data processing from on-prem to AWS ensuring daily ingestion, processing, and full traceability.*

**Answer:**
"To architect a reliable and traceable batch processing solution, I would leverage an **Event-Driven Serverless Architecture**, which is cost-effective and highly scalable.

1.  **Ingestion:** I would use **Amazon S3** as the landing zone. For daily ingestion, **AWS DataSync** or **AWS Storage Gateway** can be used to move data securely from on-prem to S3 over private connections (like Direct Connect or VPN).
2.  **Trigger & Orchestration:** **Amazon EventBridge** will trigger the workflow on a schedule or upon S3 object upload. **AWS Step Functions** would orchestrate the workflow to handle retries and error handling.
3.  **Processing:** Depending on the complexity, I’d use **AWS Glue** for ETL jobs or **AWS Lambda** for lightweight processing.
4.  **Traceability (Mandatory):** This is critical. I would implement an end-to-end audit trail:
    *   **AWS CloudTrail:** To log all API calls.
    *   **Amazon CloudWatch Logs & Metrics:** To monitor job execution status.
    *   **AWS X-Ray:** If we use microservices, X-Ray provides distributed tracing.
    *   *Pro Tip:* I would generate a unique **Correlation ID** at the start of the batch job and pass it through every step (Ingestion -> Processing -> Storage) so we can trace a single file's lifecycle in logs.

This architecture ensures reliability via Step Functions (automatic retries) and full traceability via CloudTrail/X-Ray."

---

### **3. Migration of Legacy Web App with RDBMS**

**Question:** *Migrate a legacy web application with a relational database to AWS ensuring high scalability, availability, and minimal downtime.*

**Answer:**
"For a legacy migration requiring high availability and minimal downtime, I would adopt a **Re-platforming strategy (Lift, Tinker, and Shift)** rather than a simple rehost.

1.  **Database Migration (Critical Path):** To minimize downtime, I would use **AWS Database Migration Service (DMS)**.
    *   I would set up the target as **Amazon RDS** (or Aurora for better scaling) in a Multi-AZ deployment.
    *   DMS allows **Continuous Replication** (CDC), meaning we can keep the on-prem DB live, sync data to AWS in real-time, and only switch over during a short maintenance window.
2.  **Application Layer:**
    *   I would containerize the legacy application using **Docker** and deploy it to **Amazon EKS** (Elastic Kubernetes Service). This addresses scalability requirements—we can use Horizontal Pod Autoscaler (HPA).
    *   For availability, I would deploy worker nodes across multiple Availability Zones behind an **Application Load Balancer (ALB)**.
3.  **Network & Security:**
    *   Use **AWS IAM Roles for Service Accounts (IRSA)** to grant pods least-privilege access.
    *   Store DB credentials in **AWS Secrets Manager**.

By combining DMS for near-zero downtime database migration and EKS for auto-scaling compute, we meet all requirements."

---

### **4. CloudFormation Stack Compliance & Security**

**Question:** *Maintain multiple CloudFormation stacks with strict compliance. How to ensure only approved resource configurations are deployed?*

**Answer:**
"Ensuring compliance at scale requires a 'Shift Left' approach combined with runtime guardrails.

1.  **Pre-Deployment (Shift Left):**
    *   I would implement **cfn-nag** or **Checkov** as a mandatory step in the GitLab CI/CD pipeline. This scans the CloudFormation templates *before* deployment, failing the build if insecure configurations (like open S3 buckets or overly permissive IAM roles) are detected.
    *   For advanced policy enforcement, I would use **OPA (Open Policy Agent)** with Rego policies to validate templates against company standards.

2.  **During Deployment (Guardrails):**
    *   I would utilize **AWS CloudFormation Guard**. This acts as a policy-as-code tool that prevents non-compliant stacks from being deployed if they violate the defined rules (e.g., mandating encryption or specific instance types).

3.  **Post-Deployment (Drift Detection):**
    *   I would enable **AWS CloudFormation Drift Detection** to alert us if manual changes are made outside the IaC pipeline.
    *   Additionally, **AWS Config Rules** would monitor the resources continuously to ensure they maintain compliance state over time."

---

### **5. Safely Decommissioning a Critical Production Stack**

**Question:** *Safely decommission a critical stack while ensuring compliance, retention, and avoiding data loss.*

**Answer:**
"Decommissioning critical production resources is high-risk. My approach would be methodical:

1.  **Data Retention & Backup:** Before any deletion, I would perform a final backup. For databases, I would take a final snapshot. For S3 buckets, I would enable **Object Lock** or replicate data to a dedicated 'Archive' bucket with a retention policy. The CloudFormation template must have `DeletionPolicy: Retain` set on critical resources (RDS, S3) to preserve data even if the stack is deleted.
2.  **Dependency Mapping:** I would use **AWS CloudTrail** and **VPC Flow Logs** to analyze traffic. This ensures no other active production service is secretly calling this stack’s APIs or depending on its resources.
3.  **Deregistration:** Remove the stack’s DNS entries from Route53 and deregister targets from Load Balancers to cut off traffic gracefully.
4.  **The 'Sandbox' Test:** If possible, I would first perform the decommissioning process in a Staging environment to validate the CloudFormation deletion behavior.
5.  **Execution:** Finally, delete the CloudFormation stack. Because of the `Retain` policies, the logical resources are removed from CloudFormation management, but the physical data assets remain secure for auditing purposes."

---

### **6. Balancing Speed with Robust Security**

**Question:** *Development team wants speed, but concerned about security risks. As DevSecOps expert, how to balance?*

**Answer:**
"The old mindset was 'Security as a Gatekeeper,' which slowed things down. As a DevSecOps engineer, I advocate for the **'Paved Road' or 'Golden Path' philosophy**:

1.  **Automated Guardrails, not Gates:** I integrate security scanning (SAST, SCA, Container Scanning) directly into the GitLab CI pipeline. Developers get instant feedback in their Merge Requests (MR). If a critical vulnerability is found, the pipeline breaks automatically. This removes the bottleneck of a manual security review.
2.  **Reusable Secure Templates:** Instead of asking devs to write secure infrastructure code from scratch, I provide pre-approved, security-hardened templates (e.g., a standard CloudFormation module for an EKS cluster or S3 bucket). This allows them to deploy fast, knowing the security best practices are 'baked in' by default.
3.  **Shift Left Education:** I work with teams to help them fix issues locally in their IDEs before they even push code.

This approach shifts security from being a 'blocker' to being an 'enabler'—we automate the compliance checks so developers can deploy faster, safely."

---

### **7. Python Comfort Level**

**Answer:**
"I am very comfortable with Python. I use it extensively for writing automation scripts, CI/CD glue code, and developing custom tools. For example, in my previous role, I wrote Python scripts to parse log files for auditing and automate Kubernetes deployment validations. I also frequently use the `boto3` SDK to interact with AWS services when Terraform or CloudFormation isn't the right fit for ad-hoc tasks."

---

### **8. Python Script: Log Rotation and Archiving**

**Question:** *Write a Python script that automatically rotates and archives log files in a specified directory.*

**Answer:**
"Here is a script that automates log rotation. It identifies log files, compresses them into a `.tar.gz` archive to save space, and includes a cleanup mechanism to remove archives older than a specified retention period."

```python
import os
import gzip
import shutil
import tarfile
import datetime
from pathlib import Path

def rotate_logs(log_dir, archive_dir, retention_days=30):
    """
    Rotates log files by compressing them into archives and deleting old archives.
    
    :param log_dir: Directory containing active log files.
    :param archive_dir: Directory to store compressed archives.
    :param retention_days: Days to keep archives before deletion.
    """
    log_path = Path(log_dir)
    archive_path = Path(archive_dir)
    
    # Create archive directory if it doesn't exist
    archive_path.mkdir(parents=True, exist_ok=True)
    
    timestamp = datetime.datetime.now().strftime("%Y%m%d_%H%M%S")
    
    print(f"Starting log rotation for directory: {log_dir}")
    
    # 1. Identify and compress log files
    # Assuming logs end with .log - adjust pattern as needed
    for log_file in log_path.glob("*.log"):
        try:
            # Define archive name
            archive_name = f"{log_file.stem}_{timestamp}.tar.gz"
            full_archive_path = archive_path / archive_name
            
            print(f"Archiving {log_file.name} -> {archive_name}")
            
            # Compress file into a tar.gz archive
            with tarfile.open(full_archive_path, "w:gz") as tar:
                tar.add(log_file, arcname=log_file.name)
            
            # 2. Clear or Remove original log file
            # Option A: Remove the file completely
            # os.remove(log_file) 
            
            # Option B: Truncate the file (keep file empty, useful for running processes)
            with open(log_file, 'w') as f:
                f.truncate(0)
                
        except Exception as e:
            print(f"Error processing {log_file.name}: {e}")

    # 3. Cleanup old archives (Retention Policy)
    print(f"Cleaning up archives older than {retention_days} days...")
    cutoff_date = datetime.datetime.now() - datetime.timedelta(days=retention_days)
    
    for archive in archive_path.glob("*.tar.gz"):
        if datetime.datetime.fromtimestamp(archive.stat().st_mtime) < cutoff_date:
            print(f"Deleting old archive: {archive.name}")
            os.remove(archive)

    print("Log rotation completed successfully.")

# Example Usage
if __name__ == "__main__":
    # Define your paths here
    LOG_DIRECTORY = "/var/log/myapp"
    ARCHIVE_DIRECTORY = "/var/log/myapp/archive"
    
    rotate_logs(LOG_DIRECTORY, ARCHIVE_DIRECTORY, retention_days=30)
```


