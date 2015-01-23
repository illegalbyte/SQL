``SELECT name FROM items WHERE name LIKE 'new%'``  
``SELECT city FROM customers WHERE city LIKE 'h%d'``  
**LIKE + %** ➔ Returns all names that start with new%. '%' is a wildcard in this case. This statement is not case-sensitive.  
``SELECT state FROM customers WHERE state LIKE '_L'``   
**LIKE + \_** ➔ The '\_' wildcard specifies a single character wildcard.   


``SELECT name FROM items WHERE name REGEXP 'new'``  
**REGEXP** ➔ Allows for a regular expression to be used.  