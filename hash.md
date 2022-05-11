# Hashtables
 are a data structure that utilize key value pairs. This means every Node or Bucket has both a key, and a value

#### hash 
use for security , convert string to value , to not know what the string . for example when want to convert password .

#### bucket 
-exists inside index of hashtable 

-each index is table 

-index can have multiple value if occrus collisions .

#### Collisions 
if value entered in index that in hashtable that have already value.

___________
## notes

-hashtable use for store value with key , to help u to find the value quickly using key  .
the time complexity for store it is O(1) ,exact location for all .

-example of hashtable :["Greenwood:98103", "Downtown:98101", "Alki Beach:98116"] 

numbers are key ,
string the value.

time complexity to search for specific value is O(1)

____________
### Creating a Hash

1-Add or multiply all the ASCII values together.

2-Multiply it by a prime number such as 599.

3-Use modulo to get the remainder of the result, when divided by the total size of the array.

4-Insert into the array at that index.

```
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16. 
```
_____
### HOW the key/values are stored in the array

-Each index of the array can hold many types of values

- Each Index of the array contain “buckets”. Each of these “buckets” holds one key/value pair combination

-When there is no entry in a specific bucket, the buckets (each index of the array) all start null

-The hash table starts each bucket empty and overwrites their value once a key generates a hashCode that corresponds with an index

_______
### Collisions
A collision occurs when more than one key hashes to the same index in an array.

What would happen if two different keys resolved to be the same index of the array?

#### solve ?
using linkedlist inside the bucket , so inside will be nodes pointing to next key.
______
### steps to store values 
1-accept a key

2-calculate the hash of the key

3-use modulus to convert the hash into an array index

4-store the key with the value by appending both to the end of a linked list

________
### steps to read values 

1-accept a key

2-calculate the hash of the key

3-use modulus to convert the hash into an array index

4-use the array index to access the short LinkedList representing a bucket

5-search through the bucket looking for a node with a key/value pair that matches the key you were given

_______

