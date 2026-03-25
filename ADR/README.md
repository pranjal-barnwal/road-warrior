# Architecture Decision Records

This directory contains the key architecture decisions behind the Road Warrior solution. Read the table below for a quick summary, then open the individual ADR files for the full context, decision, and trade-offs.

| ADR ID  | Title                                              | Date       | Status         | Key Decision                                                                 | Consequences (summary)                                                      | Related Goals / Requirements         |
|---------|----------------------------------------------------|------------|----------------|------------------------------------------------------------------------------|-----------------------------------------------------------------------------|--------------------------------------|
| [ADR-1](ADR-1.md) | Microservices Architecture with Event-Driven Design | 2026-03-05 | Accepted | Adopt microservices organized by business capability, with service-owned data and API/event communication. | Better scalability, team autonomy, and maintainability; added distributed-system and operational complexity. | Scalability, Team Agility, Maintainability, External Integration |
| [ADR-2](ADR-2.md) | Asynchronous Event-Driven Integration for Reservation Updates | 2026-03-05 | Accepted | Use an event-driven ingestion pipeline where agency updates are published to a message broker and consumed by an ingestion service. | Decoupled integrations and resilient near real-time updates; eventual consistency and messaging complexity. | Reliable Data Ingestion, Near Real-Time Updates, Resilience, Extensibility |
| [ADR-3](ADR-3.md) | Real-time User Interface Updates via WebSockets/SSE | 2026-03-05 | Accepted | Implement push-based client updates through WebSockets or SSE via a notification service. | Responsive UX with reduced polling; persistent connection and reconnection complexity. | Rich UI, Real-Time Updates, Performance, User Experience |
| [ADR-4](ADR-4.md) | Cloud-Native Deployment with Managed Services | 2026-03-05 | Accepted | Deploy on Azure with managed services for compute, data, and messaging. | High availability and reduced ops burden; cloud cost control and vendor lock-in risks. | Scalability, Availability, Operational Efficiency, Global Reach |
| [ADR-5](ADR-5.md) | Primary Database Choice | 2026-03-05 | Accepted | Use Azure SQL Database as the primary operational datastore for structured relational travel data. | Strong consistency and relational querying; potential scaling and schema-migration overhead at higher growth. | Data Integrity, ACID Transactions, Query Performance, Maintainability |
| [ADR-6](ADR-6.md) | Automatic Trip Grouping Logic with User Override | 2026-03-05 | Accepted | Automatically group reservations into trips using heuristics, with traveler ability to modify groupings. | Lower user effort and structured trip view; grouping inaccuracies require override UI and algorithm tuning. | Automation, Usability, Data Freshness, Adaptability |

## How to Use These ADRs

Read the ADRs in numerical order if you want the architecture story from platform shape to user-facing behavior:

1. overall system style
2. integration and ingestion model
3. live client update strategy
4. deployment approach
5. persistence strategy
6. domain-specific trip grouping behavior
