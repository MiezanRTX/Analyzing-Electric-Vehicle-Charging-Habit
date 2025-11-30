Got it — you want \*\*pure Markdown code\*\*, no fluff outside the code.

Here you go — copy → paste → done. 🚀



---



````markdown

\# ⚡ EV Charging Station SQL Analytics



This project analyzes electric vehicle (EV) charging behavior at \*\*shared charging stations\*\* using SQL. It answers key usage questions to help optimize charging infrastructure.



---



\## 📊 Objectives \& Queries



\### 1️⃣ Unique Users per Garage  

Counts the number of distinct users who have used shared charging stations in each garage.  

\- Output columns: `garage\_id`, `num\_unique\_users`

\- Sorted from most → least users  

\- Saved as: \*\*unique\_users\_per\_garage\*\*



```sql

SELECT

&nbsp;   garage\_id,

&nbsp;   COUNT(DISTINCT user\_id) AS num\_unique\_users

FROM charging\_sessions

WHERE is\_shared = TRUE

GROUP BY garage\_id

ORDER BY num\_unique\_users DESC;

````



---



\### 2️⃣ Top 10 Most Popular Charging Start Times



Finds the most common start times (weekday + hour) for shared charging sessions.



\* Output columns: `weekdays\_plugin`, `start\_plugin\_hour`, `num\_charging\_sessions`

\* Sorted from most → least sessions

\* Limited to top 10

\* Saved as: \*\*most\_popular\_shared\_start\_times\*\*



```sql

SELECT

&nbsp;   EXTRACT(DOW FROM plugin\_start\_time) AS weekdays\_plugin,

&nbsp;   EXTRACT(HOUR FROM plugin\_start\_time) AS start\_plugin\_hour,

&nbsp;   COUNT(\*) AS num\_charging\_sessions

FROM charging\_sessions

WHERE is\_shared = TRUE

GROUP BY weekdays\_plugin, start\_plugin\_hour

ORDER BY num\_charging\_sessions DESC

LIMIT 10;

```



---



\### 3️⃣ Long Duration Shared Users



Identifies users whose average shared charging session lasts > 10 hours.



\* Output columns: `user\_id`, `avg\_charging\_duration`

\* Sorted from longest → shortest durations

\* Saved as: \*\*long\_duration\_shared\_users\*\*



```sql

SELECT

&nbsp;   user\_id,

&nbsp;   AVG(charging\_duration\_hrs) AS avg\_charging\_duration

FROM charging\_sessions

WHERE is\_shared = TRUE

GROUP BY user\_id

HAVING AVG(charging\_duration\_hrs) > 10

ORDER BY avg\_charging\_duration DESC;

```



---



\## 🧠 Skills Demonstrated



\* SQL Aggregation \& Grouping

\* Time-based Analysis (weekday \& hour extraction)

\* Filtering and Ranking Insights

\* Practical EV usage analytics



---



\## 📁 Output DataFrames



| DataFrame Name                  | Description                           |

| ------------------------------- | ------------------------------------- |

| unique\_users\_per\_garage         | Distinct users per garage             |

| most\_popular\_shared\_start\_times | Top 10 busy times by weekday/hour     |

| long\_duration\_shared\_users      | Users who charge >10 hours on average |



---



🚀 This SQL analysis helps identify demand patterns and improve resource planning for EV communities.



```



---



If you'd like, I can also:

✨ Add badges + visuals  

✨ Add a short setup section  

✨ Make a portfolio version highlighting your DA skills



Want that?

```



