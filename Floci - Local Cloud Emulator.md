# Floci - Local Cloud Emulator

> **Run AWS, Azure, and Google Cloud services locally without creating a cloud account.**

Floci is a fast, lightweight, and open-source cloud emulator that allows developers to run cloud services directly on their local machine. It provides a development environment that behaves like real cloud services while eliminating cloud costs during development and testing. It supports **AWS**, **Microsoft Azure**, and **Google Cloud Platform (GCP)** through separate emulators.

---

# Table of Contents

* Introduction
* Why Floci?
* Key Features
* Supported Cloud Providers
* Use Cases
* Prerequisites
* Installation
* Getting Started
* Project Structure
* How It Works
* Example Workflow
* Best Practices
* Limitations
* Comparison with Real Cloud
* Advantages
* When You Should Use Floci
* When You Should NOT Use Floci
* Frequently Asked Questions
* Contributing
* License

---

# Introduction

Developing cloud applications usually requires:

* A cloud account
* IAM permissions
* Internet connectivity
* Cloud resources
* Monthly billing

This increases development cost and makes testing slower.

Floci solves this problem by creating a local cloud environment that behaves similarly to AWS, Azure, or GCP. Your application communicates with Floci instead of the real cloud.

Because the APIs closely match real cloud APIs, developers can build, test, and debug applications locally before deploying them to production.

---

# Why Floci?

Floci was created to provide a completely free and open-source alternative for local cloud development.

Its main goals are:

* Reduce cloud costs
* Speed up development
* Improve local testing
* Support CI/CD pipelines
* Remove dependency on cloud accounts
* Allow offline development
* Provide fast startup with low memory usage

Unlike many alternatives, Floci does not require authentication tokens or paid plans to access supported services.

---

# Key Features

* Completely Open Source
* MIT License
* Extremely Fast Startup
* Very Low Memory Usage
* Works with Docker
* AWS CLI Compatible
* AWS SDK Compatible
* Terraform Compatible
* OpenTofu Compatible
* CDK Compatible
* GitHub Actions Compatible
* GitLab CI Compatible
* Jenkins Compatible
* Testcontainers Support
* Local Development
* Local Integration Testing
* CI/CD Ready

---

# Supported Cloud Providers

Floci provides emulators for multiple cloud platforms.

## AWS

Supports dozens of AWS services including:

* Amazon S3
* EC2
* Lambda
* DynamoDB
* SQS
* SNS
* IAM
* API Gateway
* CloudFormation
* ECS
* EKS
* RDS
* Route53
* CloudWatch
* EventBridge
* Secrets Manager

…and many more.

---

## Microsoft Azure

Examples include:

* Blob Storage
* Queue Storage
* Table Storage
* Azure Functions
* Key Vault
* Event Hubs
* Service Bus

---

## Google Cloud Platform

Provides local emulation for several commonly used GCP services and continues to expand support.

---

# Use Cases

Floci is useful for:

* Learning cloud services
* Practicing AWS CLI
* Practicing Azure CLI
* Practicing GCP
* Building cloud applications
* Local backend development
* Microservices development
* Event-driven architectures
* API development
* Integration testing
* CI/CD pipelines
* Team development
* Student projects
* Cloud workshops
* Corporate training

---

# Prerequisites

Before using Floci, install:

* Docker
* Docker Compose
* Git
* AWS CLI (for AWS)
* Azure CLI (optional)
* Google Cloud CLI (optional)

---

# Installation

### Clone Repository

```bash
git clone <repository-url>
cd floci
```

### Start Floci

```bash
floci start
```

or

```bash
docker compose up -d
```

Export the environment variables:

```bash
eval $(floci env)
```

These variables configure your SDKs and CLI tools to communicate with the local emulator instead of the real cloud.

---

# Getting Started

Example using AWS CLI:

Create a bucket

```bash
aws s3 mb s3://my-bucket
```

Upload a file

```bash
aws s3 cp demo.txt s3://my-bucket
```

List buckets

