##############################
Algorithms and Data Structures
##############################

************
Fundamentals
************

Basic Programming Model
=======================


Data Abstraction
================

Bags, Queues and Stacks
=======================

Bag
---

A bag is a collection where removing items is not supported - its purpose is to provide clients with the ability to collect items and then to iterate through the collected items.

The order of iteration is unspecified and should be immaterial to the client.


.. code-block:: java

    // Definition
    public class Bag<Item> implements Iterable<Item>

    // Methods
    Bag()                           // Create an empty bag
    void add(Item item)             // Add in item
    boolean isEmpty()               // Is the bag empty ?
    int size()                      // Number of items in the bag


Implementations
^^^^^^^^^^^^^^^

Linked-list implementation :

.. code-block:: java

    // Page 155
    public class Bag<Item> implements Iterable<Item> {

        private Node first;
        private class Node {
            Item item;
            Node next;
        }

        public void add(Item item) {
            Node oldfirst = first;
            first = new Node();
            first.item = item;
            first.next = oldfirst;
        }

        public Iterator<Item> iterator() {
            return new ListIterator();
        }
        private class ListIterator implements Iterator<Item> {
            private Node current = first;

            public boolean hasNext() {
                return current != null;
            }

            public void remove() {}

            public Item next() {
                Item item = current.item;
                current = current.next;
                return item;
            }
        }
    }


FIFO Queue
----------

A FIFO queue (or just a queue) is a collection that is based on the first-in-first-out (FIFO) policy.


.. code-block:: java

    // Definition
    public class Queue<Item> implements Iterable<Item>

    // Methods
    Queue()                         // Create an empty queue
    void enqueue(Item item)         // Add an item
    Item dequeue()                  // Remove the least recently added item
    boolean isEmpty()               // Is the queue empty ?
    int size()                      // Number of items in the queue


Implementations
^^^^^^^^^^^^^^^

Linked-list implementation :

.. code-block:: java

    // Page 151
    public class Queue<Item> implements Iterable<Item> {

        private Node first;
        private Node last;
        private int N;

        private class Node {
            Item item;
            Node next;
        }

        public boolean isEmpty() {
            return first == null;
        }

        public int size() {
            return N;
        }

        public void enqueue(Item item) {
            Node oldlast = last;
            last = new Node();
            last.item = item;
            last.next = null;
            if (isEmpty()) {
                first = last;
            }
            else {
                oldlast.next = last;
            }
            N++;
        }

        public Item dequeue() {
            Item item = first.item;
            first = first.next;
            if (isEmpty()) {
                last = null;
            }
            N--;
            return item;
        }

        public Iterator<Item> iterator() {
            return new ListIterator();
        }
        private class ListIterator implements Iterator<Item> {
            private Node current = first;

            public boolean hasNext() {
                return current != null;
            }

            public void remove() {}

            public Item next() {
                Item item = current.item;
                current = current.next;
                return item;
            }
        }
    }


Pushdown (LIFO) Stack
---------------------

A pushdown stack (or just a stack) is a collection that is based on the last-in-first-out (LIFO) policy.


.. code-block:: java

    // Definition
    public class Stack<Item> implements Iterable<Item>

    // Methods
    Stack()                         // Create an empty stack
    void push(Item item)            // Add an item
    Item pop()                      // Remove the most recently added item
    boolean isEmpty()               // Is the stack empty ?
    int size()                      // Number of items in the stack


Implementations
^^^^^^^^^^^^^^^

Resizing array implementation :

.. code-block:: java

    // Page 141
    public class ResizingArrayStack<Item> implements Iterable<Item> {

        private Item[] a = (Item[]) new Object[1];
        private int N = 0;

        public boolean isEmpty() {
            return N == 0;
        }

        public int size() {
            return N;
        }

        private void resize(int max) {
            Item[] temp = (Item[]) new Object[max];
            for (int i = 0; i < N; i++) {
                temp[i] = a[i];
            }
            a = temp;
        }

        public void push(Item item) {
            if (N == a.length) {
                resize(2*a.length);
            }
            a[N++] = item;
        }

        public Item pop() {
            Item item = a[N--];
            a[N] = null;
            if (N > 0 && N == a.length/4) {
                resize(a.length/2);
            }
            return item;
        }

        public Iterator<Item> iterator() {
            return new ReverseArrayIterator();
        }

        private class ReverseArrayIterator implements Iterator<Item>{
            private int i = N;

            public boolean hasNext() {
                return i > 0;
            }

            public Item next() {
                return a[i--];
            }

            public void remove() {}
        }
    }


Linked-list implementation :

