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
![sling servlet](/assets/img/aem/sling-servlet-1.png)

<details>
<summary>Sevlet with OSGI DS 1.2 Demo</summary>
```java
@Component(
        service= {Servlet.class},
        property={
                "sling.servlet.methods="+ HttpConstants.METHOD_GET,
                SLING_SERVLET_METHODS+"="+HttpConstants.METHOD_POST,
                "sling.servlet.resourceTypes="+ "aemgeeks/components/structure/geeks-home",
                SLING_SERVLET_PATHS+"="+"/geeks/r5servlet",
                "sling.servlet.selectors=" + "geeks",
                "sling.servlet.selectors=" + "ds",
                SLING_SERVLET_EXTENSIONS+"="+"xml",
                "sling.servlet.extensions"+"="+"txt"
        })
public class GeeksServlet extends SlingAllMethodsServlet {
    @Override
    protected void doGet(final SlingHttpServletRequest req, final SlingHttpServletResponse resp) throws ServletException, IOException {
          ... 
    }

    @Override
    protected void doPost(SlingHttpServletRequest req, SlingHttpServletResponse resp)
          ... 
    }
}
```
</details>


### Sevlet with OSGI DS 1.4 Demo
![sling servlet ds1.4](/assets/img/aem/sling-servlet-2.png)

<details>
<summary>Sevlet with OSGI DS 1.4 Demo</summary>
```java
//Servlet By resourceType 
@Component(service = Servlet.class)
@SlingServletResourceTypes(
        methods = {HttpConstants.METHOD_GET,HttpConstants.METHOD_POST},
        resourceTypes = "aemgeeks/components/structure/page",
        selectors = {"geeks","test"},
        extensions = {"txt","xml"}
)
public class GeeksResourceTypesServlet extends SlingAllMethodsServlet {

    @Override
    protected void doGet(final SlingHttpServletRequest req,
                         final SlingHttpServletResponse resp) throws ServletException, IOException {
												 ...
    }
    @Override
    protected void doPost(SlingHttpServletRequest req, SlingHttpServletResponse resp)
            throws ServletException, IOException {
						 ...
		}
}
```
```java
//Servlet By Paths
@Component(service = Servlet.class)
@SlingServletPaths(
        value = {"/bin/pages","/geeks/pages"}
)
public class GeeksPathTypeServlet extends SlingAllMethodsServlet {

    @Override
    protected void doGet(final SlingHttpServletRequest req, final SlingHttpServletResponse resp) throws ServletException, IOException {
        ...    
    }

    @Override
    protected void doPost(SlingHttpServletRequest req, SlingHttpServletResponse resp)
            throws ServletException, IOException {
        ...
    }
}
```
</details>

#### ResourceType Sling Servlet Demo
![ResourceType Sling Servlet Demo](/assets/img/aem/sling-servlet-3.png)


#### Sling Servlet By ResourceType
> Note: The selectors and extensions must be used in servlets defined by resourceTypes if they are defined.
 
![ResourceType Sling Servlet in AEM](/assets/img/aem/resourceTypeServlet.png)


#### Sling Servlet By Paths
> Note: The path should be defined in `apache sling servlet/script resolver and error handler` of Sling Configuration.
> The selectors and extensions are not required in servlets defined by paths.

![Define path in Configuration](/assets/img/aem/servletByPath.png)

