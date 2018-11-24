# DDD rules of thumb

### Consider hexagonal (onion) architecture

``` bash
-/ application
---/ handlers
-/ domain
---/ commands
-/ infrastructure
-/ presentation
-/ web
- context
- main
```

### Model small Aggregates

Big Aggregates greatly increase congestion which is very dangerous in optimistic concurrency control. They may feel necessary if an user action must be transactional but in truth most of those cases can be handled by eventual consistency using front-event technique.

### Model true invariants in consistency boundaries.
The primary purpose of each _Aggregate_ is to capture business invariants. If an invariant states that _a + b = c_ then the following _Aggregate_ is valid

``` java
class Aggregate {
    a, b, c
}
```
We cannot correctly reason on Aggregate design without applying transactional analysis. Properly designed Aggregate can be modified in any way required by the business with its invariants completely consistent within a single transaction and should not impose artificial constraints from false invariants.

Likewise, properly designed Bounded Context modifies only one Aggregate instance per transaction in all cases.

### Reference other Aggregates by their identity
Storing Aggregates within other Aggregates should be avoided as it imposes higher memory consumption and may be a temptation to modify the state of two Aggregates as a result of consuming a single event, which breaks a primary Aggregates rule (and may lead to inconsistency).

### Favour eventual consistency whenever possible
There is a practical way to support eventual consistency in a DDD model. An Aggregate command method publishes a Domain Event that is in time delivered to one or more asynchronous subscribers.

1. Original Multi-Aggregate Command
2. Command Handler
3. Corresponding Domain Event
4. Event Stream Listeners
5. Actions on Aggregates emitting further events
6. Refreshing the views

### Refer to identities in events rather than to the current values

Events should remain valid as they can never be changed. While the surname of a person can change, her identity won't. The derived views can always be rebuilt to correspond to the new name.

### Be careful about including domain services inside Aggregates

Even if using a domain service from within an aggregate is not conceptually a wrong thing as long as it is a part of the ubiquitous language, it should be avoided if the service needs to perform actions which may fail and / or have side effects. The _Aggregate_ behaviour would then be much more complex and unpredictable. It is better to do the orchestration in the application layer and model the action as a pure domain object passed to or retrieved from an Aggregate (which is good anyway).

### Leverage one of the views as internal cache

Rather than applying some caches on external dependencies required to properly assemble the views, have one view which define all the details and make other views consume data from it. Be careful to avoid effect before a cause phenomena.

### Abstract away dependencies to other bounded contexts

Use only the types fully meaningful to the domain. If there is an external User service but the service considers only certain type of Users (e.g. traders), wrap that service in a repository and define a respecitve type (e.g. Trader) mapping only relevant values to it in an infrastructure layer. 