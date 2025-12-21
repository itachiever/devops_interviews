# Questions

Persistent Systems – DevOps – 1st Round Interview Questions

Can you briefly introduce yourself? What projects and technologies have you worked on?

As part of your daily tasks, what do you do?

Which CI/CD pipelines and tools have you used so far?

Are you also responsible for deploying applications?

Where do you store Docker images?

Who is responsible for developing deployment YAML files?

What is a multi-stage pipeline?

Scenario:
You have Dev and UAT stages.
To promote code from Dev to UAT:

How do you handle approvals in the pipeline?

Where do you store the approval information?

Do you know the concept of variable groups?

How do you define a variable group?

In a CI pipeline, there are multiple jobs.
If Job 1 is failing but Job 3 still needs to run, how can this be achieved?

What are triggers in a CI/CD pipeline?

Can you trigger a CI/CD pipeline based on a pull request?

If you have a feature branch and a master branch:

How do you run the CI pipeline on the master branch when there is a commit?

What is the use of service connections?

If you write a pipeline in Jenkins and want to copy a file into an Azure Storage Account:

How do you handle authentication?

Have you worked on Azure Databricks and Apache Airflow?

Which cloud platforms have you worked on?

Were you responsible for creating infrastructure?

What is the use of Terraform modules?

Where do you store Terraform state files?

Do you have experience with CI/CD, Databricks, and Airflow?

# Answers

1. Can you briefly introduce yourself? What projects and technologies have you worked on?

Model Answer:
"Certainly. My name is [Your Name], and I am a DevOps Engineer with [Number] years of experience in automating and streamlining the software development lifecycle. In my current role at [Current Company], I am part of a team responsible for managing our cloud infrastructure on Azure and implementing robust CI/CD pipelines.

Recently, I worked on a project to migrate our monolithic application to a microservices architecture running on Azure Kubernetes Service (AKS). My primary responsibilities included:

Technologies Used: Azure DevOps for CI/CD, Terraform for Infrastructure as Code, Docker for containerization, Kubernetes (AKS) for orchestration, and Ansible for configuration management.
Key Achievement: I designed and implemented a multi-stage CI/CD pipeline that automated the entire process from code commit to production deployment. This reduced our deployment time by over 80% and significantly improved the stability of our releases. I'm passionate about building scalable and efficient systems, and I'm particularly interested in how DevOps practices can be applied to data engineering and machine learning workflows."
2. As part of your daily tasks, what do you do?

Model Answer:
"My daily tasks are quite varied, which is something I enjoy about DevOps. They generally fall into a few key areas:

CI/CD Pipeline Maintenance: I spend a good portion of my day monitoring, troubleshooting, and improving our CI/CD pipelines in Azure DevOps. This could involve fixing a failed build, adding a new testing stage, or optimizing a deployment script.
Infrastructure Management: I use Terraform to manage and provision our cloud infrastructure. This includes responding to requests for new environments, updating existing resources, and ensuring our infrastructure is secure and cost-effective.
Collaboration and Support: I work closely with development teams to help them adopt our DevOps tools and practices. This involves code reviews for pipeline definitions, helping them containerize their applications, and troubleshooting deployment issues.
Monitoring and Alerting: I am responsible for setting up and maintaining monitoring and alerting for our applications and infrastructure using tools like Azure Monitor and Prometheus. This helps us proactively identify and resolve issues."
CI/CD & DevOps Tooling Questions
3. Which CI/CD pipelines and tools have you used so far?

Model Answer:
"I have extensive experience with several CI/CD platforms. My primary tool has been Azure DevOps, where I've worked extensively with YAML-based pipelines to define complex build and release workflows. Before that, I used Jenkins for several years, creating both freestyle and pipeline-as-code jobs using Groovy scripts. I've also had some exposure to GitLab CI/CD, which I find very intuitive for its tight integration with Git repositories. In addition to the pipeline orchestrators, I've integrated various tools into these pipelines, such as SonarQube for static code analysis, OWASP ZAP for security scanning, and Terraform for infrastructure deployment."

4. Are you also responsible for deploying applications?

