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
