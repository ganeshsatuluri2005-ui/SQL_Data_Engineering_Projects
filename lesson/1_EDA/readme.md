# Heading
## headigng
### heading 3

normal text  
**Bold text**  
*Itatalic text* 

- bullet 1
- buller 2

1. number 1
2. number 2



[Link Text] (https://google.com)

![project 1 overview](image adress)

```sql
 select
    sd.skills,
    round(median(jpf.salary_year_avg),0) as median_salary,
    count(jpf.salary_year_avg) as demand_count,
    median(jpf.salary_year_avg) * count(jpf.salary_year_avg) as optimal_score
from job_postings_fact as jpf
inner join  skills_job_dim as sjd
    on jpf.job_id = sjd.job_id
inner join skills_dim as sd
    on sjd.skill_id = sd.skill_id
where jpf.job_title_short = 'Data Engineer' 
    and jpf.job_work_from_home = True
group by
    sd.skills
having
    count(jpf.*) > 100
order by median_salary desc
limit 25;```