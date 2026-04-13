# Game-Purchase-Engagement-SQL-Analysis
A structured SQL project analysing gaming platform user behaviour, playtime patterns, spending habits, and purchase channel preferences using Microsoft SQL Server.



---

##  Dataset Tables

| Table | Description |
|-------|-------------|
| EngagementData | Core table with player playtime, spends, genre, and purchase data |
| AcquisitionCost | Cost data related to acquiring new users |
| PerCommunicationModeCost | Cost breakdown by communication/marketing channel |

---

##  Data Cleaning Steps

Before analysis, the following data quality issues were addressed:

- **Renamed columns** — removed spaces and special characters for cleaner SQL querying (e.g., `Total Playtime` → `Total_Playtime`, `Spends ($)` → `Spends`)
- **Removed logical outliers** — deleted records where `Total_Playtime < Online_Playtime` (logically impossible)
- **Removed junk values** — removed records with `Total_Playtime = 99999999`
- **Handled NULL values** — replaced NULL `Digital_Purchase` and `Physical_Purchase` with `0` to preserve row integrity
- **Added `Months` column** — extracted month number from `Date` field for time-based analysis

---

##  Business Questions Answered (6 Queries)

| # | Question | Key Finding |
|---|----------|-------------|
| Q1 | What is the favourite genre by playtime? | **Shooter** is the most played genre |
| Q2 | Which genre generates the most revenue? | **RPG** generates the highest revenue |
| Q3 | Are genre trends changing over time? | Yes — both playtime and revenue shift month to month |
| Q4 | Do players prefer digital or physical purchases? | Players buy **digitally** more than physically |
| Q5 | What is the spend distribution (digital vs physical)? | Digital spending significantly outpaces physical |
| Q6 | Is the spend distribution changing over time? | Yes — digital spend gap widens over time |

---

##  Key Insights

### 1. Engagement vs. Monetisation Gap
- **Shooter** attracts the most playtime but **RPG** generates the most revenue
- This means: use Shooter as an **acquisition/engagement** tool, and RPG for **monetisation**

### 2. Digital-First Player Base
- Players overwhelmingly prefer **digital purchases** over physical
- Recommendation: prioritise digital storefront experience, instant downloads, and digital-only bundles

### 3. Seasonal Trends Exist
- Both playtime and revenue shift across months
- Platform should align **game launches and promotions** with peak engagement months

### 4. Data Quality is Critical
- Logical inconsistencies (Online > Total playtime) and junk values can heavily skew analysis
- Cleaning before analysis ensures trustworthy business decisions

---

##  SQL Concepts Used

- `sp_rename` for column renaming
- `DELETE` with logical conditions for outlier removal
- `UPDATE` with `IS NULL` for null handling
- `ALTER TABLE` to add derived columns
- `DATEPART` for time-based grouping
- `GROUP BY` with `SUM`, `COUNT` aggregations
- `HAVING` clause for filtered aggregation
- Multi-table joins across `EngagementData`, `AcquisitionCost`, and `PerCommunicationModeCost`

---

## ▶️ How to Run

1. Create the database:
```sql
CREATE DATABASE gamepurchase;
USE gamepurchase;
```

2. Import the following CSV/Excel files into SQL Server:
   - `EngagementData`
   - `AcquisitionCost`
   - `PerCommunicationModeCost`

3. Run the cleaning scripts first, then execute analysis queries in order.

---

## 📌 Tools & Technologies

- **Database**: Microsoft SQL Server
- **IDE**: SQL Server Management Studio (SSMS)


---

## 👤 Author: Asrar Ahmad
Connect with me on www.linkedin.com/in/asrarlearner


