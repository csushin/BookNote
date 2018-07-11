# Data Model and Query Languages

## Relational vs Document model
### What data model leads to simpler application code?
* It more depends on the relationship of the model. 
  * If the application only uses the one-to-many relationship, it would not require many joins and hence the document model would be more appealing.
  * If the application needs many to many relationship, it would need multiple joins in the application codes and makes the codes compelx.
  * If the application needs query in the nested items, deeper nesting structure would require more logics in the application codes.
### Schema flexibility in the document model
* Schema-on-read
  * Document model does require enforce database-level requirement on the schema and hence it has more flexibility.
  * But usually we have implicit assumption on the schema when we read the data on the client side, which means the document model is actuall **schema-on-read**.
* Schema-on-write
  * Relational data model. Explictly requrie the schema and ensure that the written data follows the schema.
### Network/graph model
* Definition: each node may have multiple or zero from/to connections to the other nodes.
* Schema: the database is often partitioned into two parts: vertices and edges. 
* Query: due to the many-to-many relationships in the network model, it is possible to go to infinite loop for a query. There are also some 
  * Cypher query
  
## Query language
### Declarative, Imperative, MapReduce
* Declarative query hides the database implementation details behind and makes the langauge easy to understand. It is also easy for migration behind the scene. One good example is the CSS selector. If we use JavaScript to select DOM elements in the imperative fashion, it is very hard to let the imperative codes catch the changes.
* Imperative query allows higher optimizations such as ordering, aggregation, etc, but takes larger efforts to maintain and understand. It's also hard to parallize across multiple CPU cores/threads as it has to maintain the state during the imperative process. 
* MapReduce is a fashion between the declarative and imperative method. Map step is known as a collect step to collect/transform the elemment based on the dimension we are interested in and the reduce step is known as fold or inject which aggregates the transformed data in some manners.
  * The cons of this is that the map/reduce function needs to be a pure functions, which means they only use the data that is passe into as the input. However, within the function, it is still powerful because it can perform calculations, convert types, call library functions, etc.
