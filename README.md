# Project EduTech
---

This project is an ETL pipeline designed for a [dataset](https://goo.gl/ME6hjp) regarding assessments hosted on an ed tech service. After the data is converted into a queryable form, exploratory analysis using Spark SQL demonstrates some typical queries by the businesses that use the service. The project uses:
  - [GCP AI Platform Notebooks](https://cloud.google.com/ai-platform-notebooks)
  - [Docker](https://www.docker.com/)
  - [Kafka](https://kafka.apache.org/)
  - [Spark](https://spark.apache.org/)
  - [Hadoop](https://hadoop.apache.org/)

### Repo Structure
---

- README.md:
  - Project description
  - Links to data and tools used
  - Summary of business questions and results
- docker-compose.yml:
  - Instructions for docker-compose
  - Spins up containers connected through specified ports
- project-2.ipynb:
  - Docker container setup instructions
  - ETL pipeline setup instructions
  - Pyspark data queries and explanations
- eliu390-history.txt:
  - Command line history during project
  
### Summary of Results
---

- Each individual assessment has the following schema:

```
root
 |-- keen_timestamp: string (nullable = true)
 |-- max_attempts: string (nullable = true)
 |-- started_at: string (nullable = true)
 |-- base_exam_id: string (nullable = true)
 |-- user_exam_id: string (nullable = true)
 |-- keen_created_at: string (nullable = true)
 |-- certification: string (nullable = true)
 |-- keen_id: string (nullable = true)
 |-- exam_name: string (nullable = true)
 |-- sequences: struct (nullable = true)
 |    |-- attempt: string (nullable = true)
 |    |-- id: string (nullable = true)
 |    |-- questions: array (nullable = true)
 |    |    |-- element: struct (containsNull = false)
 |    |    |    |-- user_incomplete: boolean (nullable = true)
 |    |    |    |-- user_correct: boolean (nullable = true)
 |    |    |    |-- user_submitted: string (nullable = true)
 |    |    |    |-- id: string (nullable = true)
 |    |    |    |-- user_result: string (nullable = true)
 |    |    |    |-- options: array (nullable = true)
 |    |    |    |    |-- element: struct (containsNull = false)
 |    |    |    |    |    |-- checked: boolean (nullable = true)
 |    |    |    |    |    |-- at: string (nullable = true)
 |    |    |    |    |    |-- id: string (nullable = true)
 |    |    |    |    |    |-- submitted: string (nullable = true)
 |    |    |    |    |    |-- correct: boolean (nullable = true)
 |    |-- counts: struct (nullable = true)
 |    |    |-- incomplete: integer (nullable = true)
 |    |    |-- submitted: integer (nullable = true)
 |    |    |-- incorrect: integer (nullable = true)
 |    |    |-- all_correct: boolean (nullable = true)
 |    |    |-- correct: integer (nullable = true)
 |    |    |-- total: integer (nullable = true)
 |    |    |-- unanswered: integer (nullable = true)
```


- The dataset contains 3280 rows, each representing an assessment taken by one student.
- There are a total of 107 unique exams.
- The most popular class in the dataset was "Learning Git", with 394 recorded assessments.
- The "Learning Git" exam had 5 questions and an average score of 67.6%.
- Questions 1 and 2 on the "Learning Git" exam were the easiest, while question 3 was the hardest.