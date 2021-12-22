```sql
+-------+--------+-----------+------+------------+---------+---------+--------+
| EMPNO | ENAME  | JOB       | MGR  | HIREDATE   | SAL     | COMM    | DEPTNO |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+

mysql> select * from dept;
+--------+------------+----------+
| DEPTNO | DNAME      | LOC      |
+--------+------------+----------+
|     10 | ACCOUNTING | NEW YORK |
|     20 | RESEARCH   | DALLAS   |
|     30 | SALES      | CHICAGO  |
|     40 | OPERATIONS | BOSTON   |
+--------+------------+----------+


mysql> select * from salgrade;
+-------+-------+-------+
| GRADE | LOSAL | HISAL |
+-------+-------+-------+
|     1 |   700 |  1200 |
|     2 |  1201 |  1400 |
|     3 |  1401 |  2000 |
|     4 |  2001 |  3000 |
|     5 |  3001 |  9999 |
+-------+-------+-------+





//////////////////////////////1、取得每个部门最高薪水的人员名称
select e.ename,e.sal,e.deptno 
from emp e 
group by e.deptno
where e.sal=(select max(sal) from emp group by deptno) and ;
;


select 
    a.ename,max(a.sal),a.deptno
from 
    emp a
join
    emp b
on 
    a.empno=b.empno
group by
    deptno ;


/////////////////////////////2、哪些人的薪水在部门的平均薪水之上

    select e.ename,e.sal
    from emp e
    join (select avg(sal) avgsal,deptno from emp group by deptno) d
    on e.deptno=d.deptno
    where e.sal>d.avgsal;
+-------+---------+
| ename | sal     |
+-------+---------+
| ALLEN | 1600.00 |
| JONES | 2975.00 |
| BLAKE | 2850.00 |
| SCOTT | 3000.00 |
| KING  | 5000.00 |
| FORD  | 3000.00 |
+-------+---------+

    mysql> select avg(sal) avgsal,deptno from emp group by deptno;
+-------------+--------+
| avgsal      | deptno |
+-------------+--------+
| 2916.666667 |     10 |
| 2175.000000 |     20 |
| 1566.666667 |     30 |
+-------------+--------+

  select ename,sal,d.avgsal
    from emp e
    join (select avg(sal) avgsal,deptno from emp group by deptno) d
    on e.deptno=d.deptno;
+--------+---------+-------------+
| ename  | sal     | avgsal      |
+--------+---------+-------------+
| SMITH  |  800.00 | 2175.000000 |
| ALLEN  | 1600.00 | 1566.666667 |
| WARD   | 1250.00 | 1566.666667 |
| JONES  | 2975.00 | 2175.000000 |
| MARTIN | 1250.00 | 1566.666667 |
| BLAKE  | 2850.00 | 1566.666667 |
| CLARK  | 2450.00 | 2916.666667 |
| SCOTT  | 3000.00 | 2175.000000 |
| KING   | 5000.00 | 2916.666667 |
| TURNER | 1500.00 | 1566.666667 |
| ADAMS  | 1100.00 | 2175.000000 |
| JAMES  |  950.00 | 1566.666667 |
| FORD   | 3000.00 | 2175.000000 |
| MILLER | 1300.00 | 2916.666667 |
+--------+---------+-------------+


/////////////////3、取得部门中（所有人的）平均的薪水等级，如下
mysql> select deptno,avg(grade)
from emp e
join salgrade s
on e.sal between losal and hisal
group by deptno;
+--------+------------+
| deptno | avg(grade) |
+--------+------------+
|     10 |     3.6667 |
|     20 |     2.8000 |
|     30 |     2.5000 |
+--------+------------+


mysql> select deptno,grade
from emp e
join salgrade s
on e.sal between losal and hisal;
+--------+-------+
| deptno | grade |
+--------+-------+
|     20 |     1 |
|     30 |     3 |
|     30 |     2 |
|     20 |     4 |
|     30 |     2 |
|     30 |     4 |
|     10 |     4 |
|     20 |     4 |
|     10 |     5 |
|     30 |     3 |
|     20 |     1 |
|     30 |     1 |
|     20 |     4 |
|     10 |     2 |
+--------+-------+


///////////////////4、不准用组函数（Max），取得最高薪水（给出两种解决方案
mysql> select sal from emp order by sal desc limit 1;
+---------+
| sal     |
+---------+
| 5000.00 |
+---------+

///////////////5、取得平均薪水最高的部门的部门编号（至少给出两种解决方案）
mysql> select  deptno from emp group by deptno order by avg(sal) desc limit 1;
+--------+
| deptno |
+--------+
|     10 |
+--------+


`



    mysql> select avg(sal) avgsal,deptno from emp group by deptno;
