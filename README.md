# digital-literacy-sql-cassandra-neo4j

**Analysis of digital literacy training in rural communities using SQL, Cassandra, and Neo4j**  
Project developed for the **Complementos de Bases de Dados** course (Universidade).

## Context

Digital literacy is a key driver for social and economic inclusion.  
This project analyzes a dataset of participants in digital literacy training programs, focusing on:

- **Demographics** (age, gender, education, income, location type, employment status)  
- **Skills before and after training** (computer knowledge, internet usage, mobile literacy)  
- **Training engagement** (modules completed, time per module, quizzes, sessions)  
- **Evaluation** (feedback, adaptability, employment impact, overall literacy score)

## Research Questions

The following analytical queries were implemented in **three paradigms**: Relational (SQL), NoSQL (Cassandra), and Graph (Neo4j):

1. Which demographic profiles showed the **highest skill improvement** after training?  
2. What is the relationship between **engagement level and employment impact**?  
3. How does **literacy gain vary by age group**?  
4. Which **education levels** are associated to a higher number of completed sessions?  
5. How does **household income affect adaptability**?  

## Implementations

### SQL (MySQL)

- **Relational schema**: `User`, `Training`, `Pre_Training_Skills`, `Post_Training_Skills`, `Evaluation`  
 
File: [`sql_code.sql`](./sql_code.sql)

### Cassandra (NoSQL)

Since Cassandra does not support complex joins, the dataset was **pre-processed in Python (pandas)** to generate aggregated CSVs.

- **New metrics calculated**:
  - `avg_skill_improvement` → difference between pre and post training scores  
  - `literacy_gain` → improvement by age group  
  - Engagement & employment summaries  

- **Tables created**:
  - `user_skill_improvement` → skill improvement per demographic profile  
  - `engagement_summary` → training engagement vs employment impact  
  - `age_literacy_grouped` → literacy gain by age group  
  - `education_sessions_summary` → sessions by education level  
  - `income_adaptability_summary` → adaptability by income  

Files:  
- [`cassandra_code.sql`](./cassandra_code.sql) → Cassandra schema & queries  
- [`cassandra_new_metrics.py`](./cassandra_new_metrics.py) → pre-processing script  
- [`results_cassandra.sql`](./results_cassandra.sql) → query outputs
  
### Neo4j (Graph Database)

The dataset was modeled as a **graph** in Neo4j:

- **Nodes**:
  - `User` (demographics, age group)  
  - `PreTrainingSkill` → [:OF_USER] → User  
  - `PostTrainingSkill` → [:OF_USER] → User  
  - `Training` → [:DONE_BY] → User  
  - `Evaluation` → [:OF_USER] → User  

## Key Findings

- **SQL**: Best suited for structured analysis with joins and groupings. Clear to implement but requires more complex queries.  
- **Cassandra**: Fast retrieval once data is **pre-aggregated**. However, requires pre-processing outside Cassandra (Python used here).  
- **Neo4j**: Provided flexibility for **exploratory queries** and visualization of relationships (users, skills, training). Results aligned with SQL/Cassandra but offered richer graph insights.  



