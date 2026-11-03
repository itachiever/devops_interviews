# Interview Questions: 1st Round

## 1. Introduction and experience

1\. Can you introduce yourself and explain your current roles and responsibilities?

2\. How many years of overall experience do you have, and how much experience do you have with Azure?

3\. Have you worked with Terraform, or is infrastructure provisioning handled by a separate team?

## 2. Terraform and Infrastructure as Code

4\. Which Terraform modules have you created or worked on? Explain your experience creating VPC, subnet and VM modules.

5\. If you provision a VPC/VNet, subnet and VM together in a single Terraform apply, how do you ensure that the subnet is created before the VM? How do you establish resource dependencies in Terraform?

## 3. CI/CD and DevSecOps

6\. Have you developed CI/CD pipelines for infrastructure deployment and application deployment? Which tools have you used?

7\. Walk me through your infrastructure development pipeline end to end. What type of application was involved, and at which stages did you implement security controls?

8\. What is a quality gate? How do you define quality gates, and what criteria do you use to allow or block a pipeline?

9\. Is your application deployed on AKS or EKS? Explain the application deployment architecture.

10\. After the code checkout and build stages, what security scanning stages do you execute in your CI/CD pipeline? Explain the different scans.

11\. How do you configure and execute Fortify SAST scanning in a CI/CD pipeline? Explain the CLI commands, plugins, YAML pipeline steps, prerequisites and result publishing process.

## 4. Azure Security and Governance

12\. Have you worked with Azure Policies and Initiatives? Can you explain any custom policy or initiative you have implemented at the management group or subscription level?

13\. Have you independently created and deployed any custom Azure Policy? If yes, explain the policy and its implementation.

14\. Have you worked on identifying and remediating non-compliant resources in Azure? Explain the remediation activities you performed.

15\. Have you executed any Azure remediation task? Explain a real-time scenario and the steps you followed.

16\. Have you worked with Azure Firewall or other firewall technologies? Who manages firewall configuration in your current project?

17\. Have you configured or worked with Microsoft Defender for Cloud? What security features or recommendations have you handled?

## 5. Git Security and Secrets Management

18\. As a security engineer, how would you proactively prevent developers from accidentally pushing secrets such as API keys, passwords or tokens into GitHub/GitLab repositories? What preventive scanning mechanisms would you implement?

19\. Have you worked with GitLeaks, TruffleHog or GitGuardian? Explain how you configure GitLeaks and integrate it into a CI/CD pipeline. At which stage would you execute the scan?

20\. Where would you securely store sensitive infrastructure information such as AWS Account IDs, Azure Tenant IDs, credentials and other configuration values used in GitHub/GitLab repositories?

21\. How would you integrate an external secret manager such as AWS Secrets Manager, Azure Key Vault or HashiCorp Vault with GitHub/GitLab pipelines?

## 6. Security Monitoring and Vulnerability Management

22\. Have you worked with Microsoft Sentinel and Qualys? Explain their purpose, how they are used and your level of hands-on experience.

## 7. Cloud Networking and Architecture

23\. Consider a VM deployed inside an Azure VNet or AWS VPC. Explain the ideal end-to-end inbound traffic flow, including DNS, routing, network security controls, firewalls and the destination VM.

24\. At which different network layers can you control or restrict traffic reaching a VM? Explain the role of NSGs, Security Groups, route tables, UDRs and firewalls.

## 8. Cloud Storage Security and Troubleshooting

25\. Suppose an Azure Storage Account is configured as private, but an unauthorized external user is still able to access its Blob data. What could be the possible reasons, and how would you investigate and troubleshoot the issue?

## Additional questions from the interview closing discussion

These were not technical assessment questions, but were also asked:

1. Do you have any questions for the interview panel about the role, project or client?
2. What is your current notice period and expected last working date?
3. Do you currently have any other offer in hand?

----
# Answers: 1st Round