+-------------+--------+
| avgsal      | deptno |
+-------------+--------+
| 2916.666667 |     10 |
| 2175.000000 |     20 |
| 1566.666667 |     30 |
+-------------+--------+

/////////////////6、取得平均薪水最高的部门的部门名称
mysql> select d.dname
 from
 emp e
 join
    dept d
on
    e.deptno=d.deptno
 group by e.deptno order by avg(sal) desc limit 1;
+------------+
| dname      |
+------------+
| ACCOUNTING |
+------------+


mysql> select d.dname,e.deptno
 from
 emp e
 join
    dept d
on
    e.deptno=d.deptno;
+------------+--------+
| dname      | deptno |
+------------+--------+
| ACCOUNTING |     10 |
| ACCOUNTING |     10 |
| ACCOUNTING |     10 |
| RESEARCH   |     20 |
| RESEARCH   |     20 |
| RESEARCH   |     20 |
| RESEARCH   |     20 |
| RESEARCH   |     20 |
| SALES      |     30 |
| SALES      |     30 |
| SALES      |     30 |
| SALES      |     30 |
| SALES      |     30 |
| SALES      |     30 |
+------------+--------+



//////////////////////////////7、求平均薪水的等级最低的部门的部门名称

select d.dname
 from
 emp e
 join
    dept d
on
    e.deptno=d.deptno
 group by e.deptno order by avg(sal) asc limit 1;
+-------+
| dname |
+-------+
| SALES |
+-------+



//8、取得比普通员工(员工代码没有在 mgr 字段上出现的)的最高薪水还要高的领导人姓




//////////////////////////////////////9、取得薪水最高的前五名员工
select 
ename,sal
from 
emp
order by sal desc limit 5;
+-------+---------+
| ename | sal     |
+-------+---------+
| KING  | 5000.00 |
| SCOTT | 3000.00 |
| FORD  | 3000.00 |
| JONES | 2975.00 |
| BLAKE | 2850.00 |
+-------+---------+


////////////////////////////10、取得薪水最高的第六到第十名员工
select 
ename,sal
from 
emp
order by sal desc limit 5,5;
+--------+---------+
| ename  | sal     |
+--------+---------+
| CLARK  | 2450.00 |
| ALLEN  | 1600.00 |
| TURNER | 1500.00 |
| MILLER | 1300.00 |
| MARTIN | 1250.00 |
+--------+---------+


////////////////////////////////////11.取得最后入职的 5 名员工
select 
ename,hiredate
from 
emp
order by hiredate desc limit 5;
+--------+------------+
| ename  | hiredate   |
+--------+------------+
| ADAMS  | 1987-05-23 |
| SCOTT  | 1987-04-19 |
| MILLER | 1982-01-23 |
| FORD   | 1981-12-03 |
| JAMES  | 1981-12-03 |
+--------+------------+

////////////////////////////////////12、取得每个薪水等级有多少员工
select grade,count(ename) 
from emp e
join 
salgrade s
on e.sal between s.losal and s.hisal
group by s.grade;
+-------+--------------+
| grade | count(ename) |
+-------+--------------+
|     1 |            3 |
|     2 |            3 |
|     3 |            2 |
|     4 |            5 |
|     5 |            1 |
+-------+--------------+

////////////////////////////14、列出所有员工及领导的姓名
select a.ename,ifnull(b.ename,'没有上级')
from
emp a
left join 
emp b
on a.mgr=b.empno;
+--------+----------------------------+
| ename  | ifnull(b.ename,'没有上级')       |
+--------+----------------------------+
| SMITH  | FORD                       |
| ALLEN  | BLAKE                      |
| WARD   | BLAKE                      |
| JONES  | KING                       |
| MARTIN | BLAKE                      |
| BLAKE  | KING                       |
| CLARK  | KING                       |
| SCOTT  | JONES                      |
| KING   | 没有上级                         |
| TURNER | BLAKE                      |
| ADAMS  | SCOTT                      |
| JAMES  | BLAKE                      |
| FORD   | JONES                      |
| MILLER | CLARK                      |
+--------+----------------------------+

