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
  
#### LinkedList 
It has both list and deque features, since it implements the Deque and List
Features:  

* it has all method which list and deque have.
* get() O(n)
* Not synchronized
* Fail-Fast  
 
### Queue 


#### Deque
   