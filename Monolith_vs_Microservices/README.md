# Microservices vs Monolith Architecture

---

## Overview

This document explains:

- Monolithic Architecture  
- Microservices Architecture  
- Migration from Monolith to Microservices  
- Key Design Patterns  

---

# Monolithic Architecture

<p align="center">
  <img src="./assests/monolith_vsms.png" width="600"/>
</p>

### Definition

Monolithic architecture is a type of architecture where **all modules of an application are kept inside a single codebase**.

- All modules are tightly coupled  
- Entire system is deployed as one unit  

---

### Example: E-commerce Application

Modules:
- Auth  
- Cart  
- Order  
- Payment  

If one module fails (e.g., Payment), the whole application may crash.

---

### Problems

#### Tight Coupling
- Modules depend heavily on each other  

#### Single Point of Failure
- One failure can break the entire system  

#### Deployment Bottleneck
- Even a small change requires full application redeployment  

#### Scaling Issue

Example:
- Payment → 5 lakh requests  
- Auth → 5k requests  

The entire application must still be scaled, which increases cost.

---

### Myth

Monolith cannot scale — Incorrect.  
It can scale, but only as a whole system.

---

### When to Use

- Small applications  
- Low traffic systems  
- Early-stage projects  

---

# Microservices Architecture

<p align="center">
  <img src="./assests/microservices_img.png" width="600"/>
</p>

### Definition

Microservices architecture breaks an application into independent services, where each service handles a specific functionality.

---

### Key Features

- Loosely coupled services  
- Independent deployment  
- Each service can have its own database  

---

### Example

Services:
- User Service  
- Payment Service  

If Payment fails, the User service continues to work.

---

### Advantages

- Independent deployment  
- Individual scaling  
- Cost efficient  
- Fault isolation  

---

### Challenges

- Complex system design  
- Network latency  
- Debugging is harder  
- Data consistency issues  

---

# Monolith vs Microservices

<p align="center">
  <img src="./assests/coupling_diff.png" width="600"/>
</p>

| Feature          | Monolith       | Microservices   |
|------------------|---------------|-----------------|
| Codebase         | Single        | Multiple        |
| Coupling         | Tight         | Loose           |
| Deployment       | Full App      | Per Service     |
| Scaling          | Whole App     | Individual      |
| Failure Impact   | High          | Low             |
| Complexity       | Low           | High            |

---

# Monolith to Microservices Migration

### Example (Udemy-like System)

Modules:
- Auth  
- Payment  
- Cart  
- Courses  

Convert the Payment module into a Payment service.

---

### Steps

1. Identify high-impact modules  
2. Define API contracts  
3. Choose communication:
   - REST / gRPC (Synchronous)
   - RabbitMQ / Kafka (Asynchronous)  
4. Extract module into service  
5. Monitoring and optimization  
6. Scaling  

---

# Canary Deployment

- Start by routing a small percentage of traffic to the new service  

Example:
- 90% → Monolith  
- 10% → Microservice  

Gradually increase traffic if the system remains stable.

---

# Strangler Design Pattern

- Gradually replace parts of the monolith  
- Controlled using a routing layer  

Example:
- 90% traffic → Monolith  
- 10% → New service  

---

# Distributed Transactions

## Saga Pattern

- Series of local transactions  
- Uses compensating actions if a failure occurs  

---

## Outbox Pattern

- Ensures data consistency  
- Stores event and data in the same transaction  

---

# Conclusion

Start with Monolith for simplicity.  
Move to Microservices when scaling and system complexity increase.