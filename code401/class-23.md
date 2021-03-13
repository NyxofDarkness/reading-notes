# Implementation: Hash Tables

[Read Intro to Hash Tables](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-30/resources/Hashtables.html)

|Terminology|Definition|
|---|---|
|Hash | A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.|
|Buckets | A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.|
|Collisions | A collision is what happens when more than one key gets hashed to the same location of the hashtable.|

> Why we use them: 
1. Hold unique values
2. Dictionary
3. Library

> every Node or Bucket has both a key, and a value.

> Arrays actually have fast access. If we know the index of the information we want we can access that information in O(1) time. The reason why searching for a piece of data in a collection is O(N) isn’t because the array is slow, it’s just that we have to look through all N things in the collection.

>  the hash function takes a key and returns an integer

> hashtable traditionally is created from an array

>  size 1024. this is important for index placement. 

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

``` python
# example
Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16. 
```

> Each Index of the array contain “buckets”. Each of these “buckets” holds one key/value pair combination. When there is no entry in a specific bucket, the buckets (each index of the array) all start null



[Watch what is a hash table?]()
[Read basics of hash tables]()
[Skim hash table wiki]()