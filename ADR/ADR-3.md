## **ADR-3: Real-time User Interface Updates via WebSockets/SSE**
-   **Date:** 2026-03-05

-   **Status:** Accepted

-   **Context:** The requirement for "richest user interface possible" and updates (delays, cancellations) to be "reflected" in the dashboard implies push-based, near real-time updates to the client-side applications (web and mobile) without constant polling.

-   **Decision:** Implement a push-based communication mechanism using WebSockets or Server-Sent Events (SSE) between the backend `Notification Service` and the client applications. When a relevant update occurs (e.g., reservation change, trip status change), the `Notification Service` will broadcast the update to connected clients.

-   **Consequences:**
    -   **Pros:** Provides a highly responsive and dynamic user experience, reduces client-side polling overhead, more efficient use of network resources.
    -   **Cons:** Adds complexity to backend (managing persistent connections, connection scaling) and frontend (handling asynchronous updates), requires careful handling of reconnects and message ordering.