# digital-literacy-sql-cassandra-neo4j
Analysis of digital literacy training in rural communities using **SQL**, **Cassandra**, and **Neo4j**.   Project developed for the *Complementos de Bases de Dados* course (Universidade).
## Context
Digital literacy is a key driver for social and economic inclusion.  
This project analyzes a dataset of participants in **digital literacy training programs**, focusing on:  

- **Demographics** (age, gender, education, income, location type, employment status)  
- **Skills before and after training** (computer knowledge, internet usage, mobile literacy)  
- **Training engagement** (modules completed, time per module, quizzes, sessions)  
- **Evaluation** (feedback, adaptability, employment impact, overall literacy score, engagement)

## Research Questions
The following analytical queries were implemented in **three paradigms** (Relational, NoSQL, Graph):  

1. Which demographic profiles showed the **highest skill improvement** after training?
2. What is the relationship between **engagement level** and **employment impact**?
3. How does **literacy gain vary by age group**?  
4. Which **education levels are associated to a higher number of completed sessions**?  
5. How does **household income affect adaptability**?

## Implementations
### SQL Implementation
The relational model captures users, training sessions, skills (pre/post), and evaluations.
**Key Queries:**
-Skill improvement by demographic profile.
-Engagement level vs. employment outcomes.
-Literacy gains by age group.
-Modules completed vs. education level.
-Income vs. adaptability.

### Cassandra Implementation
Since Cassandra does not support complex joins, the dataset was pre-processed in Python (pandas) to generate aggregated CSVs.

**Calculated new metrics:**
-avg_skill_improvement (difference between pre and post training scores)
-Literacy gain per age group
-Engagement and employment impact summaries

**Cassandra Tables**
-user_skill_improvement → demographic profile with highest skill improvement
-engagement_summary → training engagement vs employment impact
-age_literacy_grouped → literacy gain by age group
-education_sessions_summary → sessions completed by education level
-income_adaptability_summary → adaptability score by household income

### Neo4j Implementation 
