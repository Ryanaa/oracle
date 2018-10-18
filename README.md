# 实验一
-查询一：
```sql
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
from hr.departments d，hr.employees e
where d.department_id = e.department_id
and d.department_name in ('IT'，'Sales')
GROUP BY department_name;
```
##有优化建议：
##可以创建索引来优化此语句的查询速度
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/web/images/hehe.png)
-查询二：
```sql
SELECT d.department_name，count(e.job_id)as "部门总人数"，
avg(e.salary)as "平均工资"
FROM hr.departments d，hr.employees e
WHERE d.department_id = e.department_id
GROUP BY department_name
HAVING d.department_name in ('IT'，'Sales');
``` 

##无优化建议
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/web/images/xixi.png)
-自行设计语句:
查询了姓名，工作的月数以及天数，运用额ROUND（）函数等，以及嵌套查询
```sql
select m.name as"姓名",
m.workmonth as"工作月份"
,m.workday as"工作天数", 
m.workmonth*m. salary_per_month as "工作每月工资"
,m.salary_per_month as"工作总工资"
FROM
（select e.salary as salary_per_month, e.first_name,e.last_name,concat(e.first_name,e.last_name)AS name,j.start_date,j.end_date,
floor(ROUND(TO_NUMBER(j.end_date-j.start_date  ))/30)as workmonth,
mod(ROUND(TO_NUMBER(j.end_date-j.start_date  )),30)as workday
from hr.employees  e,hr.job_history j
where e.employee_id=j.employee_id) m

```
##无优化建议
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/web/images/lolo.png)