Model Answer:
"Yes, absolutely. A core part of my role is automating and managing the deployment of applications to various environments, including development, testing, UAT, and production. I believe in a 'You Build It, You Run It' culture, so while I create the automated deployment pipelines, the development teams are ultimately responsible for their applications. My role is to provide them with the tools, processes, and infrastructure to deploy their code safely and reliably. This includes creating deployment scripts, managing environment configurations, and implementing strategies like blue-green or canary deployments to minimize downtime."

5. Where do you store Docker images?

Model Answer:
"We store our Docker images in a private container registry. In my current role, we use Azure Container Registry (ACR) because it integrates seamlessly with our other Azure services, like Azure Kubernetes Service (AKS) and Azure DevOps. Using a private registry is crucial for security, version control, and access management of our container images. Previously, I have also worked with Docker Hub for private repositories and Amazon ECR when working on AWS."

6. Who is responsible for developing deployment YAML files?

Model Answer:
"It's a collaborative effort between the DevOps and development teams, but the responsibilities are typically divided. The development team is usually responsible for the application-level YAML files, such as Deployment, Service, and ConfigMap manifests, because they know the application's port requirements, environment variables, and resource needs best. The DevOps team is typically responsible for the more infrastructure-related YAML files, such as Ingress controllers, NetworkPolicies, and the CI/CD pipeline YAML files themselves that use these manifests for deployment. This collaborative approach ensures that the deployments are both correct for the application and aligned with our infrastructure standards."

7. What is a multi-stage pipeline?

Model Answer:
"A multi-stage pipeline is a CI/CD pipeline that is broken down into a sequence of distinct, logical stages. Each stage represents a phase in the software delivery process, such as Build, Test, Staging, and Production.

The key benefits are:

Separation of Concerns: It allows you to group related jobs together. For example, a Build stage might compile code and create a Docker image, while a Test stage runs unit and integration tests.
Environment-Specific Deployments: You can have separate stages for deploying to different environments, like Dev and UAT.
Approvals and Gates: You can place manual approval gates between stages. For example, you can require a manual approval before a build artifact from the Test stage is deployed to the Production stage.
Visibility: It provides a clear, visual representation of your entire release process, making it easier to understand and track progress."
Scenario: Dev to UAT Promotion
8. How do you handle approvals in the pipeline?

Model Answer:
"In Azure DevOps, I handle approvals using a feature called 'environments' and 'approval checks'. Here's how it works:

I would define a UAT environment in Azure DevOps.
In the pipeline YAML, the UAT deployment stage would be configured to deploy to this UAT environment.
On the UAT environment's configuration page, I would add an 'approval' check. I can specify one or more users or groups who are required to approve the deployment.
When the pipeline reaches the UAT stage, it will automatically pause and send an email notification to the designated approvers.
The approvers can then review the changes in the Azure DevOps UI and either approve or reject the deployment. The pipeline will only proceed to the UAT deployment once it has been approved."
9. Where do you store the approval information?

Model Answer:
"The approval information, including who approved it, when they approved it, and any comments they made, is stored and audited directly within Azure DevOps. It's part of the pipeline run history. You can view the approval details for a specific stage in the pipeline run's summary page. This provides a clear audit trail for compliance and governance purposes. This information can also be accessed via the Azure DevOps API if needed for external reporting or integration."

Advanced CI/CD Concepts
10. Do you know the concept of variable groups?

Model Answer:
"Yes, I use variable groups frequently. A variable group in Azure DevOps is a way to store and manage a set of variables that can be used across multiple pipelines. It's a powerful feature for centralizing configuration and secrets."

11. How do you define a variable group?

Model Answer:
"You define a variable group in the Azure DevOps UI:

Go to your project's Pipelines section.
Click on Library.
Click on + Variable group.
Give the group a name and add the variables and their values. You can mark variables as secret to encrypt them.
For even better security, you can link the variable group to an Azure Key Vault, which allows you to access secrets directly from Key Vault without storing them in Azure DevOps.
Once the group is created, you can link it to a pipeline in the pipeline's YAML file using the variables section, like this:
yaml

variables:
- group: 'My-Variable-Group-Name'
```"

**12. In a CI pipeline, there are multiple jobs. If Job 1 is failing but Job 3 still needs to run, how can this be achieved?**

**Model Answer:**
"You can achieve this by using a `condition` on Job 3. By default, a job will only run if all preceding jobs it depends on have succeeded. To override this, you can set the condition to `succeededOrFailed()`.

Let's say Job 3 depends on Job 1 and Job 2. You would configure it like this in your YAML:
```yaml
jobs:
- job: Job1
  steps:
  - script: echo "This job might fail"
