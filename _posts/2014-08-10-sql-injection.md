---
layout: post
title:  "SQL Injection"
date:   2014-08-10
categories: post
---
SQL injection is when an SQL query is entered into a user input field in an application. 
This often occurs online with website form fields, and is considered one of the top 10 web application vulnerabilities by the Open Web Application Security Project. 
{{ more }}
An example of a simple SQL query used for injection is: SELECT * FROM users WHERE name = '' OR '1'='1';. As 1=1, this will always evaluate to TRUE and will be executed.  

There are lots of things that can happen with injected SQL code. Some of them may be invisible to the attacker, such as deleting certain parts of the database. 
Other attacks can take advantage of or access parts of the database that they shouldn't have access to (such as signing into a website with a different user's ID).  

![](http://imgs.xkcd.com/comics/exploits_of_a_mom.png)  

There are a few ways to protect against SQL injections, and they mostly take the form of detecting whether the input is actual SQL code. Escaping is a common method of guarding against injections; this is done by detecting certain characters used in SQL and escaping them. Other methods include sandboxing the permissions of the database logon, or pattern-checking inputs.  

I found this [resource](http://en.wikipedia.org/wiki/SQL_injection) from
Wikipedia to be a clear explanation of SQL injection.
