## FIRST TECHNICAL ROUND - QUESTIONS (30)

1. Can you walk me through your current role and explain what exactly you are responsible for on a day-to-day basis?

2. Tell me about a production-grade AWS or Azure architecture you have worked on. How does the traffic flow from the user to the application?

3. In your experience, where do you usually place application workloads in AWS — public or private subnets — and why?

4. Suppose your application is deployed in a private subnet and suddenly it is not able to reach the internet. How would you start troubleshooting this?

5. Can you explain how Security Groups and NACLs work together in a real production environment?

6. We see Kubernetes on your resume. How do you expose applications running inside a Kubernetes cluster to external users?

7. Let’s say traffic is reaching the load balancer, but it is not reaching the pod. What are the possible reasons and what would you check first?

8. How do you manage secrets in your CI/CD pipelines and Kubernetes deployments?

9. In your Jenkins pipelines, how do you control deployments across multiple environments like DEV, UAT, and PROD?

10. Can you explain how you have integrated security scanning into your CI/CD pipeline and at what stages?

11. Suppose a critical vulnerability is detected in production through a scan. What steps would you take immediately?

12. How do you ensure that your AWS IAM policies follow the principle of least privilege?

13. Have you worked with hybrid architectures? Can you explain how your on-prem infrastructure securely connects to cloud environments?

14. In your project, why did you introduce a DMZ layer for CI/CD, and what problem were you trying to solve?

15. What kind of monitoring and alerts do you usually configure for production systems?

16. Let’s say your application suddenly becomes slow in production. How do you identify whether it is an infrastructure issue or an application issue?

17. Can you explain the difference between ALB and NLB, and when you would choose one over the other?

18. How do you handle rollbacks if a deployment fails in production?

19. Have you ever handled a production incident? Walk me through what happened and how you resolved it.

20. How do you make sure that container images used in production are secure?

21. What is your approach to Kubernetes resource management, like CPU and memory requests and limits?

22. Suppose a pod is continuously restarting in production. How would you debug that issue?

23. How do you manage infrastructure changes using Terraform without impacting production stability?

24. What steps do you take to secure network communication between microservices?

25. How do you expose only required services to the internet while keeping internal services secure?

26. Have you worked with AWS WAF or similar tools? How do you use them in real projects?

27. How do you ensure high availability for applications running on Kubernetes or AWS?

28. What kind of logs do you collect in production, and how do you use them during troubleshooting?

29. How do you collaborate with developers and QA teams when a deployment or security issue occurs?

30. If we deploy you into our production environment tomorrow, what areas would you first look at to understand system stability and security?

---
---

## SECOND TECHNICAL ROUND – QUESTIONS (20)

1. Suppose you are asked to automate the cleanup of unused Docker images and stopped containers on a production server. How would you approach this, and can you write a simple script for it?

2. We want to create a Jenkins pipeline that builds a Docker image, scans it for vulnerabilities, pushes it to a registry, and deploys it to Kubernetes. Can you explain the pipeline flow and write a basic Jenkinsfile structure?

3. Imagine that a Terraform apply accidentally modified a critical production resource. How would you detect, rollback, and prevent this from happening again?

4. Can you write a simple Terraform example to provision an EC2 instance with a security group allowing only HTTP and HTTPS traffic?

5. How would you automate the deployment of the same application to DEV, UAT, and PROD using a single CI/CD pipeline while ensuring proper approvals?

6. Suppose Kubernetes pods are consuming more memory over time and eventually getting OOMKilled. How would you investigate and fix this?

7. Can you write a basic Kubernetes Deployment YAML with resource requests, limits, and health probes configured?

8. You are asked to restrict communication between microservices so that only specific services can talk to each other. How would you implement this in Kubernetes?

9. How would you automate the rotation of secrets used by applications without causing downtime?

10. Suppose Jenkins is deployed on-prem and Kubernetes is running in the cloud. How would you securely automate deployments between them?

11. Can you write a simple Bash or Python script to monitor disk usage and send an alert when it crosses a threshold?

12. How do you design CI/CD pipelines in such a way that security scanning does not slow down developer productivity?

13. Suppose your Kubernetes cluster certificate is about to expire. How would you detect this and handle renewal safely?

14. Can you explain how you would implement blue-green or canary deployments in Kubernetes using CI/CD pipelines?

15. Write a simple GitLab CI or Jenkins pipeline stage that runs a SAST scan and fails the build if high-severity issues are found.

16. How would you troubleshoot a situation where Terraform state is corrupted or out of sync with actual infrastructure?

17. Suppose an application requires access to AWS S3 from inside a Kubernetes pod. How would you configure this securely?

18. How would you automate infrastructure provisioning for a new environment from scratch using Terraform and Ansible?

19. Can you write or explain a script that copies logs from multiple servers, compresses them, and stores them in a central location?

20. If a deployment works fine in DEV but consistently fails in PROD, how would you approach debugging this difference?

---
