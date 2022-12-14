# Event Handling

## Event Handling Type in AEM
```mermaid
flowchart LR 

a["Event Handling"] --> b1["JCR Based Event Handling"] --- c1["The operation performed on node. e.g.add, remove, modify any node and properties in JCR"]
a --> b2["Resource Based Event Handling"] --- c2["Any event listening to JCR Based Event Handling API"] & c3["Apart from that, it can directly listen to any performation on resource \n which JCR Based Event Handling API cann't do. e.g. publishing any page or publishing any content"]
b2 --> c4[("OSGI API Based Event Handling")] & c5[("Sling API Based Event Handling")]
```

## Event Handling Types and Frameworks
![Event Handling Types and Frameworks](/assets/img/aem/event-handling-1.png)
>Note: The above event APIs except Sling JobManager/JobConsumer provides no status info.

### JCR Event Handling
- Event handling at JCR/Repository level.
-	An EventListener can be registered via the ObservationManager object.
-	Event listeners are notified asynchronously, and see events after they occur and the transaction is committed.
-	An event listener only sees events for which the session that registered it has sufficient access rights.


### Sling JobManager/JobConsumer

```mermaid
flowchart TB
subgraph one
	a1["EventHandler"] === a2["Listen for event"]
end
subgraph two
	b1["JobManager"] === b2["Create Job using JobManager"]
end
subgraph three
	c1["JobConsumer"] === c2["Create Job consumer using JobConsumer"]
end
one --> two --> |Job With Custom Topic| three
```
