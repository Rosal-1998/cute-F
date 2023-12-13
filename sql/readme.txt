1. 创建一个图书借阅系统数据库

2. 创建三个表，并添加数据
	1. 用户表
	2. 图书表
	3. 借阅记录表

3. 查询所有学生的姓名
select name from user
4. 查询某个学生的借阅记录
select * from record where uid = 1
5. 查询某本书可借的本数(isbn = 101）
SELECT COUNT(*) AS ‘本数’ ,bname FROM books WHERE isbn =101 AND STATUS = 1 
6. 查询借阅最多书本的学生
SELECT u.NAME,u.uid   
FROM user u  
WHERE u.uid IN (  
    SELECT r.uid  
    FROM record r  
    GROUP BY r.uid  
    ORDER BY COUNT(r.uid) DESC  
) LIMIT 1

7. 查询被借最多次数的图书 
SELECT b.bname,b.bid,bidtime
FROM books b
WHERE b.bid IN (
	SELECT COUNT(r.bid) AS bidtime 
	FROM record r
	GROUP BY r.bid 
	ORDER BY bidtime DESC 
)	LIMIT 1
8. 查询被借最多次数的图书的库存
SELECT COUNT(*) AS 可借本数 FROM books WHERE STATUS = 1 AND isbn = (
SELECT isbn FROM books WHERE bid = (SELECT COUNT(bid) AS bidtime FROM record GROUP BY bid ORDER BY bidtime DESC LIMIT 1) )
9. 查询一共有几个用户
SELECT COUNT(*) AS numofuser FROM user
10. 查询有违规（没按时间还书的）用户姓名