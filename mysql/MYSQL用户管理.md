1.�û���¼
```
#��ʽ:mysql -h������ַ -u�û��� -p�û�����
mysql -h 110.110.110.110 -u root -p 123
#���ؿ���ֱ��mysql �Curoot -p
```
2.�û��˳�
'exit/quit'
3.����û�
mysql.user��������û��ĵ�¼��Ϣ
ֱ�������Ȩ��
insert into mysql.user (host,user,password) values('%','walden',PASSWORD('walden'));

��Ӳ���Ȩ
grant select on ���ݿ�.* to '�û���'@'��¼����' identified by '����'

�ġ�        �û�Ȩ��
���Ȩ��
grant Ȩ�� on ���ݿ�.�� to '�û���'@'��¼����';

Ȩ�ޣ� select ,update,delete,insert(������)��create,alert,drop(��ṹ)��references(���)��create temporary tables(������ʱ��)��index(��������)��create view,show view(��ͼ)��create routine,alert routine,execute(�洢����)��all,all privileges(����Ȩ��)

���ݿ⣺���ݿ�������*(�������ݿ�)

����������*(ĳ���ݿ������б�)

����:����������%(�κ���������)

����grant selec,insert,update,delete on *.* to 'walden'@'%';

����Ȩ��
revoke Ȩ�� on ���ݿ�.�� from '�û���'@'��¼����';//��to��Ϊfrom

����revoke all on *.* from ��walden��@��%��;

�鿴Ȩ��
show grants;//�Լ�

show grants for dba@localhost;//ָ���û�ָ��host

�塢        ɾ���û�
delete from mysql.user where user='' and host='';

����        �޸�����
update mysql.user set password=PASSWORD('111111') where user='root';

�ߡ�        �һ�����
�ر�mysql����
killall -TERM mysqld

�޸������ļ�
vi /etc/my.cnf

��[mysqld]�Ķ��м���һ�䣺skip-grant-tables

���磺

[mysqld]

datadir=/var/lib/mysql

socket=/var/lib/mysql/mysql.sock

skip-grant-tables

����mysqld
service mysqld restart

��¼
mysql -uroot -p

�޸�����
update mysql.user set password=PASSWORD('111111') where user='root';

flush privileges;//ˢ��Ȩ��

�޸������ļ�
 vi /etc/my.cnf

ȥ��֮ǰ�ĸĶ�

��������
����Զ���û�
�ˡ�        Զ���û�
��     ������ָ��ip��¼hostΪip�����뿴 ���Ȩ��

��     ������Զ��ip��¼hostΪ%�����뿴 ���Ȩ��

Զ�̷���
mysql -h110.110.110.110 -uroot -p123;//ָ��hΪip�����뿴 �û���¼

 

 

һЩ��׼ʵ����

1. mysql.user��ʵ����һ����˵��Host�ֶζ�ʹ��ip�����ƣ������ǻ��������������ɱ䣬�����ر��ף�

select Host, User from user;

| 172.17.% | dev | 
| 172.17.0.% | export | 
| 172.17.0.20 | demo | 
| 172.28.0.% | dev | 
| 192.168.% | dev | 
| 110.111.126.% | demo | 
| 110.111.126.103 | helper          | 
| 110.111.127.% | webnav    | 
| localhost | backup | 
| localhost | backupdata | 
| localhost | root | 
+-----------------+-----------------+

2. ��Ȩʵ����show grants for 'helper'@'110.111.127.%'

+--------------------------------------------------------------------------------------------------------------------------------------------------+
| GRANT USAGE ON *.* TO 'helper'@'110.111.127.%' IDENTIFIED BY PASSWORD 'xxxxxxxxxxxxxxxxx' WITH MAX_USER_CONNECTIONS 200 | 
| GRANT ALL PRIVILEGES ON `helper_online`.* TO 'helper'@'110.111.127.%' | 
+--------------------------------------------------------------------------------------------------------------------------------------------------+