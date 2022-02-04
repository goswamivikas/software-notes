# Suffix Trees and Arrays

**Input Description:** A reference string $S$.

**Problem Description:** Build a data structure for quickly finding all places where an arbitrary query string q occurs in $S$.

**Discussion:**

- A ***suffix tree*** is simply a trie of all proper suffixes of $S$
- a suffix tree enables to test whether $q$ is a substring of $S$, because any substring of $S$ is the prefix of some suffix.
- a ***suffix array*** is a sorted array of all suffixes of $S$
- efficient substring search $O(lg\;n)$ string comparisons utilizing binary search
- one method to build a suffix array is to first build a suffix tree and perform an in-order traversal t read the strings in off in sorted order

<aside>
💡 Please watch [this](https://www.youtube.com/watch?v=hLsrPsFHPcQ) for a better understanding of suffix trees.

</aside>

**Applications:**

- find all occurrences of q as a substring of $S$
- longest substring  common to a set of strings
- find the longest palindrome in $S$