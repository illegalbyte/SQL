     UPPER(name)        
➔ Uppercase function.   

     SQRT(cost) AS square_root       
➔ Sqrt() gets the square root.  

     SELECT AVG(cost) AS average_cost FROM items        
➔ Avg() gets the average.   

     SELECT SUM(bids) AS bids FROM items       
➔ Sum() adds all numbers in a column.  

     SELECT COUNT(name) FROM items WHERE seller_id = 6       
➔ Counts how many items seller6 is selling.  

    SELECT COUNT(*) AS item_count,
	MAX(cost) AS max
	FROM items WHERE seller_id = 12       
➔ How to use multiple aggregate functions, and MAX()/MIN() which return the highest/lowest number, respectively. 
**FUNCTIONS**  