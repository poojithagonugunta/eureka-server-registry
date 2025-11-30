**This module acts as the centralized service registry for all microservices in the system.
Both payment-processing-service and paypal-provider-service register themselves to this Eureka Server, enabling:

Service discovery

Load balancing (if multiple instances)

Decoupled inter-service communication

Avoiding hard-coded URLs**

**Overview**
The Eureka Server allows microservices to discover each other dynamically.
In your project:
**1.processing-service → registers itself to Eureka**
**2.paypal-provider-service → registers itself to Eureka**

**processing-service → looks up paypal-provider-service using service name
(Instead of calling with a fixed URL)**

This ensures loose coupling and fault tolerance.

                +--------------------+
                |   Eureka Server    |
                | (Service Registry) |
                +---------+----------+
                          |
          -------------------------------------
          |                                   |
+------------------------+     +---------------------------+
| payment-processing     |     | paypal-provider-service   |
|  - Registers to Eureka |     |  - Registers to Eureka    |
|  - Looks up provider   |     |  - Exposes provider APIs  |
+------------------------+     +---------------------------+
