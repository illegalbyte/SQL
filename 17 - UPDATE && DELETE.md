	UPDATE items set name='cardboard box' WHERE name='box'
**UPDATE .. WHERE** ➔ Edits the value of a column based on a WHERE statement. 

	UPDATE items SET name='red box', bids='2' WHERE id=10 
**UPDATE multiple columns in same row** ➔ Self explanatory... Just separate the SET expressions with commas. 

	DELETE FROM items WHERE name='cardboard box'
**DELETE** ➔ Allows you to delete rows. 