IST 722: Data Warehousing

**Project:** Integrated Customer Item Rating Warehouse
**Team:** Najah Bell, Elizabeth Shoots, Sandra Suresh
**Tools:** dbt · Snowflake · SQL · BI Reporting Layer



Project Overview

Two companies are in the process of merging  FudgeMart (a retail operation) and FudgeFlix (a streaming service), each maintained in separate, incompatible customer feedback systems. This project designed and implemented a unified data warehouse consolidating customer rating data from both companies into a single analytical platform, enabling cross-company satisfaction analysis and strategic decision-making.



Technical Design

Star Schema

The warehouse is built on a **pure star schema** with one central fact table surrounded by six dimension tables:

**Fact Table:**
•	`fact_item_rating` — one row per rating event (one customer, one item, one date)

**Dimension Tables:**
•	`dim_customer` — unified customer records from both companies, with `source_system` attribute
•	`dim_item` — unified product/title dimension covering physical retail and streaming content
•	`dim_category` — FudgeMart departments and FudgeFlix genres
•	`dim_category_type` — preserves semantic distinction between retail and streaming classification systems
•	`dim_item_type` — distinguishes physical products from streaming titles
•	`dim_date` — full time context (date, month, quarter, year, weekday)

Key Engineering Decisions

**Surrogate Keys:** Used `dbt_utils.generate_surrogate_key` on a combination of source system IDs and `source_system` attribute to resolve identity conflicts between the two companies' independent customer ID systems.

**UNION ALL Transformations:** SQL models merged FudgeMart products and FudgeFlix streaming titles into a single `dim_item` structure using UNION ALL.

**Conformed Dimensions:** Shared dimension tables (`dim_date`, `dim_item_type`) carry consistent meaning across both source systems.



Key Findings (BI Dashboard)

| Metric | FudgeFlix (Streaming) | FudgeMart (Retail) |
|--------|----------------------|---------------------|
| Average Rating | 2.72 | 2.49 |
| Top Category | Disney | Housewares |
| Lowest Category | Africa | 20th Century Period |
| % Meeting 3.0 Target | ~47% | ~49% |

Both divisions fell below the 3.0 strategic satisfaction benchmark.

**Actionable Recommendations:**
1. Launch a quality audit for the lowest-performing retail category
2. Implement cross-platform loyalty incentives using unified customer data
3. Re-curate or reallocate budget from underperforming streaming segments



Files in This Folder

| File | Description |
|------|-------------|
| `IST722_Presentation.pdf` | Final project presentation slides |
| `dbt_models/` | SQL transformation files |



Ethical Reflection

Integrating customer data from two previously independent companies raised data governance considerations. The design decision to retain a `source_system` attribute in `dim_customer` — rather than fully merging customer identities — preserved data provenance and prevented erroneous cross-company identity assumptions that could affect how individual customers are analyzed or targeted.
<img width="468" height="637" alt="image" src="https://github.com/user-attachments/assets/e24097a6-2506-4f09-a479-8568c829da06" />

