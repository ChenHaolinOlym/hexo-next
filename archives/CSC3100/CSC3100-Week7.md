---
title: CSC3100 Week7
tags:
  - CSC3100
  - Data Structure
  - Algorithm
categories:
  - note
  - CSC3100
date: 2019-09-30 14:15:05
mathjax: true
---

Hashing

## The Search Problem

Find items with keys matching a given search key

- Given an array A, containing n keys, and a search key x, find the index i such as x=A\[i\]
- As in the case of sorting, a key could be part of a large record.

### Applications

- Keeping track of customer account information at a bank
- Keep track of reservations on flights
- Search engine 
- Applications need a lot of queries (once inserted, delete operations are not very often)

## Direct Addressing

**Assumptions:**

- Key values are distinct
- Each key is drawn from a universe U = {0, 1, . . . , m-1}

**Idea:**

- Store the items in an array, indexed by keys

**Direct-address table representation:**

- An array T[0 . . . m - 1]
- Each corresponds to a key in U
- T\[k\] stores a pointer to x (or x itself) with key k
- T\[k\] may be empty

**Notations:**

U - universe of keys
K - actual keys

### Compare with Other Solutions

Solution | Insert | Search
:-: | :-: | :-:
direct addressing | O(1) | O(1)
ordered array | O(N) | O(logN)
ordered linked list | O(N) | O(N)
unordered array | O(1) | O(N)
unordered linked list | O(1) | O(N)

## Hash Table

When K is much smaller than U, a hash table requires much less space than a __*direct-address table.*__

- Can reduce storage requirements to |K|
- Can still get O(1) search time, but on the *average* case, not the worst case

### Consist of

- A fixed size array
- A hashing function
- The key of each element is mapped (hashing) into some number in the range 0 to *TableSize - 1*, and placed in the appropriate cells.

### Hash Function

The mapping function is called a hash function, which ideally:

- Should be simple to compute;
- Should ensure that any two distinct keys get different cells;
- Or should distribute the keys evenly among the cells.

#### Remaining Problem

- Choose a hash function;
- Decide on the table size;
- Decide what to do when two keys hash to the same value (this is known as a **collision**).

#### Simple Hash Function

For numeric keys, one simple hash function is **_Key_ mod _TableSize_**, where *TableSize* is a **prime** number.

**Load Factor:** Ratio of the number of elements in the hash table to the table size. Often control as 0.5

### Solution of Hashing Collision

#### Separate Chaining

Keep a list of all elements that hash to the same value.

![1](1.png)

- Chaining could be through a list or a tree.
- A disadvantage of separate chaining is that it requires a second data structure for the chains. Time is required for the allocation of new cells on insertion.

##### Insert

- Find the hash index for the given key
- hash_index = key % size of table
- Insert a node into a linked list depending on the hash index
- Example,
  - Insert 33 to the hash table with 10 linked list
  - Hash_index = 33 % 10 = 3
  - The hash table’s 4th linked list will be used to store 33

##### Analysis

Worst Case: all elements hash into the same slot, the search is $\Theta n$

Average Case: depends on how well the hash function distributes the n keys among the m slots

If *Simple uniform hashing assumption* (Any given element is equally likely to hash into any of the m slots) is true, the search is $\Theta (\frac{n}{m})$

##### Load Factor

Load factor of a hash table T:
$\alpha = \frac{n}{m}$
n = # of elements stored in the table
m = # of slots in the table = # of linked lists

$\alpha$ encodes the average number of elements stored in a chain
$\alpha$ can be <, =, > 1

##### Successful Search and Unsuccessful Search

###### Unsuccessful Search

An unsuccessful search in a hash table takes expected time $\Theta (1+\alpha)$ under the assumption of simple uniform hashing (i.e. item not in the table)

###### Successful Search

Takes $\Theta (1+\frac{a}{2})$

(search half of a list length plus $O(1)$ to compute hash)

##### Average Time

