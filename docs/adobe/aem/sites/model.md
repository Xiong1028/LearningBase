# Sling Model

Sling Models are "pure" POJOs which maps Sling objects (resources, request objects etc.). Since Sling Models are annotation-driven Plain Old Java Objects (POJOs), annotations are used a lot. They allow you to map resource properties, assign default values, inject OSGi services and much more.

```mermaid
 flowchart LR
 a[POJO Java Class] --> b[Sling API] --> |annotation model| c(Sling Model) --> |UseClass| HTL

```

## Sling model in AEM
![sling model in AEM](/assets/img/aem/component-with-sling-model.png){width=800}
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>

## Component implementation
![Component implementation](/assets/img/aem/model-implementation.png){width=800}
<p><sup>- image from <a href="https://www.youtube.com/c/AEMGeeks" target="_blank">AEM GEEKS</a></sup></p>


## @Model() annotation
```java
@Model(
	adaptables = Resource.class
	adapters = InterfaceName.class
)


# `adaptables` defines which resource object can be adapted to and how the sling mode behave
# `adapters` - defined interface

```

### adaptables
```mermaid
flowchart LR
a[adaptables] --> a1[Resource.class] & a2[SlingHttpServletRequest.class] 

```


### annotations in fields
```mermaid
flowchart LR
a[annotations in fields] --> a1[Inject] --- a11[javax.inject.Inject]

```
