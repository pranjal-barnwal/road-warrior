## **ADR-6: Automatic Trip Grouping Logic with User Override**
-   **Date:** 2026-03-05

-   **Status:** Accepted

-   **Context:** The problem statement explicitly asks for items to be "grouped by trip," with guidance leaning towards "automatic grouping by the system." Users may have unique travel patterns that the system cannot infer perfectly.

-   **Decision:** Implement a `Trip Grouping Service` that automatically analyzes reservation data (dates, locations, PNRs) to identify and group related reservations into trips. The algorithm will prioritize date/time proximity, followed by geographical proximity. The system will provide a user interface for travelers to review, adjust, merge, or split automatically generated trips.

-   **Consequences:**
    -   **Pros:** Reduces manual effort for users, provides a structured view of travel plans, adaptable to different travel scenarios.
    -   **Cons:** Initial complexity in developing and refining the grouping algorithm, potential for incorrect groupings requiring user intervention, ongoing maintenance for algorithm improvements.