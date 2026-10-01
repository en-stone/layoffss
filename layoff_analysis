SELECT SUM(total_laid_off) AS total_laid_of ,
company 
FROM layoffs
GROUP BY company ;


SELECT AVG(total_laid_off) AS avg_laid_off , 
MAX(total_laid_off) AS max_laid_off,
company
FROM layoffs
GROUP BY company 
ORDER BY max_laid_off DESC 
LIMIT 15
;

SELECT 
YEAR(date) AS year_date , SUM(total_laid_off) AS total_laid_off 
FROM layoffs
GROUP BY year_date
ORDER BY year_date DESC 
LIMIT 15
;

SELECT  industry, 
SUM(total_laid_off) AS total_laid_off,
AVG(total_laid_off) AS avg_laid_off
FROM layoffs
GROUP BY industry
ORDER BY total_laid_off DESC
LIMIT 10 ;

#Country Analysis

SELECT country ,
SUM(total_laid_off) AS total_laid_off 
FROM layoffs
GROUP BY country
ORDER BY total_laid_off DESC
LIMIT 15 ;

SELECT country,
AVG(percentage_laid_off) * 100 AS avg_layoff_percentage 
FROM layoffs
GROUP BY country
ORDER BY  avg_p_laid_off DESC
LIMIT 15;

#Company Analysis

##Which companies had the largest layoffs
SELECT company ,
SUM(total_laid_off) AS total_laid_off
FROM layoffs
GROUP BY company
ORDER BY total_laid_off DESC
LIMIT 15 ;

#Startup Stage
#How do layoffs vary across company stages?
SELECT
    stage,
    SUM(total_laid_off) AS total_laid_off,
    SUM(total_laid_off) * 100.0 /
        (SELECT SUM(total_laid_off)
         FROM layoffs) AS percentage_of_total
FROM layoffs
GROUP BY stage
ORDER BY percentage_of_total DESC;
 
#Is there an apparent relationship between funding raised and layoffs?
SELECT
    CASE
        WHEN funds_raised_millions < 200 THEN 'Low'
        WHEN funds_raised_millions < 600 THEN 'Medium'
        ELSE 'High'
    END AS funding_level,
    COUNT(*) AS companies,
    SUM(total_laid_off) AS total_laid_off,
    AVG(total_laid_off) AS avg_laid_off
FROM layoffs
WHERE funds_raised_millions IS NOT NULL
  AND total_laid_off IS NOT NULL
GROUP BY funding_level
ORDER BY avg_laid_off DESC;

 #Which industries had the highest number of layoffs, and which had the highest layoff percentages?
 #part 1 Which industries had the highest number of layoffs
SELECT
    industry,
    SUM(total_laid_off) AS total_laid_off,
    AVG(total_laid_off) AS avg_laid_off,
    AVG(percentage_laid_off) AS avg_layoff_percentage
FROM layoffs
GROUP BY industry
ORDER BY total_laid_off DESC;

#part 2 which had the highest layoff percentages
SELECT
    industry,
    SUM(total_laid_off) AS total_laid_off,
    AVG(percentage_laid_off) AS avg_layoff_percentage
FROM layoffs
GROUP BY industry
ORDER BY avg_layoff_percentage DESC;

#How much missing data exists in each important column?

SELECT COUNT(*),
COUNT(company),
COUNT(location),
COUNT(industry),
COUNT(total_laid_off),
COUNT(percentage_laid_off),
COUNT(date),
COUNT(stage),
COUNT(country),
COUNT(funds_raised_millions)


FROM layoffs;


#Are the companies with the largest layoffs also the companies with the highest layoff percentage?

SELECT
company,
COUNT(*) AS layoff_records,
SUM(total_laid_off) AS total_laid_off,
AVG(percentage_laid_off) AS avg_layoff_percentage,

RANK() OVER (
        ORDER BY SUM(total_laid_off) DESC
    ) AS layoffs_rank,

RANK() OVER (
        ORDER BY AVG(percentage_laid_off) DESC
    ) AS percentage_rank

FROM layoffs
GROUP BY company
ORDER BY layoffs_rank;
