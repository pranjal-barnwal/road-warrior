# Road Warrior Architecture Kata

Road Warrior is an architecture kata for a next-generation trip management dashboard. The system consolidates existing airline, hotel, and car rental reservations into a traveler-facing dashboard, groups them into trips, keeps them up to date, and supports rich web and mobile experiences.

This repository is intentionally documentation-first. It captures the problem framing, the architectural characterization, the key decisions, the diagrams, and the presentation materials used to explain the solution.

![Road Warrior | Pranjal Kumar, Software Engineer](assets/social-share.jpg)

## Quick Links

- [Problem Statement](problem-statement.md)
- [Architecture Characterization Document](ACD.md)
- [ADR Index](ADR/README.md)
- [Presentation Guide](guide.md)
- [Presentation Rubric](presentation-rubric.md)
- [System Context Diagram](diagrams/system_context.png)
- [Container Diagram](diagrams/container.png)
- [Runtime View](diagrams/runtime_view.png)
- [Deployment View](diagrams/deployment.png)

## What This Repository Contains

- problem statement and evaluation rubric
- architecture characterization document
- architecture decision records
- PlantUML source and rendered architecture diagrams
- presentation guide and final presentation artifacts

There is no runnable application code in this repository. The purpose of the repo is to document and explain the architecture.

## Repository Map

### Core Documents

- [problem-statement.md](problem-statement.md): cleaned copy of the kata brief
- [ACD.md](ACD.md): architecture characterization document covering requirements, constraints, concerns, strategy, C4 views, and deployment view
- [guide.md](guide.md): slide-by-slide presentation guide and speaker support
- [presentation-rubric.md](presentation-rubric.md): presentation scoring criteria used to evaluate the solution

### ADRs

- [ADR/README.md](ADR/README.md): ADR index with one-line summaries
- [ADR/ADR-1.md](ADR/ADR-1.md): microservices architecture with event-driven design
- [ADR/ADR-2.md](ADR/ADR-2.md): asynchronous event-driven reservation ingestion
- [ADR/ADR-3.md](ADR/ADR-3.md): real-time client updates via WebSockets or SSE
- [ADR/ADR-4.md](ADR/ADR-4.md): cloud-native deployment with managed services
- [ADR/ADR-5.md](ADR/ADR-5.md): Azure SQL as the primary operational datastore
- [ADR/ADR-6.md](ADR/ADR-6.md): automatic trip grouping with traveler override

### Diagrams

- [diagrams/system_context.plantuml](diagrams/system_context.plantuml) and [diagrams/system_context.png](diagrams/system_context.png)
- [diagrams/container.plantuml](diagrams/container.plantuml) and [diagrams/container.png](diagrams/container.png)
- [diagrams/runtime_view.plantuml](diagrams/runtime_view.plantuml) and [diagrams/runtime_view.png](diagrams/runtime_view.png)
- [diagrams/deployment.plantuml](diagrams/deployment.plantuml) and [diagrams/deployment.png](diagrams/deployment.png)

### Presentation Artifacts

- [Team 4 - Road Warrior Architecture Kata.pptx](Team%204%20-%20Road%20Warrior%20Architecture%20Kata.pptx)
- [Team 4 - Road Warrior Architecture Kata.pdf](Team%204%20-%20Road%20Warrior%20Architecture%20Kata.pdf)
- [guide.pdf](guide.pdf)

## Recommended Reading Order

If you are using this repository to learn from the architecture, read the documents in this order:

1. [problem-statement.md](problem-statement.md)
2. [ACD.md](ACD.md)
3. [ADR/README.md](ADR/README.md)
4. Individual ADR files in [ADR](ADR/README.md)
5. Diagrams in [diagrams](diagrams/system_context.png)
6. [guide.md](guide.md)

## Architecture Summary

The solution uses an event-driven microservices architecture with a Backend-for-Frontend pattern.

- Reservation updates enter asynchronously through agency integration systems.
- A dedicated ingestion flow normalizes and persists reservation changes.
- Trip grouping is treated as a domain capability, not just presentation logic.
- Web and mobile clients are supported through tailored backend experiences.
- Managed cloud services are used to satisfy scalability, elasticity, and availability goals.

The architecture is optimized for scale, data freshness, responsiveness, and maintainability, while accepting the trade-offs of distributed-system complexity and eventual consistency.

## Why This Repo Is Structured This Way

Public architecture repositories are most useful when a reader can understand the problem, the decision process, and the resulting design without needing private context. This repository is organized around that learning path:

- start with the problem
- understand the requirements and constraints
- review the architecture strategy and diagrams
- inspect the decision records
- use the presentation guide to see how the story is communicated

## Notes for Contributors

If you extend this repository, keep it documentation-centric and learner-friendly.

- Prefer clear filenames and conventional indexes such as [README.md](README.md) in documentation folders.
- Keep diagrams versioned from their PlantUML source files.
- When changing the architecture, update [ACD.md](ACD.md), the relevant ADRs in [ADR](ADR/README.md), and any impacted diagrams together.
- Avoid adding scratch files or editor-generated artifacts to the root of the repo.