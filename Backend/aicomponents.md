US-12 – NLP Search
NLP query parsing converts natural language into filters (beds, price, suburb, amenities). Example: “3-bed under $700k in Tarneit with parking”.
US-13 – Agent Reply Drafting
For each enquiry, the system drafts a reply that references the property, answers the buyer’s questions, and remains editable. No auto-send; the agent reviews and sends from their email client.

Design & Data Flow
<img width="1020" height="567" alt="image" src="https://github.com/user-attachments/assets/daefce9f-a2a3-44c7-b6d6-ceaac63e5585" />

NLP Query Parser: Regex + small NER dictionary for suburbs/amenities; outputs canonical filters.
Ranking/Lead Scoring: start with heuristics (recency, price proximity, engagement signals), later upgrade to learning-to-rank when data is available.

Acceptance Criteria & KPIs
Area	Acceptance Criteria (UAT)	Initial KPI (Post‑MVP)
NLP Search (US‑12)	Given sample queries, When submitted, Then filters match expected beds/price/suburb/amenities in ≥ 9/10 cases.	≥ 90% correct parsing on UAT set; median search < 400ms.
Reply Draft (US‑13)	Given an enquiry, When opening in Agent Inbox, Then a contextually accurate, editable draft is produced without PII leakage.	Agent edits < 30% of tokens on average; zero PII exposure incidents.
