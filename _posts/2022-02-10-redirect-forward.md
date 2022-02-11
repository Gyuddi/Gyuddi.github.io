---
title:  "redirect,forward"
excerpt: "redirect,forward를 araboja"

categories:
  - WEB
tags:
  - [WEB, HTTP, Backend, JSP,Servlet,redirect,forword]

toc: true
toc_sticky: true
 
date: 2022-02-10
last_modified_at: 2022-02-10
---
redirect는 http 프로토콜로 정해진 규칙이다.   
 1. 서버는 클라로부터 요청을 받은 후, 클라에게 특정 url로 이동하라고 요청 가능하다. ->>redirect   
 2. 서버 -> 클라에게 302 코드와 함께 이동할 URL 정보를 제공. 클라는 상태값 302를 받으면 해당 URL로 재요청을 보내고, 이때 브라우저의 주소창이 전송받은 URL로 변화함.   
 3. 서블릿은 redirect를 위해 sendRedirect() 메소드를 사용한다.   
 ```
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<%
	response.sendRedirect("redirect02.jsp");
%>
```
__결국 클라이언트는 요청을 2번 보내고 서버는 응답을 2번 보내게 된다.__
***
Forward란?   

1. servlet1 이 요청을 받으면 2. servelt1은 요청을 일부 처리하고 그 결과를 HttpServletRequest에 저장. 
3. servlet1은 결과가 저장된 Request와 응답을 위한 Response를 같은 웹 어플리케이션 안의 servlet2에게 전달(Forward)
4. servelt2가 이를 처리한 후 부라우저에 결과 전송     

__forward와 redirect의 차이->__   

redirect는 url이 변하지만, forward는 url이 변하지 않음.   

*복습-클라이언트가 서버에 요청을 보내면 request와 response 객체가 형성되고 이는 결과 전송까지 유지됨.    
이를 생각해보면 redirect는 2번의 request,response객체 생성이 실행되지만, forward는 하나만 생성, 유지됨.   
servelt1에 처리된 결과값이 존재한다면?   
servelt1,2에 모두 접근 가능한 객체가 필요하다. ->request객체에 결과를 저장한다.(forward의 인자로 request,response를 넘겨준다.)   
*FrontServlet*
```java
protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		int diceValue = (int)(Math.random()*6)+1;
		//NextServlet에 옮길 값을 request에 맡긴다.
		request.setAttribute("dice",diceValue);
		//앞으로 넘긴다.
		RequestDispatcher requestDispatcher = request.getRequestDispatcher("/NextServlet");
		requestDispatcher.forward(request, response);
	}
```
*NextServlet*
```java
protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html>");
        out.println("<head><title>form</title></head>");
        out.println("<body>");
        //request에게 맡긴 값 찾아오기."dice"는 일종의 별명!
        int dice = (Integer)request.getAttribute("dice");
        out.println("dice : " + dice);
        for(int i = 0; i < dice; i++) {
            out.print("<br>hello");
        }
        out.println("</body>");
        out.println("</html>");
	}
```
___+
프로그램 로직 수행은 Servlet에서, 결과 출력은 JSP에서 하는 것이 유리하다___
Servlet에서 Jsp로의 forword도 가능하다!   
    
**LogicServlet**
```java
protected void service(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		int random1 = (int)(Math.random()*100)+1;
		int random2 = (int)(Math.random()*100)+1;
		int sum = random1+random2;
		request.setAttribute("random1", random1);
		request.setAttribute("random2", random2);
		request.setAttribute("sum", sum);
		//Servelt에서 Jsp로.
		//Jsp가 폴더 아래 있을경우 디랙토리를 명시해줘야 한다.
		RequestDispatcher requestDispatcher = request.getRequestDispatcher("/Jsp/result.jsp");
		requestDispatcher.forward(request, response);
	}
```
**result.jsp**
```jsp
<%
int random1 = (int)request.getAttribute("random1");
int random2 = (int)request.getAttribute("random2");
int sum = (int)request.getAttribute("sum");
%>
<%=random1 %> + <%=random2 %> = <%=sum %>
```