# Microservices

1. Data systems (e.g. databases) amplify the data they hold. Microservices hide the data they hold.
2. Sharing data (data-in-the-inside) between microservices without a strategic solution is possible using:
![Sharing data-in-the-inside](https://www.confluent.io/wp-content/uploads/Screenshot-2016-12-08-20.57.47-1024x381.png)
3. Beware the cycle of data inadequacy, this is why a real data system is needed.
![The Cycle of Data Inadequacy](https://www.confluent.io/wp-content/uploads/image06-1024x681.png)
4. Distributed event log is a good compromise to address the data dichtomy problem. Data is shared but the operation on this shared data is decentralized and unique to the bounded context. This in makes the services event-driven. The service states are private and this is where the logic is.
![Share data via Immutable Streams](https://www.confluent.io/wp-content/uploads/image01-1024x613.png)
5. Centralized Stream of Events is a strategic solution to sharing data in Microservices.
   ![Centralized Stream of Events](https://www.confluent.io/wp-content/uploads/Screenshot-2016-12-08-21.03.20-1024x748.png)
6. Scalability concerns move away from individual services to the broker. The service will no longer be a bottleneck having to serve data-hungry downstream in a pool fashion.
7. Using a distributed event log new services can be just plugged in without having to do anything with services already in place. Historic data outside of the log retention period can be replayed if needed.
8. Centralize an immutable stream of facts. Decentralize the freedom to act, adopt and change.
9.  Services contribute to the facts but other services can present those facts in a variety of ways (read-only).
    ![Processing](https://www.confluent.io/wp-content/uploads/image14.png)
10. Events should be used to propagate and capture state changes whereas HTTP for request-response patterns.
11. Event sourcing combines messaging with persistence.
12. Kafka can be plugged in into existing infrastructure leveraging internal database logs (Change Data Capture)
    ![Kafka Connect](https://www.confluent.io/wp-content/uploads/Screenshot-2017-08-02-08.39.55-1024x865.png)
13. Successful Kafka architecture
    ![Kafka Architecture](https://www.confluent.io/wp-content/uploads/Screenshot-2017-11-09-12.34.26.png)
14. Statelessness come at a cost. In some workloads it is better to let services store some derived data in memory (no remote calls needed), for efficient operation - Stateful Streaming rather than Request-Resposne.
    ![Kafka Stateful Streaming](https://www.confluent.io/wp-content/uploads/request_response-1.png)