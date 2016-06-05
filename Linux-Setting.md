# Linux Setting 방법 (Ubuntu EC2 기준)

## 유저 추가

$ useradd -m (user_name)

/* 
유저를 추가 하면서 홈 디렉터리를 같이 만들어 준다.
(/home/(user_name))
*/

## 유저 접속하기
sudo su - (user_name)

## 새로운 유저에 public key를 이용한 원격 접속 가능하게 만들어주기
### 유저로 접속
$ sudo su - (user_name)
(유저로 로그인 해서 홈디렉터리에서 작업 시작)

### 유저에서 key 파일 만들어주기
$ mkdir .ssh
$ chmod 700 .ssh					(폴더의 권한설정 해주는 부분 / 매우 중요)
$ touch .ssh/authorized_keys 		(key 파일 생성)
$ chmod 600 .ssh/authorized_keys	(파일의 권한설정 / 매우 중요)

### ubuntu로 돌아와서 작업
$ exit 								(ubuntu 계정으로 돌아오기)
$ vi .ssh/authorized_keys           (ubuntu의 key를 복사)
$ sudo su - (user_name)
$ vi .ssh/authorized_keys 			(유저 계정에서 authorized_keys 파일에 붙여넣기 후 저장)

### 작업완료 후 ubuntu와 같은 ppk파일이나 pem 파일로 리눅스 원격접속 가능

## JDK 설치하기	
### 자바 홈페이지 가서 .tar.gz jdk 다운
### wget으로 바로 받든 받아서 ftp로 올리든

$ tar zxvf jdk-jdk-7u7-linux-i586.tar.gz	
$ ln -s jdk1.7.0_07 java						(이름이 길어서 불편하니까 심볼릭 링크 걸어주기)
$ vi /home/(user_name)/.profile					(경로 설정해주기 )

### ./profile 설정								(유저 계정에서만 허용/전체에서 쓰려면 루트권한으로 /etc/profile 수정)
맨 위에 추가해주기

export JAVA_HOME=/home/(user_name)/java										(본인이 심볼릭 링크 걸어논곳)
export PATH="$JAVA_HOME/bin:$PATH"
export CLASSPATH=".:$JAVA_HOME/jre/lib/ext:$JAVA_HOME/lib/tools.jar"		(이건 안해줘도 될거같은데 잘 모르겠음)

저장

$ source /home/(user_name)/.profile				(바뀐 profile 파일은 시스템에 적용 시켜주기)
$ java -version 								(자바 관련된 뭔가가 출력되면 설치 성공)

## tomcat 설정하기
### tomcat 홈페이지 가서 .tar.gz tomcat 다운
### wget으로 바로 받든 받아서 ftp로 올리든

$ tar zxvf apache-tomcat-7.0.30.tar.gz			
$ ln -s apache-tomcat-7.0.30 tomcat				(이름 길어서 짱나니까)
$ vi /home/(user_name)/.profile	

아까 자바 설정해준거 밑에다 추가
export CATALINA_HOME=/home/(user_name)/tomcat	
export PATH=$PATH:$CATALINA_HOME/bin

$ cd /tomcat/bin
$ ./startup.sh									(톰켓 실행)

$ ps -eaf | grep java							(뭔가 java 관련된 긴게 떠있으면 톰켓 실행 완료)

웹브라우저에서
http://(url):8080	
tomcat manager 페이지 나오면 성공

##톰켓 포트 설정
/tomcat/conf/server.xml 수정
port="8080" 으로 되어있는부분 원하는 포트로 설정

포트를 바꿔줄땐 왠만하면 10000번 이상으로 사용

