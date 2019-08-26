- [DataStructureHierachy](#datastructurehierachy)
- [What is this?](#what-is-this)
- [这是什么](#这是什么)
- [Collection Diagram](#collection-diagram)
	- [List](#list)
		- [AbstractList](#abstractlist)
		- [ArrayList](#arraylist)
		- [LinkedList](#linkedlist)
	- [Queue](#queue)
		- [Deque](#deque)
			- [ArrayDeque](#arraydeque)
			- [ConcurrentLikedDeque](#concurrentlikeddeque)
		- [BlockingDeque](#blockingdeque)
			- [LinkedBlockingDeque](#linkedblockingdeque)
		- [AbstractQueue](#abstractqueue)
			- [Priority Queue](#priority-queue)
			- [ConcurrentLinkedQueue](#concurrentlinkedqueue)
		- [BlockingQueue](#blockingqueue)
			- [ArrayBlockingQueue](#arrayblockingqueue)
			- [DelayQueue](#delayqueue)
			- [LinkedBlockingQueue](#linkedblockingqueue)
			- [PriorityBlockingQueue](#priorityblockingqueue)
			- [SynchronousQueue](#synchronousqueue)
			- [TransferQueue - interface](#transferqueue---interface)
				- [LinkedTransferQueue](#linkedtransferqueue)
	- [Set](#set)
		- [HashSet](#hashset)
		- [LinkedHashSet](#linkedhashset)
		- [EnumSet](#enumset)
		- [SortedSet](#sortedset)
			- [NavigableSet](#navigableset)
				- [ConcurrentSkipListSet](#concurrentskiplistset)
				- [TreeSet](#treeset)
- [List or Queue or Set?](#list-or-queue-or-set)
	- [Difference](#difference)
- [Fail-Fast and Fail-Safe and Weakly Consistnt](#fail-fast-and-fail-safe-and-weakly-consistnt)
- [Serializable](#serializable)
- [Cloneable](#cloneable)
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
  
##### ArrayDeque  
From the implementation standpoint, it's too obsvious that it's named with array.  

* Most operations are O(1) exceptions remove.
* Not synchronized
* Fail-Fast - But not guaranteed
* Not Allow Null

##### ConcurrentLikedDeque  
* Concurrent insertion/removal/access deque data structure.    
* Synchronized
* Weakly Consistent Iterator
* Not Allow Null      
* Non-Blocking Algorithms


#### BlockingDeque  

##### LinkedBlockingDeque    
* Concurrent data structure    
* Blocking Algorithms  
* Weakly Consistent Iterator
* Not Allow Null
 
#### AbstractQueue  
Like abstractList or other abstract of interface which provides some common implementation.  
Note: ArrayDeque and ConcurrentLinkedDeque do not extend abstractQueue. [See why](https://stackoverflow.com/questions/25156772/why-does-the-class-arraydeque-not-extend-from-abstractqueue)  
  
##### Priority Queue  
* elements are ordered according to the natural ordering or By comparator.       
* O(log(n)) for enqueue and dequeue; O(1) for remove and contains and retrieval.  
* Fail-Fast  
* Iterator() is not guaranteed to traverse the elements in any particular order. Only queue methods will guarantee order.
* Not synchronized
* Not Allow Null    
 
##### ConcurrentLinkedQueue    
* Concurrent Data Structure  
* Weakly Consistent Iterator    
* Non-Blocking Algorithm
* Not Allow Null
  
#### BlockingQueue  
All implementaitons of this interface are synchronous data structure. They all have the similar feature addition to the queue. e.g   
* Not Allow Null;   
* Weakly Consistent;   
* Concurrent Data Structure.     
* Blocking Algorithm
  
But you may ask, what is the diff between the ConcurrentLinkedQueue and those? In a high level, that because of the underlying implementation. The concurrent-queue such as ConcurrentLinkedQueue is using Non-Blocking algorithm. However, the BlockingQueue is using Blocking algorithm. More details See Reference.
##### ArrayBlockingQueue  
* Extend all of the features from Blocking Queue;  
* Backed by Array  
* Bounded Queue
##### DelayQueue    
* Extend all of the features from Blocking Queue;    
* Unbounded Queue  
* The eles in the queue are not visible except they expired.
  
##### LinkedBlockingQueue    
* Extend all of the features from Blocking Queue;     
* Optional Bounded Queue  
 
##### PriorityBlockingQueue    
* Extend all of the features from Blocking Queue;   
* Similar to Priority Queue  
* Unbounded Queue
   
##### SynchronousQueue    
* It is interesting data strucuture, Its basically a tunnel between threads. 
  
##### TransferQueue - interface
  
###### LinkedTransferQueue
   * Unbounded queue based on linked node.  
   * Additional to the common concurrent data structure, it has one distinct feature which it can block until other thread receieves your element.   
  
    
### Set 
  In short, Set is another big part of collection family. The all known feature of Set is that contain no duplicate elements. 
  
#### HashSet  
* It is Backed by HashTable(HashMap)  
* No guarantee the order.  
* Allow Null   
* Fail-Fast    
 
#### LinkedHashSet  
* It is backed by HashTable and LinkedList - Augmented HashSet.  
* It guarantees the insertion order.    
  
#### EnumSet  
* Specialized implementation for use with enum types.  
* In natural order which the enum constants are declared.  
* Weakly Consistent.  
* Not Allow Null  
* It is an Abstract Class.   
  
#### SortedSet  
Subinterface of Set which provide additional feature which is Ordering. NOTE: It's natural ordering or by a comparetor.
Because it guarantees the ordering, it provides some methods such as  

| Method     | Desciption                                                            |
|------------|-----------------------------------------------------------------------|
| first()    | get head - first element                                              |
| last()     | get tail - last element                                               |
| headSet(e) |  sub set such that the elements in the set are strictly less than e   |
| tailSet(e) | sub set such that the elements in the set are strictly greater than e |

#####  NavigableSet  
Extended version of SortedSet which can give a more precision access to the elements or subset.   
***Addition to the Methods From SortedSet***    

| Method                             | Desciption                                                        |
|------------------------------------|-------------------------------------------------------------------|
| ceiling/floor(e)                   | the least/greatest element which is greater/less or equal than e. |
| higher/lower(e)                    | the least/greast element which is greater/less than e.            |
| headSet/tailSet(e, bool inclusive) | return equal if inclusive is true.                                |
| pollFirst()                        | Retrieve and remove the first element.                            |
| pollLast()                         | Retrieve and remove the last element.                             |
  
###### ConcurrentSkipListSet      
* Order guaranteed - natural ordering or by comparator.  
* Concurrent Set implementation based on ConcurrentSkipListMap  
* Weakly Consistent  
* Bulk operation are not guraranteed to be performed atomically.  
* Not Allow Null.
  
###### TreeSet      
* Order guaranteed - natural ordering or by comparator.  
* Set implementation based on Treemap.  
* Not Allow Null  
* Fast-Fail
  
## List or Queue or Set?  
#### Difference
The operations provided by List are mostly suitable when we need to handle a specific element or store a collection of elemnts. e.g we can get specific element or find the index of specific element.

The operations provides by queue are mostly sutiable when we apply some other operations to a collection of elements(only head or tail is accessable). e.g we have list of job which need to done so that we retrieve one and remove it.       
  
The set data structure provides no duplicate elements and some of them guarantee the ordering. Also it provides the ability which can access part of the collection more precise than the list data structure.

## Fail-Fast and Fail-Safe and Weakly Consistnt
Fail fast means raise failure as fast as possible; fail safe is opposite.; weakly consistnt never fails but not guarantee the element will be visible.
  
 Default Collection which extends Iterable has fail fast feature. Most of the data structure under java.util pkg are fail fast.  
  
 Iterators on Collections from java.util.concurrent pkg are fail safe. Remember concurrent data structure are fail safe in nature.  
   
## Serializable  
All of the concrete classes are having the implementation of Serializable interface.   
Serializability is a process of converting the data object to bytes vice versa. It is useful when we want to store the data object to a persistent storage or communicate via network etc.   
  
## Cloneable  
By default, class which implements cloneable is able to shadow/(field-to-field) clone an object.   
That means the newly cloned object only has the the reference which point to the same value in the heap.   
If we need copy the value as well then we need deep copy. See reference 7 for more details.
  
## Reference  
  1. [Java Docs](https://docs.oracle.com/javase/8/docs/api/java/util/Collection.html) 
  2. [Data Structure Time Complexity](https://gist.github.com/psayre23/c30a821239f4818b0709)  
  3. [What is amortized constant time?](https://stackoverflow.com/questions/200384/constant-amortized-time)  
  4. [Why ArrayList extends AbstractList but still need to implement List - implementation is transitive](https://stackoverflow.com/questions/18558536/why-does-arraylist-class-implement-list-as-well-as-extend-abstractlist)  
  5. [Fail-Fast and Fail-Safe](https://www.baeldung.com/java-fail-safe-vs-fail-fast-iterator)    
  6. [Blocking Algorithm and Non-Blocking Algorithm](http://tutorials.jenkov.com/java-concurrency/non-blocking-algorithms.html)  
  7. [Deep Copy and Shadow Copy](https://www.geeksforgeeks.org/deep-shallow-lazy-copy-java-examples/)
  