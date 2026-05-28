# 📡 Discovery Server (Instagram Clone Backend)

The **Discovery Server** acts as the service registry for the [Instagram Clone Microservices Backend](https://github.com/Instagram-Api-Clone) when running in local development environments. Built using **Spring Cloud Netflix Eureka Server**, it keeps track of all active microservice instances, their hostnames, IP addresses, and operational health.

---

## 🛠️ Features & Responsibilities
* **Service Registry**: Dynamically registers all microservice instances (`user-service`, `post-service`, `follow-service`, etc.) upon boot.
* **Service Discovery**: Allows client-side load balancers (like Spring Cloud Gateway or OpenFeign) to query active microservice endpoints without hardcoding static URLs.
* **Heartbeat & Health Checks**: Monitors registered service heartbeats. Automatically deregisters dead or unresponsive instances from the active lookup pool.
* **Local Development Accelerator**: Bypasses the need for complex networking configurations locally, facilitating quick inter-service communication.

> [!NOTE]
> When deployed inside a Kubernetes cluster, Eureka is bypassed in favor of native **Kubernetes CoreDNS** and Kubernetes Services, which handle service discovery natively.

---

## 🧱 Tech Stack
* **Framework**: Spring Boot 3 & Spring Cloud Netflix Eureka Server
* **Language**: Java 21
* **Monitoring**: New Relic APM agent
* **Containerization**: Docker (via Jib container builder)

---

## 🖥️ Management Dashboard

When running locally, you can access the interactive Eureka Administration Dashboard in your browser:
* **URL**: [http://localhost:8761](http://localhost:8761)

Here you can view:
1. Currently registered microservice names.
2. Number of active instances per service.
3. Node IP addresses, ports, and lease status.

---

## ⚙️ Running Locally

### Launching
1. Run the application:
   ```bash
   ./gradlew bootRun
   ```
   * The server starts up locally on port **`8761`**.
