---
title: "[STS] How to set java code template in STS IDEA"
date: 2020-10-28 09:48:00
categories: jekyll update
---
This setting is setting of Mac os Environment.<br>
1.First Step : top right Spring Tool Suit4 Button > Preferences > Java > Code Style > Code Templates > Comments > Edit

2.Second Step : Configure generated code and comments<br>
<br>
[Method]
```
/**
 *
 * METHOD : ${enclosing_method}
 * DESCRIPTION : 
 *
 * ${tags}
 *
 */
``` 
[Types]
```
/**
 *  @Path 			${package_name}
 *  @FileName 		${file_name}
 *  @Creator 		${user}
 *  @CreateDate 	${date}
 *  @LastModifier	${user}
 *  @LastModifyDate ${date} 
 *  @Version 		1.0
 *  @Outline  		
 *  @Desction 		
 * 
 *  
 ************** 소스 수정 이력 ****************************************************
 *  date					 Modifier				Description
 *******************************************************************************
 *  ${date}			 ${user}				클래스 최초 생성
 *******************************************************************************
 */
```
[Information about variables]
```
  ${date} : Current date (현재 날짜)
  ${dollar} : The dollar symbol (달러문양)
  ${enclosing_type} : The type enclosing the method (선택된 메소드의 타입)
  ${file_name} : Name of the enclosing compilation (선택된 편집파일 이름)
  ${package_name} : Name of the enclosing package (선택된 패키지 이름)
  ${project_name} : Name of the enclosing project (선택된 프로젝트 이름)
  ${tags} : Generated Javadoc tags (@param, @return...) (Javedoc 태그 생성)
  ${time} : Current time (현재 시간)
  ${todo} : Todo task tag ('해야할일'태그 생성)
  ${type_name} : Name of the current type (현재 타입의 이름)
  ${user} : User name (사용자 이름)
  ${year} : Current year (현재 연도)
```