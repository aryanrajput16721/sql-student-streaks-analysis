# 🎓 Student Streaks Analysis with SQL

This is my **SQL-based learner engagement project**, designed to identify the most consistent students on an EdTech platform by analyzing their daily learning streaks.  
It highlights users who maintained long-term activity and celebrates those with **30+ day streaks** — the top performers!

---

## 👋 Overview

- Analyze user activity logs to detect learning streaks  
- Use SQL logic to calculate and rank streaks  
- Identify top learners with 30+ day streaks  
- Demonstrate real-world EdTech analytics using SQL

---

## 🧑‍💻 About Me

Hi, I’m **Aryan Kashyap**, currently preparing to become a **Data Analyst**.  
This project is part of my hands-on SQL practice and portfolio building journey.

---

## 🗂️ Project Files

| File Name                          | Description                                      |
|-----------------------------------|--------------------------------------------------|
| `user_streaks_database.sql`       | Database structure & sample data                |
| `longest_user_streaks_part_1.sql` | SQL script for calculating and ranking streaks  |
| `student-streaks-analysis-sql1.png` | Workbench output showing initial setup         |
| `student-streaks-analysis-sql2.png` | Variable initialization and temp table creation |
| `student-streaks-analysis-sql3.png` | Calculation of streak length logic             |
| `student-streaks-analysis-sql4.png` | Query execution and result preview             |
| `student-streaks-analysis-sql5.png` | Final output showing top learners              |

---

## 🧩 SQL Concepts Used

- **User-defined variables** to track streak continuity  
- **Temporary tables** for intermediate calculations  
- **CASE logic** to increment/reset streaks  
- **GROUP BY**, **HAVING**, and **ORDER BY** for aggregation and filtering  
- **MySQL Workbench** for query execution and visualization  

---

## 📊 Step-by-Step Logic

1️⃣ **Initialize Variables**  
Set up counters and trackers to monitor streak continuity per user
```sql
SET @streak_count := 0;
SET @prev_user_id := NULL;
SET @prev_streak_active := NULL;


2️⃣ **Calculate Each User’s Streak**  
Loop through each user’s activity in chronological order.  
If the current day continues a streak, increment the counter; otherwise, reset it
CREATE TEMPORARY TABLE streaks_new AS (
  SELECT 
    user_id,
    streak_created,
    streak_active,
    CASE
      WHEN @prev_user_id = user_id AND @prev_streak_active = 1 AND streak_active = 1
      THEN @streak_count := @streak_count + 1
      ELSE @streak_count := 0
    END AS streak_length,
    @prev_user_id := user_id,
    @prev_streak_active := streak_active
  FROM user_streaks_sql
  ORDER BY user_id, streak_created
);

3️⃣ **Identify Top Performers**  
Aggregate streaks per user, filter those with streaks ≥ 30 days, and rank them by consistency
SELECT 
  user_id, 
  MAX(streak_length) AS max_streak
FROM streaks_new
GROUP BY user_id
HAVING max_streak >= 30
ORDER BY max_streak DESC;


---

## ✨ Key Insights

- 🔥 Identified users with **30+ day streaks** — showcasing long-term learner commitment  
- 🧠 Demonstrated **SQL logic** for real-world EdTech analytics  
- 📈 Highlighted **user engagement and consistency**  
- 💪 Strong example of **data-driven learner analysis**

---

## 🧰 Tools Used

| Tool | Purpose |
|------|----------|
| 🧮 **MySQL Workbench** | Writing and executing SQL queries |
| 🗂️ **365 Data Science SQL Practice Database** | Source database for simulation |
| 💻 **GitHub** | Documentation, screenshots, and sharing |

---

## 🧠 Learning Outcomes

- Mastered use of **variables and conditional logic** in SQL  
- Learned how to **track behavioral patterns** from raw data  
- Practiced **aggregation and filtering** techniques  
- Built a reusable logic for **engagement analysis**

---

## 🚀 Use Cases

- EdTech learner consistency tracking  
- Gamified streak-based rewards system  
- Behavioral analytics for student retention  
- SQL practice for real-world scenarios

---

## 👤 Author Spotlight

**Aryan Kashyap**  
📊 *Aspiring Data Analyst* | *SQL & Data Visualization Enthusiast*  
❤️ Passionate about turning raw data into actionable insights  
📍 *India*
# 🎓 Student Streaks Analysis with SQL

### 👋 Overview
This SQL project identifies the **most consistent learners** on an EdTech platform by analyzing their daily learning streaks.  
It measures how long users remained active and finds those who achieved **30+ day streaks** — the top performers!

---

### 🧑‍💻 About Me
Hi, I’m **Aryan Kashyap**, currently preparing to become a **Data Analyst**.  
This project is part of my hands-on SQL practice and portfolio building journey.  

---

### 🗂️ Project Files
| File Name | Description |
|------------|-------------|
| `user_streaks_database.sql` | Database structure & sample data |
| `longest_user_streaks_part_1.sql` | SQL script for calculating and ranking streaks |
| `student-streaks-analysis-sql1.png` | Workbench output showing initial setup |
| `student-streaks-analysis-sql2.png` | Variable initialization and temporary table creation |
| `student-streaks-analysis-sql3.png` | Calculation of streak length logic |
| `student-streaks-analysis-sql4.png` | Query execution and result preview |
| `student-streaks-analysis-sql5.png` | Final output showing top learners |

---

### 🧩 SQL Concepts Used
- **User-defined variables** (`@streak_count`, `@prev_user_id`)  
- **Temporary tables** (`CREATE TEMPORARY TABLE`)  
- **CASE statements** for conditional logic  
- **GROUP BY**, **HAVING**, and **ORDER BY** for aggregation & ranking  
- **MySQL Workbench** for execution & visualization  

---

### 📊 Step-by-Step Logic

#### 1️⃣ Initialize Variables
```sql
SET @streak_count := 0;
SET @prev_user_id := NULL;
SET @prev_streak_active := NULL;

#### 2️⃣ Calculate Each User’s Streak
CREATE TEMPORARY TABLE streaks_new AS (
  SELECT 
    user_id,
    streak_created,
    streak_active,
    CASE
      WHEN @prev_user_id = user_id AND @prev_streak_active = 1 AND streak_active = 1
      THEN @streak_count := @streak_count + 1
      ELSE @streak_count := 0
    END AS streak_length,
    @prev_user_id := user_id,
    @prev_streak_active := streak_active
  FROM user_streaks_sql
  ORDER BY user_id, streak_created
);

#### 3️⃣ Identify Top Performers
SELECT 
  user_id, 
  MAX(streak_length) AS max_streak
FROM streaks_new
GROUP BY user_id
HAVING max_streak >= 30
ORDER BY max_streak DESC;

---

## ✨ Key Insights

🔥 Identified users with **30+ day streaks** — showcasing long-term learner commitment  
🧠 Demonstrated **SQL logic** for real-world EdTech analytics  
📈 Highlighted **user engagement and consistency**  
💪 Strong example of **data-driven learner analysis**

---

## 🧰 Tools Used

| Tool | Purpose |
|------|----------|
| 🧮 **MySQL Workbench** | Writing and executing SQL queries |
| 🗂️ **365 Data Science SQL Practice Database** | Source database for simulation |
| 💻 **GitHub** | Documentation, screenshots, and sharing |

---

## 👤 Author Spotlight

**Aryan Kashyap**  
📊 *Aspiring Data Analyst* | *SQL & Data Visualization Enthusiast*  
❤️ Passionate about turning raw data into actionable insights  
📍 *India*

