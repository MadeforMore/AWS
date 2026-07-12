AWS Case Study: Ticket Platform Architecture

<img width="800" height="436" alt="image" src="https://github.com/user-attachments/assets/ea69ce43-a628-4a0f-9b9b-565f2983ddd7" />

#### 🌐 1. Edge Routing & Static Optimization
 * **AWS Route 53:** Serves as the highly resilient DNS, routing global user traffic efficiently.
 * **Amazon S3 & CloudFront:** Static assets (UI layouts, images) are stored in S3 and cached globally via CloudFront (CDN), slashing latency and offloading the core servers.
#### 🔒 2. Zero-Trust Network Isolation
 * **Amazon VPC:** Isolates the backend infrastructure within a secure private network.
 * **Public vs. Private Subnets:** The Load Balancer (ALB) sits in a public subnet to receive web traffic, but the application servers (EC2) stay hidden in private subnets, shielded from the internet.
#### ⚖️ 3. Dynamic Compute Elasticity
 * **Application Load Balancer (ALB):** Evenly distributes incoming traffic across the server fleet.
 * **EC2 Auto Scaling:** Dynamically spins up new EC2 instances during a sudden traffic spike and scales down afterward to optimize costs.
#### 💾 4. Polyglot Persistence
 * **Amazon RDS (Relational):** Handles structured data requiring strict transactional guarantees (e.g., user profiles, billing details) using a Primary/Replica model.
 * **Amazon DynamoDB (NoSQL):** Offloads heavy read spikes with single-digit millisecond lookups, perfect for real-time seat availability checks.
#### 🏗️ 5. Decoupling & Event-Driven Execution
 * **Amazon SQS (Message Queue):** Buffers incoming purchase requests in a FIFO queue. This decouples the frontend from the backend, manages execution flow, and eliminates double-selling.
 * **AWS Lambda & SES:** A serverless Lambda function processes the queued purchases in the background and triggers Amazon SES to instantly fire off confirmation emails.
#### 🛡️ 6. The Operational Pillar
 * **IAM & Security Groups:** Enforces least-privilege access control and network firewalls.
 * **Amazon CloudWatch:** Provides deep real-time monitoring and alert visibility.
 * **Infrastructure as Code (IaC):** The entire stack is written in code (Terraform/CloudFormation) for rapid, reproducible deployments.
