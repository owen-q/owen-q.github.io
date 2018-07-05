---
title: mysql collate
categories:
  - Tech
tags:
  - db
  - mysql 
date: 2018-07-06 08:23:37
thumbnailImage: 
---

# Character Set & Collate 

문자열 Datatype에는 문자셋(Character set)과 콜레이션(Collation) 속성이 있다. 

문자셋은 각 문자가 컴퓨터에 저장될 때 어떠한 '코드'로 저장될지에 대한 규칙의 집합 
Collation은 특정 문자셋에 의해 데이터베이스에 저장된 값들을 비교 검색하거나 정렬 등의 작업을 위해 문자들을 서로 비교할 때 사용하는 규칙들의 집합을 의미한다. 


- Charset은 server, database, table, column level에서 지정이 가능하다.

# Character Sets & Collations in General 
(https://dev.mysql.com/doc/refman/5.7/en/charset-general.html) 


#### Character Set이란?
- character set은 set of symbols & encodings.
- 예를들어,  문자열 A,B,C,D가 있다.
이때 각 문자열에 대해서 A=0, B=1, C=2, D=3 이라고 했을때, 
0, 1, 2, 3은 **encoding** 에 해당된다.

따라서 Symbol 'A,B,C,D'와 encoding '0,1,2,3'을 합친것을 *** Character Set *** 이라 한다. 


* Character Set 조회 
show character set;

* 서로 다른 char set들은 같은 collation을 가질 수 없다. 
* Char set은 default collation을 가지고 있다. 




* ASCII <= UNICODE 
( ascii로 저장되어 있는 것들은 UNICODE로 전환하여도 손실이 없다.) 




* Connection Character Sets and Collations
(https://dev.mysql.com/doc/refman/5.7/en/charset-connection.html) 

- Server's character set & collation :: character_set_server, collation_server variables 

Client가 Server에 연결후 쿼리를 요청하면, client는 해당 쿼리를 'character_set_client'에 설정되어 있는 character set으로 전송한다. 

**get mysql system variable**  
  - select @@{system_variable}

서버가 connection을 통해서 statement를 받으면, 아래와 같은 일이 발생한다.
  - client로부터 받은 statement를 'character_set_client'에서 'character_set_connection'으로 변환한다.
  - 'collation_connection'은 String 비교시에 중요하게 사용된다. 하지만 column에 설정되어 있는 collation이 더 상위이므로 이때에는 'collation_connection'은 무시된다.

Server가 Client에게 값을 반환할 때에는 'character_set_results'를 사용한다. 


* SET NAMES 'CHARSET-NAME' 
  이 쿼리는 해당 connection을 통해서 보내어지고 받을 데이터들의 charaset을 정의한다.
  ```character_set_client```, ```character_set_results```, ```character_set_connection``` 을 한번에 'CHARSET-NAME'으로 설정한다.  





