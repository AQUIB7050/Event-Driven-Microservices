# Event-Driven Microservices with Apache Kafka (Spring Boot)

[![Java](https://img.shields.io/badge/Java-16-blue)](https://www.oracle.com/java/)
[![Spring Boot](https://img.shields.io/badge/Spring_Boot-4.0.1-brightgreen)](https://spring.io/projects/spring-boot)
[![Apache Kafka](https://img.shields.io/badge/Kafka-4.1.1-orange)](https://kafka.apache.org/)

---

## 📌 Project Overview

This project demonstrates a **real-world event-driven microservices architecture** built using **Spring Boot** and **Apache Kafka**.  
Independent microservices communicate asynchronously via Kafka topics, enabling:

- High scalability  
- Loose coupling  
- Fault tolerance and resilience  

### Microservices Included

- **order-service** – Handles customer orders and publishes order events  
- **stock-service** – Consumes order events and updates inventory  
- **email-service** – Consumes order events and sends notifications  
- **base-domains** – Shared domain models and DTOs  

---

## 🏗 Architecture

```text
+----------------+        Kafka Topic        +----------------+
| order-service  | -----------------------> | stock-service  |
+----------------+                          +----------------+
         |
         | Kafka Topic (order events)
         v
+----------------+
| email-service  |
+----------------+

```
Each service runs independently and can scale horizontally.

Kafka ensures asynchronous communication and decoupling between services.



## 🛠 Technologies Used

Java 16

Spring Boot 4.0.1

Spring Kafka 4.0.1

Apache Kafka 4.1.1

Maven

Docker (optional)

SLF4J & Logback

## ✨ Features

Event-driven communication using Kafka

JSON message serialization and deserialization

Kafka topic auto-creation via Spring Kafka

Environment-based configuration

Structured logging

## 🚀 Setup & Run Locally

### Prerequisites

Java 16 or higher

Apache Kafka & Zookeeper

Maven 3.x

Git

Clone Repository

```
git clone https://github.com/AQUIB7050/Event-Driven-Microservices.git
cd Event-Driven-Microservices/Microservices
```




Start Kafka
```
# Start Zookeeper
bin/zookeeper-server-start.sh config/zookeeper.properties

# Start Kafka broker
bin/kafka-server-start.sh config/server.properties
```

Build & Run Microservices
```
# Run inside each microservice directory
mvn clean install
mvn spring-boot:run
```

order-service → Produces order events

stock-service → Consumes order events

email-service → Consumes order events

Verify Kafka Topics
```
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

## 📂 Folder Structure

| Folder / File       | Description                              |
|---------------------|------------------------------------------|
| base-domains        | Shared DTOs and domain models             |
| email-service       | Email notification microservice           |
| order-service       | Order management & Kafka event producer   |
| stock-service       | Inventory update Kafka consumer           |
| .gitignore          | Git ignore configuration                  |


## 🔄 How It Works
Order Service publishes an event when an order is placed

Kafka delivers the event asynchronously

Stock Service updates inventory

Email Service sends order confirmation

Kafka enables scalable, fault-tolerant communication without tight coupling.

## 🤝 Contributing
Fork the repository

Create a feature branch

```
git checkout -b feature-name
```
Commit changes
```
git commit -m "Add feature"
```

Push to GitHub
```
git push origin feature-name
```

Open a Pull Request

📄 License
This project is MIT Licensed.
