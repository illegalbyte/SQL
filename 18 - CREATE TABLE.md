	CREATE TABLE users(
	id int, 
	username varchar(30),
	password varchar(60),
	PRIMARY KEY(id)
	)
**CREATE TABLE** ➔ Create a freaking table! PRIMARY KEY(x) specifies which column is the primary key. 

	CREATE TABLE users(
	id int NOT NULL AUTO_INCREMENT, 
	username varchar(30) NOT NULL,
	PRIMARY KEY(id)
	)
**NOT NULL** ➔ Specifies that your table column cannot be empty (aka NULL).   
**AUTO_INCREMENT** ➔ Automatically increases by 1 every time a new row is made. 
