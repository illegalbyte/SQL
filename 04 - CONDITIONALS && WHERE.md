``SELECT id, name FROM customers WHERE id>10``  
``SELECT id, name FROM customers WHERE id<10``  
``SELECT id, name FROM customers WHERE id<=10``  
``SELECT id, name FROM customers WHERE id>=10``  
``SELECT id, name FROM customers WHERE id!=10``  
``SELECT id, name FROM customers WHERE id=10``  
``SELECT id, name FROM customers WHERE name = 'Charlie Jones'``  
**WHERE** ➔ This allows basic expressions to be used in your query. Non numeric equality statements must be wrapped in quotes. 
``SELECT id, name FROM customers WHERE id BETWEEN 10 AND 20``  
**WHERE + BETWEEN** ➔ Allows you to define a range between two numbers.  
``SELECT id, city, state, name FROM customers WHERE state='MA' AND city='Boston'``  
**WHERE + AND** ➔ Equivalent to '&&' syntax.  
``SELECT id, city, state, name FROM customers WHERE state='MA' OR state='DC'``  
**WHERE + OR** ➔ Equivalent to '||' syntax.  
``SELECT id, city, name FROM customers WHERE (id=1 OR id=50) AND city='Rayleigh'``  
**WHERE + ()** ➔ For parsing your WHERE statements correctly.  
