## Algorithm

Algorithm means a solution of a problem.

## Notation

To measure the performance of the algorithm.

## Collection

It is a group of elements.

Types of collections:

- List: can contain all types together
- Arrays: can contain only one type of element

### Time complexities

1. List

The Average Case assumes parameters generated uniformly at random.

Internally, a list is represented as an array; the largest costs come from growing beyond the current allocation size (because everything must move), or from inserting or deleting somewhere near the beginning (because everything after that must move). If you need to add/remove at both ends, consider using a collections.deque instead.

![List Time Complexity](./images/list-time-complexity.jpg)

1. collections.deque

A deque (double-ended queue) is represented internally as a doubly linked list. (Well, a list of arrays rather than objects, for greater efficiency.) Both ends are accessible, but even looking at the middle is slow, and adding to or removing from the middle is slower still.

![Collections.deque time complexity](./images/collections.deque-time-complexity.jpg)

1. Set

As seen in the source code the complexities for set difference s-t or s.difference(t) (set_difference()) and in-place set difference s.difference_update(t) (set_difference_update_internal()) are different! The first one is O(len(s)) (for every element in s add it to the new set, if not in t). The second one is O(len(t)) (for every element in t remove it from s). So care must be taken as to which is preferred, depending on which one is the longest set and whether a new set is needed.

To perform set operations like s-t, both s and t need to be sets. However you can do the method equivalents even if t is any iterable, for example s.difference(l), where l is a list.

![Set Time complexity](./images/set-time-complexity.jpg)

1. Dict

The Average Case times listed for dict objects assume that the hash function for the objects is sufficiently robust to make collisions uncommon. The Average Case assumes the keys used in parameters are selected uniformly at random from the set of all keys.

Note that there is a fast-path for dicts that (in practice) only deal with str keys; this doesn't affect the algorithmic complexity, but it can significantly affect the constant factors: how quickly a typical program finishes.

![Dict time complexity](./images/dict-time-complexity.jpg)

Source - https://wiki.python.org/moin/TimeComplexity

---

## Linked List

Linkedlist implementation is there in the code file `2. linked-list.py`.

## Stack

It is like a stack of elements. It is used in LIFO (Last in, fast out)

Push -> put an element on the top
Pop -> delete the topmost element

Stack implementation is there in the code file `3. stack.py`.

## Queue

It uses FIFO, First in, first out.

Head -> element1 -> element2 -> ... -> Tail

Head : first element and the oldest element in the queue, also called peek.

Tail : latest new element added into the queue.

Dequeue : Remove an element from head, is called dequeue.

Enqueue : Add a new element at the tail, it is call enqueue.

**Dequeue:** Can perform dequeue and enqueue from both ends.

**Priority Queue :** Each element has a priority, we remove the highest priority element first. If two element has the same priority then oldest one is removed.

Stack implementation is there in the code file `4. queue.py`.

---

## Searching and Sorting

## Binary Search

A search with O(logn) complexity in sorted array.

## Recursion

Function calls itself with a base condition.

## Sorting

**Inplace Sorting** : No need for extra space to sort the elements.

### Bubble sort

It is a naive algorithm. It is inplace algorithm.

Time Complexity:

- Worse case - O(n^2)
- Average case - O(n^2)
- Best case - O(n)

Space Complexity: O(1)

### Merge Sort

It is based on divide and conquer. This is **not** a inplace algorithm.

Time Complexity - O(n log(n))
Space Complexity - O(n)

### Quick Sort

You select a random index and move all the larger element to right side and all the smaller element to the left side. The random index is called pivot.
Then you recursively select pivot in the left and right array. Convention is to choose last element in the array as a pivot.

Time Complexity -

- Worse case - O(n^2) (when the pivot is already at right place)

- Average and Best case - O(n log(n)) (Pivot is moved to the middle)

Space Complexity - O(1)

## Some more data structures

1. Map: We can store values as a key value pair. If I need to get a perticular value then I need to use the key to find it's value.
2. Set: In set, there is not a particular ordering of element and set also doesn't allow duplicate element.

