	SELECT name, cost, bids FROM items WHERE bids >100
	UNION
	SELECT name, cost, bids FROM items WHERE cost >200  
**UNION** ➔ This simple keyword joins a two queries' results into one data set. If you did the above without union, the query would effectively be run twice and give you two datasets. Useful for complex filtering. *NOTE:* When using unions, your columns must be the **same** for both queries.  

	SELECT name, cost, bids FROM items WHERE bids >100
	UNION ALL
	SELECT name, cost, bids FROM items WHERE cost >200
**UNION ALL** ➔ Allows you to 