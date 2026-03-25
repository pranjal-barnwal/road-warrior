## **ADR-2: Asynchronous Event-Driven Integration for Reservation Updates**
-   **Date:** 2026-03-05

-   **Status:** Accepted

-   **Context:** The system needs to automatically load and refresh reservation data from multiple agency systems, with updates reflected near real-time. Direct polling of external systems by a monolithic API could lead to bottlenecks, tightly coupled dependencies, and make it difficult to scale and manage updates efficiently.

-   **Decision:** Implement an asynchronous, event-driven integration model where agency systems (or their proxy adapters) publish reservation updates as events to a central message broker. A dedicated `Reservation Ingestion Service` will consume these events, process them, and update the system's internal data store.

-   **Consequences:**
    -   **Pros:** Decouples Road Warrior from external systems, improves scalability and resilience (spikes in updates can be buffered), enables near real-time updates without constant polling, supports easier integration of new agency systems.
    -   **Cons:** Increases complexity of the overall system (distributed messaging, eventual consistency concerns), requires robust error handling and dead-letter queues for failed event processing.