## Hashing

To get value in constant time.

```python
Load Factor = Number of Entries / Number of Buckets
```

### Hash Map

Hash table or hashmap is a type of data structure that maps keys to its value pairs.

## Trees

It has root and children.

- Trees should be connected.
- Must not have any cycles.

**Level** : How many connection does it take to reach the root + 1.
(Level of root node is 1)

**Height** : the number of edges between it and the furthest leaf on the tree. [height]
(Height of furthest leaf is 0)

**Depth** : the number of edges to the root.
(Depth of root is 0)

### Tree Traversal

![Tree 1](./images/tree-1.png)

Breath First Search(BFS) : D, B, E, A, C, F

Depth First Search(DFS) :

- Pre-Order: D, B, A, C, E, F
- InOrder: A, B, C, D, E, F
- PostOrder: A, C, B, F, E, D

### Search and Delete

#### Search:

In worse case, we have to traverse every single element of the tree to check if the element exists or not.

Time Complexity: O(n)

### Delete:

There should be in three situation.

1. If the deleted node is leaf node, then just delete the node.

2. If the deleted node has one child, then after deleting the node, attach the parent with it's child.

3. If it has 2 nodes, replace the deleted node with a leaf node.

Time Complexity: O(n)

### Insert:

We just need to find a open spot, it may be a leaf node or node has single child.

How much time to take, to find the open spot, where we insert the new node?

In worse case, we have to go into height of the tree. It will take O(log(n)) time in worse case.

Time Complexity: O(log(n))

## Binary Search Tree (BST)

It is a type of binary tree.
It is sorted tree means,
`left child < parent < right child`

Search Time complexity
if n is the node of element
Best Case : O(log(n))
worst Case (Unbalance tree) : O(n)

## Heaps

It is a type of tree.
Tree is either in maximum or minimum order. So that root element either the maximum or minimum element of the tree.

- Heaps doesn't need to be a binary tree. So it can have any number of children.

- It should be a complete tree. means all levels except the last one should be completely full. If the last level isn't totally full, values are added from left to right.

Types:

- Max Heap : Parent element is bigger among it's children. So, root element became the biggest element in the tree.

- Min Heap : Parent element is smaller among it's children. So, root element became the smaller element in the tree.

Search Time Complexity - O(n)

- For example if we take a max heap for searching, and when we get a element smaller that find_val then we will not go to subtree.
- If we check that root is smaller then the find_val, then immediately we stop calculating.

### Insert

Insert the new element in the first open spot of the tree. Then we **Heapify**.

### Heapify - Max Heap

if the parent element is smaller that it's child the we swap those elements.

Time Complexity - O(log(n))
Height of the tree

### Heap Implementation

We can use array or LinkedList to store heap.

## Graph (also called Network)

It is a data structure to show relationship between two objects.

`Tree is a specific type of graph.`

### Eulerian Paths

Traverse the graph such a way that each edge should be traversed at least once.

### Eulerian Cycle

Traverse the graph such a way that after traversal each edge should be traverse exactly once and your starting and ending vertex should be the same vertex.

### Haimiltonian Paths

Traverse the graph such a way that each vertex should be traversed at least once.

### Haimiltonian Cycle

Traverse the graph such a way that after traversal each vertex should be traverse exactly once and your starting and ending vertex should be the same vertex.

---

# Technical interview

1. Clarifying the Question - Confirm the right variant of question

2. Confirming inputs - Make sure of the input and output signature of the algorithm, that you are using.

3. Test Cases - Query about all the edge input cases. eg - null & empty inputs.

4. BrainStorming - Use test cases to find the solution, need a good communication

5. Runtime Analysis - Find the time complexity and tell interviewer before coding

6. Coding - While writing the code, tell the purpose of the code to the interviewer (and not just read the code loud as it is)

7. Debugging - After writing code, see if something wrong with the logic. And dry run the test cases.
