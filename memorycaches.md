# Memory Caches

## 1. Locality

- Caching involves **pairing a small, fast memory** (cache) with a **large, slow memory** (main memory/RAM).
- Caches exploit locality, which refers to:
  - **Spatial locality:** Accesses to nearby addresses tend to occur close together.
  - **Temporal locality:** Recently accessed data is likely to be accessed again soon.
- Writing cache-friendly code that exhibits good locality can significantly **improve performance**.

### How to build a cache that uses temporal locality
- Maintain recently accessed data in the cache.
- Prioritize evicting data that hasn't been accessed recently.

### How to build a cache that uses spatial locality
- Organize memory access patterns to utilize spatial locality.
- Optimize data structures and access patterns to minimize cache misses.

**Example:**
Consider two functions computing the same value from a 2D array `a`:
```c
double loop1(double **a, size_t n) {
  double frobenius = 0;
  for(int i=0; i<n; i+=1)
    for(int j=0; j<n; j+=1)
      frobenius += a[i][j]*a[i][j];
  return sqrt(frobenius);
}

double loop2(double **a, size_t n) {
  double frobenius = 0;
  for(int j=0; j<n; j+=1)
    for(int i=0; i<n; i+=1) 
      frobenius += a[i][j]*a[i][j];
  return sqrt(frobenius);
}
```
`loop2` runs much **faster** than `loop1` for large `n` due to better cache utilization. In `loop2`, **accessing elements column-wise exploits spatial locality**.

## 2. Warming up the cache

- Cache misses occur when accessed data is not found in the cache.
- Cold misses occur the first time a region of memory is accessed.
- Warming up the cache involves running code once before timing to reduce cold-cache runtime.
- For cold-cache runtime measurements, the cache can be flushed by accessing large amounts of memory.

## 3. Caching everywhere

- Caching is ubiquitous in computing, utilized in memory hardware, disks, browsers, and various software applications.
- Cache systems can sometimes lead to **unexpected behaviors**, such as using stale copies of data.
- Managing cache coherence and resolving staleness are complex topics beyond the scope of this discussion.
