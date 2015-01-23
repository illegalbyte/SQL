	SELECT name, cost FROM items WHERE cost>(	
		SELECT AVG(cost) FROM items
	) ORDER BY cost DESC  
**Subqueries** ➔ Wrap a query within a query in brackets. The above example retrieves all the items that cost more than the average price (and then orders them in DESC).  


	SELECT name, MIN(cost) FROM items WHERE name LIKE '%boxes' AND seller_id IN (
		SELECT seller_id FROM items WHERE name LIKE '%boxes'
	)
**Subqueries 2** ➔ A more useful example that incorporates the IN operator to limit our search to only those sellers that are actually selling boxes.