- job: Job2
  dependsOn: Job1
  steps:
  - script: echo "This job runs after Job1"
- job: Job3
  dependsOn: 
  - Job1
  - Job2
  condition: succeededOrFailed() # This is the key
  steps:
  - script: echo "This job runs even if Job1 or Job2 fails"
This ensures that Job 3 will always execute after Job 1 and Job 2 have completed, regardless of their outcome."

13. What are triggers in a CI/CD pipeline?

Model Answer:
"Triggers are what cause a pipeline to automatically run. They are events that initiate the pipeline execution. The most common types of triggers are:

Continuous Integration (CI) Triggers: These trigger a pipeline when a new commit is pushed to a specific branch or set of branches. This is the foundation of CI.
Pull Request (PR) Triggers: These trigger a pipeline when a pull request is created or updated. This is used to validate the proposed changes before they are merged into the target branch.
Scheduled Triggers: These trigger a pipeline on a defined schedule, using a CRON expression. This is useful for running nightly builds, security scans, or other maintenance tasks."
14. Can you trigger a CI/CD pipeline based on a pull request?

Model Answer:
"Yes, absolutely. Triggering a pipeline on a pull request is a very common and important practice. It's often called 'pull request validation' or 'merge check'. The purpose is to automatically build and test the changes from the feature branch against the target branch (e.g., master or main). This helps to catch bugs and integration issues early, before the code is actually merged, which maintains the quality and stability of the main branch."

15. If you have a feature branch and a master branch: How do you run the CI pipeline on the master branch when there is a commit?

Model Answer:
"You configure this in the pipeline's YAML file using a trigger block. You would specify the branches that should trigger the pipeline. To run the pipeline only on commits to the master branch, you would configure it like this:

yaml

trigger:
- master
If you wanted it to run on commits to master and any other branches, you could use:

yaml

