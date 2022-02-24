---
title:  "Maven and JDBC"
excerpt: "Maven과 JDBC에 대해 araboja"

categories:
  - SQL
tags:
  - [SQL, MYSQL,Maven,JDBC]

toc: true
toc_sticky: true
 
date: 2022-02-24
last_modified_at: 2022-02-24
---
   
**JDBC란?**   
- 자바를 이용한 데이터베이스 접속과 SQL문장의 실행,그리고 실행 결과로 얻어진 데이터의 핸들링을 제공하는 방법과 절차에 관한 규약. 즉, 자바 프로그램 내에서 SQL문을 실행하기 위한 자바 API.   
+ Maven은 의존성(dependency)를 추가해주면 간단하게 사용 가능.
    

**JDBC를 이용한 프로그래밍 방법**
1. import java sql.*;
2. 드라이버를 로드한다. - 데이터베이스 벤더가 제공해주는 라이브러리 사용을 위해 연결   
```java 
Class.forName( "com.mysql.jdbc.Driver" );
```
3. Connect 객체를 생성한다. - db에 접속   
```java 
String dburl  = "jdbc:mysql://localhost/dbName";   
Connection con =  DriverManager.getConnection ( dburl, ID, PWD );
```
4. Statement 객체를 생성 및 질의를 수행한다. - 쿼리문 생성 및 실행
```java 
Statement stmt = con.createStatement();
ResultSet rs = stmt.executeQuery("select no from user" );
```
5. SQL문에 결과물이 있다면 ResultSet객체를 생성한다.
```java 
ResultSet rs =  stmt.executeQuery( "select no from user" );   
while ( rs.next() )   
  System.out.println( rs.getInt( "no") );
```
6. 모든 객체를 반대 순서로 닫는다. - 클라이언트와의 접속 해제
```java
rs.close();
stmt.close();
con.close();
```


