Architectural and Design Write-up (CI/CD + Monitoring)



\## Solution Overview (1–2 paragraphs)

This project implements a cloud-native microservices deployment for a containerised To-Do application on AWS. The application is split into two services: a Frontend (static site served via Nginx) and a Backend (Node.js Express API). All core infrastructure is provisioned using a single AWS CloudFormation template (Infrastructure as Code), including the VPC networking layer, security groups, ECS cluster, task definitions, services, and an Application Load Balancer (ALB). Amazon ECS with Fargate was selected to run containers without managing EC2 instances, improving operational simplicity and scalability. Amazon ECR is used to securely store container images and integrate directly with ECS for deployments.



For CI/CD, GitHub is used as the source repository to enable version control and collaboration, and to avoid AWS CodeCommit access limitations in a learning/free-tier environment. AWS CodePipeline is used to orchestrate the continuous delivery workflow, while AWS CodeBuild is used for automated builds (including Docker image build and push to ECR). For monitoring and reliability, Amazon CloudWatch is used for centralized logging and operational visibility. ECS task logs are streamed to CloudWatch Log Groups/Streams, enabling fast troubleshooting of task startup failures and runtime errors. CloudWatch was selected because it integrates natively with ECS/Fargate, provides both logs and metrics, and supports evidence-based reliability monitoring during deployments.



\## AWS Service Justification (Summary)

\- \*\*CloudFormation (IaC):\*\* Repeatable, consistent provisioning of all AWS resources using a single declarative template.

\- \*\*ECS (Fargate):\*\* Serverless container runtime—no EC2 management; scalable and production-aligned.

\- \*\*ECR:\*\* Secure container image registry with direct ECS integration.

\- \*\*ALB:\*\* Reliable public entry point and traffic distribution to services.

\- \*\*GitHub (Source):\*\* Industry-standard SCM; used instead of CodeCommit due to access/cost constraints and strong CI/CD integration support.

\- \*\*CodePipeline:\*\* Automates workflow from source → build → deploy, reducing manual deployment errors.

\- \*\*CodeBuild:\*\* Performs automated builds and Docker image publishing to ECR.

\- \*\*CloudWatch:\*\* Centralized logging/metrics for troubleshooting, visibility, and reliability validation.



\## Evidence / Screenshots to Attach

1\. ECS Cluster showing both services (Frontend + Backend) running.

2\. ECS Tasks page showing tasks in RUNNING state.

3\. CloudWatch Log Groups showing log groups for frontend and backend.

4\. Example CloudWatch Log Stream (frontend).

5\. Example CloudWatch Log Stream (backend).

6\. CI/CD pipeline page (CodePipeline stages) OR build history page (CodeBuild) if used.

7\. ECR repositories showing pushed image tags for frontend and backend.

