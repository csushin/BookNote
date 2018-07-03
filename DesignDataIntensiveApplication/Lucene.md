# Basic concept
1. Index
2. Segment and how to construct/merge segment
3. Document
4. Term

# Term vector
* Good to read: http://makble.com/what-is-term-vector-in-lucene
> A term vector is a list of the document's terms and their number of occurrences in that document

More than the occurences of the terms, it can also be the terms' offset, positions, etc.

## Usage of term vectors
1. Show the digest surrounding the query terms in the search result. This is using the position and offset stored in the terms vector.
  * Example: http://makble.com/how-to-do-lucene-search-highlight-example
2. Find similar document, which can use the occurrences, position data in some similarity metircs.

# Indexing and Query
1. How to store/query terms in an efficient way: 
  * FST (a transformation of trie)
    * Quick example: in general, the analyzer will build the trie based on prefix to count the frequency of the text. But another important feature is to support range queries. Based on the example below, we can aggregate the terms from terms400 to terms 499 into a single block and support range queries within that range.
    ```
    num1 = [doc1, doc2, doc3]
    num2 = [doc2, doc3]
    ...
    num400-num499 = [doc1, doc3,...]
    numN = [doc5, doc6]
    ```
2. How to encode values of the indexes in an efficient way: 
  * Modified framed of reference delta
    * Quick Example:
    ```
    term = [1,2,4,5,8,20,25,28,34] which will consume more than 50 bits to store all the data
    -> [1,1,2,1,3,12,5,3,6] which is the delta between two adjcent numbers and can reduce the number of bits required
    -> [1,1,2,1], [3,12,5,3],6 which aggregates the above arrays
    ```

# Others to read:
* [Lucene: The Good Parts](https://blog.parse.ly/post/1691/lucene/)
