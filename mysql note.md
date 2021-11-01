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
