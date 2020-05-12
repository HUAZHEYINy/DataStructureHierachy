
# Map Diagram  
![Map Diagram](https://github.com/HUAZHEYINy/DataStructureHierachy/blob/master/Map/map.png)  

## [Map](https://docs.oracle.com/javase/8/docs/api/java/util/Map.html) 
Map is Key-Value pair data strucutre. All map data structure are having all below properties  
* *No Duplicate Key* *One to One Mapping - Key/Value* 
* Three *collection views* key set; value list; key-value set.  
* The order of a map varies with the iterator implementation.     
    
I usually doing the this way to initialize map. For example,
```Java  
Map<String, Integer> map = new HashMap();  // Explicility defines the key type and value type - help to detect wrong type accidentally assign worng type; Declare Map so that we can change the implementation easily.
``` 
  
## [AbstractMap](https://docs.oracle.com/javase/8/docs/api/java/util/AbstractMap.html)  
Simillar to AbstractList, AbstractMap implements (pretty much) all methods from Map interface and (pretty much) all concrete map classes extend it and override with their own requirements.    

### [EnumMap](https://docs.oracle.com/javase/7/docs/api/java/util/EnumMap.html)  
Specialized Map implementation for use with *enum* type keys. Pls always use EnumMap if the key is a set of constants.    

* Collection Views:  
  * keySet() - `The set's iterator will return the keys in their natural order (the order in which the enum constants are declared).`  
  * values() - `Same order as the keys.` 
  * entrySet() - `Same order as the keys.`    
  * [weakly consistent](https://github.com/HUAZHEYINy/DataStructureHierachy/blob/master/Collection/Collection.md#fail-fast-and-fail-safe-and-weakly-consistent) - No exception but does NOT guarantee to be visible.
* *No Null Key; Null Value is ok*  
* O(1) for all basic operations - likely to be faster than HashMap.
  
### [HashMap](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html)  
Most popular map implementation in its family and it's [Hash Table](https://en.wikipedia.org/wiki/Hash_table) based implementaion.  
  
Internally, The key is hashed by *hashCode* method and used that to find the correct *bucket* where we store the key/value pair; And then use *equals* method to scan the entries and find the key that equals to the input key. E.g when you use an object as key, then you will need to override the *hashCode* and *equals* methods to make it work as expected.

* Collection Views:    
  * *collection view methods* do NOT guarantee order.  
  * [fail-fast](https://github.com/HUAZHEYINy/DataStructureHierachy/blob/master/Collection/Collection.md#fail-fast-and-fail-safe-and-weakly-consistent) for the collection views iterators except *remove* method of the iterators.
* *Null Key and Value is ok*   
* Performance affects by *initial capacity; load factor*    
* *Not synchronized*  
* *HashTable* based implementation.
    
### IdentifyHashMap
*This class is not a general-purpose Map implementation! While this class implements the Map interface, it intentionally violates Map's general contract, which mandates the use of the equals method when comparing objects. This class is designed for use only in the rare cases wherein reference-equality semantics are required.* 
  
Copying the definition from Java Docs and the common features are pretty much identifical to *HashMap* 

* Collection Views:    
  * *collection view methods* do NOT guarantee order.  
  * [fail-fast](https://github.com/HUAZHEYINy/DataStructureHierachy/blob/master/Collection/Collection.md#fail-fast-and-fail-safe-and-weakly-consistent) for the collection views iterators except *remove* method of the iterators.
* *Null Key and Value is ok*   
* Performance affects by *initial capacity; load factor*    
* *Not synchronized*    
* *HashTable* based implementation.
  
### WeakHashMap  
https://community.oracle.com/blogs/enicholas/2006/05/04/understanding-weak-references
  
### Feature  
* Guarantee order?
*Note*  
* Object as key? (use equals and hashcode?)  
* Support Null?  
