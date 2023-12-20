![[Pasted image 20231204232534.png | 600]]

Big memories are slower then smaller memories because increased decoding, multiplexing, for larger number of entities along with the signal needed to propagate further for each entry.

# DRAM (Dynamic Ram)

Composes main memory and made out of a single transistor & capacitor. 

This capacitor leaks charge so it requires periodic refreshing to maintain state. 

DRAM has a larger energy footprint because of this, and is more volatile due to it's dependent on energy. 

However it is cheap & dense.

# SRAM (Static Ram)

Composed of d-flip-flops, which made out of six transistors.

No need for refreshing state, but a lot of power is still used.

More expensive since more hardware is required.

# Secondary Storage

Non-volatile, external storage.

**Hard Drives** (HDD)
- Magnetic Storage on spinning disks
- Large capacity, but slow

**Solid-State** Drives (SSD)
- Flash memory
- Faster access times and transfer rates
- More expensive

Most systems use hybrid approach.

# DRAM vs SRAM

SRAM:
- Is faster (6x+)
- Requires more parts
- More expensive (5-20x+)

Large main memory thus utilizes DRAM, while more frequently accessed memory uses SRAM (cache).

# Cache

Main memory access can take 40ns (1GHz processor a cycle is 1ns)

Cache can take 5ns or less to access with the goal of getting to 1 clock cycle.

Cache contains copies of  predicted relevant main memory values, by exploiting typical data access patterns.

# Exploited Patterns

**Temporal Locality** - values that have been used before may be used again soon

**Spatial Locality** - values that are next to each other in memory are likely to be used soon