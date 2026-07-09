# Interview Questions: 1st Round

1. **Tell about yourself, your roles and responsibilities, your achievements, or anything interesting.**

2. **You are taking care of the security part as well, right?**

3. **Are you also taking care of infrastructure provisioning?**

4. **Do you create Terraform modules for the team so that others can execute them?**

5. **Do you also design the Terraform CI/CD pipeline?**

6. **Which CI/CD tool are you using?**

7. **Are you using GitHub Actions?**

8. **Can you explain how you designed your Terraform CI/CD pipeline?**

9. **How do you secure Terraform resources/modules that will be used in production?**

10. **How do you prevent production resources from being accidentally destroyed by an entry-level engineer?**

11. **If `prevent_destroy = true` is configured but the resource still gets destroyed, is that possible? If yes, where do you think it went wrong?**

12. **Suppose you have `prevent_destroy = true`, but now you receive a request to decommission that production resource (for example, an Azure DB or AWS RDS). How would you decommission it?**

13. **You have worked on EKS/AKS, right?**

14. **Suppose an AKS cluster has two node pools. One node pool was initially provisioned with two nodes using Terraform, but autoscaling increased it to ten nodes. Now you're upgrading Kubernetes or adding tags, and Terraform wants to scale it back to two. How would you avoid that?**

15. **Where would you configure the `ignore_changes` lifecycle setting? Is it possible to put it in the resource block?**

16. **Since you've worked on microservices, assume an API is running inside an AKS cluster and is publicly exposed. Walk me through how a request from your local machine reaches the Kubernetes pod.**

17. **Once the request reaches the Kubernetes cluster, what role does an Ingress play, and what role does a Service play?**

18. **Suppose you're calling an API endpoint and receiving an HTTP 500 error. How would you debug this scenario?**

19. **Do you have any questions for us?**

---

### Main technical topics covered

* Terraform modules
* Terraform CI/CD pipeline
* Jenkins, GitHub Actions, GitLab CI
* Terraform security best practices
* IAM and secrets management
* `prevent_destroy` lifecycle
* Resource decommissioning
* `ignore_changes` lifecycle
* AKS/EKS
* Kubernetes networking
* DNS resolution
* Load Balancer
* Ingress Controller
* Kubernetes Services
* kube-proxy
* Debugging Kubernetes applications (HTTP 500 errors)


