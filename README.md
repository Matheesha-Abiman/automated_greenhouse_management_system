# 🌱 Automated Greenhouse Management System (AGMS)

## 🏢 System Architecture

```
                  +------------------------+
                  |      API Gateway       |  :8080
                  |  (Spring Cloud GW)     |
                  +-----------+------------+
                              |
        +---------------------+---------------------+
        |                     |                     |
+-------+--------+   +--------+--------+   +--------+--------+
|   Auth Service |   |  Zone Service   |   | Sensor Service  |
|     :8085      |   |     :8081       |   |     :8082       |
+----------------+   +-----------------+   +-----------------+
        |                     |                     |
        |             +-------+--------+            |
        |             | Automation     |            |
        |             | Service :8083  |            |
        |             +----------------+            |
        |                                           |
+-------+--------+                                  |
|  Crop Service  |                                  |
|     :8084      |                                  |
+----------------+                                  |
        |                                           |
        +---------------------+---------------------+
                              |
                  +-----------+------------+
                  |   Service Registry     |  :8761
                  |   Config Server        |  :8888
                  +------------------------+
```

---

## 📦 Services Overview

### Infrastructure Services
| Service | Port | Description |
|--------|------|------------|
| Service Registry | 8761 | Service discovery (Eureka) |
| Config Server | 8888 | Centralized configuration |
| API Gateway | 8080 | Routing and security |

### Domain Services
| Service | Port | Description |
|--------|------|------------|
| Auth Service | 8085 | Authentication and JWT |
| Zone Service | 8081 | Zone management |
| Sensor Service | 8082 | IoT data processing |
| Automation Service | 8083 | Rule engine |
| Crop Service | 8084 | Crop lifecycle |

---

## 🛠 Tech Stack

```
Java 21
Spring Boot 3.5.x
Spring Cloud 2025.x
MySQL
JWT
Maven
WebFlux
Lombok
```

---

## ⚙️ Run Instructions

### Start Infrastructure
```bash
cd serviceregistry && ./mvnw spring-boot:run
cd configserver && ./mvnw spring-boot:run
cd api-gateway && ./mvnw spring-boot:run
```

### Start Services
```bash
cd auth-service && ./mvnw spring-boot:run
cd zone-service && ./mvnw spring-boot:run
cd sensor-service && ./mvnw spring-boot:run
cd automation-service && ./mvnw spring-boot:run
cd crop-service && ./mvnw spring-boot:run
```

---

## 🔐 Authentication Flow

```
POST /auth/register
POST /auth/login → accessToken + refreshToken
Authorization: Bearer <token>
POST /auth/refresh
```

---

## 🌐 Base URL

```
http://localhost:8080
```

---

## 📁 Project Structure

```
automated-greenhouse-management-system/
├── api-gateway/
├── auth-service/
├── automation-service/
├── configserver/
├── crop-service/
├── sensor-service/
├── serviceregistry/
├── zone-service/
├── docs/
├── AGMS_Postman_Collection.json
└── README.md
```

---

## 📊 Monitoring

```
http://localhost:8761
```

All services should show status: UP

---

## 📄 License

Educational Project
