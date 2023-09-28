# Introduction
The goal of this project was to analyze real-world medical appointment data through Time Series Analysis. My tasks included dataset cleaning, comprehensive analysis, and extracting insights using Python and MySQL.

## Project Description
The "Healthcare Appointments Analytics" project is a comprehensive data analysis initiative that delves into the intricacies of medical appointments and explores factors influencing patient attendance and no-show rates. By leveraging advanced analytical techniques, the project aims to uncover valuable insights that can positively impact patient engagement and resource allocation in healthcare settings.



## SQL Analyses

USE hospital_timeseries;

-- How many values are there in the given dataset
SELECT COUNT(*)
FROM patients;


-- Count the number of appointments for each day in the given dataset:
SELECT 
    AppointmentDay, COUNT(*) AS Appointments
FROM patients
GROUP BY AppointmentDay; 

-- Calculate the average number of appointments(Set to nearest whole number) per day in the given dataset.
WITH CTE AS (SELECT 
    AppointmentDay, COUNT(*) AS counts
FROM patients
GROUP BY AppointmentDay)
SELECT ROUND(AVG(counts), 0) AS avg_counts
FROM CTE


-- Find the day with the highest number of appointments in the given dataset.
SELECT 
    AppointmentDay, COUNT(*) AS counts
FROM patients
GROUP BY AppointmentDay
ORDER BY counts DESC
LIMIT 1; 


-- Calculate the monthly average number of appointments in the given dataset.
WITH Monthly_count AS (SELECT 
   EXTRACT(MONTH FROM (AppointmentDay)) AS month,
   COUNT(*) AS counts
FROM patients
GROUP BY month)
SELECT month, ROUND(AVG(counts), 0) AS avg_counts
FROM Monthly_count
GROUP BY month



-- the month with the highest number of appointments in the given dataset.
SELECT 
   EXTRACT(MONTH FROM (AppointmentDay)) AS months, COUNT(*) AS counts
FROM patients
GROUP BY months
ORDER BY counts DESC
LIMIT 1;


-- Calculate the weekly average number of appointments in the given dataset.
WITH Weekly_count AS (SELECT 
   EXTRACT(WEEK FROM (AppointmentDay)) AS week,
   COUNT(*) AS counts
FROM patients
GROUP BY week)
SELECT week, ROUND(AVG(counts), 0) AS avg_counts
FROM Weekly_count
GROUP BY week;


-- Find the week with the highest number of appointments in the given dataset.
SELECT 
   EXTRACT(WEEK FROM (AppointmentDay)) AS weeks, COUNT(*) AS counts
FROM patients
GROUP BY weeks
ORDER BY counts DESC
LIMIT 1;


-- What is the distribution of appointments based on gender in the dataset?
SELECT 
    Gender, COUNT(*) AS counts
FROM patients
GROUP BY Gender;


-- Calculate the number of appointments per weekday in the given dataset.
SELECT 
   (WEEKDAY(AppointmentDay)) AS weekday, COUNT(*) AS counts
FROM patients
GROUP BY weekday
ORDER BY weekday;

-- OR
SELECT 
   (DAYNAME(AppointmentDay)) AS dayname, COUNT(*) AS counts
FROM patients
GROUP BY dayname
ORDER BY counts;

-- Calculate the average time between scheduling and the appointment day in the given dataset.
SELECT 
   ROUND(AVG(DATEDIFF(AppointmentDay, ScheduledDay)), 0) AS Avg_time 
FROM patients;
