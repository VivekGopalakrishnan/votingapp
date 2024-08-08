Scenario 2 - Production Set-Up: Detailed Steps
1. Infrastructure Setup
1.1 Created a VPC

Purpose: To isolate and secure the network environment for the application.
Details: Set up a Virtual Private Cloud (VPC) with appropriate CIDR block (e.g., 172.31.0.0/16).
1.2 Created Subnets

Purpose: To segment the VPC into different availability zones.
Details: Created public and private subnets in multiple availability zones to ensure high availability.
1.3 Set Up an Application Load Balancer (ALB)

Purpose: To distribute incoming traffic across multiple instances of the application.
Details: Created an ALB with the DNS name voteapp-ALB-620084343.us-east-1.elb.amazonaws.com.
1.4 Configured Security Groups

Purpose: To control inbound and outbound traffic to the instances and ALB.
Details:
Created security groups for the ALB to allow traffic on ports 80 (HTTP) and 443 (HTTPS).
Configured security groups for application instances to allow traffic from the ALB.
2. Kubernetes Setup
2.1 Deployed Kubernetes Cluster on AWS

Purpose: To host the application and manage deployments.
Details: Used Amazon EKS (Elastic Kubernetes Service) to set up a Kubernetes cluster.
2.2 Deployed the Example Voting Application

Purpose: To run the example voting application in the cluster.
Details:
Vote Application: Deployed with NodePort service 31000.
Result Application: Deployed with NodePort service 31001.
Worker Application: Deployed with NodePort service 31002.
2.3 Configured NodePort Services

Purpose: To expose the application services for external access.
Details:
Created NodePort services to expose the vote, result, and worker applications on ports 31000, 31001, and 31002, respectively.
2.4 Installed and Configured Argo CD

Purpose: To manage continuous deployment and synchronization.
Details: Installed Argo CD on the Kubernetes cluster and configured it to sync the applications from the Git repository.
3. Application Deployment
3.1 Configured Deployment Manifests

Purpose: To define how the applications should be deployed in the Kubernetes cluster.
Details:
Deployment Files: Created Kubernetes manifests for the vote, result, and worker applications, including deployment, service, and ingress resources.
3.2 Applied Kubernetes Manifests

Purpose: To deploy the applications to the Kubernetes cluster.
Details: Applied the manifests using kubectl apply -f <file> for each application.
3.3 Created and Applied Ingress Resource

Purpose: To manage access to the applications through the ALB.
Details:
Ingress Configuration: Set up an Ingress resource with rules to route traffic from the ALB to the appropriate services in the Kubernetes cluster.
4. CI/CD and Observability
4.1 Configured CI/CD Pipelines

Purpose: To automate the build, test, and deployment processes.
Details:
CI Tool: Configured GitHub Actions to build and test the application.
CD Tool: Used Argo CD to automate deployment and synchronization with the Git repository.
4.2 Set Up Observability Tools

Purpose: To monitor and analyze the application's performance and logs.
Details:
Prometheus and Grafana: Installed and configured for metrics collection and visualization.
ELK Stack: Set up for logging and log analysis.
5. Networking and DNS Management
5.1 Configured Route 53 for DNS Management

Purpose: To manage DNS records for the application.
Details:
Created A or CNAME records pointing to the ALB's DNS name.
5.2 Applied Networking Protection Rules

Purpose: To secure the network and control access.
Details:
Configured security group rules to restrict access to necessary ports and IP ranges.
6. Reliability and Scalability
6.1 Configured Auto-Scaling

Purpose: To handle changes in application load.
Details:
Horizontal Pod Autoscaler: Set up to scale application pods based on CPU/memory usage.
Cluster Autoscaler: Enabled to adjust the number of nodes in the cluster based on demand.
6.2 Implemented Multi-AZ Deployments

Purpose: To ensure high availability.
Details: Distributed application instances across multiple availability zones.
7. Alerting and Incident Management
7.1 Set Up Alerting

Purpose: To receive notifications about application issues.
Details:
Prometheus Alertmanager: Configured to send alerts based on defined metrics.
PagerDuty/OpsGenie: Integrated for incident management and alert notifications.
Repository URL: Your GitHub Repository

Documentation: Included detailed instructions and configuration files in the repository for reproducibility.

Feel free to adjust or expand on these steps based on any additional specifics or requirements you may have.
