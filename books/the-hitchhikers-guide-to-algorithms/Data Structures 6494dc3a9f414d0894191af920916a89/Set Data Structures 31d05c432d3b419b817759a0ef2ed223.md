# Set Data Structures

**Input:** A universe of items $U = \{u_1,...,u_n\}$ on which is defined a collection of subsets $S =  \{S_1,...,S_n\}$

**Problem description:** Represent each subset so as to efficiently $1.$ test whether $u_i \in S_j$ , $2.$ compute the union or intersection of $Si$  and $S_j$, and $3.$ insert and delete members of $S$

**Discussion:**

- *multisets* permit elements to have more than one occurrence, the data structure for which can be extended by maintaining a count field, or a linked list of equivalent entries for each element
- when every subset contains exactly two elements, they can be thought of edges in *graph*, if we remove the cardinality restrictions, it could be thought as *hypergraph*

 **Implementation Choices:**

- **Bit Vectors**
    - An $n$-bit vector can represent any subset $S$  on a universal set $U$ containing $n$ items.
    - Bit i is set to 1 if $i \in S$, and 0 if not. perform “and-ing” or “or-ing” for intersection and union respectively.
    - space-efficient. the primary drawback is its performance on sparse subsets
- **Containers or dictionaries**
    - A subset $S$ can also be represented using a linked list, array, or dictionary containing exactly the elements in $S$