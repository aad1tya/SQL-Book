
### A Very Comprehensive Guide on SQL

And other things I tell myself when I am starting an article. 

This is more of a brain dump of my learning than something I wrote because of marketing purposes but I have tried to optimize this for as much readability as possible. So, enjoy!

## INDEX 

- [What is it?](#sqlwhat-isit)
- [Why use SQL?](#but-why-usesql)
- [Fields of SQL use](#fields-where-sql-is-used-extensively)
- [SQL: The HOW](#sql-thehow)
- [Database Management Systems](#database-management-systemsand-why-we-are-going-to-use-postgresql)
- [How to install PostgreSQL](#how-to-install-postgresql)
    - [Running your first query](#running-your-first-query)
    - [Inserting data into a column](#inserting-data-into-a-column-in-sql)
- [PostgreSQL Datatypes](#postgresql-datatypes)
    - [Boolean](#boolean)
    - [Character](#character)
    - [Numeric](#numeric)
    - [Decimals](#decimals)


Let’s do a brief introduction. Meet SQL.

### SQL — What is it?

SQL stands for Structured Query Language. It is used for **accessing and managing** data held in various types of databases that we’ll see further down in the article.

---

**_What is a Database though?_** According to definition by Oracle, “It is an organized collection of structured information, or data, typically stored electronically in a computer system”. Very formal. 

Exemplifying classically, it can be information about various employees working in a firm. Like their names, addresses, roles, salaries, joining date, etc. You can store the information on paper, but what’s better is that you store it on a computer so that you can **access it anytime, copy and share it, run several analyses on it to help the company both financially and improve its work environment.**

You’d need some tool to help you do all of that. This is where SQL comes in.

---

SQL was initially developed in early 1970s by Donald D. Chamberlin and Raymond F. Boyce after they learnt the [relational model](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwi397XZt4L7AhUkgWMGHUv6Df8QFnoECAkQAQ&url=https%3A%2F%2Fwww.seas.upenn.edu%2F~zives%2F03f%2Fcis550%2Fcodd.pdf&usg=AOvVaw0HymNIyGsw4MDwPW98GlLb) from Edgar F. Codd.

It didn’t entirely adapt that model, but it still became the most popular database language.

---

**_A relational database_** has various records that we call tables of data dependent on each other. Let’s say you are a bookseller. You get a lot of customers every day and you have a table storing the customers’ information. However, it doesn’t make a lot of sense to store the information about what product they bought in that same table. Then, you create another table with products bought by each customer. In this table, you do not repeat information like names of customer’s name, **instead you keep common an ID** in both tables.

Furthermore, you have another table having information about each product and so on. This makes everything easier to manage and track who is buying what and when.

Or continuing with our older example of employees, you’d have a table of all the employees’ basic information and then maybe another table with the work history of employees.

### But why use SQL?

One of the most recurring questions I used to have before I learnt SQL was that, why not use Excel to store and handle large data? It’s a tool that has survived the test of time and has become one of greatest invention by humans.

I have found 3 reasons to answer that question:

1.  SQL is faster. After a million rows or so Excel would start to slow down and given how much data is processed every day, many tables can easily surpass a million rows.
2.  SQL’s relational capabilities. Excel is not a database. It can certainly contain a lot of data but when you have store relative information in a lot of rows and multiple tables, it begins to look dull in comparison.
3.  SQL separates data from the analysis. When you do something, let’s say, sort a list alphabetically in Excel, you are changing the file you are editing. Instead, in SQL, you ask a query to the database, and the database answers back without any modification in the original data.

In plain terms, for what we want to do, SQL is faster, has necessary features to properly handle a database, and does precisely what we want it to do.

Now to remind you that SQL is no replacement for Excel: Excel’s much simpler to use for basic tasks, has a nice user interface and still capable of doing a large number of things you won’t need or want SQL for.

### SPECIFYING THE APPLICATIONS OF SQL

Here is something that I came across the web while looking to generalize the applications of SQL.

Moreover, the whole of SQL can be divided into parts according to SQL. It will be then much easier to learn.

This is about to get formal.

-   SQL as DDL (Data Definition Language): It’s not that complicated as it sounds but before creating a database, you should have a scheme on what kind of data (strings, dates, integers, etc.) will go into every column of the database.   
    Sometimes, you want to change the type of data a column accepts. It can be done using SQL without altering the data at all. 
-   SQL as DQL (Data Querying Language): You have multiple tables that contain data. You’d obviously want to know what data those tables store and would like to see that according to your personal needs. That’s where querying the data comes into the picture.   
    You ask (very informally speaking) SQL, “Hey SQL can you SELECT this data from this table if the data matches this criterion and umm, please sort it according to the age column.” And SQL will return a response based on the query without altering the original data at all. This is done using a very special mechanism as we would see.
-   SQL as DML (Data Manipulation Language): This goes without saying, you would need to change existing data, add into it or remove some parts f it. SQL has a set of queries that are used to do this Manipulation ✨.
-   SQL as DCL (Data Control Language): One important feature of SQL databases is that they are collaborative. A data control language deals with who has the rights and permissions to access the database you’ve created.   
    This is quite essential as I figured out and you will too as dive further into this.

### Fields where SQL is used extensively

1.  Data Analytics  
    As discussed earlier, when you have a ton of data, you can extract that sweet information out of it. SQL provides a ton of basic tools to do some basic data analysis on the data stored in your database. 
2.  Database Administration  
    A database administrator is responsible for adding, updating, removing, and overall managing the quality of data stored in a database. To make sure the quality of the data and its security (because a lot of information in the database is sensitive) a role of data administrator is important. 
3.  Backend Development  
    Lastly, but definitely one of the best applications of SQL comes into picture when you do Backend Development. Let’s say you are using Spotify, you “like” a song, which then gets added to your Library. When you switch devices, or uninstall and install Spotify again, that song still remains in the library. This is due to the fact that the information about your library is stored somewhere on Spotify’s server in a database. 

Now that we are done with what and why of SQL, let’s see how to SQL, shall we?

### SQL: The HOW

As we saw above, there were several applications of SQL. What’s important to note is that no SQL query is common between those applications. Therefore, we can draw a clear distinction between all of those queries and divide them accordingly.

People complain SQL is hard to learn, that’s because they jumble up what every type of query against each other. Separating each SQL statement and queries makes it a lot easier to understand.

But first, you would need have a proper setup to run the queries. A proper setup for SQL consists of 3 parts:

1.  A database engine
2.  An SQL client, and of course,
3.  An SQL query.

Let’s see what a database engine is first:

It’s the underlying system a database uses to function. The way queries are being handled after you execute them is seen by a database engine. It’s the component that actually stores and retrieves the data for you.

### Database Management Systems — and why we are going to use Postgresql

A DBMS or Database Management System is a tool that handles with data from the database and applications. It’s like a data storage but more “computerized”. 

There are various DMBSes available in the market, let’s see the most popular ones to get a hint on how they differ and what similar among them.

Firstly, there are two types of databases, relational and non-relational. Also known as SQL and NoSQL respectively.

**THE FIVE MOST POPULAR DBMS**

1.  MySQL
2.  MariaDB
3.  Oracle
4.  PostgreSQL
5.  MSSQL

#### MYSQL

This is one of the most popular relational database systems out there. It used be an open source application but now Oracle owns it. Because of the popularity and the base of C/C++, it is easy to use on any type of system. 

Some of the advantages being **Free Installation**, **Simple to use**, and **Cloud compatibility.**

Disadvantages being it has a few Scalability challenges and not being fully open source.

#### MARIADB

MariaDB is an open source fork of MySQL. The relevant user experience of using a DBMS is same as that of MySQL.

Even after being open source, a software doesn’t have to be less secure. MariaDB has additional encryption features that make it more. Other advantages of using it are **wider functionality** and **performance.**

The disadvantage of using MariaDB arrives from it being dependent on MySQL. What if they release a feature that is only available on MySQL? Another disadvantage also being that MariaDB’s user community is still small, so finding help if you’re stuck is less likely than others.

#### ORACLE

Compared to the previous two entries, Oracle is a database that is fully proprietary. The recent releases also focus hugely on cloud computing.

It can be said that this DBMS is the most “advanced” out there. With every release Oracle keeps up with the innovation going on in the world. While it’s focus of it being on information security.

Some pros of Oracle are **strong support**, **documents**, and **increased capacity.**

If it’s proprietary, there are going to be certain disadvantages of using it, first one obviously being very costly for the full version. The other two are that it has a **difficult learning curve**, and **high resource munching**.

#### POSTGRESQL — The one we’ll use

Completely open source. It is owned by PostgreSQL Global Development Group. It is a lot similar to MySQL, including it being also very popular. The focus of PostgresSQL is on making standards of compliance stronger and increasing extensibility.  
It provides plethora of tools to analyze data as well.

PostgreSQL has amazing **scalability**, **easy integration to 3rd party tools**, being **open-source & community support**, and **support to handle various custom data types like JSON, XML, etc**.

Nothing is perfect, PostgreSQL has cons like **documentation that is not standardized** leading to inconsistency, and there’s always the chance that if something goes wrong developers will notice it too late because **lack of reporting issues**.

#### MSSQL

Owned by Microsoft, it’s proprietary. It has T-SQL, the Transact SQL, which is just what Microsoft provides in addition to the standard SQL.

It’s again one of the most popular ones available in the field. It is more “free to use” than MySQL as there are various choices available to install the tool and use. For example, developer version and the Express version are free. There are also versions like Enterprise editions that provide administrative tools & services and of course cost money.

Other advantages are that it **provides a good solution to business data problems**, **has great documentation & support**, and **cloud DB support** (obvious as Azure is owned by Microsoft).

The cons are again obvious. It has **high cost**, and additionally the **pricing can be hard to understand** sometimes. Another con is also that it’s **difficult to begin working on with**.

---

### How to install PostgreSQL

Installing PostgreSQL can be a typical task varying from different platforms. Sometimes after installing the software, you might run into permission issues, server not running errors, etc. 

In this, we will look on how to install PostgreSQL and run the very first command.

#### Install PostgreSQL for Windows/Linux 

1.  Follow this [link](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads). Click on the download link that best suits your system OS and architecture.
2.  i)   
    After the setup has finished downloading. To install PostgreSQL on a Windows system, right click the setup and run it as administrator.  
    ii)  
    Else to install PostgreSQL on a Linux machine, first give the setup permission to be executed using **chmod.  
    _$ chmod 755 postgresql-10.22–1-linux-x64.run  
    _**Then execute the script as superuser:**_  
    $ sudo ./postgresql-10.22–1-linux-x64.run_**

3. You will see a dialog open up like this:

![](https://cdn-images-1.medium.com/max/1000/1*C8nY-GEjCGGzbcmbLItkHA.png)

Click on next.

![](https://cdn-images-1.medium.com/max/1000/1*tNC4o5hwNEhTdFIRKgixZQ.png)

By default, the installation directory of PostgreSQL is set to be at /opt/PostgreSQL/__version__. Change it if you want to.

![](https://cdn-images-1.medium.com/max/1000/1*GMG9wlwbYb51iW0OhIhWWw.png)

Here, you select everything you want to install. I am going to use everything, hence I leave them as they are by default. Click on next.

![](https://cdn-images-1.medium.com/max/1000/1*tlT8hXpr3zXdCBBE6gR5OQ.png)

Next, PostgreSQL installer asks you about where the data is going to get stored. Change it if you have something special in mind.

![](https://cdn-images-1.medium.com/max/1000/1*J0-Bz5I45c5KVcnOaD5mVg.png)

On the next dialog, PostgreSQL asks you for a master password. **PLEASE DO NOT FORGET THIS.** As you’d have to go through a lot of trouble if you do not remember this. 

Click next.

![](https://cdn-images-1.medium.com/max/1000/1*vxBPxDHAWKxfEvtbidHk7A.png)

PostgreSQL will have to run a database server. That server would be on a specific port. You can change ports even after the setting up the software but by default it is 5432. 

![](https://cdn-images-1.medium.com/max/1000/1*HsE9hMeRPqEhOExtIVRRew.png)

Select your locale, then click next.

![](https://cdn-images-1.medium.com/max/1000/1*yA_ZaSWV5vwNwb_N9vs_0A.png)

Finally PostgreSQL will ask you to review your choices. Click next if you don’t want to make any changes.

Click next again.

![](https://cdn-images-1.medium.com/max/1000/1*ftwTurZs4ZdqbjabCUzOoA.png)

Now, PostgreSQL will be installed on your system. Finally click on Finish. 

Once you are finished with the setup, you’d notice pgAdmin has been installed in your Applications list. Click on it to run.

You’d see a pop up like this asking for you master password you entered earlier.

![](https://cdn-images-1.medium.com/max/1000/1*Py76ArWWFQjVYabVkGA4_Q.png)

Enter it, and now you are all done to use PostgreSQL!! Congrats.

---

We have PostgreSQL installed. Time to introduce you to some basic queries! Like creating a Table in a Database.

 If you look on the left pane of pgAdmin, you’d see an unopened drop down **Servers.** Click on it to expand it. You will notice something.

![](https://cdn-images-1.medium.com/max/1000/1*UFTyxVCJRNuC_qFkA6m18Q.png)

  
By default, PostgreSQL provides you with a _database_ **postgres** and a server named **PostgreSQL_<version>.** 

We are going to create a new database. I have named it **_test_** very creatively. To create a database by yourself, right click on the server name (PostgreSQL_<version>), go to “Create”and then select “Database…”.

![](https://cdn-images-1.medium.com/max/1000/1*VbXoyRizIjV33RwGD8rVTw.png)

Give a name to your database.

![](https://cdn-images-1.medium.com/max/1000/1*6S6lsfcq4ThEzuZzmU35_w.png)

Then press save. As you would see on the left pane, PostgreSQL has created a new database for you under the server.

A database can have multiple tables, schemas, etc. Let’s understand more by taking an example of creation of a table.

#### Running your first query

We are going to create a table of employees, their first and last name, and email ID.
    
```
CREATE TABLE employees  
(  
first_name varchar(50),  
last_name varchar(50),  
email_id varchar(100)  
);
```
    
Notice the syntax, first we tell SQL that we want to CREATE something, it’s a TABLE, and then we call that table _employees._ In this, we also have to specify the column names and the data types those columns would be accepting.

How do you run this in pgAdmin though? 

![](https://cdn-images-1.medium.com/max/1000/1*LM-6wrxxiM8ETRRwL6a-Cg.png)

Select the newly created database you have, then right click, you would have the option to use the query tool. Select it and the Query Editor will open where you can write this.

![](https://cdn-images-1.medium.com/max/1000/1*ANlnSaMhHoMQO_URCyTfJQ.png)

After writing the query, you can execute it using the Play icon in the middle of the upper tab. You might have a Lightning Bolt **⚡** icon instead of the Play icon depending on what version you are using. 

When you hit that icon, your query should execute perfectly given the syntax is correct.   
On a successful query execution, PostgreSQL will show this in the output tab.

![](https://cdn-images-1.medium.com/max/1000/1*SLyVVnwHC4NfhVhDFemv-w.png)

That created the employees table for you. But how can you make sure it’s created? In the left pane, right click and enter **Refresh**. Expand the new database, then follow Schemas -> Public -> Tables. Here you’ll see that our employees table has been created and pgAdmin is showing information about what columns, constraints, etc it has.

![](https://cdn-images-1.medium.com/max/1000/1*mE5eBiA2pjnUFVKoQbqmEw.png)

Don’t worry if you don’t get what anything except Columns mean, I will talk about everything in the later sections and they are not important to get started.

Wait a minute though, there’s a more official and formal way to make sure that your table has been created. It’s by checking (using a query) what it contains.

We do that by simply running:

SELECT * FROM employees;

That’s it. The asterisk symbol is a wildcard that tells SQL to select EVERYTHING from the employees table. When you execute the query by hitting that Play/Lightning icon above, you should expect this in the output tab below.

![](https://cdn-images-1.medium.com/max/1000/1*HDi5am8seuKain82yP8pwQ.png)

As you can see it shows the table with column names and their data types. But it’s looking very empty in here. That’s because we never _inserted_ any data in our table. Time to do just that!

#### Inserting data into a column in SQL

Here’s how you can insert data into a column in SQL:

INSERT INTO employees (first_name, last_name, email_id)   
VALUES   
(‘John’, ‘Smith’, ‘johnsmith@genericname.com’),  
 (‘Harry’, ‘Potter’, ‘harrypotter@hogwarts.com’);  
  
SELECT * FROM employees;

**Note:** In SQL, single quotes are used to identify strings. If you were to use double quotes “”, you’d have gotten an error. That is because double quotes are used for SQL identifiers like column or table names.

Running the above query returns the following output. You can see how PostgreSQL automatically adds an index column.

![](https://cdn-images-1.medium.com/max/1000/1*CRxzbx9ORQC_BQpg8uFWaA.png)

To INSERT something in a database in SQL, you have to mention the columns that you want to be filled, followed by the term “VALUES” and then the value of the row.

I will not go on a detour and talk about data types just now, they will be covered later. But just know that data types are essential to databases as they specify what type of data each column should be accepting. This way you can’t put an integer value into the first or last name of an employee.

In the example above, we create three columns with the data type varchar. Varchar(n) in PostgreSQL is used to store an indefinite length long variable string, but it accepts a parameter _n_ that tells the database to not accept a string greater than n characters.

What if you tried to enter values that are not what the columns are expecting? Let’s say an integer? Well, it will still get inserted but first it will be converted to a varchar type.

Let’s create another table with a wider set of column types.

CREATE TABLE teachers (  
 id bigserial,  
 first_name varchar(25),  
 last_name varchar(50),  
 school varchar(50),  
 joining_date date,  
 salary money  
 );  
  
SELECT * FROM teachers

![](https://cdn-images-1.medium.com/max/1000/1*hR1AMiNjHw-fxxrFVJ8UtQ.png)

In the above query we mentioned _bigserial_ datatype which is a large autoincrementing data type that we are using as an index. How large you may ask? It can go up to 9223372036854775807, which would be more than sufficient for any table that you might have.

Next we use a familiar data type, varchar, to take in the values of names of teachers and their schools. 

To accept dates, we are using _date_ datatype that takes values in the default format **yyyy-mm-dd**. Then, finally we have the salaries of the teachers as _money_ datatype. The money datatype in PostgreSQL is used to store money values with a fixed precision value.  
Let’s try to insert some values in our newly created table to understand how they differ for each variable and what the output looks like.

INSERT INTO teachers (first_name, last_name, school, joining_date, salary) VALUES  
(‘Matt’, ‘Smith’, ‘JPV School’, ‘2020–11–08’, 35120),  
(‘Lizzy’, ‘Bennet’, ‘JPV School’, ‘2019–12–15’, 38230.22),  
(‘Terry’, ‘Crux’, ‘JPV School’, ‘2021–06–14’, ‘$32000.00’);  
  
SELECT * FROM teachers;

![](https://cdn-images-1.medium.com/max/1000/1*wpUPerzJQ-gaHQij55yPJw.png)

The first thing to notice in the output of our executed queries is the autoincrementing index value. We didn’t insert anything for the id column yet it increased according to each entry.

It made sense to wrap names of teachers and the school name in ‘’ quotes but the same is also true for the date column. PostgreSQL will accepts the date like a string and then stores it in the format. 

Lastly, we inserted money into the table in three different ways, i.e., as an integer, a float, and lastly as a formatted dollar string. But how did Postgres knew that the money is in dollars?   
Without going into much detail, PostgreSQL uses a variable called lc_monetary to handle the money locale for the input and output values. If not passed, it retrieves from the server (can be local) where the database is stored.

### PostgreSQL Datatypes

The datatypes in PostgreSQL can be categorized into the following:

#### BOOLEAN

Values that can only be either one of two things are stored using this datatype. 

Or in other terms, values that can either be true or false should follow this datatype.   
Anything inserted under this datatype with value true, 1, t, y, and yes gets converted to ‘true’. On the other hand, the values false, 0, f, and no gets converted to ‘false’.

#### CHARACTER

Character string data types in PostgreSQL can be inserted in three ways.

i) char(n)  
n is the value you enter to specify for how many characters the inserted string can go. If you enter characters less than n, the remaining string of the characters in the row will be padded with spaces.

This is used quite infrequently as it’s going to consume the fixed amount of data no matter the size of data.

ii) varchar(n)

Unlike _char,_ if you input characters with length less than n, PostgreSQL will not store extra spaces. This makes it much better for memory use. But like char, it accepts n as a parameter which restricts the number of characters you can insert into the row.

iii) text

The longest possible string you can store in a row is of 1 gigabyte. There is no restriction on the input string and obviously no extra spaces will be stored to compensate. 

This datatype is not a part of the standard SQL standard but there are similar datatypes available in other database management systems. 

When you are unsure the size of the input text, this data type can be used. 

#### NUMERIC

With numeric data types, you can store values that are, well, numbers! Two types of number types are present in SQL that are further divided into subcategories but I will include when and where to use each in the end, so it’ll be easier.

_Integers_

These are the most common data types you’ll find while exploring any kind of database. These are basic whole numbers. The value of these can be both positive and negative.

The basis of categorization lies in the range of each type can go up to. Here are they:

i) smallint: This is a datatype that stores the number in a 2 bytes storage. The range of this is from -32768 to +32767.

ii) integer: 4 bytes, ranges from -2147483648 to +2147483647.

iii) bigint: 8 bytes, ranges from −9223372036854775808 to −9223372036854775808.

_Auto-incrementing Integers_

In the teachers table we created above, there was a bigserial datatype which incremented itself whenever we added a column. Similar to _bigserial,_ there is also _smallserial_ and _serial._ 

And obviously, these are used for IDs and indices, the auto-incrementing data type does not range to negative values.

#### DECIMALS

Decimals represent integers in addition to a fraction of an integer. In SQL, they are represented in two forms:

i) Fixed-Point Numbers  
See it as a fixed length string. Only you decide how many total digits are going to be there in the number and how many digits there can be on the right hand side.

This is done by passing arguments. Either _numeric(precision, scale)_ or _decimal(precision, scale)_ can be used. **Precision** tells how many total digits are going to be there in the entire number and **scale** tells the maximum number of digits allowed on the right side of the decimal point , e.g., 12.4 has a precision of 3 and a scale of 1.

What if you don’t tell the database the values of precision and scale? Well, it will allow you to store the maximum number of values possible for each. That means up to 131072 digits on the left hand side and 16383 on the right hand side.

ii) Floating-Point Numbers

In the floating-point numbers, the decimal point can “float” anywhere instead of staying at one place like you’d expect from a fixed-point number above.

The floating point numbers are further divided into _real_ and _double precision._ Only difference between the two being the amount of data they can store.

The real data type can store upto six decimal digits whereas double precision can go upto 15 digits.

To get a clearer understanding of their working and the difference from the fixed point numbers, let’s take an example:

CREATE TABLE number_example (  
fixed_col numeric(15, 5),  
real_col real,  
double_col, double precision  
);  
INSERT INTO number_example  
VALUES   
(.1, .1, .1),  
(1.132, 1.132, 1.132),  
(5.423242344, 5.423242344, 5.423242344);  
  
SELECT * FROM number_example;

When you execute the query above, the following table is shown in the output:

![](https://cdn-images-1.medium.com/max/1000/1*G0nuGIQUQ0YtHR-MWGoi1Q.png)

Notice the fixed and the floating nature of the decimal point in each column? That’s the first thing you notice. But also see that in the fixed point column, we passed the scale of the number to be of 5 (numeric(15, **_5_**)), and therefore, in the third row, the number is truncated after the 5th digit on the right side. 

As already mentioned, the real data type has a precision of only 6, and similar thing happens with it too in the third column. Only double precision data type is able to represent the number exactly according to the input due to its high precision value.

Here are a few tips I came across the web on using number data types:

-   Use integers whenever possible. If your data does not have any decimal values, then what’s the point of using a decimal data type?
-   Float types save space due to how they are stored in the memory but if you want your calculations to be exact, always use _numeric_ or _decimal._
-   Use a large enough data type. When working with decimals, set precision and scale accordingly and when working with whole numbers, use a more than sufficient data type like _bigint_ unless you are extremely sure that a lower integer data type will be able to hold your data.

#### DATE & TIME

For date and time, PostgreSQL provides major data types:

-   date: Only date, no time is supported. Date supported is from 4713 BC to 5874897 AD. Stored in 4 bytes.
-   time: Only time, no date is supported. 24 hours format. 8 bytes required for storage. You would want to mention the timezone using _“with time zone”_ (I will give an example below). It becomes very difficult to track time across the globe without having a time zone value.
-   timestamp: Both date and time are supported ranging from 4713 BC to 294276 AD. 8 bytes needed to store it. Again, _“with time zone”_ would be wanted.
-   interval: Interval is the difference between two timestamps. This data type supports +-178000000 years of time interval. It also takes 16 bytes to store.

Let’s take an example:

CREATE TABLE date_time_example (  
timestamp_col timestamp with time zone,  
interval_col interval  
);  
INSERT INTO date_time_example  
VALUES  
('2022–11–20 05:00 EST', '5 days'),  
('2022–11–20 05:00 -8', '1 month'),  
('2022–11–20 05:00 Australia/Melbourne', '1 year'),  
(now(), '2 weeks');  
  
SELECT * FROM date_time_example;

When you run the above query, you get this:

![](https://cdn-images-1.medium.com/max/1000/1*FwitKXOFRBlUVwpidRXHBg.png)

**NOTE:** Also if you want to add an Indian timestamp, don’t use IST as it refers to Israel Standard Time instead of Indian Standard Time. Use Asia/Kolkata instead.

The time format used by default is yyyy-mm-dd hh:mm:ss which is the ISO standard for timekeeping. Another formats are also supported.

I know the output is a bit confusing. But see it with respect to my time zone which is Indian. So when you write EST, it converts 5 AM to Indian time in the first row, sets the time zone **behind 8 hours to UTC** (which is Pacific Time or PT) then converts 5 AM India time to PT in second row, and converts Australian 5 AM time to Indian in the third row. 

**Note that UTC is 00:00 and refers to overall world time standard so 8 hours behind it would be the Pacific Time zone.**

Also there’s the third row using now() function that retrieves the current time from the system where the PostgreSQL’s server is running.

We have seen the working of timestamp property till now quite enough. But what’s the interval data type doing there? What’s it purpose?

Let’s see that by running the following query:

SELECT   
timestamp_col,   
interval_col,  
timestamp_col + interval_col AS time_after_col  
FROM date_time_example;

![](https://cdn-images-1.medium.com/max/1000/1*98j2rcch85Tr6MSu39q7KA.png)

This is the output you get, as you can whatever interval value that was in interval column got added to our timestamps producing a third column. 

In the query, we used the AS keyword in SQL to give an alias to the newly computed column. Computed columns are formally called expressions in SQL.

#### _MORE TYPES IN POSTGRESQL_

i). **Arrays**

Data in rows can also be stored as Arrays in PostgreSQL. They are variable and multidimensional. To input into an array, you can use {} braces to represent a single input. For example:

CREATE TABLE sal_emp (  
    name            text,  
    pay_by_quarter  integer[],  
    schedule        text[][]  
);  
  
INSERT INTO sal_emp  
    VALUES ('Bill',  
    '{10000, 10000, 10000, 10000}',  
    '{{"meeting", "lunch"}, {"training", "presentation"}}');  
  
INSERT INTO sal_emp  
    VALUES ('Carol',  
    '{20000, 25000, 25000, 25000}',  
    '{{"breakfast", "consulting"}, {"meeting", "lunch"}}');  
  
  
SELECT * FROM sal_emp;

Running the above query yields the following results.

![](https://cdn-images-1.medium.com/max/1000/1*wYkOzOaa0N_ifZj-HFX1og.png)

ii). **UUID**

These are unique identifiers that have a better chance of uniqueness than the SERIAL data type that only provides unique values only within a single database. 

An example being:

I will use these later in relevant situations.
  

### SQL QUERIES

For a better understanding of SQL and various types of queries you can execute, let’s divide them up!

#### Data Definition Queries:

All the statements in Data Definition category are used to define or change database schemas. So that data can be inserted later according to that schema.

When you are creating an application with SQL to manage your data in the back end. The user of your application must not be able to access these queries from their side. Everything should be managed by the owner.

CREATE query  
When this query is executed, a new object in a database is created e.g., a table, a function, etc. You can even a create a new database using the CREATE statement.

The syntax to create a table is the following:

CREATE TABLE table_name (  
  col1 column_type,  
  col2 column_type,  
  .  
  .  
  colN column_type  
);

ALTER query

This query is used to modify how the schema of your database or the database components are designed. For example, after creating a table, you might want to change the data type of a column, maybe change the name of the column, etc.

Let’s see what the syntax of ALTER statement is:

ALTER TABLE table_name <expression>

The first words in the statement above makes the table modifiable. But what to do after that? That’s what <expression> represents above.

Here’s an example of what you can do:

CREATE TABLE example   
(  
  col1 text,  
  col2 text  
);  
  
ALTER TABLE example ADD COLUMN col3 text;  
  
SELECT * FROM example;

![](https://cdn-images-1.medium.com/max/1000/1*fv6PDZDiJeHyfPSy2o0JhQ.png)

As you can another column got added to our table. In the ALTER statement, we told SQL to add a column with a certain name and a certain data type. Just like when you would while creating a table.

You can change the data type of an already present column using the following query. Note the way syntax is written, do not try to memorize the query.

ALTER TABLE example ALTER COLUMN col3 SET DATA TYPE varchar(50);  
SELECT * FROM example;

This produces the expected results changing the third column’s data type to varchar with 50-character limit.

![](https://cdn-images-1.medium.com/max/1000/1*ZGfJZNoTM4mngM9YulRyuQ.png)

  

DROP query

The DROP statement in SQL is used to wipe out a table, database, a constraint, a column, etc.

You can drop an entire table or a database using single query. The syntax is:

DROP TABLE table_name

The above query will delete/drop the table you mention. But what if you want to do something less spectacular than that? What if you only want to remove a single column?

That can be achieved using a combination of ALTER and DROP.

ALTER TABLE table_name DROP COLUMN col_name

TRUNCATE Query

The TRUNCATE query has quite a similar function to DROP. It empties the table or other object but doesn’t remove its structure.

This is what the TRUNCATE syntax looks like: 

TRUNCATE table_name;

Using the above query will empty whatever data the table had but if you do SELECT * FROM table_name, then you’d still get an empty table with preserved structure.

Some things you should know that are different. DROP vs TRUNCATE

-   TRUNCATE is generally faster at removing data and is ideal for removing a **temporary table*.**
-   TRUNCATE preserves the table structure unlike DROP.
-   There is a chance of recovering the data you remove via TRUNCATE. The same cannot be said about DROP. Hence, DROP must be used wisely.
-   Temporary tables will be discussed soon.

The queries discussed above can be used in the combination of each other. An example of which you have already seen above. But more will be used later and it will become natural with time.

#### Data Query Language and Data Exploration:

The DQL statements are used to query the database. Let me correct myself. The DQL statement is used to query the database. That’s because, there is only one.

It is the SELECT statement that we have already seen multiple times. But now let’s actually _see_ what it can do. 

SELECT Query

You use this query to extract and organize data from a database. What makes it the most useful query is the fact that how much and how variably it is used. Most of the query you’ll be running will be either to update the data in your database or actually seeing it.

Let’s explore the SELECT query more.

A SELECT query can have 4 parts. 

SELECT <projection>  
FROM <table name>  
WHERE <boolean expression>  
ORDER BY <columns names>

We will focus on the projection part first to get started. 

For exploration, let’s setup a table first! You would want to copy the csv file I am using from my Github if you want to follow along.

Link to the **employees.csv**: [**_https://github.com/aad1tya/SQL-Book_**](https://github.com/aad1tya/SQL-Book)

CREATE TABLE employee (  
 EMPLOYEE_ID smallint,  
 FIRST_NAME varchar(30),  
 LAST_NAME varchar(30),  
 EMAIL varchar(70),  
 PHONE_NUMBER varchar(15),  
 HIRE_DATE date,  
 JOB_ID varchar(10),  
 SALARY decimal(8, 2),  
 MANAGER_ID smallint,  
 DEPARTMENT_ID smallint  
);  
  
COPY employee --- COPY command to import employee.csv with a HEADER and CSV format.  
FROM '/employees/employees.csv'  
WITH (FORMAT CSV, HEADER);  
  
SELECT * FROM employee;

This is what the output looks like when you run the above query. 

![](https://cdn-images-1.medium.com/max/1000/1*8HmnsnKrfVFwOr4UEFccrQ.png)

---

Back to the projection part of the SELECT statement! 

The asterisk * in the above query basically tells SQL to grab everything from the employee table. 

What if you want to get only a few selected columns?

SELECT first_name, last_name, salary  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*j6JfXSpoQWIROIjZGOA2sw.png)

Our query, instead of using a wildcard, just tells SQL to get all of the mentioned columns. 

Using the “AS” keyword, you can provide an alias for the column you want to retrieve as many times, the column names doesn’t make sense/look good when retrieved.

SELECT first_name as EmployeeName  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*PyIIg2HLtuF-Ca6nXJJIpQ.png)

What if you want to provide an alias that has a space in it, because an alias should be able to look like normal English without any underscores, right? Well, if you try to do that normally, like this — 

SELECT first_name as "First Name"  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*7FdnFmWx8MZOjpGOMQUR4Q.png)

 — SQL will follow you up with an error. To avoid this, and to make your query run successfully, you’d have to wrap up your alias in double quotes like this:

SELECT first_name as "First Name"  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*GzR4jhGzpKmUPsDMYjYsQQ.png)

It works! 

Similarly, you can provide aliases for multiple columns one by one like this:

SELECT first_name AS "First Name", last_name AS "Last Name"  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*VEs5vtY4ogCShMJcXEDMGw.png)

**NOTE:** You are not changing anything while running the SELECT statement. 

What if I told you “AS” is optional? It’s true, you can provide an alias without AS. The following query will also provide the same results as the above but you should avoid this approach of writing queries as it doesn’t read well.

SELECT first_name "First Name", last_name "Last Name"  
FROM employee;

Another what if. What if you want to get the full name of an employee in a single column. You can do that in PostgreSQL like this.

SELECT first_name || ' ' || last_name AS "Full Name"  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*o0CjrzOnqWod7uAdtEoTPg.png)

Basically, the || operator joins two mentioned columns with a space in between. It’s like basically saying, _first_name + ‘ ’ + last_name._

You can add or subtract two column values as well. Let’s say, for example, you want to find the number of days an Employee has stayed at the current organization. That can be done using the following query:

SELECT now()::date - hire_date AS "Employee Days"  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*MH7f4e1KE80aLpKWxl04EQ.png)

Okay, a lot to unpack here. First of all, now() returns the current time. It depends on where your PostgreSQL server is running. now() function returns a timestamp with both date and time value, we only care about the current date.   
So, to get only the date we use “::date” which converts the timestamp to date only. After that is done, we simply subtract the stored date from it. 

You can find the difference between two date. Similarly, you can do the same with integers, you can add them, you can subtract them. But before you start doing that, first get to know casting in PostgreSQL as dealing with integers and decimals can get finnicky. 

SELECT first_name, last_name, job_id, cast(salary as bigint)   
FROM employee;

In the original table, salary is mentioned as a numeric with a fixed decimal point. Using the above query, we convert the salary table to integer and get this:

![](https://cdn-images-1.medium.com/max/1000/1*AcNFJ6YgD6peGEmbo2BiOg.png)

  

This was to just give you an example, salaries stay in decimal point. Those clerks are already getting paid so less!

Now you know how to deal with column projections along with SELECT statement. In the following section, we deal with the conditional part of the SELECT statement.

---

I want to find out which employees get paid more than 10000 as a salary. How do I do that? That’s where conditions in SQL come in.

SELECT first_name, last_name, salary  
FROM employee  
WHERE salary > 10000;

Running this gets us the expected results, i.e., we get a table with first names, last names, and salaries of employees that are paid more than 10000. 

![](https://cdn-images-1.medium.com/max/1000/1*53kS5yYQ24LERK5YK4eqyw.png)

 Let’s do something more useful! Querying the database to only return a table of employees that work in IT.

That can be done easily using:

SELECT first_name, last_name, hire_date, job_id  
FROM employee  
WHERE job_id = 'IT_PROG';

![](https://cdn-images-1.medium.com/max/1000/1*umsIfKQt8z6RS-4UKmoiuw.png)

Using a single WHERE statement is quite straightforward. Let’s say you want to know for some reason, the employees in IT who joined after year 2006. How would you do that?

That’s where AND operator comes in. 

SELECT first_name, last_name, hire_date, job_id  
FROM employee  
WHERE job_id = 'IT_PROG' AND hire_date > '2006-01-01';

![](https://cdn-images-1.medium.com/max/1000/1*e3bJznXhc6U8VBecr634wA.png)

The AND operator compares both of our conditions (where the job_id is IT and hire_date is greater than 2006) and returns rows that satisfy both of those needs. What if you want to run a query that might satisfy one of the conditions?

Question. Find the employees who are either clerks _OR_ work in the IT department. 

It’s similar to using the AND operator. 

SELECT first_name, last_name, hire_date, job_id  
FROM employee  
WHERE job_id = 'IT_PROG' OR job_id = 'ST_CLERK'; 

Running the above query returns over 20 results (hidden in the picture below) as we have a lot of clerks. It basically returns values that are true for either IT_PROG or ST_CLERK.

![](https://cdn-images-1.medium.com/max/1000/1*UCZWCVBTJ4gmMSjdsU9esQ.png)

When you filter out a table based on a specific column (in the above case, **_job_id_**), it is a good idea normally to have that filter column in the output as it can help you make more sense of the data.

Till now we have seen the “>” greater than and “=” equal to operator. Let’s have all of them listed down below.

-   The equal to (“=”) operator: This operator checks if two values are equal or not. After comparison, if the values are not equal the condition is False, and if they are equal the condition is True.
-   The not equal to (“!=” or ”<>”) operator: Either one can be used. They check if the two values are equal or not. If the values are not equal, the condition becomes True and if they are equal, the condition becomes False.
-   Greater than (“>”) operator: Checks if the left side operand is bigger than the right side operand. The condition is True if that is the case else False.
-   Smaller than (“<”) operator: Checks if the left side operand is smaller than the right side operand. The condition is True if that is the case else False.
-   Greater than or equal to (“>=”): Condition is True if the left operand is greater than or equal to the right side operand else False.
-   Smaller than or equal to (“<=”): Condition is True if the left operand is smaller than or equal to the right side operand else False.

All of these operators and AND & OR enable you to ask better questions when used with WHERE statement and this is what makes SQL a great language to query your data. 

Those operators are alright. But there is another one left. What if you want to find values that are BETWEEN two values.

The comparison operator for that exact task is, you guessed it, the BETWEEN operator. 

Let’s take an example by asking the question that who are the employees who earn in a certain range:

SELECT first_name, last_name, salary  
FROM employee  
WHERE salary BETWEEN 4000 AND 8000;

The above query returns the following output.

![](https://cdn-images-1.medium.com/max/1000/1*TnYt3MBE72tzArJMk2wa9w.png)

You got a task assigned, find the employees who have the ID 111, 121, 112, and 123. The first answer your mind will come up with might look like this:

SELECT employee_id, first_name, last_name  
FROM employee  
WHERE employee_id = 111 OR employee_id = 121 OR  
employee_id = 112 OR employee_id = 123;

Sure, this will return the desired result, but there’s a better, more sophisticated way to ask the same question. 

Use the “IN” operator. 

SELECT employee_id, first_name, last_name  
FROM employee  
WHERE employee_id IN (111, 121, 112, 123);

Both return the same result below but the latter looks cleaner and you can add as many values as you want. 

![](https://cdn-images-1.medium.com/max/1000/1*772SOPYJPgha46tRY-ppaQ.png)

#### SQL Pattern Matching

You can find out what column has values that match your specific pattern. For example, you might want to find employee names that start with U. Or, a better example would be that you want to find out employees whose phone numbers start with “515”. 

Well, how do you do that in SQL? The answer is simple, pattern matching. 

PostgreSQL has two operators, LIKE and ILIKE for pattern matching. Let’s see each one in action and also understand the very basic difference both have.

LIKE and ILIKE

The only difference between LIKE and ILIKE is that LIKE is case-sensitive (for it, “hello” and “HELLO”) are different. ILIKE on the other hand is case-insensitive, lower and uppercase letters mean the same to it.

SELECT first_name, last_name, job_id, phone_number  
FROM employee  
WHERE phone_number LIKE '515%'

The above query returns the following results:

![](https://cdn-images-1.medium.com/max/1000/1*eM5LV305xouxkKOaW7XbDA.png)

As you can see, we only got employees that have phone numbers starting with 515. The “%” in “_WHERE phone_number LIKE ‘515%’_” acts as a wildcard. It basically says “I only care about 515 and if just 515 matches the string, I will pick it up regardless what comes after it.”

Similarly, you can have employees with phone numbers that start with 515 and end with 9 with whatever comes between as a wildcard. Like this:

SELECT first_name, last_name, job_id, phone_number  
FROM employee  
WHERE phone_number LIKE '515%9'

![](https://cdn-images-1.medium.com/max/1000/1*2zz0uIgoE_avml9v38IUVw.png)

You can also search for values that contain a specific letter/letters between a string. This can be done by using underscore “_” instead of “%”.

SELECT first_name, last_name, job_id  
FROM employee  
WHERE first_name LIKE '%_am_%'

![](https://cdn-images-1.medium.com/max/1000/1*zR-pzfHZ44sq6ZtQO4Gt8w.png)

  

It returns names with “am” in a string and then two whatever characters in the side and then wildcards. You might be thinking how does it differ from simply using “%am%”. Well, the “%_am_%” requires for the database to have at least two surrounding characters, the “%am%” does not require that. Here’s the result of the latter.

![](https://cdn-images-1.medium.com/max/1000/1*2HFrcBZt2yxmRurLb5Cw7g.png)

Notice how the second one also returns the names that end with “am”?

**A more important thing to notice is this:** If you only run the query with just “_am_”, it will return nothing. Because there’s no first name that has four letters AND contains “am” in it.

SQL NOT operator: 

Let’s say you want to find out the rows that do not match the “%_am_%” pattern? How do you do that?

The NOT operator in SQL provides that exact functionality.

SELECT first_name, last_name, job_id  
FROM employee  
WHERE first_name NOT LIKE '%_am_%'

The query returns the following result that doesn’t include the two employees with the name “James”.

![](https://cdn-images-1.medium.com/max/1000/1*h1UrRkFdDIR1C2-5Wl4H4Q.png)

There’s more to SQL than single line filters. It somewhat qualifies for the “Language” part in Structured Query Language. 

I am saying that because SQL allows you to write IF-ELSE loops in it and based on those IF-ELSE clauses you can have a lot of extra leverage that you didn’t have previously.

**CASE statement in PostgreSQL**

If you have are familiar with programming languages (which I think you can’t avoid because of how urgent it is to learn them), then you’d know IF loops. The CASE statement allows you to do just the same in PostgreSQL. Except instead of “IF”, the keyword is “WHEN”. Potato Potatoh.

Let’s see how the syntax of it works.

**_CASE   
 WHEN <condition 1> THEN <result 1>  
 WHEN <condition 2> THEN <result 2>  
 .  
 .  
 WHEN <condition n> THEN <result n>_**

 **_ELSE <result of else>  
END_**

This doesn’t make complete sense without a proper example, so let’s do just that. I will use the employee table for this.

The job_ids doesn’t give us a proper idea of what the person actually does. Sure, it’s somewhat indicative of their role but you can’t be sure. So let’s classify each job_id into a role that is descriptive of what the person does.

Here’s how you can do that using CASE.

SELECT first_name, last_name, job_id, ---Notice the comma after the last column  
CASE  
  WHEN job_id LIKE 'IT%' THEN 'Programmer'  
  WHEN job_id LIKE '%CLERK' THEN 'Clerk'  
  WHEN job_id LIKE '%MGR%' THEN 'Manager'  
  ELSE 'Unknown'  
END job_title  
FROM employee;

This query creates a column in the result that enters Clerk against all the job_ids that have the word “CLERK” in them, Programmer against the IT people, and Manager against all the managers. 

The ELSE block handles all of the other job_ids and does “unknown” for now.

![](https://cdn-images-1.medium.com/max/1000/1*U6qGMBoYQTXEtaI5q5JGFg.png)

**Note:** You have to end the WHEN clause with the END keyword after finishing to write the conditions. Also, the ELSE statement in the query above is only optional.

SQL —LIMIT, DISTINCT, and ORDER BY statements

It’s not a proper database management tool if it does not have basic functionalities like sorting.

The ORDER BY clause in SQL sorts the table by the column/columns mentioned. Let’s have a look.

SELECT first_name, last_name  
FROM employee  
ORDER BY first_name;

![](https://cdn-images-1.medium.com/max/1000/1*6_dbCSOm-FUBjhSH1pKFzA.png)

Our table got sorted relative to the first_name. By default, the sorting gets done in the Ascending order. You can specify to SQL the type of sorting you want to do like this:

SELECT first_name, last_name  
FROM employee  
ORDER BY first_name DESC;

![](https://cdn-images-1.medium.com/max/1000/1*EqCmhsVbUMwOeJSJrsZ99A.png)

You can do the same with the numbers as well. Let’s see who earns the most in our database!

SELECT first_name, last_name, money  
FROM employee  
ORDER BY money DESC;

![](https://cdn-images-1.medium.com/max/1000/1*NoRbT56d-WFOxPzDhfk7xA.png)

Steven King. Fitting.

Similar to sorting on the basis of a single column, you can also sort based on multiple columns. How does _that_ work?

SELECT first_name, last_name  
FROM employee  
ORDER BY first_name, last_name DESC;

![](https://cdn-images-1.medium.com/max/1000/1*uONiY4mueI1kjVODBDTkPQ.png)

Our query first sorts the table according to the first_name, then if two or more first names are duplicate, it sorts those duplicates in descending order based on their last name. **You can see the same happening for the row 2 and 3.**

Let’s see the total number of distinct values for job_ids we have. You can do that using the DISTINCT keyword.

SELECT DISTINCT job_id  
FROM employee  
ORDER BY job_id;

![](https://cdn-images-1.medium.com/max/1000/1*54Da2bCcfBAcIkp0JogJDA.png)

We have 17 different job_ids in our table. But is their a better way to do this instead of checking the index? Yes, there is. It is by using COUNT.

SELECT COUNT (DISTINCT job_id)  
FROM employee;

![](https://cdn-images-1.medium.com/max/1000/1*Ng6py2228qo1Fz4EBT6YAQ.png)

COUNT keyword counts the values returned by the SELECT projection. The count is an aggregate function that is one of the many that we will see later.

Let’s see what does LIMIT keyword do. It does what it is supposed to do. It basically returns the first N number of rows out of your query result. Taking an example would make you understand it better.

SELECT first_name, last_name  
FROM employee  
LIMIT 10;

![](https://cdn-images-1.medium.com/max/1000/1*VncwG2Nm--vMOF4gymVZdA.png)

The output gets limited to the first 10 rows. 

**Aggregate Functions and GROUP BY**

Aggregate functions are called aggregate because they perform an operation on rows and return the answer in a single row.

We have already seen the example of COUNT() function that took the entire table and returns the number of rows that table has.

These aggregate functions are often used along with GROUP BY statement. You’d understand what GROUP BY does with the help of an example. 

But first let’s see each aggregate function with an example. How’d you go about finding the average salary from the employee table? Well, for that SQL has a standard function called avg(). Let’s have a look.

SELECT avg(salary) AS average_salary  
FROM employee;

You can easily calculate the maximum value from a column using max() like this:

SELECT max(salary)  
FROM employee;

The max() function returns the maximum value from a column. To get all of the employees that have the salary equal to maximum salary, you could either sort the table in descending order with respect to the salary column and then limit the output to just get the right number of employees (**_this would be wrong_**) OR you can use the max() function like this:

SELECT first_name, last_name, salary  
FROM employee  
WHERE salary = (SELECT max(salary) FROM employee);

Now, I realized, was a good time to introduce to you that you can use the output of an another SELECT statement to use for comparison in a WHERE condition.

Similar to the max() function, we have the min() function that returns the smallest value from the column. Asking the same question we asked above but replace the maximum with minimum.

SELECT first_name, last_name, salary  
FROM employee  
WHERE salary = (SELECT max(salary) FROM employee);

The SUM() function tells you the sum of an entire column. And this is the perfect time to also understand the working of the GROUP BY clause. Let’s first understand SUM() function with an example:

SELECT sum(salary) AS company_spending  
FROM employee;

Now, a question, how much the company spends on each job role. That’s where the GROUP BY statement comes in. Watch attentively.

SELECT sum(salary) AS job_spending  
FROM employee  
GROUP BY job_id  
ORDER_BY job_id;

See how it sums salaries from each job role separately? That is because the GROUP BY statement groups by the table from each job_id and then runs the sum() function on them as it is the second one that gets executed. That’s how things are with SQL. It’s the weird employee but it gets the job done.

COMMON TABLE EXPRESSIONS and WITH statements

CTEs or Common Table Expressions allow us to simplify the queries that we write with the SELECT statement.

Because of the way SQL processes a query, if you write the following in the Query Editor, it will result in an error.

SELECT job_id, CAST (avg(salary) as bigint) AS avg_salary  
FROM employee  
GROUP BY job_id  
WHERE avg_salary > 5000; --- SQL doesn't know that avg_salary exists yet.

![](https://cdn-images-1.medium.com/max/1000/1*rGqyrKueUgnUq4idnk1Dcg.png)

What we wrote above was a table values expression. Any query that returns a table is a table valued expression. So to run the above query properly, a WITH clause can help.

Let’s see how.

WITH avg_salary_table AS ( --- avg_salary_table is the new table created  
  SELECT job_id, CAST(avg(salary) as bigint) AS avg_salary  
  FROM employee  
  GROUP BY job_id  
) --- Finishing the query just here will result in error  
  
SELECT * FROM avg_salary_table --- WITH is followed by SELECT and  
WHERE avg_salary > 5000; ---       it must have table alias WITH used.

![](https://cdn-images-1.medium.com/max/1000/1*MrNfW1FLmjMTzCs8v5PPsw.png)

The above query, on the other hand, works perfectly fine. It returns us the job departments that have an average salary of more than 5000.

**Note: A thing to note above is that you will have to write a SELECT statement after the WITH clause and you will have to use the alias table you used in the WITH statement.**

Now, let’s actually witness the usefulness of the WITH clause by asking a question. What if I want to see the average job role salary against each employee working in that specific department?   
To explain it further, if employee A works in IT and employee B works as a clerk, then I want to see the average salaries of their respective department against A and B. How do I do that?

It can be done with the help of the WITH clause. Here’s how:

WITH table_one as ( --- A basic SELECT query to get some relevant columns  
  SELECT first_name, last_name, salary, job_id  
  FROM employee  
),   
table_two as ( --- A query that calculates each job_id's avg salary  
  SELECT job_id, CAST(avg(salary) as bigint) as avg_salary  
  FROM employee  
  GROUP BY job_id  
)  
SELECT t1.*, t2.avg_salary --- Wherever job_id matches, normally join the two tables  
FROM table_one AS t1 JOIN table_two AS t2 ON t1.job_id = t2.job_id  
ORDER BY t1.first_name;

You can create a series of table separated by comma with the WITH clause. Each table created will have an alias that can be used later in the SELECT query.

![](https://cdn-images-1.medium.com/max/1000/1*XR7Q9fFHIFpFR9FIYTdtlQ.png)

  

**WINDOW Functions in SQL**

 Window functions in SQL make it easier to get the result we want from a database. They allow us to do a second search from a result, that may allow us to ask better questions and get better answers.

They come right after the SELECT statement and are part of the projection.

Here’s the syntax of the WINDOW functions.

**_window_function_name() OVER (  
<columns>  
ORDER BY <columns>  
)_**

There are 3 types of WINDOW functions:

-   Aggregate
-   Value
-   Ranking

To understand the superiority of the window functions, I am going to write the last query I wrote using WITH clause again using a window function. The type of Window function I am going to use below is as an Aggregate window function.

SELECT first_name, last_name, job_id, salary,  
  CAST(AVG(salary) OVER (PARTITION BY job_id) AS BIGINT) AS avg_salary_jobid  
FROM employee  
ORDER BY first_name;

![](https://cdn-images-1.medium.com/max/1000/1*i2GpGbRB5-4EoUE4J9ZZYQ.png)

Exact same result using a much more sophisticated query! I know it’s hard to believe that the last 15 something line query gives the same result as this 5 lines query we have written above.

Let me explain the query:  
- First I select the columns normally, then  
- We average the salary column OVER a partition, and  
- The partitions are over the job_id column, so basically it means that average the salary over these groups and then include those in the result.

You can also use multiple Window functions in a single query of course. When using multiple window functions that do the same partitions, it’s always nice to use an alias for them then use the WINDOW clause to define that alias. For example, instead of writing,

SELECT first_name, last_name, job_id, salary,  
  CAST(AVG(salary) OVER (PARTITION BY job_id) AS BIGINT) AS avg_salary_jobid,  
  CAST(MAX(salary) OVER (PARTITION BY job_id) AS BIGINT) AS max_salary_jobid  
FROM employee  
ORDER BY first_name;

You can write,

SELECT first_name, last_name, job_id, salary,  
  CAST(AVG(salary) OVER part AS bigint), --- "part" is the name of the alias  
  CAST(MAX(salary) OVER part AS bigint)  
FROM employee  
WINDOW part AS (PARTITION BY job_id) --- we use "part" again to define partitions  
ORDER BY first_name;

**PostgreSQL Views**

Until now, whatever SELECT queries we used did not create any new data in your database. 

Views in SQL gives you the ability to store new tables out of SELECT statements. It’s not storing up your new data separately, it’s just providing you a saved “view”.

Let’s create one.

CREATE VIEW it_people as  
  SELECT *   
  FROM employee  
  WHERE job_id LIKE 'IT%'

When you run the above query, you don’t see any output. That’s because whatever we selected got saved up for the view. If you are using PostgreSQL, if you refresh the left pane, you’d see the view created like this:

![](https://cdn-images-1.medium.com/max/1000/1*a4vW2cvz1iN7W2HnpMIWfg.png)

And if you run this query:

SELECT *  
FROM it_people

![](https://cdn-images-1.medium.com/max/1000/1*SpLodIOPX58Avy6Mr9M75g.png)

You’d see an output that is basically the query that got saved as the view. 

But what is the use case here? 

The one of the reasons to use views is that you can write very complicated queries. That is because now, unlike the previous SELECT statements, we have a query that is permanently saved and can be reused. 

The second reason is that when you are owner of a database, you might not want everyone to have the access to the main database you have, you might want to give them access to a certain view or views.

**Temporary Tables**

Temporary tables are tables that only live in the database memory until the next time you start your SQL session.

They can be great to do intermediate data processing. For example, you can create temporary tables for some intermediate data processing and then do further operations on that data.

The syntax to creating a temporary table can be either:

**_CREATE TEMPORARY TABLE table_temp (…);_**

OR

**_CREATE TEMP TABLE table_temp (…);_**

For example, creating a temporary table based on the employee table would look something like this:

CREATE TEMPORARY TABLE employee_temp (LIKE employee);  
  
SELECT * FROM employee_temp;

![](https://cdn-images-1.medium.com/max/1000/1*7BgsRztO2K4_hjvXIKGXBw.png)

The employee_temp is a table that has no data, from the query above it only copies the table design of the employee table instead of copying the data. 

To also copy the data, you’d have to run:

INSERT INTO employee_temp  
SELECT * FROM employee;  
  
SELECT * FROM employee_temp;

![](https://cdn-images-1.medium.com/max/1000/1*j5BDMvNtkI8w97wbO-nsew.png)

This way you get a table that is an exact copy of the employee table. We will talk about the INSERT clause later in the course.

Now that you have this table in the database, you can freely apply any sort of manipulation operations that you wanted to run on your original table without any sense of feeling that you might accidentally mess up the database. 

Another thing temporary tables are good for is that you can update values, create new columns out of them and if that column matches what you wanted, you can add them to your original table.

But to do that, you first need to know another form of SQL, that is, Data Manipulation Language.

### **SQL as Data Manipulation Language**

You have some data in your table. There are obviously times when you want to change that data, maybe not particularly in that specific table, maybe in a temporary table or a view. How do you do that?

There are 4 SQL statements that enable you to do that in various ways:

INSERT clause

Using the INSERT clause you can insert values and columns in your already existent table.

In that too, you can either insert only the values and values & columns both together.

Let’s take an example of both. First, let’s create a new table. 

CREATE TABLE persons (  
id bigserial,  
first_name varchar(30),  
last_name varchar(30),  
email_id varchar(80),  
phone_num varchar(10)  
)

After the table has been created, let’s start inserting!

INSERT only values.

INSERT INTO persons (first_name, last_name, email_id, phone_num)  
VALUES  
('Mary', 'Sue', 'marysue@gmail.com', '1245681901');  
  
SELECT * FROM persons;

![](https://cdn-images-1.medium.com/max/1000/1*4UTNFEdbqZh9jowwlL-q-Q.png)

That was easy! You can also add multiple rows by separating the values with a comma. Like this:

INSERT INTO persons (first_name, last_name, email_id, phone_num)  
VALUES  
('Mary', 'Sue', 'marysue@gmail.com', '1245681901'),  
('Mary', 'Sue', 'marysue@gmail.com', '1245681901'),  
('Mary', 'Sue', 'marysue@gmail.com', '1245681901');  
  
SELECT * FROM persons;

![](https://cdn-images-1.medium.com/max/1000/1*PCCmK5iG31o_AhgbdnN8Iw.png)

As you can see, 3 more columns got added to our database!

You can also specifically add values to columns if you don’t have enough data present. For example, maybe you don’t the person’s last name. 

INSERT INTO persons (first_name, email_id, phone_num)  
VALUES  
('Mary', 'marysue@gmail.com', '1245681901')  
  
SELECT * FROM persons;

![](https://cdn-images-1.medium.com/max/1000/1*bJBYfhCtLy0gabdMx75UFA.png)

In such a case, SQL would show null instead of the data in the table.

To find the median from a column in the data, PostgreSQL doesn’t provide any function, and neither the ANSI SQL standards have any requirement. But what we do have is two functions to calculate the percentile from a group. 

i). The _percentile_disc()_ function.  
ii). The _percentile_cont()_ function.

The first function finds the discrete percentile value and the second finds the continuous value. But how can we use this to find the median from the data set?

We know that the median value is the middle value in a sorted data. It is the value above which lie half of the greater (or smaller values depending on how you have sorted the data) values and below lie the other half of the values that are smaller than it.

By finding the 50th percentile i.e., finding the value that is greater than 50 percentage of the values in the population, we are basically finding the median.

But what is the difference between the two functions above?

As the names might suggest, the percentile_disc() only checks for a discrete value from the dataset. Meaning, if you have an even number of values in your data, then you’d have two median values e.g., 14 and 15. Then this function will return either one of them.

percentile_cont() on the other hand finds the continuous value. If we have two values in the middle, it will give us the average of those two values. This fits the definition of what a Median is.

The query 

_percentile_cont(0.5)_ WITHIN GROUP (ORDER BY “column_name”)

returns the value of the 50th percentile in the column, hence the median. But what about all the keywords like “WITHIN GROUP” and why are we using “ORDER BY”. As we know, that ORDER BY sorts our database in ascending by default. We also know that to calculate Median, we should have data that is sorted. 

So, the query above is basically saying, ORDER the database using this column, and find the 50th percentile (median) for that column we mentioned.

Instead of finding just the median you can also use percentile_cont() function to find other percentiles, like the first quartile (lowest 25 percent of data), second quartile (which is again Median of course), third quartile, etc.

---

You can also calculate the Mode in the dataset. Mode is the value that appears most often in the dataset.

Similar to the Median, it is not a part of the standard SQL but Postgresql provides it.

The syntax is very similar to that of calculating Median.

_SELECT mode() WITHIN GROUP (ORDER BY p0010001)_

_FROM table_name;_

The above query sorts the table and finds mode from within the group of the sorted column.

Doing basic mathematical operations such as these is important to working with SQL. My main language is Python so while learning about this stuff I kept thinking why I can’t just copy the data to Python and deal with it there.

But no, I (and now you) was learning SQL, and this is part of it.

---

### **JOINING TABLES IN A RELATIONAL DATABASE — The good stuff**

In relational databases, there are multiple tables. Each table contains data about a single thing. Let’s say if there’s a table that has data about Cars and another with Purchases data.

To work with multiple tables at once, we have to join them. A JOIN in SQL allows us to attach rows of one column to the rows of another.

See how I capitalized above? That’s because it’s an SQL keyword. Let’s see what the proper syntax of JOINing two tables look like.

_SELECT *_

_FROM table_a JOIN table_b_

_ON table_a.key_column = table_b.foreign_key_column;_

When you hit that lightning bolt to execute the above query, SQL selects everything from the first table and then checks if values in the mentioned column of the first table matches the values of the mentioned column of the second table. If they match, then great, join them!

Of course, you can do more complicated condition to join the tables. Like, if the values of a column in the first table are smaller than the second one’s _then_ join them.

_SELECT *_

_FROM table_a JOIN table_b_

_ON table_a.key_column <= table_b.foreign_key_column;_

Joining tables by comparing lesser than or greater than operator will be always a rare case because of how less the need/application arises, but it’s always there if you need it.

**NOTE:** Use that semicolon to tell SQL that you are done. Don’t leave it hanging.

---

**KEY COLUMNS**

During comparison, key columns are used to identify rows that are to be related.

For this single striking purpose, all of the key column values must be unique. They are used to identify each row separately. One example of a key column is just the serial number in table. But that is not quite useful as having the same serial numbers in another table won’t be of much information. 

But what _can_ be important is let’s say an ID, a unique code for each row of a table. For example, you can have table about customers’ information, their names, contact details, etc. Each row in this table has a unique ID. Another table can have information on when the customers visited, but instead of using customer’s name, we can use an ID to identify them.  
This way both of the columns will be related.

CREATE TABLE customers   
( Id UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),   
 first_name varchar(25),  
last_name varchar(25) );  
  
INSERT INTO customers VALUES   
(“Max”, “Burton”), (“John”, ”Smith”);  
  
CREATE TABLE visit_date  
(Id UNIQUEIDENTIFIER PRIMARY KEY DEFAULT NEWID(),  
visit_date DATE);  
  
INSERT INTO visit_date   
SELECT Id FROM customers;  
  
INSERT INTO visit_date VALUES  
(“2020–05–11”, “2020–05–12”);

Following the above example, you can have two tables with a column with similar keys.

Let’s take another example. You have data about some school staff and how they are getting paid.   
But instead of arranged nicely in simply a single table, it arrives to you in the format of multiple CSV files. How do you deal with it let alone analyze it?

The answer is straightforward. Let’s work our way through it.

So you now have multiple CSV containing not only teachers’ names and salaries but also for what are they teaching in the school. If you get into a situation like this. Always make sure to create a unique key column for the related tables in the database.

To follow the relational database model, we are going to create a single sharing _id_ for every table. That way the table containing salary information will also be related to the subject of a teacher indirectly.

---

Let’s have a look at the code.

---1  
CREATE TABLE subjects (   
subject_id bigserial,  
subject varchar(100),  
CONSTRAINT subject_key PRIMARY KEY (subject_id));  
  
---2  
CREATE TABLE teachers (   
teacher_id bigserial,  
first_name varchar(50),  
last_name varchar(50),  
salary integer,  
subject_id integer REFERENCES subjects (subject_id),  
CONSTRAINT teacher_key PRIMARY KEY (teacher_id),  
CONSTRAINT teacher_subject_unique UNIQUE (teacher_id, subject_id)  
);  
  
---3  
INSERT INTO subjects (subject) VALUES   
('Mathematics'), ('Chemistry'), ('Chemistry');  
  
INSERT INTO teachers (first_name, last_name, salary, subject_id)  
VALUES  
('John', 'Spektor', 42000, 1),  
('Mary', 'Thomas', 41000, 2),  
('Carly', 'Shelby', 35000, 2);

---

Let’s see what happened in each of the queries above.

1.  We created a table that handles the subject data. It has an index column _subject_id_ that is of type bigserial, so that it increments automatically whenever you add values to the table.   
    Then, simply a varchar subject name.  
    **_But, what’s that last line about?_** Constraints are rules that a table _has_ to follow. Here, we set the primary key constraint which means that all of the rows in this table has to be different. The subject_id becomes the primary key and subject_key is the name of the primary key surrounded by the keywords CONSTRAIN and PRIMARY KEY. This means that each record will have a unique identifier (in this case, _subject_id_).  
      
    
2.  It’s easy stuff till we define salary column as an integer. We created a table about teachers’ information.  
    Then, we use the REFERENCES keyword to tell Postgresql that the subject_id for each teacher’s subject will reference the subject_id from the subject table we created earlier.   
    Similar to the subject table, we then create teacher_id primary key for our teacher’s table.   
    Now, we saw the keyword PRIMARY KEY. UNIQUE is similar to it. It makes sure that all of the entries in our table cannot have same (teacher_id, subject_id) meaning that a single teacher cannot teach multiple subjects. Not the most perfect example out there, but it works well to explain and makes me understand as well.  
      
    
3.  Now, we are just inserting values in the tables. Note that, when doing insertion in the teachers table, two of the teachers have the same subject_id. That can be possible as the another teacher can be the substitute teacher. 

You can notice that in the second table, the subject_id references the subject_id in the first one. Note that this is only possible if the first table has a column named subject_id. This subject_id in the teacher’s table called a foreign key.

**_Many questions arise, the most important one being how does arranging our data like this benefit us?_**

Let’s say if you had all the data arranged in the same table. What would you risk then?

1.  If we had data about multiple schools instead of one, which would be the case, then multiple teachers would teach the same subject. Let’s say they are teaching “Defense against the dark arts”, if you have a few hundred rows, it’s not a big deal because you can repeat that information. But when you are dealing with a million columns, having a string repeating, for let’s say, more than 100k times, it is going to consume a lot more memory than simply assigning an integer id (like we did).
2.  What if they change the name of the subject “Defense against the dark arts” to “The cursed subject” tomorrow? You’d have to update all of the entries if you had a single table. That is not the case here as you’d simply update the name once in the subject’s table.

**How Does Querying With JOIN Works?**

When you JOIN two tables using the query mentioned earlier, SQL joins all of the columns at the rows that satisfies the condition that we put in.

For example,

SELECT *  
FROM teachers JOIN subjects  
ON teachers.subject_id = subjects.subject_id;

The above query returns all the rows where both of the IDs are common. Meaning you’d get a table that contains all the information with combination of teachers teaching specific subjects instead of just the subject ids. Like this:

![](https://cdn-images-1.medium.com/max/1000/1*lwv0NDs5mlrk5LZ-2YR81A.png)

  

Hence, even though the tables are separate, you now have a unique view in a single table.

**Types of JOIN**

While joining two tables, you can specify in the query that how do you want to join them.

The query that we wrote above mentions two tables, one on the left, the other on the right. It’s important to see that distinction as that is how types of JOINS are separated. 

1.  JOIN
2.  LEFT JOIN
3.  RIGHT JOIN
4.  FULL OUTER JOIN
5.  CROSS JOIN

JOIN

If you join two tables using this type of JOIN (alternate syntax is INNER JOIN). SQL will return rows from both tables where matching values are where you joined the two tables.

LEFT JOIN

This will return every row from the left table along with rows that match in the joining column from the right table.  
What happens when left table doesn’t have a match in the right table? The result shows nothing from the right side.

RIGHT JOIN

This will return every row from the right table along with rows that match in the joining column from the left table.  
What happens when the right table doesn’t have a match in the left table? The result shows nothing from the left side.

FULL OUTER JOIN

All of the rows are returned from the left and right table both, then rows are joined where the values are matched.

CROSS JOIN

This returns everything that is possible from the combination of the two tables. Based on the joining column of course.
