```mysql
CREATE DATABASE `sql_lesson`;
SHOW DATABASES;
#DROP DATABASE `sql_lesson`; -- 删除数据库
USE `sql_lesson`;

CREATE TABLE student(
	`student_id` INT PRIMARY KEY,
	`name` VARCHAR(20),
	`major` VARCHAR(20)
); -- 新建表格

DESCRIBE `student`;

ALTER TABLE `student` ADD gpa DECIMAL(3,2); -- 增加列
DESCRIBE `student`;

ALTER TABLE `student` DROP COLUMN gpa; -- 删除列
DESCRIBE `student`;

INSERT INTO `student` VALUES(3,'孙悦','歌手'); -- 插入数据
INSERT INTO `student`(`name`,`major`,`student_id`) VALUES('宋江',NULL,4); -- 插入数据并指定属性顺序
SELECT * FROM `student`; -- 搜寻指定表格的全部资料 *表示全部的意思

-- constraints 限制 约束
CREATE TABLE `stars` (
	`star_id` INT PRIMARY KEY AUTO_INCREMENT, -- 表示该属性每次自动+1
	`name` VARCHAR(20), #NOT NULL,-- 表示该属性不能为空
    `major_0` VARCHAR(20), #UNIQUE, -- 表示该属性的值不能重复
    `major_1` VARCHAR(20) DEFAULT '讲解员' -- 表示指定该属性的默认值
);
INSERT INTO `stars` (`name`,`major_0`) VALUES('孙悟空','弼马温');
INSERT INTO `stars` (`name`,`major_0`) VALUES('唐僧','话痨');
SELECT * FROM `stars`;
DROP TABLE `stars`;

-- 修改、删除资料
SET SQL_SAFE_UPDATES = 0;
ALTER TABLE `student` ADD score  INT DEFAULT 50;
ALTER TABLE `student` DROP COLUMN score;
INSERT INTO `student`(`score`) VALUES(50);
SELECT * FROM `student`;

UPDATE `student` -- 修改指定的表格
-- SET `major` = '大忽悠' -- 修改指定属性的值
-- SET `score` = 89
SET `name` = '齐宣王', `score` = 200
-- WHERE `major` = '相声'; -- 如果满足指定的条件
-- WHERE `student_id` = 4;
-- WHERE `student_id` = 2 OR `student_id` = 4;
WHERE `student_id` = 4;

DELETE FROM `student` -- 删除指定的资料
WHERE `student_id` = 2;
SELECT * FROM `student`;
DELETE FROM `student`; -- 删除表格内的全部资料

-- 取得资料
SELECT `name`,`major` FROM `student`;
SELECT * FROM `student` ORDER BY `score`; -- 按照指定的属性排序显示
SELECT * FROM `student` ORDER BY `score` DESC; -- 倒序显示
SELECT * FROM `student` ORDER BY `score`,`student_id`;
SELECT * FROM `student` LIMIT 2; -- 限制显示的行数
SELECT * FROM `student`
WHERE `major` IN('艺人','大忽悠');


-- 创建公司数据库表格

create table `employee`(
`emp_id` int primary key,
`name` varchar(20),
`birth_date` date,
`sex` varchar(1),
`salary` int,
`branch_id` int,
`sup_id` int
);

create table `branch`(
`branch_id` int primary key,
`branch_name` varchar(20),
`manager_id` int,
foreign key (`manager_id`) references `employee`(`emp_id`) on delete set null
);

alter table `employee`	-- 在 employee 表格中
add foreign key(`branch_id`)	-- 新增 foreign key 属性到branch_id
references `branch`(`branch_id`)	-- 对应到 branch 表格的 branch_id 属性
on delete set null;

alter table `employee`
add foreign key(`sup_id`)
references `employee`(`emp_id`)
on delete set null;

create table `client`(
`client_id` int primary key,
`client_name` varchar(20),
`phone` varchar(20)
);

create table `work_with`(
`emp_id` int,
`client_id` int,
`total_sales` int,
primary key(`emp_id`, `client_id`),
foreign key (`emp_id`) references `employee`(`emp_id`) on delete cascade,
foreign key (`client_id`) references `client`(`client_id`) on delete cascade
-- on delete set NULL 意思是：如果删除数据，那么对应的属性就设置为NULL
);

-- 新增表格数据

insert into `employee` values(206,'黄盖'，'0209-10-08','M',50000,1,NULL); -- 此时执行会报错，因为branch表格中的branch_id还没有创建
-- 先新增 branch 的资料
insert into `branch` values(1,'研发',NULL);
insert into `branch` values(2,'行政',NULL);
insert into `branch` values(3,'资讯',NULL);
insert into `branch` values(4,'偷懒',NULL);

-- 再新增 employee 的资料
insert into `employee` values(206,'杨坚','0541-07-21','M',50000,1,NULL);
insert into `employee` values(207,'李渊','0566-04-07','M',29000,2,206);
insert into `employee` values(208,'李玄霸','0599-10-21','M',35000,3,206);
insert into `employee` values(209,'李世民','0598-01-23','M',39000,3,207);
insert into `employee` values(210,'李隆基','0685-09-08','M',84000,1,207);

-- 修改资料
update `branch`
set `manager_id` = 208
where `branch_id` = 3;

-- 新增 client 的资料
insert into `client` values(400,'翟让','25435467834');
insert into `client` values(401,'单雄信','27097096832');
insert into `client` values(402,'徐世勋','15487649826');
insert into `client` values(403,'裴仁基','21433783436');
insert into `client` values(404,'秦叔宝','37855467834');

-- 新增 work_with 资料
insert into `work_with` values(206,400,'70000');
insert into `work_with` values(207,401,'24000');
insert into `work_with` values(208,402,'9800');
insert into `work_with` values(208,403,'24000');
insert into `work_with` values(210,404,'87580');

-- 取得表格资料
select * from `employee` order by `salary`;
select * from `client`;
select * from `employee` order by `salary` desc limit 3;
select `name` from `employee`;

-- 聚合函数 aggregate function
-- 取得员工人数
select count(*) from `employee`;

-- 取得出生于0600-01-01之后的男性员工人数
select count(*) from `employee`
where `birth_date` > '0600-01-01' and `sex` = 'M';

-- 取得员工的平均薪水
select avg(`salary`) from `employee`;

-- 取得所有员工薪水的总和
select sum(`salary`) from `employee`;

-- 取得薪水最高的员工
select max(`salary`) from `employee`;

-- 取得薪水最低的员工
select min(`salary`) from `employee`;

-- 万用字元 wildcards %代表多个字元，_代表一个字元
-- 取得电话号码结尾是34的客户
select * from `client`
where `phone` like '%34';

-- 取得姓裴的客户
select * from `client`
where `client_name` like '裴__';

-- 取得生日在7月的员工
select * from `employee`
where `birth_date` like '____-07-__';

-- 联集 union 把两个搜寻的结果联接起来
-- 员工名字union客户名字
select `name` from `employee` -- 使用 union 的时候各表格提取的属性数量和数据类型必须一致
union
select `client_name` from `client`
union
select `branch_name` from `branch`;

-- 员工id + 员工名字 union 客户id + 客户名字
select `emp_id` as `total_id`,`name` as `total_name` from `employee` -- 可以给属性改名称
union
select `client_id`,`client_name` from `client`;

-- 员工薪水union销售金额
select `salary` from `employee`
union
select `total_sales` from `work_with`;

-- 连接 join 可以把两个表格连接在一起
-- 取得所有部门经理的名字
select `emp_id`,`name`,`branch_name` from `employee`
left join `branch` -- left 表示无论如何都回传前边的表格，而后边的表格如果不符合条件就不回传，right 表示相反的意思
on `employee`.`emp_id` = `branch`.`manager_id`; -- 防止出现相同属性名称产生的混乱，可以在属性名称前添加表格名称

-- 子查询 subquery 从一个查询结果中查找特定的结果
-- 找出研发部门的经理名字
select `name` from `employee`
where `emp_id` = (
	select `manager_id` from `branch`
    where `branch_name` = '研发'
);

-- 找出对单一客户销售金额超过50000的员工名字
select `name` from `employee`
where `emp_id` in( -- 如果返回的结果不止一个，就要用 in，而不是 =
	select `emp_id` from `work_with`
    where `total_sales` > 50000
);

/*-----------------------------------------------------------------*/
INT 				-- 整数
DECIMAL(m,n)		-- 浮点数，m表示一共几位数，n表示小数部分有几位
VARCHAR(10)			-- 字符串 10表示字符串最多10位
BLOB				-- (Binary Large Object)图片 视频 档案……
DATE				-- 'YYYY-MM-DD' 日期
TIMESTAMP			-- 'YYYY-MM-DD HH:MM:SS' 时间戳

>	-- 大于
<	-- 小于
>=	-- 大于等于
<=	-- 小于等于
<>	-- 不等于
```
