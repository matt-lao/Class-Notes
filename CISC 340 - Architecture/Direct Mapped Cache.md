Each main memory address is mapped to exactly a single spot in cache. 

This can be achieved using the *MOD* operation on the address, since it defines a set of values by generating remainders.

However MOD is expensive, so using a couple of the LSBs works as a remainder. How many bytes depends on what you are dividing by (how many spots in memory).

However the addresses are byte aligned (multiples of 4), so we ignore the first two LSBs.


# Reading From Cache

Address value should be stored along with value so the value coming from cache.

Address is made up of:
- Byte offset 
- Index - index in cache
	- The number of bits for the index is determined by the number of entries
- Tag - id for address value has in main memory
	- Left over bits


# Valid Bits

Cache serves all programs so the validity bit is set to 0 if the value in cache is for a program that is finished. If the entry is valid, the validity bit will be 1.

# Hardware

![[Pasted image 20231206175901.png | 600]]

# Access Patterns

Temporal Locality is exploited as the value stays in the cache until it is overwritten by data at an address that has a collision with the one currently in cache.

# Spatial Locality

Direct mapped cache does not exploit spatial locality.

In order to exploit spatial locality is to grab words in blocks.

![[Pasted image 20231206180314.png]]

The block offset is included in the address to indicate which word in the block an entry is.

# How to determine make up of an address

- Byte offset is always 2 bits
- Block offset is determined by the block size (need to enumerate all words in a block)
- Index is determined by the number of entries (need to enumerate all entries)
	- Divide # of words cache can hold by word block size to find number of entries
- Tag uses the remaining bits

# Quiz
- Write Through
	- Write to memory
	- Needs a buffer
- Write Back
	- Write to cache
	- Write to main memory when victimized
	- If we have a collision, we need to victimize the block in cache, and then fetch block of memory we want.
		- Requires a stall
	- Things are only written back when the block is victimized
- Victimization
	- when a block is removed from the cache to make room for new block
- Block size
	- Block offset tells us which word
	- Increases collisions if block size is larger (and number of entries is smaller)