///////////////////////////15、列出受雇日期早于其直接上级的所有员工的编号,姓名,部门名称
select a.empno,a.ename,d.dname 
from
emp a
join
    dept d
on
    a.deptno=d.deptno
join emp b
on a.mgr=b.empno
where a.hiredate < b.hiredate
;
+-------+-------+------------+
| empno | ename | dname      |
+-------+-------+------------+
|  7782 | CLARK | ACCOUNTING |
|  7369 | SMITH | RESEARCH   |
|  7566 | JONES | RESEARCH   |
|  7499 | ALLEN | SALES      |
|  7521 | WARD  | SALES      |
|  7698 | BLAKE | SALES      |
+-------+-------+------------+

/////////////////////////////////////16、列出部门名称和这些部门的员工信息,同时列出那些没有员工的部门
select d.dname,e.empno,e.ename,e.job,e.mgr,e.hiredate,e.sal,e.comm,e.deptno
from emp e
right join
dept d
on  e.deptno=d.deptno
order by d.deptno;
+------------+-------+--------+-----------+------+------------+---------+---------+--------+
| dname      | empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+------------+-------+--------+-----------+------+------------+---------+---------+--------+
| ACCOUNTING |  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
| ACCOUNTING |  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
| ACCOUNTING |  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
| RESEARCH   |  7369 | SMITH  | CLERK     | 7902 | 1980-12-17 |  800.00 |    NULL |     20 |
| RESEARCH   |  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
| RESEARCH   |  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
| RESEARCH   |  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
| RESEARCH   |  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
| SALES      |  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
| SALES      |  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
| SALES      |  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
| SALES      |  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
| SALES      |  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
| SALES      |  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
| OPERATIONS |  NULL | NULL   | NULL      | NULL | NULL       |    NULL |    NULL |   NULL |
+------------+-------+--------+-----------+------+------------+---------+---------+--------+


///////////////////////17、列出至少有 5 个员工的所有部门
select d.dname,countd
from (select deptno,count(deptno) countd from emp group by deptno) e
right join dept d
on d.deptno=e.deptno
where countd>=5;
+----------+--------+
| dname    | countd |
+----------+--------+
| RESEARCH |      5 |
| SALES    |      6 |
+----------+--------+

select deptno,count(deptno) from emp  group by deptno ;
+--------+---------------+
| deptno | count(deptno) |
+--------+---------------+
|     10 |             3 |
|     20 |             5 |
|     30 |             6 |
+--------+---------------+


///////////////////////////////////18、列出薪金比"SMITH"多的所有员工信息.
select e.empno,e.ename,e.job,e.mgr,e.hiredate,e.sal,e.comm,e.deptno
from emp e
where sal>(select sal from emp where ename='smith');
+-------+--------+-----------+------+------------+---------+---------+--------+
| empno | ename  | job       | mgr  | hiredate   | sal     | comm    | deptno |
+-------+--------+-----------+------+------------+---------+---------+--------+
|  7499 | ALLEN  | SALESMAN  | 7698 | 1981-02-20 | 1600.00 |  300.00 |     30 |
|  7521 | WARD   | SALESMAN  | 7698 | 1981-02-22 | 1250.00 |  500.00 |     30 |
|  7566 | JONES  | MANAGER   | 7839 | 1981-04-02 | 2975.00 |    NULL |     20 |
|  7654 | MARTIN | SALESMAN  | 7698 | 1981-09-28 | 1250.00 | 1400.00 |     30 |
|  7698 | BLAKE  | MANAGER   | 7839 | 1981-05-01 | 2850.00 |    NULL |     30 |
|  7782 | CLARK  | MANAGER   | 7839 | 1981-06-09 | 2450.00 |    NULL |     10 |
|  7788 | SCOTT  | ANALYST   | 7566 | 1987-04-19 | 3000.00 |    NULL |     20 |
|  7839 | KING   | PRESIDENT | NULL | 1981-11-17 | 5000.00 |    NULL |     10 |
|  7844 | TURNER | SALESMAN  | 7698 | 1981-09-08 | 1500.00 |    0.00 |     30 |
|  7876 | ADAMS  | CLERK     | 7788 | 1987-05-23 | 1100.00 |    NULL |     20 |
|  7900 | JAMES  | CLERK     | 7698 | 1981-12-03 |  950.00 |    NULL |     30 |
|  7902 | FORD   | ANALYST   | 7566 | 1981-12-03 | 3000.00 |    NULL |     20 |
|  7934 | MILLER | CLERK     | 7782 | 1982-01-23 | 1300.00 |    NULL |     10 |
+-------+--------+-----------+------+------------+---------+---------+--------+


