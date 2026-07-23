## Building Scalable Event-Driven Architectures on AWS 

![Uploading image.png…]()


💻 AWS CloudShell: Used for quick console-based CLI management, automated deployments, and testing scripts directly in the AWS environment without needing local setup.
📁 Amazon S3: Serves as the primary object storage for incoming files (CSV, media, logs) and triggers real-time events.
⚡ AWS Lambda: Acts as the lightweight serverless compute to process S3 triggers instantly.
🖥️ Amazon EC2: Handles heavy, long-running backend microservices and core application logic.
🗄️ Amazon RDS: Provides a managed relational database for structured, high-reliability data persistence.
📢 Amazon SNS: Handles real-time messaging and notifications across services or directly to end users.

