# Linux Setting ��� (Ubuntu EC2 ����)

## ���� �߰�

$ useradd -m (user_name)

/* 
������ �߰� �ϸ鼭 Ȩ ���͸��� ���� ����� �ش�.
(/home/(user_name))
*/

## ���� �����ϱ�
sudo su - (user_name)

## ���ο� ������ public key�� �̿��� ���� ���� �����ϰ� ������ֱ�
### ������ ����
$ sudo su - (user_name)
(������ �α��� �ؼ� Ȩ���͸����� �۾� ����)

### �������� key ���� ������ֱ�
$ mkdir .ssh
$ chmod 700 .ssh					(������ ���Ѽ��� ���ִ� �κ� / �ſ� �߿�)
$ touch .ssh/authorized_keys 		(key ���� ����)
$ chmod 600 .ssh/authorized_keys	(������ ���Ѽ��� / �ſ� �߿�)

### ubuntu�� ���ƿͼ� �۾�
$ exit 								(ubuntu �������� ���ƿ���)
$ vi .ssh/authorized_keys           (ubuntu�� key�� ����)
$ sudo su - (user_name)
$ vi .ssh/authorized_keys 			(���� �������� authorized_keys ���Ͽ� �ٿ��ֱ� �� ����)

### �۾��Ϸ� �� ubuntu�� ���� ppk�����̳� pem ���Ϸ� ������ �������� ����

## JDK ��ġ�ϱ�	
### �ڹ� Ȩ������ ���� .tar.gz jdk �ٿ�
### wget���� �ٷ� �޵� �޾Ƽ� ftp�� �ø���

$ tar zxvf jdk-jdk-7u7-linux-i586.tar.gz	
$ ln -s jdk1.7.0_07 java						(�̸��� �� �����ϴϱ� �ɺ��� ��ũ �ɾ��ֱ�)
$ vi /home/(user_name)/.profile					(��� �������ֱ� )

### ./profile ����								(���� ���������� ���/��ü���� ������ ��Ʈ�������� /etc/profile ����)
�� ���� �߰����ֱ�

export JAVA_HOME=/home/(user_name)/java										(������ �ɺ��� ��ũ �ɾ���)
export PATH="$JAVA_HOME/bin:$PATH"
export CLASSPATH=".:$JAVA_HOME/jre/lib/ext:$JAVA_HOME/lib/tools.jar"		(�̰� �����൵ �ɰŰ����� �� �𸣰���)

����

$ source /home/(user_name)/.profile				(�ٲ� profile ������ �ý��ۿ� ���� �����ֱ�)
$ java -version 								(�ڹ� ���õ� ������ ��µǸ� ��ġ ����)

## tomcat �����ϱ�
### tomcat Ȩ������ ���� .tar.gz tomcat �ٿ�
### wget���� �ٷ� �޵� �޾Ƽ� ftp�� �ø���

$ tar zxvf apache-tomcat-7.0.30.tar.gz			
$ ln -s apache-tomcat-7.0.30 tomcat				(�̸� �� ¯���ϱ�)
$ vi /home/(user_name)/.profile	

�Ʊ� �ڹ� �������ذ� �ؿ��� �߰�
export CATALINA_HOME=/home/(user_name)/tomcat	
export PATH=$PATH:$CATALINA_HOME/bin

$ cd /tomcat/bin
$ ./startup.sh									(���� ����)

$ ps -eaf | grep java							(���� java ���õ� ��� �������� ���� ���� �Ϸ�)

������������
http://(url):8080	
tomcat manager ������ ������ ����

##���� ��Ʈ ����
/tomcat/conf/server.xml ����
port="8080" ���� �Ǿ��ִºκ� ���ϴ� ��Ʈ�� ����

��Ʈ�� �ٲ��ٶ� �ظ��ϸ� 10000�� �̻����� ���

