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




INT 				    -- 整数
DECIMAL(m,n)		-- 浮点数，m表示一共几位数，n表示小数部分有几位
VARCHAR(10)			-- 字符串 10表示字符串最多10位
BLOB				    -- (Binary Large Object)图片 视频 档案……
DATE				    -- 'YYYY-MM-DD' 日期
TIMESTAMP		  	-- 'YYYY-MM-DD HH:MM:SS' 时间戳
```
