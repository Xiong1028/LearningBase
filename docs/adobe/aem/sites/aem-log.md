# AEM Log

```java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
```

## Log level

```mermaid
flowchart TB

a[Log Level] --> a1["Trace"] & a2["Debug"] & a3["Info"] & a4["Warn"] & a5["error"]
```
<em> &nbsp;&nbsp;&nbsp;&nbsp;=====  Only Log from choosen level to last level(error) will print ======> &nbsp;&nbsp;&nbsp;&nbsp;</em> 

## Log support in AEM
![Log Support](/assets/img/aem/log-support.png){width=400}


## Logging Writer
`/system/console/configMgr` >> `Apache Sling Logging Writer Configuration`

### Two patterns
![Log writter configure](/assets/img/aem/log-pattern.png){width=600}

![Log writter configure](/assets/img/aem/logger-writer-config.png){width=600}
