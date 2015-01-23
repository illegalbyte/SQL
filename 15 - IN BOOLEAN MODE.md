	SELECT name, cost FROM items WHERE Match(name) Against("-car +box" IN BOOLEAN MODE)
**IN BOOLEAN MODE** ➔ Enables google dork like operators to the search statement your matching Against().   