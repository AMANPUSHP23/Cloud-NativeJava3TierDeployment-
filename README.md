# 🚀 Cloud-NativeJava3TierDeployment

[![Java Version](https://img.shields.io/badge/Java-17-orange.svg)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
[![Spring Boot](https://img.shields.io/badge/Spring--Boot-3.1.3-green.svg)](https://spring.io/projects/spring-boot)
[![Infrastructure](https://img.shields.io/badge/Infrastructure-AWS-FF9900.svg)](https://aws.amazon.com/)
[![Automation](https://img.shields.io/badge/Automation-Ansible-red.svg)](https://www.ansible.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Overview
This project demonstrates a production-grade refactoring and deployment of a multi-tier Java application (VProfile) into a **Cloud-Native AWS ecosystem**. The architecture is designed for high availability, scalability, and automated configuration management using **Ansible**.

By moving from a traditional monolith setup to a structured cloud environment, this project showcases how to integrate various middleware services like caching, messaging, and search into a unified Spring-based application.

---

## 🏗 Multi-Tier Architecture
The application follows a robust N-tier architecture pattern:
1.  **Web Tier**: Nginx / AWS ELB for high-performance load balancing.
2.  **Application Tier**: Apache Tomcat hosting the Spring MVC backend.
3.  **Database Tier**: MySQL 8.0 for persistent relational data storage.
4.  **Caching Tier**: Memcached for session management and database query optimization.
5.  **Messaging Tier**: RabbitMQ for asynchronous task processing and decoupled communication.
6.  **Search Tier**: ElasticSearch for advanced data indexing and retrieval.

---

## 🛠 Tech Stack

| Category | Technology |
| :--- | :--- |
| **Language** | Java 17 (OpenJDK) |
| **Framework** | Spring MVC, Spring Security, Spring Data JPA |
| **Build Tool** | Apache Maven 3.x |
| **Automation** | Ansible |
| **Database** | MySQL 8.0 |
| **Middleware** | RabbitMQ, Memcached, ElasticSearch |
| **UI Engine** | JSP (Java Server Pages), JSTL |

---

## 📂 Project Structure

```text
├── ansible/                # Playbooks for automated server provisioning
├── src/
│   ├── main/java           # Backend Logic (Controllers, Services, Repositories)
│   ├── main/resources      # Config properties and Database SQL Dumps
│   └── main/webapp         # UI Components and static assets
├── pom.xml                 # Project Object Model & Dependency Management
└── README.md               # Project Documentation
```

---

## 🚀 Getting Started

### Prerequisites
Ensure you have the following installed:
*   **JDK 17**
*   **Maven 3**
*   **MySQL 8**
*   **Ansible** (for automated deployment)

### 1. Database Setup
The application requires an initial data schema. A SQL dump is provided in the resources.

```bash
# Import the database dump
mysql -u <user_name> -p accounts < src/main/resources/db_backup.sql
```

### 2. Build the Project
Compile and package the application into a `.war` artifact using Maven:

```bash
mvn clean install
```

### 3. Deployment
For manual deployment, move the generated `vprofile-v2.war` from the `target/` directory to your Tomcat `webapps` folder. For automated cloud deployment, refer to the Ansible Documentation.

---

## 🔧 Configuration
Key application settings can be found in:
*   `src/main/resources/application.properties`: Database credentials, RabbitMQ connection strings, and Memcached end-points.

---

## 🤝 Contributing
1.  Fork the repository.
2.  Create a Feature Branch (`git checkout -b feature/NewFeature`).
3.  Commit your changes (`git commit -m 'Add some feature'`).
4.  Push to the branch (`git push origin feature/NewFeature`).
5.  Open a Pull Request.

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.

Copyright (c) 2025 **Aman Pushp**
