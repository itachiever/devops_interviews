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


# Questions: Mixed all small questions and follow-ups together


1. Introduce yourself. Tell us about your roles, responsibilities, achievements, and anything interesting about your work.

2. Apart from the security aspect, are you also involved in infrastructure provisioning? Do you create reusable Terraform modules for your team?

3. Do you design the CI/CD pipeline for Terraform? Which CI/CD tools have you worked with? Have you used GitHub Actions?

4. Explain how you designed the CI/CD pipeline for Terraform.

5. When creating Terraform modules for production infrastructure, how do you secure those resources from a security standpoint?

6. How do you prevent production resources from being accidentally destroyed by an engineer? Explain how `prevent_destroy` works, whether a resource can still be deleted even after enabling it, and how you would safely decommission such a resource when required.

7. Consider an AKS cluster provisioned using Terraform where the user node pool was originally created with two nodes but later autoscaled to ten. During a Kubernetes version upgrade or another Terraform change, Terraform tries to scale it back to two nodes. How would you avoid this issue?

8. Can `lifecycle.ignore_changes` be used inside a Terraform resource block? If yes, where would you configure it?

9. Explain the complete request flow when a client accesses a publicly exposed API running inside an AKS Kubernetes cluster, starting from the local machine until the request reaches the application Pod.

10. What is the role of an Ingress, and what is the role of a Kubernetes Service?

11. If an API endpoint returns an HTTP 500 Internal Server Error, how would you troubleshoot and identify the root cause?


# Answers:



# 1. Introduce yourself. Tell us about your roles, responsibilities, achievements, and anything interesting about your work.

### Answer:

Hi, I'm **Yuvaraju**, a **DevSecOps Engineer** with **4+ years of experience** in DevOps, DevSecOps, cloud infrastructure, and CI/CD automation.

Currently, I'm working at **Talakunchi Networks**, deployed to a **fintech client (InSolutions Global)** that provides payment solutions to major banks.

My responsibilities include:

* Designing and maintaining **Jenkins CI/CD pipelines**
* Building reusable **Terraform modules** and automating infrastructure provisioning
* Containerizing applications using **Docker** and deploying them on **Kubernetes (AKS)**
* Integrating security tools such as **Fortify SAST, DAST, Sonatype IQ, Trivy and GitLeaks** into CI/CD
* Managing artifact repositories using **Sonatype Nexus**
* Implementing security gates to achieve **PCI-DSS compliance**
* Monitoring applications using **Prometheus and Grafana**
* Working closely with development teams for vulnerability remediation and secure SDLC implementation.

Recently, I received the **Employee of the Quarter Award** for successfully driving compliance initiatives for our fintech client.



# 2. Apart from the security aspect, are you also involved in infrastructure provisioning? Do you create reusable Terraform modules for your team?

### Answer:

Yes.

Although we have a dedicated cloud infrastructure team, I actively collaborate with them.

My responsibilities include:

* Developing reusable **Terraform modules**
* Standardizing infrastructure provisioning
* Integrating Terraform into CI/CD pipelines
* Reviewing infrastructure code
* Supporting infrastructure automation whenever new environments are required

This helps different teams provision infrastructure consistently across environments.



# 3. Do you design the CI/CD pipeline for Terraform? Which CI/CD tools have you worked with? Have you used GitHub Actions?

### Answer:

Yes.

I have integrated Terraform workflows into our Jenkins-based CI/CD pipelines.

Tools I have worked with include:

* Jenkins (primary)
* GitLab CI
* Azure DevOps
* Basic exposure to GitHub Actions workflows

Most of my production experience has been with Jenkins.



# 4. Explain how you designed the CI/CD pipeline for Terraform.

### Answer:

Our Terraform pipeline follows this flow:

1. Developers commit Terraform code into GitLab.
2. A Merge Request triggers the Jenkins pipeline.
3. Pipeline executes:

   * Terraform fmt
   * Terraform validate
   * Security scanning (Trivy/Snyk where applicable)
4. Terraform Plan is generated.
5. Plan is reviewed and approved.
6. Terraform Apply provisions or updates infrastructure.
7. Terraform remote state is maintained securely using a backend.

This process ensures infrastructure changes are validated, reviewed and deployed consistently.



# 5. When creating Terraform modules for production infrastructure, how do you secure those resources from a security standpoint?

### Answer:

We follow a secure-by-default approach.

Some of the controls include:

