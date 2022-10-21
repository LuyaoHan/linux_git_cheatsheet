# Terminologies
	Blocks (or "lines") = continugous memories from the main memory.

# Cache size = Block Size * #Blocks/Set * #Sets
			 = Block Size * Associativity * #Sets

# Three kind of cache miss
	- Cold Miss: First time access a data not present in cache
		- Fix: increase block size, bring more data for a miss and use spatial locality.
	- Capacity: Cache to small relative to secondary memory, not be able to hold all concurrently required data.
		- Fix: Increase cache capacity, improve both by spatial and temporal locality.
	- Conflit Miss: Two addresses mapped to the same address.
		- Fix: Higher associativity. Same address more space, cause lower miss rate but higher delay.
	
