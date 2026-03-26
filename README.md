<div align="center">

# Cloud-NativeJava3TierDeployment

<p><strong>Java web application deployment on AWS with Elastic Beanstalk, managed services, CDN delivery, and scalable traffic handling.</strong></p>

[![Java 17](https://img.shields.io/badge/Java-17-orange?style=for-the-badge)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
[![Spring MVC](https://img.shields.io/badge/Spring-MVC-green?style=for-the-badge)](https://spring.io/)
[![AWS](https://img.shields.io/badge/AWS-Cloud_Native-FF9900?style=for-the-badge)](https://aws.amazon.com/)
[![Elastic Beanstalk](https://img.shields.io/badge/Elastic_Beanstalk-Deployment-232F3E?style=for-the-badge)](https://aws.amazon.com/elasticbeanstalk/)
[![Ansible](https://img.shields.io/badge/Ansible-Automation-EE0000?style=for-the-badge)](https://www.ansible.com/)
[![MIT License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge)](https://opensource.org/licenses/MIT)

</div>

---

## Overview

This project showcases a Java web application deployed on AWS using a cloud-native, multi-tier architecture. The application is hosted through **AWS Elastic Beanstalk**, fronted by an **Application Load Balancer**, and scaled with **Auto Scaling** for resilient traffic handling.

The stack integrates **Amazon RDS** for relational data, **Amazon ElastiCache** for low-latency caching, **Amazon MQ** for asynchronous messaging, and **Amazon S3** for artifact storage. **Amazon CloudFront** and **Amazon Route 53** improve DNS routing and content delivery performance.

## Highlights

> Deployed Java web application using AWS Elastic Beanstalk with load balancing and auto scaling.
>
> Integrated AWS services including RDS, ElastiCache, Amazon MQ, and S3.
>
> Improved performance using CloudFront CDN and Route 53 DNS.

## Architecture Diagram

```mermaid
flowchart LR
    U[Users] --> R53[Amazon Route 53]
    R53 --> CF[Amazon CloudFront]
    CF --> ALB[Application Load Balancer]

    subgraph EB[AWS Elastic Beanstalk Environment]
        APP1[Tomcat App Instance 1]
        APP2[Tomcat App Instance 2]
    end

    ALB --> APP1
    ALB --> APP2

    APP1 --> RDS[Amazon RDS MySQL]
    APP2 --> RDS

    APP1 --> CACHE[Amazon ElastiCache]
    APP2 --> CACHE

    APP1 --> MQ[Amazon MQ]
    APP2 --> MQ

    S3[Amazon S3 Artifacts] --> EB
```

## Request Flow

```mermaid
sequenceDiagram
    participant User
    participant Route53 as Route 53
    participant CloudFront
    participant ALB as Load Balancer
    participant EB as Elastic Beanstalk
    participant RDS
    participant Cache as ElastiCache
    participant MQ as Amazon MQ

    User->>Route53: Request domain
    Route53->>CloudFront: Resolve and route
    CloudFront->>ALB: Forward dynamic request
    ALB->>EB: Distribute traffic
    EB->>Cache: Read or update cache
    EB->>RDS: Persist or fetch data
    EB->>MQ: Publish async events
    EB-->>User: Return application response
```

## Tech Stack

| Layer | Services / Tools |
| :--- | :--- |
| Application | Java 17, Spring MVC, Spring Security, Spring Data JPA |
| Packaging | Maven WAR build |
| Compute Platform | AWS Elastic Beanstalk |
| Traffic Management | Application Load Balancer, Auto Scaling |
| Database | Amazon RDS MySQL |
| Cache | Amazon ElastiCache |
| Messaging | Amazon MQ |
| Storage | Amazon S3 |
| Delivery | Amazon CloudFront |
| DNS | Amazon Route 53 |
| Automation | Ansible |
| View Layer | JSP, JSTL |

## Why This Architecture

- **Elastic Beanstalk** simplifies deployment, environment provisioning, and health management.
- **Load Balancer + Auto Scaling** improve availability under variable traffic.
- **RDS** offloads database operations to a managed service.
- **ElastiCache** reduces database pressure and improves response times.
- **Amazon MQ** decouples application workflows.
- **S3 + CloudFront** improve artifact management and delivery performance.
- **Route 53** provides reliable DNS routing for the application entry point.

## Project Structure

```text
ansible/                    # Provisioning and deployment support
src/
  main/java                 # Controllers, services, repositories, business logic
  main/resources            # application.properties, SQL dump, app resources
  main/webapp               # JSP pages and static frontend assets
pom.xml                     # Maven build configuration
README.md                   # Main project documentation
```

## Deployment Flow

1. Build the application into a WAR with Maven.
2. Store the deployment artifact in Amazon S3.
3. Create or update an Elastic Beanstalk application version.
4. Deploy to the Elastic Beanstalk environment.
5. Route production traffic through CloudFront and Route 53.

## Local Build

```bash
mvn clean install
```

## Configuration

Runtime settings are managed in `src/main/resources/application.properties`, including:

- JDBC database connectivity
- Cache host configuration
- Messaging broker configuration
- Spring MVC and security settings

## License

Distributed under the MIT License.

Copyright (c) 2025 Aman Pushp
