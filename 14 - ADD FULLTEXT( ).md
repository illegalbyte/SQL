	ALTER TABLE items ADD FULLTEXT(name)
**ADD FULLTEXT()** ➔ Enables full text searching on a table column. 

	SELECT name, cost FROM items WHERE Match(name) Against("car")
**Fulltext search** ➔ Faster than other search queries. 'Search engine' like behaviour. (faster than LIKE and REGEXP).  