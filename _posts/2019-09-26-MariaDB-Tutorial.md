---
layout: post
title: "MariaDB Tutorial Summary from Internet"
use_math: false
lang: en
tags: notes
desc: This is a record of basic operations of MariaDB on Manjaro OS. 
---

<br>

### 1. MariaDB Installation on Manjaro 

Reference: [manjaro.site](https://manjaro.site/a-complete-guide-to-install-mariadb-server-on-manjaro-18-0/) 

```shell
# installation
sudo pacman -S mariadb

# testing
mysqladmin --version

# first initialization
sudo mysql_install_db --user=mysql --basedir=/usr --datadir=/var/lib/mysql

# start and enable the server
# for 'restart', 'stop' also
sudo systemctl start mariadb
sudo systemctl enable mariadb

# Initial settings, just follow the recommendations
sudo mysql_secure_installation

# Optional: install mysql-workbench, which provides a GUI management tool
# sudo pacman -S mysql-workbench
```

First time log in: 

```shell
sudo mysql -u root -p
```

**Suggestion:** Do not try to get rid of the `sudo` by any operation on the default `'root'@'localhost'` account. 

After logging in MariaDB, we can check the default databases: 

```mysql
show databases;
```

<br>

### 2. Account Management 

Reference: [cnblogs.com/conanwang](https://www.cnblogs.com/conanwang/p/5932579.html) 

**Create, drop, rename an user account.** 

```mysql
# create an account
create user 'user_name'@'host' [identified by 'password']

# drop an account
drop user 'user_name'@'host';

# rename an account
rename user 'old_user_name'@'host' to 'new_user_name'@'host';
```

Note that, `host` constrains the request host where users visit the account. Even with a same name, different hosts mark different accounts. 

If an account doesn't require a specific host, the wild-card character `%` can be applied. 

<br>

**Privileges management of an account.** 

```mysql
# show grants of an account
show grants for 'user'@'host';

# grant an account
grant (privileges) on (db.table) to an 'user'@'host' [identifed by 'password'];

# revoke the privileges on an account
revoke (privileges) on (db.table) from 'user'@'host';
```

Here `db.table` means a specific table from a database. If we want to grant all privileges on all databases or all tables of a database, we can use `*`. 

The `(privileges)` should be replaced by specific privileges list. 

<br>

**Example.** 

```mysql
create database test;
create user 'jonathan'@'localhost' identified by '123456';
grant all on test.* to 'jonathan'@'localhost'; # for "root" we add "with grant option"
show grants for 'jonathan'@'localhost';
```

We will use the account `'jonathan'@'localhost'` as example in our following examples. 

<br>

### 3. Database & Table Management 

Reference 1: [w3cschool](https://www.w3cschool.cn/mariadb/mariadb_introduction.html)<br>
Reference 2: [liaoxuefeng.com](https://www.liaoxuefeng.com/wiki/1177760294764384) 

**Basic Operations.** 

```mysql
# database
create database (database_name);
drop database (database_name);
use (database_name);

# table
show tables;
desc (table_name); # check table structure
create table (table_name) (col_name col_type [not null auto_increment], ..., primary key (key_col)); # auto_increment for key column only
drop table (table_name);

# add a column on a table
alter table (table_name) add column (col_name) (type) [not null];
# change the name of a column
alter table (table_name) change column (old_col_name) (new_col_name) (type) not null;
# delete a column
alter table (table_name) drop column (col_name)
```

<br>

**Types.** 

Note, the `type` here could be any listed on [techonthenet.com](https://www.techonthenet.com/mariadb/datatypes.php). Here is a short note of the webpage:

*1. Strings:* 

| Type              |  Max Size   | Explanation                                                  |
| ----------------- | :---------: | ------------------------------------------------------------ |
| CHAR(size)        |  255 chars  | Fixed-length strings. Space padded on right to equal size characters. |
| VARCHAR(size)     |  255 chars  | Variable-length string.                                      |
| TEXT(*size*)      | 65535 chars |                                                              |
| LONGTEXT(*size*)  |  4GB chars  |                                                              |
| BINARY(*size*)    |  255 chars  | Fixed-length strings. Space padded on right to equal ***size*** characters. |
| VARBINARY(*size*) |  255 chars  | Variable-length string.                                      |

*2. Numerics:* 

| Type            | Range (Signed)                              | Range (Unsigned)          | Explanation                                                  |
| --------------- | ------------------------------------------- | ------------------------- | ------------------------------------------------------------ |
| BIT             | -128 to 127                                 | 0 to 255                  |                                                              |
| TINYINT(*m*)    | -128 to 127                                 | 0 to 255                  |                                                              |
| SMALLINT(*m*)   | -32768 to 32767                             | 0 to 65535                |                                                              |
| MEDIUMINT(*m*)  | -8388608 to 8388607                         | 0 to 16777215             |                                                              |
| INT(*m*)        | -2147483648 to 2147483647                   | 0 to 4294967295           |                                                              |
| BIGINT(*m*)     | -9223372036854775808 to 9223372036854775807 | 0 to 18446744073709551615 |                                                              |
| FLOAT(*m*,*d*)  |                                             |                           | Where ***m*** is the total digits and ***d*** is the number of digits after the decimal. |
| DOUBLE(*m*,*d*) |                                             |                           | Where ***m*** is the total digits and ***d*** is the number of digits after the decimal. |
| BOOL            |                                             |                           | Synonym for TINYINT(1). Treated as a boolean data type where a value of 0 is considered to be FALSE and any other value is considered to be TRUE. |

*3. Dates:* 

| Type           | Max Size                                               | Explanation           |
| -------------- | ------------------------------------------------------ | --------------------- |
| DATE           | '1000-01-01' to '9999-12-31'                           | 'YYYY-MM-DD'          |
| DATETIME       | '1000-01-01 00:00:00' to '9999-12-31 23:59:59'         | 'YYYY-MM-DD HH:MM:SS' |
| TIMESTAMP(*m*) | '1970-01-01 00:00:01' UTC to '2038-01-19 03:14:07' UTC | 'YYYY-MM-DD HH:MM:SS' |
| TIME           | '-838:59:59' to '838:59:59'                            | 'HH:MM:SS'            |
| YEAR[(2\|4)]   | Year value as 2 digits or 4 digits.                    | Default is 4 digits.  |

*4. Large Objects:* 

| Type         | Max Size         | Explanation                                           |
| ------------ | ---------------- | ----------------------------------------------------- |
| TINYBLOB     | 255 bytes        |                                                       |
| BLOB(*size*) | 65,535 bytes     | Where ***size*** is the number of characters to store |
| MEDIUMBLOB   | 16,777,215 bytes |                                                       |
| LONGTEXT     | 4GB              |                                                       |

<br>

**Example.** 

We login with the account `'jonathan'@'localhost'` and add a table `userlist` into database `test`. The dataset contains `name`, `password` and `type` of the users. Here `type` could be 

- 0 for superviser;
- 1 for users;
- 2 for managers;

```mysql
use test;
create table userlist (id int not null auto_increment, primary key (id));
alter table userlist add column name varchar(255) not null;
alter table userlist add column password varchar(255) not null;
alter table userlist add column type char(1) not null;
desc userlist;

+----------+--------------+------+-----+---------+----------------+
| Field    | Type         | Null | Key | Default | Extra          |
+----------+--------------+------+-----+---------+----------------+
| id       | int(11)      | NO   | PRI | NULL    | auto_increment |
| name     | varchar(255) | NO   |     | NULL    |                |
| password | varchar(255) | NO   |     | NULL    |                |
| type     | char(1)      | NO   |     | NULL    |                |
+----------+--------------+------+-----+---------+----------------+
3 rows in set (0.001 sec)
```

<br>

### 4. Data manipulation

```mysql
# Insert data into a table
insert into (table_name) (col_1, col_2, ...) values (v_1, v_2, ...), (v_1, v_2, ...);

# Update data of a table
update (table_name) set col_1 = v_1, col_2 = v_2, ... where ...;

# Remove data from a table
delete from (table_name) where ...
```

<br>

**Example.** 

We want to add a user into our `test.userlist` table. The user is called `'jonathan'`, and the password is `'123456'`.

```mysql
# check whether 'jonathan' already exists
select * from userlist where name = 'jonathan';
Empty set (0.000 sec)

# if not exists, insert a new item
insert into userlist (name, password, type) values ('jonathan', '123456', 0);
```

Note that, here we do not set the value of `id`, because it is set to increase its value automatically. 