trigger:
- master
- features/*
This configuration ensures that the pipeline will automatically start every time a new commit is pushed to the specified branches."

16. What is the use of service connections?

Model Answer:
"Service connections are a crucial feature in CI/CD platforms like Azure DevOps. They are essentially a secure way to store the credentials and connection information needed to connect to external services or tools. Instead of hard-coding secrets like API keys, passwords, or service principal credentials directly in your pipeline YAML, you create a service connection.

The main uses are:

Security: It keeps sensitive information out of your source code and pipeline definition.
Centralization: It provides a single place to manage and update credentials.
Ease of Use: It simplifies the pipeline configuration, as you just reference the name of the service connection in your tasks, and the platform handles the authentication behind the scenes.
Common examples include service connections for Azure subscriptions, AWS accounts, GitHub repositories, Kubernetes clusters, and external APIs."
17. If you write a pipeline in Jenkins and want to copy a file into an Azure Storage Account: How do you handle authentication?

Model Answer:
"There are a few ways to handle authentication, but the most secure and recommended approach is to use a Service Principal.

Create a Service Principal in Azure Active Directory: This service principal will have an identity that Jenkins can use to authenticate with Azure.
Assign RBAC Role: Assign the service principal the 'Storage Blob Data Contributor' role on the specific storage account or container you want to write to. This follows the principle of least privilege.
Store Credentials in Jenkins: Store the service principal's Client ID, Client Secret, and Tenant ID as secret text credentials in Jenkins.
Use Azure CLI in the Pipeline: In your Jenkins pipeline script, you would use the az login command with the service principal credentials to authenticate to Azure. Then, you would use the az storage blob upload command to copy the file.
Here's a snippet of what the Jenkinsfile might look like:

groovy

withCredentials([string(credentialsId: 'spn-client-id', variable: 'ARM_CLIENT_ID'),
                 string(credentialsId: 'spn-client-secret', variable: 'ARM_CLIENT_SECRET'),
                 string(credentialsId: 'spn-tenant-id', variable: 'ARM_TENANT_ID')]) {
    sh """
        az login --service-principal -u $ARM_CLIENT_ID -p $ARM_CLIENT_SECRET --tenant $ARM_TENANT_ID
        az storage blob upload --file 'my-file.txt' --container-name 'my-container' --name 'my-file.txt' --account-name 'mystorageaccount'
    """
}
This method is much more secure than using storage account access keys, as you can grant granular permissions and easily rotate the credentials."

Infrastructure as Code & Cloud Questions
18. Have you worked on Azure Databricks and Apache Airflow?

Model Answer:
"Yes, I have experience with both. In a previous project, we built a data platform for a client where Azure Databricks was the core processing engine for our big data and machine learning workloads. We used it for ETL jobs, data streaming, and training ML models.

Apache Airflow was used as the workflow orchestration tool. We defined our data pipelines as Directed Acyclic Graphs (DAGs) in Airflow, which allowed us to schedule, monitor, and manage complex dependencies between our different data processing tasks, including running Databricks jobs. For example, an Airflow DAG might trigger a Databricks job to process raw data, and upon its successful completion, trigger another job to train a machine learning model."

19. Which cloud platforms have you worked on?

Model Answer:
"I have professional experience working primarily with Microsoft Azure and Amazon Web Services (AWS). I am most proficient in Azure, having worked with a wide range of its services, including Azure DevOps, AKS, ACR, Azure Functions, and Azure SQL. I also have hands-on experience with AWS, where I have worked with services like EC2, S3, RDS, and CloudFormation. I also have some basic knowledge of Google Cloud Platform (GCP) from personal projects."

20. Were you responsible for creating infrastructure?

Model Answer:
"Yes, creating and managing infrastructure is a significant part of my DevOps role. I am a strong advocate for Infrastructure as Code (IaC). I have used Terraform extensively to define and provision our cloud infrastructure in a repeatable and automated way. This includes everything from virtual networks and subnets to Kubernetes clusters, databases, and storage accounts. Using IaC allows us to version control our infrastructure just like our application code, making it easier to manage changes, collaborate, and ensure consistency across environments."

21. What is the use of Terraform modules?

Model Answer:
"Terraform modules are a fundamental concept for organizing and reusing Terraform code. A module is a container for multiple resources that are used together. The main uses of modules are:

Reusability: You can create a module for a common piece of infrastructure, like a web server or a database, and then reuse that module multiple times with different configurations. This avoids code duplication.
Organization: They help to keep your Terraform configuration clean and organized by breaking it down into smaller, manageable components.
Consistency and Standardization: By using a common module, you ensure that the same infrastructure is deployed consistently every time, which reduces configuration drift and errors.
Maintainability: It's easier to update and maintain a single module than to find and update the same resource configuration in multiple places."
22. Where do you store Terraform state files?

Model Answer:
"Terraform state files must be stored in a remote backend. Storing the state file locally is not a viable option for team collaboration. A remote backend allows the state to be stored centrally and securely, and it provides features like state locking and encryption.

My preferred remote backends are:

Azure Blob Storage: When working on Azure, I use an Azure Storage Account container to store the Terraform state file. I also enable versioning and encryption on the storage account.
Amazon S3: When working on AWS, I use an S3 bucket. It's crucial to enable versioning, server-side encryption, and to configure state locking, which can be achieved using a DynamoDB table.
Terraform Cloud: This is a managed solution from HashiCorp that provides a secure and feature-rich remote backend for storing state, managing variables, and controlling access."
23. Do you have experience with CI/CD, Databricks, and Airflow?

Model Answer:
"Yes, I have experience integrating all three. As I mentioned earlier, I've worked on projects where we used Azure DevOps for CI/CD to deploy our code to Azure Databricks and Apache Airflow.

Our CI/CD pipeline would look something like this:

CI Stage: When a developer committed code for a Databricks notebook or an Airflow DAG, the pipeline would trigger.
Build and Test: The pipeline would run linting and unit tests on the code.
Deploy to Databricks: The pipeline would use the Databricks CLI or REST API to deploy the updated notebooks or libraries to the Databricks workspace.
Deploy to Airflow: The pipeline would package the Airflow DAGs and deploy them to the Airflow DAGs folder, often using a CI/CD tool like a Docker image or a sync process.
This setup allowed us to automate the deployment of our data pipelines, ensuring that new code was tested and deployed to our data platform in a reliable and controlled manner."
