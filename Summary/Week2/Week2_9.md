# Maven

# 9-1. Maven이란?
### CoC(convention over Configuration)
- 일종의 관습
- 소스파일,컴파일된 파일 등이 특정 위치에 있어야함(미리 정해짐)

### Maven
- 의존성 라이브러리 관리
- 설정 파일에 몇 줄 적어서 다운받지않아도 라이브러리 사용가능

- pom.xml에 작성
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/maven-v4_0_0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>kr.or.connect</groupId>
    <artifactId>examples</artifactId>
    <packaging>jar</packaging>
    <version>1.0-SNAPSHOT</version>
    <name>mysample</name>
    <url>http://maven.apache.org</url>
    <dependencies>
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>3.8.1</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
</project>
```

# 8-2. Maven을 이용한 웹 어플리케이션 실습

### 프로젝트 생성
- File - New - Maven Project
- Next,Next
- org.apache.maven.archetypes | maven-archetype-webapp | 1.0
- Grop id : 도메인 이름 거꾸로 (예: kr.or.connect)
- Artifact id : 프로젝트 이름 (예: mavenweb)
- Finish

### java 폴더 생성
- pom.xml 파일 선택
```xml
<dependencies>
<dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>javax.servlet-api</artifactId>
        <version>3.1.0</version>
        <scope>provided</scope>
</dependency>
<dependency>
        <groupId>javax.servlet</groupId>
        <artifactId>jstl</artifactId>
        <version>1.2</version>
 </dependency>
</dependencies>
  <build>
    <finalName>mavenweb</finalName>
        <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.6.1</version>
            <configuration>
                <source>1.8</source>
                <target>1.8</target>
            </configuration>
        </plugin>
    </plugins>
  </build>
```
- 프로젝트 선택 - 우클릭 - properties
- Maven/Java EE Integration 선택
- Enable Project Specific Settings 체크
- Apply and Close

### web.xml 수정
- WEB-INF/web.xml 선택
```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd" version="3.1">
  <display-name>Archetype Created Web Application</display-name>
</web-app>
```
- window -> Show View -> Navigator
- .settings/org.eclipse.wst.common.project.facet.core.xml 선택
```xml
<?xml version="1.0" encoding="UTF-8"?>
<faceted-project>
  <fixed facet="wst.jsdt.web"/>
  <installed facet="jst.web" version="3.1"/>
  <installed facet="wst.jsdt.web" version="1.0"/>
  <installed facet="java" version="1.8"/>
</faceted-project>
```

### 에러 발생시
- Servers에서 tomcat 삭제
- project -> 
- 재실행


