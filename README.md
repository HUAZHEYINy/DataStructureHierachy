# DataStructureHierachy
Java Data Structure Hierachy - 数据结构关系结构  


#What is this?  
This article mainly shows the hierarchical relationship and structure between Java data structures, Let everyone can understand the various data structures more intuitively and how they are implemented and the differences between them. So that, it helps us to choose a data structure that fits the actual use case more efficient.  
  
  For example: For ArrayList we know that it implements the List Interface, but it is actually an "indirect" implementation. It first inherits the Abstract List. Since Abstract List implements List, it implements List indirectly. The problems derived here are : Why is there an AbstractList? What is the relationship between it and its parent class and the implemented interface? What is the essential difference between ArrayList and LinkedList from an internal implementation?

#这是什么  
本文主要展示了 Java 数据结构的之间的层级关系和层次架构，让大家更加直观的理解各种数据结构以及他们是如果实现、他们的之间的区别。从而帮助我们更快、更好的选择适合实际用例的数据结构。    

 例如： 对于ArrayList 我们知道它是实现了List Interface，但是它实际上是“间接”实现，它首先继承了Abstract List 因为Abstract List 实现了List所以它就间接的实现了List. 这里衍生出来的问题有： 为什么会有AbstractList的出现? 它以及它父类和实现的interface的关系是什么？ArrayList 和 LinkedList从内部实现上看有什么本质的区别?
