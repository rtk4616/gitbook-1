mysql��װĿ¼�µ�my-default.ini�޸ĳ�����
```
basedir ="D:\\engine\\mysql-5.7.16-winx64\\"
datadir ="D:\\engine\\mysql-5.7.16-winx64\\data"
port = 3306
```
ʹ�ù���ԱȨ�޴�dos���ڣ����뵽Ŀ¼[�������]binĿ¼�£�ִ������������ʼ�����ݿ�
```dos
mysqld --initialize --user=mysql --console
```
��װwindows����
```dos
mysqld --install MySQL
```
�����װʧ�������⣬����ʹ�����������ɾ������
```dos
mysqld --remove MySQL
```
�����ʼ����ʱ��û�м�סroot�ĳ�ʼ�����룬ʹ������������¼ 
```dos
#�ر�mysql����
net start mysql
#ʹ�ò����ģʽ����������
mysqld --skip-grant-tables
```
ʹ�����������޸�root����
```sql
use mysql
update user set authentication_string=password('new_password') where user='root' and Host = 'localhost';
#����֮�����޸�����
ALTER USER 'root'@'localhost' IDENTIFIED BY 'new_password';
```