* Principle of Least Privilege using IAM/RBAC
* No hardcoded secrets; secrets are retrieved from Azure Key Vault or HashiCorp Vault
* Security scanning of Terraform code before deployment
* Encryption enabled for storage resources
* Logging and monitoring enabled by default
* Reusable modules follow organizational security standards
* Mandatory code reviews before production deployment

This ensures every infrastructure resource is created securely from the beginning.



# 6. How do you prevent production resources from being accidentally destroyed by an engineer? Explain how `prevent_destroy` works, whether a resource can still be deleted even after enabling it, and how you would safely decommission such a resource when required.

### Answer:

For critical production resources, we use:

* `lifecycle { prevent_destroy = true }`
* RBAC with least privilege
* Approval-based production deployments
* Protected production branches
* Cloud-native resource locks wherever applicable

`prevent_destroy` prevents Terraform from deleting the resource during normal operations.

However, it is **not an absolute protection**.

Deletion is still possible if:

* The lifecycle rule is removed intentionally.
* The resource is deleted manually outside Terraform (if permissions exist).
* State or configuration is intentionally modified.

When decommissioning a production resource:

1. Take backups.
2. Obtain required approvals.
3. Remove or disable `prevent_destroy`.
4. Review Terraform Plan.
5. Execute Terraform Apply through the production pipeline.
6. Verify successful cleanup.

This keeps the process controlled and auditable.



# 7. Consider an AKS cluster provisioned using Terraform where the user node pool was originally created with two nodes but later autoscaled to ten. During a Kubernetes version upgrade or another Terraform change, Terraform tries to scale it back to two nodes. How would you avoid this issue?

### Answer:

This happens because Terraform compares the current state with the configuration.

To avoid this:

* Enable Cluster Autoscaler for node scaling.
* Configure

```terraform
lifecycle {
  ignore_changes = [
    node_count
  ]
}
```

for the node pool.

This allows the Cluster Autoscaler to manage the node count while Terraform manages the remaining infrastructure configuration.

As a result, unrelated infrastructure changes like upgrades won't unintentionally scale the cluster back.



# 8. Can `lifecycle.ignore_changes` be used inside a Terraform resource block? If yes, where would you configure it?

### Answer:

Yes.

`ignore_changes` is configured inside the **lifecycle block** of the Terraform resource.

Example:

```terraform
resource "azurerm_kubernetes_cluster_node_pool" "userpool" {

...

lifecycle {
    ignore_changes = [
        node_count
    ]
}

}
```

Terraform will ignore changes to the specified attributes while continuing to manage the rest of the resource.



# 9. Explain the complete request flow when a client accesses a publicly exposed API running inside an AKS Kubernetes cluster, starting from the local machine until the request reaches the application Pod.

### Answer:

The request flow is:

1. Client sends request to the API endpoint.
2. DNS resolves the domain to the public IP.
3. Request reaches the Azure Load Balancer/Public IP.
4. Traffic is forwarded to the Ingress Controller (NGINX).
5. Ingress performs:

   * TLS termination
   * Host/path-based routing
   * Routing policies
6. Request reaches the Kubernetes Service.
7. Service uses kube-proxy networking to forward traffic.
8. Traffic is load balanced to one of the healthy Pods.
9. The application processes the request.
10. Response follows the same path back to the client.



# 10. What is the role of an Ingress, and what is the role of a Kubernetes Service?

### Answer:

**Ingress**

* Provides external HTTP/HTTPS access.
* Performs host-based and path-based routing.
* Handles TLS termination.
* Routes requests to the correct Kubernetes Service.

**Service**

* Provides a stable virtual IP for Pods.
* Load balances traffic across healthy Pods.
* Abstracts dynamic Pod IP addresses.
* Enables reliable communication inside the cluster.

In short:

* **Ingress decides where traffic should go.**
* **Service delivers traffic to the correct Pods.**



# 11. If an API endpoint returns an HTTP 500 Internal Server Error, how would you troubleshoot and identify the root cause?

### Answer:

I follow a systematic troubleshooting approach:

1. Verify whether the Pods are running and healthy.
2. Check application logs using `kubectl logs`.
3. Verify Kubernetes Events for any failures.
4. Confirm the Service endpoints are pointing to healthy Pods.
5. Check Ingress Controller logs and routing configuration.
6. Validate application configuration, ConfigMaps and Secrets.
7. Test connectivity from the Pod to backend services like databases or APIs.
8. Review recent deployments or configuration changes.
9. Check monitoring dashboards (Prometheus/Grafana) for resource usage, latency and errors.

Based on these observations, I can determine whether the issue is with:

* Application code
* Kubernetes networking
* Ingress configuration
* Backend dependency
* Infrastructure resource issue


