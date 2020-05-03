
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

## [EnumMap](https://docs.oracle.com/javase/7/docs/api/java/util/EnumMap.html)  
Specialized Map implementation for use with *enum* type keys. Pls always use EnumMap if the key is a set of constants.    

* Collection Views Order:  
  * keySet() - `The set's iterator will return the keys in their natural order (the order in which the enum constants are declared).`  
  * values() - `Same order as the keys.` 
  * entrySet() - `Same order as the keys.`  
* *No Null Key; Null Value is ok*  
* O(1) for all basic operations - likely to be faster than HashMap.

### Feature  
* Guarantee order?
*Note*  
* Object as key? (use equals and hashcode?)  
* Support Null?  
