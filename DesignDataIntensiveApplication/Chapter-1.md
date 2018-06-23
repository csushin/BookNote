# Chapter 1

* Types of data system functionalities:
  * Data base: to store the data and find it later
  * Search/query: to allow users find data through various ways
  * Cache: to remember the result of an expensive operation
  * Stream processing: to handle user messages asynchronously
  * Batch processing: to periodically crunch a large amount of acumulated darta.

## Reliability

* Difference of fault and failures
  * Failure: Fail the entire system and cannot serve user's request
  * Fault: certain components are deviated from its specs. Faults from many components will cause the failure of the whole system.
  
## Scalability

* Describe the load
* Describe the performance
  * Latency and response time:
    * Latency: the waiting time of the queued request to be handeld by the service
    * Response time: the entire time that the clients can see the response of their request including the network roundtrip, etc. So it often doesn't make sense to analyze a specific request with large response time. We need to focus on the distribution of the response time.
      * Implementing percentile:
        * Becase we focus on the distribution of the response time, it doesn't make sense to do any level of aggregation or average. Instead, we can keep a list of response time within a time window, sort that list and get the percentile.
        
## Maintainability

## Evolvability
