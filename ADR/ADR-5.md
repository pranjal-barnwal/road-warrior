## **ADR-5: Primary Database Choice**
-   **Date:** 2026-03-05

-   **Status:** Accepted

-   **Context:** The system needs to persistently store structured data for reservations, trips, and user profiles, maintaining relationships between these entities. Key quality goals include scalability, data freshness, and maintainability.

-   **Decision:** The primary operational database for Road Warrior will be **Azure SQL Database**.

-   **Consequences:**
    -   **Pros:** 
        - Strong data integrity and consistency
        - Robust and efficient querying for structured and related data
        - Reduced operational overhead with a managed PaaS service
    -   **Cons:** 
        - Potentially more complex horizontal scaling strategies (e.g., sharding) if data volume and write throughput grow significantly beyond projections
        - Schema changes require more structured planning compared to schema-less databases

---

### Justification

**Data Structure Fit**  
Reservation data, user profiles, and their grouping into trips naturally form a relational structure with well-defined schemas and relationships. Azure SQL's relational model is highly effective for managing this structured data and enforcing data integrity.

**Data Consistency**  
Operations like manual reservation entry and user profile updates benefit from the strong consistency and ACID (Atomicity, Consistency, Isolation, Durability) properties inherent in a relational database, ensuring immediate data integrity.

**Querying Capabilities**  
Complex queries involving joins (e.g., retrieving all reservations for a specific trip, or all trips for a user with associated favored vendors) are efficiently handled by SQL's declarative querying language, leveraging mature indexing and optimization capabilities.

**Managed Service Benefits**  
Azure SQL Database is a fully managed PaaS offering, providing built-in high availability, disaster recovery, automatic backups, robust security features, and elastic scaling capabilities (e.g., elastic pools, vCore scaling) to meet the system's growth requirements.

---

### Alternatives Considered

**MongoDB / NoSQL (e.g., Azure Cosmos DB for MongoDB API)**  
While NoSQL databases like MongoDB (or Azure Cosmos DB's MongoDB API) offer schema flexibility and excellent horizontal scaling for massive, unstructured or semi-structured data, they introduce complexities for managing relational data patterns and enforcing referential integrity.

For the current scope and known data structures, the benefits of a relational model—strong consistency, complex querying of related data, and data integrity—outweigh the flexibility of NoSQL. The expected scale (100k users, 3–5 reservations per trip) is well within Azure SQL's capabilities with proper scaling strategies.

