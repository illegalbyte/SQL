     SELECT name FROM customers ORDER BY name     
     SELECT name FROM customers ORDER BY id     
     SELECT name FROM customers ORDER BY state, name          
**ORDER BY** ➔ Orders results alphabetically or numerically based on column given. Adding a second column allows for duplicates of the first entry to be sorted by the second's criteria.  
     SELECT name FROM customers ORDER BY id DESC        
**ORDER BY x DESC** ➔ Orders results in descending order or, reverse alphabetical order.  
     SELECT id FROM customers ORDER BY id DESC LIMIT 1       
**ORDER BY + LIMIT 1** ➔ Orders a list in descending order, but limits to 1 result. In abstract: retrieving the highest value. This would also work with alphabetical entries.  