//////////19、列出所有"CLERK"(办事员)的姓名及其部门名称,部门的人数
select e.ename,d.dname,c.cc
from emp e
join (select deptno,count(deptno) cc from emp  group by deptno) c
on c.deptno=e.deptno
join dept d
on e.deptno=d.deptno
where e.job='clerk';
+--------+------------+----+
| ename  | dname      | cc |
+--------+------------+----+
| SMITH  | RESEARCH   |  5 |
| ADAMS  | RESEARCH   |  5 |
| JAMES  | SALES      |  6 |
| MILLER | ACCOUNTING |  3 |
+--------+------------+----+


////////////////////////////////r//////20、列出最低薪金大于 1500 的各种工作及从事此工作的全部雇员人数.
select e.job,count(e.empno)
from emp e
join dept d
on e.deptno=d.deptno
where e.sal>1500
group by e.job;
+-----------+----------------+
| job       | count(e.empno) |
+-----------+----------------+
| ANALYST   |              2 |
| MANAGER   |              3 |
| PRESIDENT |              1 |
| SALESMAN  |              1 |
+-----------+----------------+

////21、列出在部门"SALES"<销售部>工作的员工的姓名,假定不知道销售部的部门编号

直接查部门编号


//22、列出薪金高于公司平均薪金的所有员工,所在部门,上级领导,雇员的工资等级.
select e.ename,s.ename 'ld'
from emp e
left join emp s
on e.mgr=s.empno
where e.sal>(select avg(sal) avgsal from emp)
left join dept d on d.deptno=e.deptno;
left join salgrade g
on e.sal between g.losal and g.hisal





mysql> select e.ename,s.ename 'ld'
    -> from emp e
    -> left join emp s
    -> on e.mgr=s.empno
    -> where e.sal>(select avg(sal) avgsal from emp);
+-------+-------+
| ename | ld    |
+-------+-------+
| JONES | KING  |
| BLAKE | KING  |
| CLARK | KING  |
| SCOTT | JONES |
| KING  | NULL  |
| FORD  | JONES |
+-------+-------+







/////23、列出与"SCOTT"从事相同工作的所有员工及部门名称.
select e.ename,d.dname
from emp e
join dept d
on e.deptno=d.deptno
where e.job=(select job from emp where ename='scott') and e.ename!='scott';
+-------+----------+
| ename | dname    |
+-------+----------+
| FORD  | RESEARCH |
+-------+----------+

///////////////////24、列出薪金等于部门 30 中员工的薪金的其他员工的姓名和薪金.


用 in


///////////////////25、列出薪金高于部门 30 中员工的薪金的其他员工的姓名和薪金.
select e.ename,e.sal,d.dname 
from emp e
join dept d
on e.deptno = d.deptno
where e.sal>(select max(sal) from emp where deptno=30);
+-------+---------+------------+
| ename | sal     | dname      |
+-------+---------+------------+
| KING  | 5000.00 | ACCOUNTING |
| JONES | 2975.00 | RESEARCH   |
| SCOTT | 3000.00 | RESEARCH   |
| FORD  | 3000.00 | RESEARCH   |
+-------+---------+------------+



//26.列出在每个部门工作的员工数量,平均工资和平均服务期限
select count(e.ename),avg.(sal)
from emp e 
join dept d 
on e.deptno = d.deptno
group by e.deptno
;

select d.dname,count( e.ename),avg(e.sal)
from emp e 
join dept d 
on e.deptno=d.deptno
group by e.deptno
;
+------------+-----------------+-------------+
| dname      | count( e.ename) | avg(e.sal)  |
+------------+-----------------+-------------+
| ACCOUNTING |               3 | 2916.666667 |
| RESEARCH   |               5 | 2175.000000 |
| SALES      |               6 | 1566.666667 |
+------------+-----------------+-------------+





