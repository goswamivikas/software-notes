# Dictionaries

**Input description:** A set of n records, each identified by one or more keys.

**Problem description:** Build and maintain data structure to efficiently locate, insert, and delete the record associated with any query key q.

<aside>
💡 carefully isolate the implementation of any data structure from its interface

</aside>

**Discussion:**

- how many items will you have in your data structure?
    - simple implementation enough?
    - consider running out of memory?
- do you know the relative frequencies of insert, delete and search operations?
    - decide static, semi-dynamic, or fully-dynamic data structures accordingly
- will the access pattern of keys be uniform and random?
    - distribution is skewed in many applications.
    - elements have **temporal locality** - meaning elements likely to be repeatedly accessed in clusters instead of at fairly regular intervals.
    - data structures such as **splay trees** can take advantage of a skewed and clustered universe.
- is it critical that each individual operation be fast, or only that the total amount of work done over the entire program be minimized?
    
    

**Implementation Choices:**

- ***unsorted linked lists or arrays***
    - unsorted array - very easy to maintain
    - Linked structures can have terrible cache performance compared to array
    - once the dictionary becomes larger, linear search time is not maintainable
    - ***self-organizing list*** - whenever a key is accessed or inserted, move it to head. much better than sorted or unsorted lists as it utilizes uneven access frequencies and temporal locality (aka locality of reference)
- ***sorted linked list or arrays***
    - lists not worth the effort, can’t perform binary search in such a data structure
    - a sorted array will be appropriate iff there are not many insertions and deletions
- ***hash tables***
    - for applications involving a moderate-to-large number of keys, a hash table is probably the right way to go.
    - use a function(*aka hash function*) to map all keys between 0 and m-1, maintain an array of m buckets, each bucket implemented as an unsorted linked list
        
        ![a hash table representation from Wikipedia, here m=256](Dictionaries%20153dc4759cfc49c2a406c42ea0e03bbf/hashtable-wiki.png)
        
        a hash table representation from Wikipedia, here m=256
        
    - A well-tuned hash table will outperform a sorted array in most application
    - pertinent questions
        - how do i deal with collisions? [open addressing vs bucketing](https://stackoverflow.com/questions/2556142/chained-hash-tables-vs-open-addressed-hash-tables)
        - how big should the table be?
            - with bucketing m $\approx$ number of items you expect.
            - with open addressing m $\approx$ 30% to 50% larger
            - selecting m to be a prime number minimizes the dangers of a bad hash function. [check here.](https://stackoverflow.com/questions/1145217/why-should-hash-functions-use-a-prime-number-modulus)
            - what hash function should i use?
- **binary search trees**
    - may use balanced trees like AVL, 2/3, red-black trees and splay trees
    - depends on implementation rather than a particular flavor
- **B-trees**
    - self-balancing tree data structure
    - the idea behind a B-tree is to collapse several levels of binary search tree into a single large node, so that we can make the equivalent of several search steps before another disk access is needed
    - well suited for storage systems that read and write heavy blocks of data

**C++ Implementations**

```cpp
// implemented as red-black tree in c++
std::map<string, int> my_map;
std::multimap<string, int> my_map1; //allows duplicate keys

// implemented as hash tables in c++
std::unordered_map<string, int> hash_map;
std::unordered_multimap<string, int> hash_map1; //allows duplicate keys

// some common operations available on above implementations
my_map.insert({"aman", 25});
my_map.insert(pair<string, int>("axe", 26));

my_map.begin(); // return itr to beginning
my_map.end(); // return itr to end, after last element
my_map.size() ;
my_map.max_size();
my_map.empty();

my_map.erase(itr position);
my_map.erase(const key);
my_map.clear()
```