### Role: DevSecOps Enginee | Interview: 1st Round | Company: Capgemini
# Interview Questions

1. Give me an introduction about yourself.

2. What technologies are you working on right now, and what are your years of experience?

3. How good are you in Azure?

4. I have an RBAC role assigned, but I am not able to access the Key Vault; why would this happen?

5. How would you deploy resources in a scenario where the setup is sitting behind a private endpoint and requests should not go outside?
6. Would you recommend having a different repository for the CD part or doing CI and CD in the same repository?
7. Do you know how to create Docker images?
8. Can you write a normal pipeline in Azure DevOps for Continuous Deployment with three stages: building the artifact, testing it with SonarQube, and deploying it with a self-hosted agent?
9. What is the best practice for tagging Docker images when multiple developers are involved?
10. Can you give me a brief understanding of the architecture of Kubernetes?
11. What is the function of Ingress in a Kubernetes cluster?
12. How would you restrict access in Kubernetes for a user who has Contributor access in Azure RBAC but should not have privileges in the Kubernetes cluster?
13. Can a Docker container start automatically?
14. What is the difference between a Docker image and a Dockerfile?
15. Do you have experience in Terraform?
16. Where are you storing the Terraform state file in your setup?
17. Have you broken down your main.tf file into different modules?
18. How are you storing secrets in your Terraform setup?
19. Which resources are you deploying using your modules and main.tf file?
20. Do you have both AWS and Azure in your setup?
21. Why do you have a setup with both AWS and Azure?
22. Which resources are located in AWS and which are located in Azure?
23. Does your Terraform infrastructure as code deploy to AWS or Azure?
24. How do you handle remote state lock issues in Terraform when working with multiple teams across both AWS and Azure?

---
# Answers:


**1. Give me an introduction about yourself.**
*   **Answer:** 4+ Years Exp DevOps/DevSecOps.

**2. What technologies are you working on right now?**
*   **Answer:** Azure (AKS, KeyVault), Kubernetes, Docker, Terraform, Jenkins, and Security tools (Fortify, SonarQube).

**3. How good are you in Azure?**
*   **Answer:** Proficient. Experience with AKS (Private Clusters), KeyVault, Azure Monitor, RBAC, and Networking.

**4. I have an RBAC role assigned, but I am not able to access the Key Vault; why?**
*   **Answer:** Difference between **Management Plane** vs **Data Plane**.
*   Need explicit **Access Policy** or **Key Vault Secrets User** role for data access.

**5. How would you deploy resources behind a private endpoint?**
*   **Answer:** Use **Self-Hosted Agents** deployed inside the same VNet or peered VNet to access private IPs.

**6. Different repository for CD or same?**
*   **Answer:** **Separate Repos** recommended.
*   Ensures Separation of Concerns and prevents developers from accidentally modifying deployment logic.

**7. Do you know how to create Docker images?**
*   **Answer:** Yes. Write Dockerfiles, use multi-stage builds to optimize size, and manage registries.

**8. Write a normal pipeline in Azure DevOps (Build, Test, Deploy).**
*   **Answer:**
    *   **Stage 1:** Maven task (Build Artifact).
    *   **Stage 2:** SonarQubePrepare & Analyze task (Test).
    *   **Stage 3:** Deployment job on Self-Hosted Pool.

**9. Best practice for tagging Docker images?**
*   **Answer:** Use **Immutable Tags** like **Git Commit SHA** or **Build ID**. Avoid `latest` tag for production traceability.

**10. Brief understanding of the architecture of Kubernetes?**
*   **Answer:**
    *   **Control Plane:** API Server, Scheduler, etcd (Brain).
    *   **Worker Nodes:** Kubelet, Kube-proxy, Container Runtime (Muscle).

**11. What is the function of Ingress?**
*   **Answer:** Acts as an API Gateway. Routes external traffic to services based on **URL Path** or **Hostname**. Handles SSL termination.

**12. Restrict K8s access for user with Azure Contributor access?**
*   **Answer:** Azure RBAC != K8s RBAC.
*   Ensure user has **No RoleBinding** inside the K8s cluster to restrict `kubectl` access.

**13. Can a Docker container start automatically?**
*   **Answer:** Yes. Use Restart Policies: `always`, `unless-stopped`, or `on-failure`.

**14. Difference between Docker image and Dockerfile?**
*   **Answer:** **Dockerfile** = Instructions/Source Code. **Image** = Executable Artifact built from it.

**15. Do you have experience in Terraform?**
*   **Answer:** Yes, 3+ years. Provisioning AWS and Azure resources using modular code.

**16. Where are you storing the Terraform state file?**
*   **Answer:** Remote Backends. **Azure Blob Storage** (for Azure) or **S3 + DynamoDB** (for AWS).

**17. Have you broken down main.tf into modules?**
*   **Answer:** Yes. Separated into **Network, Compute, Security,** and **Database** modules for reusability.

**18. How are you storing secrets in Terraform?**
*   **Answer:** Fetch dynamically from **Azure Key Vault** or **AWS Secrets Manager** using `data` sources. Never hardcode.

**19. Which resources are you deploying using modules?**
*   **Answer:** VPC/VNet, Subnets, AKS/EKS Clusters, IAM Roles, Storage Accounts.

**20. Do you have both AWS and Azure?**
*   **Answer:** Yes. **Hybrid Cloud** setup. Azure for core apps, AWS for legacy/storage.

**21. Why setup with both AWS and Azure?**
*   **Answer:** Legacy migration requirements and to prevent **Vendor Lock-in**.

**22. Which resources located in AWS and Azure?**
*   **Answer:** **Azure:** Core App (AKS), KeyVault. **AWS:** S3 (Archive), Legacy EC2.

**23. Does Terraform deploy to AWS or Azure?**
*   **Answer:** Both. Use separate **Directories/Configs** with specific Providers for each cloud.

**24. How do you handle remote state lock issues?**
*   **Answer:** Backend handles locking automatically.
*   **AWS:** DynamoDB. **Azure:** Blob Lease.
*   Manual release: `terraform force-unlock` if needed.


