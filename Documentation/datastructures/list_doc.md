#### File - list.cpp


#### Function: generateRandom

```cpp
template<typename T>
void generateRandom(unordered_set<T>& rs, const int MAX, const int N)
```

1) Generates a unique set of random integers.

This function will utilize an unordered set for generating
unique random integers. The find operation will be useful due to
constant time on average.

**Parameters**
- `rs` , the random set utilized to store random integers.
- `MAX` bound, the value set for the highest range for the distribution.
- `N` bound, the value set for the number of random integers to generate.

**Return Value**

1) `void`, however will output to stderr for measurements.

**Complexity:** At most `(N*MAX)` steps

#### Function: insert
```cpp
template<typename T>
void insert(const unordered_set<T> us, list<T>& lis);
```
1) Inserts elements from a randomly unsorted set in non-decreasing order into a list.

This function will iterate over an unordered set and sorting in place in non-decreasing
order into a list by utilizing an offset.

**Parameters**
- `us`, the random set iterated on.
- `lis`, the list to be inserted into.

**Return Value**

1) `void`, however will output to stderr for measurements.

**Complexity:** At most `(N*M)` steps

#### Function: erase
```cpp
template<typename T>
void erase(list<T>& lis)
```
1) Erases random elements within a list.

This function creates a random integer based on a distribution sized by the
shrinking list size. An iterator will be generated on the list to use as an
offset for deletion.

**Parameters**
- `lis`, the list to be used to randomly delete elements until empty.

**Return Value**

1) `void`, however will output to stderr for measurements.

**Complexity:** At most `(N)` steps

#### Function: find

```cpp
template<typename T>
bool find(list<T>& lis, T target)
```

1) Finds a target within a sorted list utilizing binary search.

This function will return a boolean based on whether or not target
is within list.

**Parameters**
- `lis`, the list to search in.
- `target`, the desired element.

**Return Value**

1) `bool`, `1` if element is in list `0` otherwise.

**Complexity:** At most `(log N)` steps

**Example of all functions within list.cpp:**
```cpp
int main() {
  int MAX = 1000000;
  int N = 10000; // Default num integers.
  unordered_set<int> rs;
  generateRandom(rs,MAX,N);
  list<int> lis;

  auto start = system_clock::now();
  insert(rs,lis);
  find(lis.begin(),lis.end(),*rs.begin());
  erase(lis);
  auto end = system_clock::now();
  auto time_trial = duration_cast<milliseconds>(end-start).count();
  cerr << "List Time: " << time_trial << "ms\n";

	return 0;
}
```