//27、列出所有员工的姓名、部门名称和工资。

select e.ename,d.dname,e.sal
from emp e 
join dept d
on e.deptno=d.deptno; 
+--------+------------+---------+
| ename  | dname      | sal     |
+--------+------------+---------+
| CLARK  | ACCOUNTING | 2450.00 |
| KING   | ACCOUNTING | 5000.00 |
| MILLER | ACCOUNTING | 1300.00 |
| SMITH  | RESEARCH   |  800.00 |
| JONES  | RESEARCH   | 2975.00 |
| SCOTT  | RESEARCH   | 3000.00 |
| ADAMS  | RESEARCH   | 1100.00 |
| FORD   | RESEARCH   | 3000.00 |
| ALLEN  | SALES      | 1600.00 |
| WARD   | SALES      | 1250.00 |
| MARTIN | SALES      | 1250.00 |
| BLAKE  | SALES      | 2850.00 |
| TURNER | SALES      | 1500.00 |
| JAMES  | SALES      |  950.00 |
+--------+------------+---------+


//28、列出所有部门的详细信息和人数
select d.deptno,d.dname,d.loc,count(e.ename)
from dept d 
left join emp e 
on d.deptno =e.deptno
group by d.deptno;
+--------+------------+----------+----------------+
| deptno | dname      | loc      | count(e.ename) |
+--------+------------+----------+----------------+
|     10 | ACCOUNTING | NEW YORK |              3 |
|     20 | RESEARCH   | DALLAS   |              5 |
|     30 | SALES      | CHICAGO  |              6 |
|     40 | OPERATIONS | BOSTON   |              0 |
+--------+------------+----------+----------------+


//29、列出各种工作的最低工资及从事此工作的雇员姓ming


select e.sal, e.ename,e.job
from emp e 
left join (select min(sal) minsal,job,deptno,ename from emp group by job) b
on e.job=b.job
where e.sal=b.minsal;


//30、列出各个部门的 MANAGER(领导)的最低薪金

select d.deptno,min(e.sal)
from emp e
join dept d 
on d.deptno = e.deptno 
where e.job='manager'
group by d.deptno
;
+--------+------------+
| deptno | min(e.sal) |
+--------+------------+
|     10 |    2450.00 |
|     20 |    2975.00 |
|     30 |    2850.00 |
+--------+------------+


////////////////////////////31、列出所有员工的年工资,按年薪从低到高排序
select ename,(sal+ifnull(comm,0))*12 income 
from emp
order by income asc;

+--------+----------+
| ename  | income   |
+--------+----------+
| SMITH  |  9600.00 |
| JAMES  | 11400.00 |
| ADAMS  | 13200.00 |
| MILLER | 15600.00 |
| TURNER | 18000.00 |
| WARD   | 21000.00 |
| ALLEN  | 22800.00 |
| CLARK  | 29400.00 |
| MARTIN | 31800.00 |
| BLAKE  | 34200.00 |
| JONES  | 35700.00 |
| FORD   | 36000.00 |
| SCOTT  | 36000.00 |
| KING   | 60000.00 |
+--------+----------+


//////////////////////////////////32、求出员工领导的薪水超过 3000 的员工名称与领导名称
select a.ename,b.ename
from emp a 
 join emp b 
on a.mgr =b.empno
where b.sal >3000;
+-------+-------+
| ename | ename |
+-------+-------+
| JONES | KING  |
| BLAKE | KING  |
| CLARK | KING  |
+-------+-------+


///////////33、求出部门名称中,带'S'字符的部门员工的工资合计、部门人数.
select d.dname,ifnull(sum(e.sal),''),count(e.deptno)
from emp e 
right join dept d
on d.deptno=e.deptno 
where d.dname like '%S%' 
group by d.deptno
order by count(e.deptno) asc
;
+------------+-----------------------+-----------------+
| dname      | ifnull(sum(e.sal),'') | count(e.deptno) |
+------------+-----------------------+-----------------+
| OPERATIONS |                       |               0 |
| RESEARCH   | 10875.00              |               5 |
| SALES      | 9400.00               |               6 |
+------------+-----------------------+-----------------+



```

