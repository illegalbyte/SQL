	SELECT seller_id, COUNT(*) AS item_count FROM items GROUP BY seller_id   
**GROUP BY** ➔ Similar to a WHERE statement but it covers all the values. The above use-case retrieves all the seller_ids and shows their item_count.  

	SELECT seller_id, COUNT(*) AS item_count FROM items GROUP BY seller_id HAVING item_count>2 ORDER BY item_count DESC  
**HAVING** ➔ HAVING is similar to WHERE, but for GROUPS.  