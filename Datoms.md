First Technical Round — 23 Interview Questions

Tell me about a recent CI/CD pipeline you built end-to-end. Walk me through stages, tools, failure handling, and how you enforced security gates.

Explain how you would design a multi-environment (DEV → UAT → PROD) Jenkins pipeline that supports approvals and safe rollouts. What branching strategy and artifacts promotion approach would you use?

You wrote that you integrated SAST/DAST/SCA into pipelines. Pick one of those (e.g., Snyk or Fortify) and explain exactly how you integrated it into CI, what scan results you blocked on, and how you handled false positives.

Describe how you provision infrastructure with Terraform. How do you organize modules, manage state, and handle environment isolation and secrets?

A Kubernetes deployment is crashing in PROD with CrashLoopBackOff. Describe your debugging steps (kubectl commands, log checks, common root causes, remediation).

How do you design Kubernetes clusters for high availability and security in a cloud environment (nodes, control plane, network policies, private clusters vs public)?

Explain how you would securely store and inject secrets into a CI/CD pipeline and into Kubernetes workloads. Compare at least two options (e.g., Vault, Azure Key Vault, Kubernetes Secrets) and trade-offs.

Describe a time you diagnosed and fixed a production outage. What monitoring/alerts led you to the problem, how did you triage, what was the root cause, and what postmortem actions did you take?

For an IoT platform with high-throughput ingestion, which data stores and messaging systems would you consider (Kafka, Redis, ClickHouse), and how would you scale and make them resilient?

Walk me through how you would set up centralized logging and monitoring for microservices using Prometheus, Grafana, and the ELK stack. What metrics and alerts are critical?

How do you ensure container image security and provenance (build process, image scanning, immutable tags, registry policies)? Explain a typical pipeline flow you’d implement.

Explain how you would implement network segmentation for a secure CI/CD environment with a DMZ exposing limited Jenkins endpoints. What components, rules, and access controls are needed?

Give an example of an automation you wrote in Python or Bash that saved time or reduced incidents. Show the logic, error handling, and idempotency considerations.

How do you manage cloud costs (FinOps) in AWS/Azure/GCP for a microservices platform? Provide specific levers you’d use to reduce waste.

You mentioned VPN connectivity between on-prem and cloud. How do you set up a secure VPN (or ExpressRoute/VPN Gateway), and what network considerations (routing, BGP, CIDR overlap) matter?

Explain how RBAC works in Kubernetes and how you would design RBAC for developers, SREs, and CI systems to follow the principle of least privilege.

A developer reports intermittent high latency for a specific service. What steps and tools do you use to pinpoint whether it’s application, network, or infra related?

Describe how you would implement policy-as-code and shift-left security in a pipeline. Which tools would you pick and how would you enforce policies pre-merge?

How do you perform blue/green or canary deployments in Kubernetes? Explain traffic shifting, rollout strategies, and how you handle database schema changes safely.

Explain a complex Terraform gotcha or a state-management issue you encountered and how you solved it. What would you do to prevent similar problems?

What’s your approach to secrets scanning (e.g., GitLeaks) and preventing secrets from entering git history? How do you remediate when secrets are leaked?

Tell me about a time you had to collaborate with application developers and product owners to deliver a production feature. How did you balance speed, reliability, and security?

If hired, what immediate improvements (first 30–60–90 days) would you propose for a DevOps/DevSecOps platform supporting IoT workloads?
