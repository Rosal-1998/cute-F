1. ����һ��ͼ�����ϵͳ���ݿ�

2. �������������������
	1. �û���
	2. ͼ���
	3. ���ļ�¼��

3. ��ѯ����ѧ��������
select name from user
4. ��ѯĳ��ѧ���Ľ��ļ�¼
select * from record where uid = 1
5. ��ѯĳ����ɽ�ı���(isbn = 101��
SELECT COUNT(*) AS �������� ,bname FROM books WHERE isbn =101 AND STATUS = 1 
6. ��ѯ��������鱾��ѧ��
SELECT name FROM user WHERE uid = (
SELECT COUNT(uid) AS uidtime FROM record GROUP BY uid ORDER BY uidtime DESC LIMIT 1)
7. ��ѯ������������ͼ�� 
SELECT bname FROM books WHERE bid = (
SELECT COUNT(bid) AS bidtime FROM record GROUP BY bid ORDER BY bidtime DESC LIMIT 1)
8. ��ѯ������������ͼ��Ŀ��
SELECT COUNT(*) AS �ɽ豾�� FROM books WHERE STATUS = 1 AND isbn = (
SELECT isbn FROM books WHERE bid = (SELECT COUNT(bid) AS bidtime FROM record GROUP BY bid ORDER BY bidtime DESC LIMIT 1) )
9. ��ѯһ���м����û�
SELECT COUNT(*) AS numofuser FROM user
10. ��ѯ��Υ�棨û��ʱ�仹��ģ��û�����