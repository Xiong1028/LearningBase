# Sling Servlet

## Servlet types
```mermaid
flowchart LR

a["Sling Servlet"] ---- b1["resourceTypes"] & b2["paths"]
b1 --> c1["Servlet is registered to/with resource type and it is an absolute resource path."]
b1 --> c2["resource-bound servlet can be access controlled via JCR repository ACL"]
b1 --> c3["resource servlets binding mapping is transparent"]
b1 --> c4["resource servlets use methods, selectors and extenions"]
b2 --> d1["Servlet is registered to/wth path and it is an absolute path"]
b2 --> d2["path-bound servlets can not be access controlled using JCR repository ACL"]
b2 --> d3["Define path under which this servlet can be accessed as a resource"]
```

---

##  Writing Servlet
```mermaid
flowchart LR

a["Writing Servlet"] --> a1["OSGI DS 1.4 (R7)"] & a2["OSGI DS 1.2 (R5)"] & a3["Felix SCR"]
a1 --> a11["bnd-maven-plugin 4.0+"]
a2 --> a21["maven-bundle-plugin 3.0+"]
a3 --> a31["maven-scr-plugin"]
```

---

## Sling Servlet extends - interface
```mermaid
flowchart LR
a["Servlet extends"] --> |parent class| a1["SlingSafeMethodServlet"] & a2["SlingAllMethodsServlet"] 
a1 --> a11["Read Operation/Get"]
a2 --> a21["Read Operation/Get"] & a22["Write Operation/Post"]
```

### Sevlet with OSGI DS 1.2 Demo
![sling servlet](/assets/img/aem/sling-servlet-1.png){width=600}

<details>
<summary>Sevlet with OSGI DS 1.2 Demo</summary>
```java


```
</details>


### Sevlet with OSGI DS 1.4 Demo
![sling servlet ds1.4](/assets/img/aem/sling-servlet-2.png){width=600}

<details>
<summary>Sevlet with OSGI DS 1.4 Demo</summary>
```java


```
</details>

#### ResourceType Sling Servlet Demo
![ResourceType Sling Servlet Demo](/assets/img/aem/sling-servlet-3.png){width=600}
