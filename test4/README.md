# 实验四
- 1.查询某个员工的信息
```sql
select * from employees where employee_id=1;
```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.1.png)
- 2.递归查询某个员工及其所有下属，子下属员工。(一下sql查找的是id为11的节点下的所有直属子类节点，包括子辈的和孙子辈的所有直属节点。)
```sql
select * from employees m start with m.EMPLOYEE_ID=11 connect by m.MANAGER_ID=prior m.EMPLOYEE_ID;
```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.2.png)

- 3.查询订单表，并且包括订单的订单应收货款: Trade_Receivable= sum(订单详单表.ProductNum*订单详单表.ProductPrice)- Discount。
```sql
select sum(b.PRODUCT_NUM*b.PRODUCT_PRICE)
from orders a,order_details b
where a.order_id=b.order_id
GROUP BY b.order_id
```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.3.png)

- 4.查询订单详表，要求显示订单的客户名称和客户电话，产品类型用汉字描述。
```sql
select a.CUSTOMER_NAME as "客户姓名",a.CUSTOMER_TEL as "客户电话",PRODUCT_NAME as "产品名字"
from orders a,order_details b
where a.order_id=b.order_id

```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.4.png)
- 5.查询订单详表，要求显示订单的客户名称和客户电话，产品类型用汉字描述。

```sql
select a.DEPARTMENT_NAME as "部门",b.name as "负责人"
from departments a,employees b
WHERE a.department_id=b.department_id

```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.5.png)


- 6.查询部门表，同时显示部门的负责人姓名。
```sql
select a.DEPARTMENT_NAME as "部门",b.name as "负责人"
from departments a,employees b
WHERE a.department_id=b.department_id

```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.6.png)
- 7.查询部门表，统计每个部门的销售总金额。
```sql
select DEPARTMENT_NAME,SUM(c.Trade_Receivable)AS "销售总金额"
from DEPARTMENTS a,EMPLOYEES b,ORDERS c
where a.DEPARTMENT_ID=b.DEPARTMENT_ID and b.EMPLOYEE_ID=c.EMPLOYEE_ID group by DEPARTMENT_NAME;


```
![binaryTree]( https://github.com/Ryanaa/oracle/blob/master/test4/image/4.7.png)