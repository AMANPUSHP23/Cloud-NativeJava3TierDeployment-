# 🚀 Cloud-Native Java Web Application Deployment

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen.svg)](https://github.com/your-username/your-repo/actions) <!-- Update with actual CI/CD build status link -->
[![Java Version](https://img.shields.io/badge/Java-8-orange.svg)](https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html)
[![Spring Framework](https://img.shields.io/badge/Spring-4.x-green.svg)](https://spring.io/)
[![Ansible](https://img.shields.io/badge/Ansible-Automation-red.svg)](https://www.ansible.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📌 Overview
This project features a **Cloud-Native Java Web Application** designed with a multi-tier architecture. It focuses on the refactoring and automated deployment of the application onto **AWS Infrastructure**, leveraging **Ansible** for seamless configuration management and scalability. It serves as a robust example of modern enterprise application development and deployment practices.

The project demonstrates a production-ready environment setup including load balancing, auto-scaling, and integrated caching and messaging services.

---

## 🏗 Architecture
The application consists of the following tiers:
1.  **Web Tier**: Nginx/Apache (Load Balancer).
2.  **App Tier**: Apache Tomcat 8 (Java Spring Application).
3.  **Database Tier**: MySQL (User Data).
4.  **Messaging Tier**: RabbitMQ (Queue Management).
5.  **Caching Tier**: Memcached (Session/Data Caching).

---

## 🛠 Tech Stack

| Category | Technology |
| :--- | :--- |
| **Language** | Java 8 (OpenJDK) |
| **Framework** | Spring MVC, Spring Security |
| **Automation** | Ansible 2.x |
| **App Server** | Apache Tomcat 8 |
| **Database** | MySQL 5.7+ |
| **Middleware** | RabbitMQ, Memcached |
| **Frontend** | Bootstrap, jQuery, Select2, Popper.js |

---

## 📂 Project Structure

```text
├── ansible/                # Infrastructure Automation
│   ├── tomcat_setup.yml    # Tomcat 8 installation & OS hardening
│   └── vpro-app-setup.yml  # Deployment of WAR artifact from Nexus
├── src/                    # Source Code
│   ├── main/java           # Spring Controller & Services
│   ├── main/resources      # Properties and Config files
│   └── main/webapp         # UI Assets (JSPs, CSS, JS, Bootstrap, jQuery, Popper.js)
└── pom.xml                 # Maven Dependencies
```

---

## 🚀 Deployment Guide

### Prerequisites
*   An AWS Account.
*   Ansible installed on your control node.
*   Java 8 and Maven installed locally for builds.

### 1. Build the Artifact
```bash
mvn clean install
```
*This generates `vprofile-v2.war` in the target directory.*

### 2. Infrastructure Automation (Ansible)
Navigate to the `ansible/` directory and run the playbooks to provision your servers.

**Setup Tomcat:**
```bash
ansible-playbook -i inventory tomcat_setup.yml
```

**Deploy Application:**
```bash
ansible-playbook -i inventory vpro-app-setup.yml --extra-vars "vprofile_version=v1"
```

---

## 🔧 Configuration Details
The application configuration is managed via `application.properties`.
*   **Database Connectivity**: Managed via JDBC.
*   **File Uploads**: Profile images are stored at `${catalina.home}/tmpFiles`.
*   **Validation**: Custom messages are defined in `validation.properties`.

---

## 🤝 Contributing
1.  Fork the Project.
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`).
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`).
4.  Push to the Branch (`git push origin feature/AmazingFeature`).
5.  Open a Pull Request.

---

## 📄 License
Distributed under the MIT License. See `LICENSE` for more information.