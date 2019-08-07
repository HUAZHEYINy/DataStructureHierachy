- [DataStructureHierachy](#datastructurehierachy)
- [What is this?](#what-is-this)
- [这是什么](#这是什么)
- [Collection Diagram](#collection-diagram)
	- [List](#list)
		- [AbstractList](#abstractlist)
		- [ArrayList](#arraylist)
		- [LinkedList](#linkedlist)
	- [Queue](#queue)
		- [AbstractQueue](#abstractqueue)
		- [Deque](#deque)
		- [ArrayDeque](#arraydeque)
		- [ConcurrentLikedDeque](#concurrentlikeddeque)
		- [Priority Queue](#priority-queue)
- [List or Queue?](#list-or-queue)
	- [Difference](#difference)
- [Fail-Fast and Fail-Safe](#failfast-and-failsafe)
- [Reference](#reference)
  
# DataStructureHierachy
Java Data Structure Hierachy - 数据结构关系结构  


# What is this?  
This article mainly shows the hierarchical relationship and structure between Java data structures, Let everyone can understand the various data structures more intuitively and how they are implemented and the differences between them. So that, it helps us to choose a data structure that fits the actual use case more efficient.  
  
  For example: For ArrayList we know that it implements the List Interface, but it actually inherits the Abstract List first and implements List at the same time. The questions derived here are: Why is there an AbstractList? What is the relationship between it and its parent class and the implemented interface? What is the essential difference between ArrayList and LinkedList from the internal implementation? Why is the AbstractList already inherited in the ArrayList but does it still need to implement the List directly?

# 这是什么  
本文主要展示了 Java 数据结构的之间的层级关系和层次架构，让大家更加直观的理解各种数据结构以及他们是如果实现、他们的之间的区别。从而帮助我们更快、更好的选择适合实际用例的数据结构。    

 例如： 对于ArrayList 我们知道它是实现了List Interface，但是它实际上首先继承了Abstract List 与此同时又实现了List. 这里衍生出来的问题有： 为什么会有AbstractList的出现? 它以及它父类和实现的interface的关系是什么？ArrayList 和 LinkedList从内部实现上看有什么本质的区别?  为什么ArrayList已经继承了AbstractList但是它还是需要直接实现List呢？  
   
# Collection Diagram  
![Collection Img](https://github.com/HUAZHEYINy/DataStructureHierachy/blob/master/Collection.png)

  
### List
In real life, When we need to maintain a sequence of elements then we typically will choose List. Two well known implementation classs are ArrayList and LinkedList. 
From a high level, List interface provides "CRUD" operations. 
   
   * "Create": add/addAll methods.
   * "Read": get/indexOf/contains/containsAll
   * "Update": set/replaceAll/retainAll
   * "Delete": clear/remove/removeAll  
 
#### AbstractList  
From the Diagram you can see, ArrayList and LinkedList they all extend the abstractList. 
 Why do we need that? A: It provides common implementation for the concrete subclass, that is the beauty of inheritance in java.  
 However, in the actual subclass implementation, we still override some of the methods to make it best fit the actual implementation.
   
#### ArrayList  
Internally, It is using Resizable-array to actually store the elements.  
 
what is resizable-array?   By looking at the source code, it seems super interesting - It is just an array which initialized with certain size(if u do not specify the capacity) and We will grow the array list when the size of the elements equals to the capacity by copying the original array to an new array with a larger size.  
  
 Some well known features:  
 
  * It has all of methods which list has
  * get/set/size/isEmpty/iterator/listIterator will have O(1)  
  * add(index,ele) will have O(n) and add() have O(1)
  * Not  synchronized - Not Thread Safe
  * Fail-Fast
  * Allow Null
  
#### LinkedList 
It has both list and deque features, since it implements the Deque which is double and List
Features:  

* it has all method which list and deque have.
* get() O(n)
* Not synchronized
* Fail-Fast    
* Allow Null
 
### Queue   
Top level interface for all queues e.g Deque, BlockingQueue which is synchronzied data structure. 
Besides basic Collection operations, it provides

|                       | Throws Exception | Returns Special Value |
|-----------------------|------------------|-----------------------|
| Insert                | add(e)           | offer(e)              |
| Remove | remove()         | poll()                |
| Examine               | element()        | peek()                |

#### AbstractQueue  
Like abstractList or other abstract of interface which provides some common implementation.  
Note: ArrayDeque and ConcurrentLinkedDeque do not extend abstractQueue. [See why](https://stackoverflow.com/questions/25156772/why-does-the-class-arraydeque-not-extend-from-abstractqueue)  

#### Deque
Deque - Double End Queue. With queue, we can only add to the end of the queue and remove from the head of the queue.    

Deque is basically evolved version of queue which provides add to the head of the queue and remove from the tail of the queue.    

With addition to the Queue methods which FIFO.

|         | Throws Exception | Returns Special Value | Throws Exception | Returns Special Value |
|---------|------------------|-----------------------|------------------|-----------------------|
| Insert  | addFirst(e)      | offerFirst(e)         | addLast(e)       | offerLast(e)          |
| Remove  | removeFirst()    | pollFirst()           | removeLast()     | pollLast()            |
| Examine | getFirst()       | peekFirst()           | getLast()        | peekLast()            |  

It also provides stack methods which LIFO.    

| Stack Method | Deque Method  |
|--------------|---------------|
| push(e)      | addFirst（）  |
| pop()        | removeFirst() |
| peek()       | peekFirst()   |
  
#### ArrayDeque  
From the implementation standpoint, it's too obsvious that it's named with array.  

* Most operations are O(1) exceptions remove.
* Not synchronized
* Fail-Fast
* Not Allow Null

#### ConcurrentLikedDeque  
* Concurrent insertion/removal/access deque data structure.    
* Synchronized
* Fail-Safe  
* Not Allow Null 
  
#### Priority Queue  
* elements are ordered according to the natural ordering or By comparator.       
* O(log(n)) for enqueue and dequeue; O(1) for remove and contains and retrieval.  
* Fail-Fast  
* Iterator() is not guaranteed to traverse the elements in any particular order. Only queue methods will guarantee order.
* Not synchronized
* Not Allow Null
    
## List or Queue?  
#### Difference
The operations provided by List are mostly suitable when we need to handle a specific element or store a collection of elemnts. e.g we can get specific element or find the index of specific element.

The operations provides by queue are mostly sutiable when we apply some other operations to a collection of elements(only head or tail is accessable). e.g we have list of job which need to done so that we retrieve one and remove it.     
  
## Fail-Fast and Fail-Safe  
Fail fast means raise failure as fast as possible; fail safe is opposite.  
  
 Default Collection which extends Iterable has fail fast feature. Most of the data structure under java.util pkg are fail fast.  
  
 Iterators on Collections from java.util.concurrent pkg are fail safe. Remember concurrent data structure are fail safe in nature.
  
  ## Reference  
  1. [Java Docs](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) 
  2. [Data Structure Time Complexity](https://gist.github.com/psayre23/c30a821239f4818b0709)  
  3. [What is amortized constant time?](https://stackoverflow.com/questions/200384/constant-amortized-time)  
  4. [Why ArrayList extends AbstractList but still need to implement List - implementation is transitive](https://stackoverflow.com/questions/18558536/why-does-arraylist-class-implement-list-as-well-as-extend-abstractlist)  
  5. [Fail-Fast and Fail-Safe](https://www.baeldung.com/java-fail-safe-vs-fail-fast-iterator)  
  