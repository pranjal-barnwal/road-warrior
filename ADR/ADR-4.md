## **ADR-4: Cloud-Native Deployment with Managed Services**
-   **Date:** 2026-03-05

-   **Status:** Accepted

-   **Context:** The system needs to support significant growth, high availability, and international users, while minimizing operational burden for a new team. The host also clarified to assume a simple model within a trusted boundary, but without explicit on-premise mandate.

-   **Decision:** Deploy the Road Warrior system to a major cloud provider (e.g., Azure) utilizing managed services wherever possible (e.g., managed containers like Azure Kubernetes Service (AKS) or Azure Container Apps, managed databases like Azure Database for PostgreSQL, managed message brokers like Azure Service Bus/Event Hubs/Azure Managed Kafka).

-   **Consequences:**
    -   **Pros:** High scalability and elasticity (auto-scaling), increased availability and disaster recovery capabilities, reduced operational overhead (no server management), access to a rich ecosystem of services.
    -   **Cons:** Vendor lock-in, potential for higher operational costs if not optimized, requires cloud-specific expertise for optimal configuration and management, security responsibility shared with cloud provider.