
---

→ what are your job responsibilities? How are you managing things? How are you doing collaborative work? What kind of projects are you supporting? How do you handle day-to-day activities?

→ For CI/CD are you using Jenkins? Let’s say I have Kubernetes environment might be I am going with DEV, UAT, and Production. How are you handling the pipelines? Are you having multiple Jenkins jobs triggered per environment, or is it a single job triggering from development to production? How is it happening?

→ In your Kubernetes environment, how many services and pods are running? How many applications are actually deployed?

→ How are you managing deployments? Do you have a single pipeline or multiple pipelines per branch?

→ Let’s say I am moving services to production—6 out of 10 services—from dev to production. How are you managing this workflow?

→ How do you come to know about the requirements? How do you move the code and understand how your Jenkins pipelines run? Once a Jenkins job is finished—let’s say it builds and releases to Kubernetes—how do you know things are working fine in production after deployment?

→ For DEV, UAT, and Production, are you using separate Git branches? Why do you need separate branches?

→ Let’s say you are moving code from development to pre-prod. Once pre-prod is fine, you move the code to the main/master branch for release. If something goes wrong in production and a hotfix/bugfix is needed—and rollback is not possible due to database or backend changes—what strategy do you follow to fix bugs in production?

→ Let’s say you created a hotfix branch from master. After fixing the issue, do you merge it back to master and also into the development branch?

→ How do you manage release versioning?

→ Are you creating a single Docker image for all environments, or are you creating images separately for each environment?

→ Can we use one image for the entire environment?

→ When pushing images to Artifactory/Nexus, how are you managing the lifecycle of those images?

→ Let’s say developers are creating multiple images. By the end of the month, there are many images in Nexus. How do you manage the image lifecycle? How do you decide which images need to be purged and which need to be kept? Does the same strategy apply for pre-prod and prod?

→ How do you create a Dockerfile for Node.js? Which version do you use, what base image, and what is the final image size? How do you manage node_modules? Do you install node modules every time, or do you copy them from somewhere? How do you handle these things?

→ If the image size becomes very large, how do you handle that?

→ What are the things you do using Terraform?

→ Can you give a recent example where you worked with Terraform, and what tasks you performed?

→ Have you used Terraform workspaces?

→ How do you differentiate environments within Terraform?

→ How do you manage multiple environments using Terraform?

→ Are you responsible for writing Terraform modules? For example, if you want to write a module for EC2, what best practices do you follow? How do you write reusable modules for different Terraform scripts, and what kind of standardization have you implemented?

→ You also work with Python, right? How do you handle exceptions in Python? Can you give a simple example of an exception—where and why we use it, and where we should not use exceptions?

→ How do you read a file in Python line by line?

→ Have you worked with Lambdas?

→ Do you know Lambda handlers? How do they work?

---