```bash
aws s3 ls
```

Everything happens locally.

No AWS account.

No billing.

No internet required for the emulated services.

---

# Project Structure

```
project/
│
├── docker-compose.yml
├── src/
├── tests/
├── terraform/
├── configs/
├── README.md
└── .env
```

---

# How It Works

```
Application
      │
      ▼
 AWS SDK / CLI
      │
      ▼
 Local Endpoint
(http://localhost:4566)
      │
      ▼
     Floci
      │
      ▼
Local Emulated Cloud Services
```

Instead of sending requests to AWS, Azure, or GCP, your application sends requests to the local Floci endpoint, enabling faster development and testing.

---

# Example Workflow

1. Start Floci.
2. Configure environment variables.
3. Run your application.
4. Create cloud resources locally.
5. Test your application.
6. Fix issues.
7. Repeat.
8. Deploy to the real cloud when ready.

---

# Best Practices

* Use separate configurations for local and production.
* Keep production credentials out of local development.
* Use Infrastructure as Code (Terraform/OpenTofu/CloudFormation) against Floci before deploying.
* Run automated integration tests locally.
* Store persistent emulator data in Docker volumes if needed.
* Validate critical workflows on the real cloud before release.

---

# Limitations

Although Floci closely emulates cloud services, it is **not** a complete replacement for real cloud environments.

Some limitations include:

* Not every cloud service is implemented.
* Some advanced features may not yet be available.
* Real cloud networking is not fully reproduced.
* Performance characteristics differ from production.
* Managed service integrations may be simplified.
* Cloud quotas, billing, and pricing cannot be tested.
* High availability and multi-region behavior cannot be fully simulated.
* Production-scale security testing still requires real cloud infrastructure.

Always validate production deployments using the actual cloud provider before releasing software.

---

# Comparison with Real Cloud

| Feature           | Floci             | Real Cloud |
| ----------------- | ----------------- | ---------- |
| Cost              | Free              | Paid       |
| Internet Required | Mostly No         | Yes        |
| Development Speed | Very Fast         | Moderate   |
| Startup Time      | Milliseconds      | Minutes    |
| Billing           | No                | Yes        |
| IAM Testing       | Partial/Supported | Complete   |
| Production Ready  | No                | Yes        |
| Local Testing     | Excellent         | Limited    |

---

# Advantages

* Faster feedback loop
* Zero infrastructure cost
* Safe experimentation
* Offline development
* Easier debugging
* Better developer productivity
* Great for education
* Ideal for CI/CD
* No cloud account required
* No authentication tokens required for supported emulators

---

# When You Should Use Floci

Use Floci when:

* Learning cloud services
* Developing cloud-native applications
* Testing infrastructure
* Running integration tests
* Building microservices
* Developing serverless applications
* Practicing DevOps
* Teaching cloud concepts
* Working without internet access

---

# When You Should NOT Use Floci

Avoid relying solely on Floci when:

* Performing production performance testing
* Running load or stress tests against real cloud infrastructure
* Validating cloud billing behavior
* Testing region-specific managed services
* Verifying compliance or security in production
* Releasing applications to customers without testing on the real cloud

---

# Frequently Asked Questions

### Is Floci free?

Yes. Floci is open source and MIT licensed.

### Do I need an AWS account?

No.

### Can I use AWS SDKs?

Yes.

### Does it support Docker?

Yes.

### Can I use Terraform?

Yes.

### Is it suitable for production?

No. Floci is intended for local development, testing, education, and CI/CD workflows. Production deployments should target the actual cloud provider.

---

# Contributing

Contributions are welcome.

You can help by:

* Reporting bugs
* Improving documentation
* Adding new cloud services
* Optimizing performance
* Submitting pull requests

---

# License

Floci is distributed under the **MIT License**, allowing both personal and commercial use. Refer to the official project documentation for the complete license details.

---

# Acknowledgements

Thanks to the Floci community and contributors for building an open-source platform that makes local cloud development faster, easier, and more accessible.
