# MySQL34道练习题

1. 取得每个部门最高薪水的人员名称

   ```mysql
   select e.ename,d.*
   from emp e
   right join (select deptno,max(sal) as maxsal 
               from emp 
               GROUP BY deptno) d
on d.deptno=e.deptno and d.maxsal=e.sal;
   ```
   
2. 哪些人的薪水在部门的平均薪水之上

   ```mysql
   select e.ename,e.sal 
   from emp e 
   right join (select deptno,avg(sal) avgsal 
               from emp 
               group by deptno) t1 
   on e.deptno=t1.deptno and e.sal>t1.avgsal;
   ```

3. 取得部门中（所有人的）平均的薪水等级

   ```mysql
   select t2.deptno,avg(grade) 
   from (select t1.deptno,t1.sal,s.grade 
         from salgrade s 
         join (select deptno,sal 
               from emp) t1 
         on t1.sal 
         between s.losal and s.hisal) t2 
   group by t2.deptno 
   order by t2.deptno;
   ```

4. 不用分组函数（Max），取得最高薪水

   ```mysql
   select sal 
   from emp 
   order by sal desc 
   limit 0,1;
   ```

5. 取得平均薪水最高的部门的部门编号

   ```mysql
   select deptno 
   from emp 
   group by deptno 
   order by avg(sal) desc 
   limit 0,1;
   ```

6. 取得平均薪水最高的部门的部门名称

   ```mysql
   select d.dname 
   from dept d 
   right join (select deptno 
               from emp 
               group by deptno 
               order by avg(sal) desc 
               limit 0,1) t1 
   on d.deptno=t1.deptno;
   ```

7. 求平均薪水的等级最低的部门的部门名称

   ```mysql
   select d.dname 
   from dept d 
   right join (select deptno 
               from emp 
               group by deptno 
               order by avg(sal) asc 
               limit 0,1) t1 
   on d.deptno=t1.deptno;
   ```

8. 取得比普通员工(员工代码没有在mgr字段上出现的)的最高薪水还要高的领导人姓名

   ```mysql
   select t2.ename 
   from (select * 
         from emp 
         where empno 
         in (select mgr 
             from emp 
             where mgr 
             is not null)) t2 
   join (select * 
         from emp 
         where empno 
         not in (select mgr 
                 from emp 
                 where mgr 
                 is not null) 
         order by sal desc 
         limit 0,1) t1 
   on t2.sal>t1.sal;
   ```

9. 取得薪水最高的前五名员工

   ```mysql
   select * 
   from emp 
   order by sal desc 
   limit 0,5;
   ```

10. 取得薪水最高的第六到第十名员工

    ```mysql
    select * 
    from emp 
    order by sal desc 
    limit 5,5;
    ```

11. 取得最后入职的5名员工

    ```mysql
    select * 
    from emp 
    order by hiredate desc 
    limit 0,5;
    ```

12. 取得每个薪水等级有多少员工

    ```mysql
    select s.grade,count(t1.sgrade) 
    from salgrade s 
    left join (select e.*,s.grade sgrade 
               from emp e 
               join salgrade s 
               on e.sal between s.losal and s.hisal) t1 
    on s.grade=t1.sgrade 
    group by s.grade; 
    ```

13. 列出所有员工及领导的姓名

    ```mysql
    select e2.ename '员工', e1.ename '领导' 
    from emp e1 
    left join emp e2 
    on e1.empno=e2.mgr;
    ```

14. 列出受雇日期早于其直接上级的所有员工的编号,姓名,部门名称

    ```mysql
    select t4.empno,t4.ename,d.dname 
    from dept d 
    right join (select e.empno,e.ename,e.deptno 
                from emp e 
                right join (select t2.员工 
                            from (select t1.员工, t1.员工入职日期, e.ename '领导',e.hiredate '领导入职日期' 
                                  from(select ename '员工',hiredate '员工入职日期',mgr 
                                       from emp) t1 
                                  left join emp e 
                                  on t1.mgr=e.empno) t2 
                            where t2.员工入职日期<t2.领导入职日期) t3 
                on e.ename=t3.员工) t4 
    on d.deptno=t4.deptno;
    ```

15. 列出部门名称和这些部门的员工信息,同时列出那些没有员工的部门

    ```mysql
    
    ```

16. 列出至少有5个员工的所有部门

    ```mysql
    
    ```

17. 列出薪金比"SMITH"多的所有员工信息

    ```mysql
    
    ```

18. 列出所有"CLERK"(办事员)的姓名及其部门名称,部门的人数

    ```mysql
    
    ```

19. 列出最低薪金大于1500的各种工作及从事此工作的全部雇员人数

    ```mysql
    
    ```

20. 列出在部门"SALES"<销售部>工作的员工的姓名,假定不知道销售部的部门编号

    ```mysql
    
    ```

21. 列出薪金高于公司平均薪金的所有员工,所在部门,上级领导,雇员的工资等级

    ```mysql
    
    ```

22. 列出与"SCOTT"从事相同工作的所有员工及部门名称

    ```mysql
    
    ```

23. 列出薪金等于部门30中员工的薪金的其他员工的姓名和薪金

    ```mysql
    
    ```

24. 列出薪金高于在部门30工作的所有员工的薪金的员工姓名和薪金.部门名称

    ```mysql
    
    ```

25. 列出在每个部门工作的员工数量,平均工资和平均服务期限

    ```mysql
    
    ```

26. 列出所有员工的姓名、部门名称和工资

    ```mysql
    
    ```

27. 列出所有部门的详细信息和人数

    ```mysql
    
    ```

28. 列出各种工作的最低工资及从事此工作的雇员姓名

    ```mysql
    
    ```

29. 列出各个部门的MANAGER(领导)的最低薪金

    ```mysql
    
    ```

30. 列出所有员工的年工资,按年薪从低到高排序

    ```mysql
    
    ```

31. 求出员工领导的薪水超过3000的员工名称与领导名称

    ```mysql
    
    ```

32. 求出部门名称中,带'S'字符的部门员工的工资合计、部门人数

    ```mysql
    
    ```

33. 给任职日期超过30年的员工加薪10%

    ```mysql
    
    ```
    
34. 创建视图查询学号，姓名，年龄及所选课号

    ```mysql
    create view v1 as select s.sno,s.sname,s.sage,sc.cno from student s,sc where s.sno=sc.sno;
    ```

35. 创建视图查询学号，姓名，年龄及所选课程名称

    ```mysql
    create view v2 as select s.sno,s.sname,s.sage,c.cname from student s,sc,course c where s.sno=sc.sno and c.cno=sc.cno;
    ```

36. 创建视图显示没有选修课程的学生信息

    ```mysql
    create view v3 as select s.* from student s where s.sno not in (select distinct sno from sc where cno is not null);
    ```

37. 创建视图查询选1号课程学生信息

    ```mysql
    create view v4 as select s.* from student s,sc where s.sno=sc.sno and sc.cno=01;
    ```

38. 创建视图查询选修‘C#’课程的学生信息

    ```mysql
    create view v5 as select s.* from student s,sc,course c where s.sno=sc.sno and sc.cno=c.cno and c.cname='C#';
    ```