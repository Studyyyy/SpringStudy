# 2016.06.05  Spring Study -1

1. JPA 란 ? 
	- java persistance api
	- JPA는 여러 ORM 전문가가 참여한 EJB 3.0 스펙 작업에서 기존 EJB ORM이던 Entity Bean을 JPA라고 바꾸고 JavaSE, JavaEE를 위한 영속성(persistence) 관리와 ORM을 위한 표준 기술이다. JPA는 ORM 표준 기술로 Hibernate, OpenJPA, EclipseLink, TopLink Essentials과 같은 구현체가 있고 이에 표준 인터페이스가 바로 JPA이다.
	-  ORM(Object Relational Mapping)이란 RDB 테이블을 객체지향적으로 사용하기 위한 기술이다.
	-  참조 링크 : [JPA란 무엇인가?](http://blog.woniper.net/255)

2. Java의 Reflection 기능이란?
	- 참조 링크 : [Java 리플렉션(Reflection)](http://hiddenviewer.tistory.com/114)
	- 리플렉션은 구체적인 클래스 타입을 알지 못해도, 컴파일된 바이트 코드를 통해 역으로 클래스에 대한 정보를 알아내어 클래스를 사용할 수 있는 기법.
	- 리플렉션을 통해 얻을 수 있는 정보는 아래와 같다.
	-- Class Name
    -- Class Modifier ( public, private, syncronized 등 )
    -- Package Info
    -- Implemented Interface
    -- Constructors
    -- Methods
    -- Fields
    -- Annotations

3. DI ( Dependency Injection )
- Dependency 란 ?
	- 한 클래스가 다른 클래스의 메서드를 실행할때 이를 ‘의존’한다 라고 표현.
	- 의존은 변경에 의해 영향을 받는 관계를 의미한다. MemberDao의 insert() 메서드의 이름을 insertMember() 라고 변형하면, 이 메서드를 사용하는 MemverRegisterService 클래스의 소스코드도 함께 변경된다. 이렇게 변경에 따른 영향이 전파되는 관계를 ‘의존’한다라고 표현

- 의존하는 대상을 구현하는 방법에는 세가지? 가 있는 것 같음

	(1) 객체를 직접 생성하는 방법
    	public class MemberRegisterService {
		private MemberDao memberDao = new MemberDao();
		}

	이렇게 되면 MemberRegisterService 객체를 생성하는 순간에 MemberDao 객체도 생성된다.  -> 만들기는 쉬우나 유지보수 관점에서 문제가 된다.

	(2) DI
	생성자를 통해서 의존하고 있는 객체를 전달받는다.
		public class MemberRegisterService {
			private MemberDao memberDao;

			public MemberRegisterService( MemberDao memberDao ) {
				this.memberDao = memberDao;
			}
		}
	DI pattern 이라고 한다.
   
	(3) 서비스 로케이터


4.pojo ( Plain Old Java Object )
- java 본연의 프로그래밍만 하자
- 그럴듯한 이름으로.. 프로그래머들이 좋아함


5.STS란?
- Spring Tool Suite 
- 이클립스에서 스프링을 위해.. 편하게 나온 프레임워크 인가보다
