	INSERT INTO items VALUES('101','WD HD','300','1','0')
**INSERT INTO** ➔ Finally, what you've been waiting for. A way of inputting data to the database. 

	INSERT INTO items(id,name,cost,seller_id, bids) VALUES(101,'WD22','10','1','0')
**Specifying input order** ➔ By using items(x,x,x,x) we have specified the order of the data that we will be inputting using VALUES. Despite any changes to the table's order, this will still function properly.  

***Default** value for **numbers** is **0***   
***Default** value for **strings** is **'null'***  

	INSERT INTO items(id,name,cost,seller_id, bids) VALUES (101,'WD22','10','1','0'),
	(102,'WD21','12','1','0'),
	(103,'WD23','10','1','0')
**Multiple INSERTs** ➔ How to input mutiple VALUES using brackits and commas. 

	INSERT INTO items(id, name, cost, seller_id, bids) SELECT id, name, cost, seller_id, bids FROM anothertable 
**INSERT INTO + SELECT** ➔ If you wanted to merge two tables - that had the same structure - together.