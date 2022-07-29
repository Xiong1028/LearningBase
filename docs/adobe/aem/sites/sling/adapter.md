# Apache Sling Adapters

```mermaid  
    flowchart LR
    a[Resource] -->b[<em>Interface</em>:Adaptable]
    c[ResourceResolver] -->b --> |adaptTo|a1[javax.jcr.Node<br>org.apache.sling.api.script.SlingScript<br>...] & c1[javax.jcr.Session<br>...]
```

## Interface Adaptable

```java
/**
 * Adapts the adaptable to another type.
 *
 * @param <AdapterType> The generic type to which this resource is adapted
 *            to
 * @param type The Class object of the target type, such as
 *            <code>javax.jcr.Node.class</code> or
 *            <code>java.io.File.class</code>
 * @return The adapter target or <code>null</code> if the resource cannot
 *         adapt to the requested type
 */
<AdapterType> AdapterType adaptTo(Class<AdapterType> type);
```

## How to check possible Adaptation?
- Go to `web console`
    - `/system/console/adapters`
    - `/system/console/status-adapters`