.. code-block:: java

    // Page 149
    public class Stack<Item> implements Iterable<Item> {

        private Node first;
        private int N;

        private class Node {
            Item item;
            Node next;
        }

        public boolean isEmpty() {
            return first == null;
        }

        public int size() {
            return N;
        }

        public void push(Item item) {
            Node oldfirst = first;
            first = new Node();
            first.item = item;
            first.next = oldfirst;
            N++;
        }

        public Item pop() {
            Item item = first.item;
            first = first.next;
            N--;
            return item;
        }

        public Iterator<Item> iterator() {
            return new ListIterator();
        }
        private class ListIterator implements Iterator<Item> {
            private Node current = first;

            public boolean hasNext() {
                return current != null;
            }

            public void remove() {}

            public Item next() {
                Item item = current.item;
                current = current.next;
                return item;
            }
        }
    }


Analysis of Algorithms
======================

Order-of-growth classifications
-------------------------------

+--------------+-----------------+--------------------+-------------------+
| Description  | Order of growth | Description        | Example           |
+==============+=================+====================+===================+
| Constant     | :math:`1`       | Statement          | Add two numbers   |
+--------------+-----------------+--------------------+-------------------+
| Logarithmic  | :math:`log N`   | Divide in half     | Binary search     |
+--------------+-----------------+--------------------+-------------------+
| Linear       | :math:`N`       | Loop               | Find the maximum  |
+--------------+-----------------+--------------------+-------------------+
| Linearithmic | :math:`N log N` | Divide and conquer | Mergesort         |
+--------------+-----------------+--------------------+-------------------+
| Quadratic    | :math:`N^2`     | Double loop        | Check all pairs   |
+--------------+-----------------+--------------------+-------------------+
| Cubic        | :math:`N^3`     | Triple loop        | Check all triples |
+--------------+-----------------+--------------------+-------------------+
| Exponential  | :math:`2^N`     | Exhaustive search  | Check all subsets |
+--------------+-----------------+--------------------+-------------------+

Case Study: Union-Find
======================

Union-Find
----------

.. code-block:: java

   // Definition
   public class UF

   // Methods
   UF(int N)                        // Initialize N sites with integer names (0 to N-1)
   void union(int p, int q)         // Add connection between p and q
   int find(int p)                  // Component identifier for p (0 to N-1)
   boolean connected(int p, int q)  // Return true if p and q are in the same component
   int count()                      // Number of components


Implementations
^^^^^^^^^^^^^^^

.. code-block:: java

    // Page 221
    public class WeightedQuickUnionUF {

        private int[] id;
        private int[] sz;
        private int count;

        public WeightedQuickUnionUF(int N) {
            count = N;
            id = new int[N];
            for (int i = 0; i < N; i++) {
                id[i] = i;
            }
            sz = new int[N];
            for (int i = 0; i < N; i++) {
                sz[i] = 1;
            }
        }

        public int count() {
            return count;
        }

        public boolean connected(int p, int q) {
            return find(p) == find(q);
        }

        public int find(int p) {
            while(p != id[p]) {
                p = id[p];
            }
            return p;
        }

        public void union(int p, int q) {
            int i = find(p);
            int j = find(q);

            if (i == j) {
                return;
            }

            if (sz[i] < sz[j]) {
                id[i] = j;
                sz[j] += sz[i];
            }
            else {
                id[j] = i;
                sz[i] += sz[j];
            }
            count--;
        }
    }

*******
Sorting
*******

Elementary Sorts
================

Mergesort
=========

Quicksort
=========

Priority Queues
===============

Applications
============


*********
Searching
*********

Symbol Tables
=============

.. code-block:: java

    // Definition
    public class ST<Key, Value>

    // Methods
    ST()                            // Create a symbol table
    void put(Key key, Value val)    // Put key-value into the table (remove key from table if value is null)
    Value get(Key key)              // Value paired with key (null if key is absent)
    void delete(Key key)            // Remove key (and its value) from table
    boolean contains(Key key)       // Is there a value paired with key ?
    boolean isEmpty()               // Is the table empty ?
    int size()                      // Number of key-value pairs in the table
    Iterable<Key> keys()            // All the keys in the table


Binary Search Trees
===================

Balanced Search Trees
=====================

Hash Tables
===========

Applications
============

.. Page 342

******
Graphs
******

Undirected Graphs
=================

Directed Graphs
===============

Minimum Spanning Trees
======================

Shortest Paths
==============


*******
Strings
*******

String Sorts
============

Tries
=====

Substring Search
================

Regular Expressions
===================

Data Compression
================
