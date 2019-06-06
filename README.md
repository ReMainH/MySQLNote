# MySQLNote
复制表结构:
create table xs1 like xs;
包括内容复制:craete table xs2(select * from xs);
# MySQLNote
复制表结构:
# S2(2)
create table xs1 like xs;
包括内容复制:craete table xs2(select * from xs);
# S2(3)
alter table Departments modify DempartmentsID int not null;
alter table Departments add column 备注 char(6);
alter table Departments engine = MyISAM

# S3(1)
use YGGL;
insert into Departments
  values('v1', 'v2', 'v3', int, etc...); 
  
或者使用set
insert into Departments
  set 学号='',XX='',etc....
# S3(2)
create table Departments2 (select * from Department);

update Departments2
  set 部门名称 = ‘后勤部’, 备注 = '三级单位'
  where 部门号 = ‘3’;
  
update Salary1
  set 收入 = 收入 + 500, 支出 = 支出 - 20.19;
  
update Salary1
  set 收入 = 2019
  where 编号 = 020018;
  
delete from Departments1
  where 部门名称 = ‘财务部’,'市场部';
select * from Departments1;

truncate table Salary1;  #清空表

# S4(1)
select * from employees join salary on Employees.编号 = Salary.编号
  where 收入 < 2500;
  
select * from Employees
  where 编号 in(
  select 编号 from Salary where 收入 < 2500;
  
select 姓名 from Employees
  where 出生日期 < all (
    select 出生年月 from Employees where 编号 in (
      select 编号 from Departments where 部门名称 = '市场部'));
  
selet 姓名 from Employees where 编号 in (
  select 编号 form Departments where 部门号 = '研发部')
  and
  编号 in (select 编号 from Salary where 收入 > all 
          (select 收入 from Salary where 编号 in 
          (select 编号 from Employees where 编号 =
          (select 编号 from Departments where 部门号 = '市场部'))));