If m (# of slots) is proportional to n (# of elements in the table):

- $n = O(m)$
- $\alpha = \frac{n}{m} = \frac{O(m)}{m} = O(1)$

So searching takes constant time on average

#### Open Addressing

- If we have enough contiguous memory to store all the keys (m > N), we can store the keys in the table itself
- No need to use linked lists anymore
- Basic idea:
  - Insertion: if a slot is full, try another one, until you find an empty one
  - Search: follow the same sequence of probes
  - Deletion: more difficult ... (we’ll see why)
- Search time depends on the length of the probe sequence.

##### Hash Function

A hash function contains two arguments now: *Key Value* and *Probe Number*.

h(k,p), p=0,1,...,m-1

##### Probe Sequences

<h(k,0), h(k,1), ..., h(k,m-1)>

- Must be a permutation of <0,1,...,m-1>

- There are m! possible permutations 

##### Collision Resolution Strategies

- Linear Probing
- Quadratic Probing
- Double Hashing


##### Linear Probing

###### Insert

**Idea:** when there is a collision, check the next available position in the table (i.e., probing)

###### Find

**Three Cases:** 

1. Position in table is occupied with an element of equal key
2. Position in table is empty
3. Position in table occupied with a different element

For case 3: Probe the next higher index until the element is found or an empty position is found. The process wraps around to the beginning of the table.

**Infinity Loop:** Remember to check that whether the probe index equals to the original index to avoid infinity loop.

###### Delete

**Problem:** 

We cannot mark the slot as empty, because it's impossible to retrieve keys inserted before that deleted slot but index larger than that slot.

**Solution:**

Mark the slot with a sentinel value DELETED.

So the deleted slot can later be used for insertion.

Searching will be able to find all the keys.

###### Prmary Clustering Problem

Linear probing always adds 1 in the previous hash index. 

So Long chunks of occupied slots are created $\Rightarrow$ Collisions happens more often $\Rightarrow$ search time increases a lot.

##### Quadratic Probing

**hash function:** h(x) = x % size of table(still the same)

**index = h(x) + C2, where *C = number of collisions***

$h(x) + C^2 \rightarrow h(x + C^2)$

- Make the index number in the correct range

- $0 \leq C \leq size\ of\ table$

Initially, C = 0

For insertion, if collision occurs, C = C + 1

###### Insert

Start with C = 0. Do the hash function to compute the index.

When collision occurs, C = C + 1 and compute index again.

###### Find

Start with C = 0. If the number does not fit, C = C + 1 and compute index again.

###### Delete

Mark the slot with a sentinel value DELETED.(The same as linear probing)

##### Double Hashing

Have two hash functions.

**Hash Function 1:** $h_1(x) = x \% size\ of\ table$

**Hash Function 2:** $h_2(x) = p – (x \% p)$, *where __p__ is a __prime__ number smaller than __size of table__*

$index = h_1(x) + C \times h_2(x)$, *where C is number of collisions*

$h_1(x) + C \times h_2(x) \rightarrow h_1(h_1(x) + C\times h_2(x))$

- Make the index number in the correct range

- $0 \leq C \leq size\ of\ table$

If collision occurs, C = C + 1

###### Insert

Start with C = 0. Do the hash function to compute the index.

When collision occurs, C = C + 1 and compute index again.

###### Find

Start with C = 0. If the number does not fit, C = C + 1 and compute index again.

###### Delete

Mark the slot with a sentinel value DELETED.(The same as linear probing)

##### String to a Number

e.g. Add up the ASCII values of the characters in the string

An example of hash function for strings

##### Analysis of Open Addressing

###### Unsuccessful Retrieval

$E(\\#steps) = \sum^m_{k=1}(1-a) \leq \sum^\infty_{k=0}ka^{k-1}(1-a) = (1-a)\frac{1}{(1-a)^2} = \frac{1}{1-a}$

###### Successful Retrieval

$E(\\#steps) = \frac{1}{a}ln(\frac{1}{1-a})$







