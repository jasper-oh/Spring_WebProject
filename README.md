## Spring Project

### 💫 Context

    1. 작업 의의
    2. 사용 툴
    3. 수정, 보완 사항
    4. 향후 발전 계획

#### 1. 작업 의의

<br/>
<br/>

[JSP PROJECT](https://github.com/jasper-oh/JSP_WebProject) 를 진행하면서 Maintanece 와 Performance 를 향상 시킬 필요성을 느껴 개인 적으로 프로젝트를 진행

<br/>
<br/>

#### 2. 사용 툴

<br/>
<br/>

[![Java Badge](https://img.shields.io/badge/Java-007396?style=for-the-badge&logo=java&logoColor=black)](http://java.com/)
[![Eclipse Badge](https://img.shields.io/badge/Eclipse-2C2255?style=for-the-badge&logo=eclipse&logoColor=white)](http://eclipse.org/)
[![Spring Badge](https://img.shields.io/badge/Spring_MyBatis-04ff00?style=for-the-badge&logo=spring&logoColor=white)](http://spring.io/)
[![Tomcat Badge](https://img.shields.io/badge/Apache_Tomcat-CB9F18?style=for-the-badge&logo=Apache&logoColor=white)](http://spring.io/)

<br/>
<br/>

### 3. 수정, 보완 사항

<br/>
<br/>

📌 기존에 MVC model 을 이용하여

    Model -> Dao

    View -> JSP

    Controller -> Controller

사용하여 작업을 했었습니다. 하지만 작업을 완료하고, 팀원들과 리뷰를 한 결과 여러 에러사항이 발견되었습니다. 그중에 몇가지를 열거하자면,

1️⃣ 결제 방식에 있어서 get 방식을 사용해서 Modeling 이 진행되어 보안상에 여러 문제가 발견되었습니다.<br/>
2️⃣ 코드량이 많고, db 와 연결되는 부분에서 많은 데이터를 관리 할 경우에 퍼포먼스가 느리게 발현되는 현상을 발견하였습니다.

위의 사항을 해결할 방법을 찾고 싶어 여러 리서치를 통해 Spring MVC 와 MyBatis 를 사용하게 된다면 퍼포먼스 향상 및 유지보수에도 용이 할것 같아 개인적으로 작업을 진행 하게 되었습니다.

보편적으로 DAO 부분과 Controller 부분을 수정해 나갈 것이며, 이 부분을 수정해 나감과 동시에 보안적인 측면에서도 향상 시켜 나갈 예정입니다.

#### 4. 향후 발전 계획

실제로 서비스를 배포함에 따라 트래픽 관리를 진행할 예정입니다.

기존의 작업 방식과는 다르게 Spring MVC 로 개선하여 유지보수를 원활하게 작업할 수 있도록 만들 예정이기 때문에 이슈 발생시 향후 좀더 발전된 웹을 만들 수 있을거라 예상됩니다.

#### 5. 기초 Setting 사항

<br/>
<br/>

```XML
    <!-- Pom.xml -->
    <!-- JDBC -->
    <dependency>
    	<groupId>org.springframework<groupId>
    	<artifactId>spring-jdbc</artifactId>
    	<version>4.1.4.RELEASE</version>
    </dependency>

	<!-- myBatis -->
	<dependency>
		<groupId>org.mybatis</groupId>
		<artifactId>mybatis</artifactId>
		<version>3.2.8</version>
	</dependency>
	<dependency>
	    <groupId>org.mybatis</groupId>
	    <artifactId>mybatis-spring</artifactId>
	    <version>1.2.2</version>
	</dependency>

    <!-- servlet-context.xml -->
    <beans:bean name="dataSource" class="org.springframework.jdbc.datasource.DriverManagerDataSource">
		<beans:property name="driverClassName" value="com.mysql.cj.jdbc.Driver"/>
		<beans:property name="url" value="jdbc:mysql://localhost:3306/useraddress?serverTimezone=Asia/Seoul&amp;characterEncoding=utf8&amp;useSSL=false"/>
		<beans:property name="username" value="root"/>
		<beans:property name="password" value="qwer1234"/>
	</beans:bean>
	<beans:bean name="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
		<beans:property name="dataSource" ref="dataSource"/>
		<beans:property name="mapperLocations" value="classpath:com/*Personal Root*/*.xml" />
	</beans:bean>
	<beans:bean name="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
		<beans:constructor-arg index="0" ref="sqlSessionFactory" />
	</beans:bean>



```
